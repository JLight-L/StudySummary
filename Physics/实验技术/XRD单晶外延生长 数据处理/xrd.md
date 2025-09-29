```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import find_peaks
from matplotlib.ticker import AutoMinorLocator

class XRDData:
    def __init__(self, name, data, lam, d_substrate):
        self.lam = lam
        self.d_substrate = d_substrate

        self.name = name
        self.theta2 = np.array(data[:, 0])  # 2*theta
        self.intensity = np.array(data[:, 1])
        self.intensity_for_peaks = self.intensity  # 可修改来方便找峰
        self.log_intensity = np.log(np.maximum(self.intensity, 1))

        # 找峰参数
        self.prominence=30
        self.rel_height=0.5
        self.width=1.0
        self.distance=40

        # n/d 分析
        self.peaks_idx = None  # 为峰顶在原始信号 self.intensity 中的位置索引
        self.peaks_2theta = None  # calc after ``self.peaks_idx``
        self.raw_ndinv_arr = None  # ndinv : n/d
        self.sub_ndinv_arr = None  # calc after ``self.raw_ndinv_arr``
        self.kept_ndinv_arr = None  # 减去衬底峰附近的信号
        self.kept_idx = None  # calc after ``self.kept_ndinv_arr``
        self.filtered_ndinv_arr = None  # 一次拟合后过滤掉杂峰
        self.filtered_idx = None  # calc after ``self.filtered_ndinv_arr``

        # c 拟合
        self.cinv_grid = None
        self.RMS = None
        self.best_cinv_idx = None
        self.best_cinv = None  # calc after ``self.best_cinv_idx``
        self.best_cinv_arr = None  # calc after ``self.best_cinv_idx``
        self.best_RMS = None  # calc after ``self.best_cinv_idx``

    def _show_loginten_2theta(self,data=False, with_peaks=None,
                              peaks_vlines=False, raw_peaks=None, sub_peaks=None, kept_peaks=None, filtered_peaks=None, predicted_peaks=None):
        assert data is not peaks_vlines
        plt.figure(figsize=(12, 4))
        if data:
            x_data = self.theta2
            x_label = "2θ"
        else:
            x_data = self.raw_ndinv_arr
            x_label = "n/d(1/Å)"
        plt.xlabel(x_label)
        plt.ylabel("Intensity (log)")
        plt.xticks(np.linspace(min(x_data), max(x_data), 10))
        
        if data:
            plt.plot(self.theta2, self.log_intensity, marker='.', markersize=0.2)
            if with_peaks:
                plt.scatter(self.peaks_2theta, self.log_intensity[self.peaks_idx], color='red', s=40, edgecolor='lightgray', linewidth=0.5)    # 标记峰的位置
        if peaks_vlines:
            if raw_peaks:
                plt.vlines(self.raw_ndinv_arr, ymin=0, ymax=self.log_intensity[self.peaks_idx],
                   color='r', linestyle='--', linewidth=1, label='raw')
            if sub_peaks:
                plt.vlines(self.sub_ndinv_arr, ymin=0, ymax=plt.ylim()[1], color='b', linestyle='--', linewidth=0.6, label='substrate')
            if kept_peaks:
                plt.vlines(self.kept_ndinv_arr, ymin=0, ymax=self.log_intensity[self.peaks_idx[self.kept_idx]],
                   color='r', linestyle='--', linewidth=1, label='kept')
            if filtered_peaks:
                plt.vlines(self.filtered_ndinv_arr, ymin=0, ymax=self.log_intensity[self.peaks_idx[self.kept_idx[self.filtered_idx]]],
                   color='r', linestyle='--', linewidth=1, label='kept')
            if predicted_peaks:
                max_raw_ndinv = self.raw_ndinv_arr.max()
                n_max = int(np.ceil(max_raw_ndinv / self.best_cinv))
                pred_ndinv_arr = np.arange(1, n_max + 1) * self.best_cinv
                plt.vlines(pred_ndinv_arr, ymin=0, ymax=plt.ylim()[1], color='orange', linestyle='-', linewidth=0.9, label='predicted')
            plt.legend()
        
        ax = plt.gca()
        ax.xaxis.set_minor_locator(AutoMinorLocator(5))
        plt.grid(True, which='both', linestyle='--', linewidth=0.5, alpha=0.7)
        plt.title(self.name);plt.tight_layout(); plt.show()

    def show_raw_data(self, with_peaks=False):
        self._show_loginten_2theta(data=True, with_peaks=with_peaks)

    def show_peaks(self,raw=False, sub=False, kept=False, filtered=False, predicted=False):
        if filtered and self.filtered_ndinv_arr is None:
            self._show_loginten_2theta(peaks_vlines=True,raw_peaks=raw,sub_peaks=sub,
                                   kept_peaks=True,filtered_peaks=False,predicted_peaks=predicted)
            return
        self._show_loginten_2theta(peaks_vlines=True,raw_peaks=raw,sub_peaks=sub,
                                   kept_peaks=kept,filtered_peaks=filtered,predicted_peaks=predicted)

    def show_RMS_cinv(self):
        plt.figure(figsize=(9,3.5))
        plt.plot(self.cinv_grid, self.RMS, label="RMS_all")
        plt.axvline(self.best_cinv, color="r", linestyle="--")
        plt.text(self.best_cinv + (self.cinv_grid[-1]-self.cinv_grid[0])/50, self.best_RMS,
                 f"best 1/c ≈ {self.best_cinv:.4f} Å", color="r", va="bottom")
        plt.xlabel("1/c (1/Å)"); plt.ylabel("RMS residual (1/Å)")
        plt.legend(); plt.tight_layout(); plt.show()

    def set_peak_calc_param(self,
                            prominence=30,
                            rel_height=0.5,
                            width=1.0,
                            distance=40):
        """
    
        基于 ``scipy.signal.find_peaks`` 实现，先按 *prominence* 保证峰足够凸出，
        再用 *distance* 去除过密峰，最后通过 *width* 与 *rel_height* 过滤尖刺/窄峰。
    
        Parameters
        ----------
        prominence : float, optional
            最小 prominence（凸出度），默认 40。
        rel_height : float, optional
            计算宽度时使用的相对高度比例，默认 0.5。
        width : float, optional
            允许的最小宽度（样本点数），默认 1.0。
        distance : int, optional
            两峰之间最小索引间隔，默认 40。
        """
        self.prominence = prominence
        self.rel_height = rel_height
        self.width = width
        self.distance = distance
        print(f"Peak calculation parameters updated:\n"
              f"  prominence : {prominence}\n"
              f"  rel_height : {rel_height}\n"
              f"  width      : {width}\n"
              f"  distance   : {distance}")
    
    def calc_peaks(self):
        """
        在质谱 (或色谱) 信号中检测峰，并把峰顶索引保存到 ``self.peaks``。
        """
        print(f"Peak calculation parameters:\n"
              f"  prominence : {self.prominence}\n"
              f"  rel_height : {self.rel_height}\n"
              f"  width      : {self.width}\n"
              f"  distance   : {self.distance}")
        peaks, props = find_peaks(
            self.intensity_for_peaks,
            height=None,
            threshold=0,
            distance=self.distance,
            prominence=self.prominence,
            width=self.width,
            wlen=None,
            rel_height=self.rel_height,
            plateau_size=None,
        )
        self.peaks_idx = peaks
        self.peaks_2theta = self.theta2[self.peaks_idx]
        print(self.peaks_2theta)
        
    def get_peak_near_x(self, x):
        """
        返回横坐标（2θ）离 x 最近的一个峰的索引
        """
        if self.peaks_idx is None:
            raise RuntimeError("Please run calc_peaks() first.")
        # 找到最近峰
        nearest_idx = np.argmin(np.abs(self.peaks_2theta - x))
        return nearest_idx
        
    def remove_peak(self, *idxs):
        """按从左到右的顺序索引，删除对应峰；
        索引从1开始"""
        if self.peaks_idx is None:
            raise RuntimeError("Please run calc_peaks() first.")
        order = np.argsort(self.peaks_2theta)  # 从左到右排列，避免原本处在无序状态
        del_idxs = []
        for idx in idxs:
            if idx > 0:
                idx -= 1
            true_idx = order[idx]       # 在 self.peaks_idx 里的位置
            del_idxs.append(true_idx)
        # 删除
        self.peaks_idx = np.delete(self.peaks_idx, del_idxs)
        self.peaks_2theta = np.delete(self.peaks_2theta, del_idxs)

    def add_peak_near_x(self, x, tol=0.1):
        """
        在 x±tol 范围内寻找强度最高的数据点，将其加入峰列表
        """
        if self.peaks_idx is None:
            raise RuntimeError("Please run calc_peaks() first.")
        mask = np.abs(self.theta2 - x) <= tol
        if not np.any(mask):
            print(f"No data point found within ±{tol}° of {x}")
            return
        # 强度最高的点
        idx_new = np.argmax(self.intensity * mask)   # mask 外强度被置 0
        # 避免重复
        if idx_new in self.peaks_idx:
            print(f"Point at 2θ={self.theta2[idx_new]:.3f}° already in peak list.")
            return
        # 插入并维持 2θ 有序（方便后面人眼检查）
        insert_pos = np.searchsorted(self.peaks_2theta, self.theta2[idx_new])
        self.peaks_idx = np.insert(self.peaks_idx, insert_pos, idx_new)
        self.peaks_2theta = np.insert(self.peaks_2theta, insert_pos, self.theta2[idx_new])

    def erase_peak(self, *idxs):
        """
        把原数据里某个峰“抹平”
        """
        for idx in idxs:
            if idx > 0:
                idx -= 1
            if self.peaks_idx is None:
                raise RuntimeError("Please run calc_peaks() first.")
            order = np.argsort(self.peaks_2theta)          # 从左到右
            erase_idx = order[idx]
            # 对应到原始数据里的索引
            idx_in_raw = self.peaks_idx[erase_idx]
            # 修改原始强度
            self.intensity_for_peaks[idx_in_raw] = (self.intensity_for_peaks[idx_in_raw+1]-self.intensity_for_peaks[idx_in_raw-1])/2

    def unerase_peak(self):
        self.intensity_for_peaks = self.intensity
    
    def change_2theta_to_ndinv(self):
        """把 2θ 峰位转成 n/d 值，并生成衬底对应的 n/d 等差序列。"""
        self.raw_ndinv_arr = 2 * np.sin(np.deg2rad(self.peaks_2theta / 2)) / self.lam
        dinv_sub = 1/self.d_substrate
        max_raw_ndinv = self.raw_ndinv_arr.max()
        n_max = int(np.ceil(max_raw_ndinv / dinv_sub))
        self.sub_ndinv_arr = np.arange(1, n_max + 1) * dinv_sub

    def remove_substrate_peaks(self,tol=0.015):
        """:param tol 与衬底峰的最小距离"""
        distances = np.abs(self.raw_ndinv_arr[:, np.newaxis] - self.sub_ndinv_arr)
        to_remove = np.any(distances <= tol, axis=1)
        self.kept_ndinv_arr = self.raw_ndinv_arr[~to_remove]
        self.kept_idx = np.where(~to_remove)[0]  # 使用整数索引

    def calc_residual_for_cinv(self,
                               cinv_range: tuple | None = None,
                               step: float = 0.0001,
                               Lmax: int | None = None):
        """
        对当前 self.kept_ndinv_arr 做 1/c 网格扫描，计算 RMS 残差曲线。
        结果保存在 self.cinv_grid / self.RMS / self.best_cinv_idx / self.best_cinv / self.best_RMS
        """
        if self.filtered_ndinv_arr is None:
            dinv = self.kept_ndinv_arr
            # 权重
            weight = self.log_intensity[self.peaks_idx[self.kept_idx]]
        else:
            dinv = self.filtered_ndinv_arr
            # 权重
            weight = self.log_intensity[self.peaks_idx[self.kept_idx[self.filtered_idx]]]
        if dinv.size == 0:
            raise ValueError("kept_ndinv_arr 为空，需先执行 remove_substrate_peaks。")

        if cinv_range is None:               # 自动范围
            if self.cinv_grid is None:
            # --- 1. 生成 1/c 扫描网格 ---
                min_delta = np.min(np.diff(np.sort(dinv)))
                cinv_range = (min_delta / 2, min_delta * 10)
                print(f'Use 1/c range:{cinv_range}')
                self.cinv_grid = np.arange(cinv_range[0], cinv_range[1] + step / 2, step)
        else:
            self.cinv_grid = np.arange(cinv_range[0], cinv_range[1] + step / 2, step)
            
        if Lmax is None:                     # 自动阶数上限
            Lmax = min(40, int(np.ceil(np.max(dinv) / self.cinv_grid[0])))
        
        # --- 3. 计算每个 1/c 的加权 RMS ---
        RMS_all = np.empty_like(self.cinv_grid)
        for k, cinv in enumerate(self.cinv_grid):
            l = np.clip(np.rint(dinv / cinv).astype(int), 1, Lmax)
            resid = np.abs(dinv / l - cinv)              # 核心残差
            RMS_all[k] = np.sqrt(np.sum(weight * resid ** 2) / np.sum(weight))

        # --- 3. 保存结果到类属性 ---
        self.RMS = RMS_all
        # 自动选取最小残差点
        self.calc_best_cinv()

    def filter_with_best_cinv(self, tol=0.02):
        distances = np.abs(self.kept_ndinv_arr[:, np.newaxis] - self.best_cinv_arr)
        in_tol = np.any(distances <= tol, axis=1)
        self.filtered_ndinv_arr = self.kept_ndinv_arr[in_tol]
        self.filtered_idx = np.where(in_tol)[0]  # 使用整数索引

    def calc_best_cinv(self,cinv_range=None):
        if cinv_range is None:
            # 自动选取最小残差点
            self.best_cinv_idx = int(np.argmin(self.RMS))
        else:
            # 局部区间最小
            mask = (self.cinv_grid >= cinv_range[0]) & (self.cinv_grid <= cinv_range[1])
            if not np.any(mask):
                raise ValueError("给定的 cinv_range 与扫描网格无交集！")
    
            idx_local = int(np.argmin(self.RMS[mask]))  # 在掩码内的索引
            # 转回原始网格索引
            self.best_cinv_idx = int(np.where(mask)[0][idx_local])
        self.best_cinv = float(self.cinv_grid[self.best_cinv_idx])
        self.best_RMS = float(self.RMS[self.best_cinv_idx])
        max_ndinv = self.kept_ndinv_arr.max()
        n_max = int(np.ceil(max_ndinv / self.best_cinv))
        self.best_cinv_arr = np.arange(1, n_max + 1) * self.best_cinv

    @property
    def c(self):
        return 1/self.best_cinv
```

