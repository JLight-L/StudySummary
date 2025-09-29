# 晶体结构-CrystalStructure
## 周期性结构
晶体由无限重复排列的原子团构成
### 基元-Basis
#def 组成无限重复排列结构的单元，晶体由基元重复排列而成
### 晶格-Lattice
具体的晶格被称作[布拉伐格子](#布拉伐格子-BravaisLattice)
#def 晶体的抽象结构，即所有由基元抽象而成的几何点的集合（周期性点阵），可记为$\Lambda = \left\{ \vec{r} = n_1 \vec{a_1} + n_2 \vec{a_2} + n_3 \vec{a_3}, n_i \in \mathbb{Z} \right\}$
### 原生晶格矢量-PrimitiveLatticeVectors
#def $a_1,a_2,a_3$ ，**所有**晶格矢量可以描述为 $\vec{r}=\Sigma_{i=1}^3 n_i\vec{a_i},\ n_i\in \mathbb{Z}$
#property not unique
### 原胞-PrimitiveCell
最小的晶胞
#def 在原生晶格矢量作用下，可以无重叠无缺漏地铺满整个晶体的区域
#property not unique，所有取法的原胞体积相同
#prop 一个原胞内必定有且只有一个格点（一个基元）
#### Wigner-SeitzCells
一种特殊的原胞
#def 由选定格点和其它周围所有格点连线的垂直平分线围成，
即 $\Gamma = \left\{ \vec{x} : |\vec{x}| < |\vec{x} - \vec{r}|,\ \forall \vec{r} \in \Lambda\ \text{ s.t. } \vec{r} \neq \vec{0} \right\}$
### 布拉伐格子-BravaisLattice
#def 对某种具体的晶格的统称
#prop 一种[晶体平移群](群论-GroupTheory.md#晶体平移群)对应一个布拉伐格子
#### ……
# 晶体衍射-DiffractionOfWavesByCrystals
## 布拉格定律-TheBraggLaw
每个晶格平面对光线进行镜面反射，反射率与基元组成有关。在某些角度上会出现干涉相长的情况
## ……
## 衍射条件
#prop 一组倒格矢决定可能存在的X射线反射
……
### 劳厄方程-LaueEquations
给出晶体衍射条件的另一种形式
几何意义

## 结构因子
给出散射振幅
# 倒易空间-ReciprocalSpace
由傅里叶变换联系实空间周期函数与倒空间
## 倒格矢（倒易晶格矢量）-ReciprocalLatticeVector
#def 倒格矢 $G$：
$$\begin{align}
&\vec{G} = v_1\vec{b_1} + v_2\vec{b_2} + v_3\vec{b_3}\\
&v_1,v_2,v_3\in \mathbb{Z},\\
&\vec{b_i} \cdot \vec{a_j} = 2\pi \delta_{ij}
\end{align}$$
其中 $a_i$ 为晶格基矢， $b_i$ 取为 $2\pi\frac{\vec{a_{i+1}}\times a_{i+2}}{V},\ where\ V = \vec{a_1}\cdot \vec{a_2} \times \vec{a_3}$
#prop 空间周期函数 $n(r)=\Sigma n_G exp(i\vec{G}\cdot \vec{r})$ ，满足 $n(r)=n(r+T)$
## 倒格子
## 布里渊区-BrillouinZone
可以给出所有可能的散射波矢
#important 
#def 倒空间中的[Wigner-Seitz元胞](#Wigner-SeitzPrimitiveCell)，倒格矢见[倒格矢（倒易晶格矢量）-ReciprocalLatticeVector](#倒格矢（倒易晶格矢量）-ReciprocalLatticeVector)
### 第一布里渊区-TheFirstBrillouinZone
……
# 晶体的结合-CrystalBinding
## 内聚能
吸引相互作用
排斥相互作用-RepulsiveInteraction
## 不同类型晶体
### 惰性气体晶体
#### 诱导偶极相互作用
范德瓦尔斯-伦敦相互作用（Van der Waals-London Interaction）
### 离子晶体
#### 静电相互作用
### 共价晶体
### 金属晶体
见[自由电子气](#自由电子气-FreeElectronGas)
## 氢键
## 弹性应变
### ……
# 声子-Phonons
#def 晶格振动的量子化单位
声子运动=>振动传播
$\omega\sim k$ 关系（色散关系）
$k$ 的取值
## 弹性波
### 单原子原胞（基元）
#### 色散关系
横和纵
### 多原子原胞（基元）
#### 色散关系
横和纵
光学支和声学支
## 声子的散射
### ……
## 声子的热学性质
### 晶体比热容-LatticeHeatCapacity
比热容通常指的是定容热容 $C_V=\left(\frac{\partial U}{\partial T}\right)_V$
#def 声子对比热容的贡献
#denote $C_{lat}$
### 全同谐振子的分布
普朗克分布？
……
#### 态密度
……
### ……
## 非谐项
三次及以上
# 自由电子气-FreeElectronGas
## 费米-狄拉克分布
基于量子力学，满足泡利不相容
$f(\epsilon) = \frac{1}{e^{(\epsilon-\mu)/k_BT}+1}$，其中 $\mu$ 为化学势，在绝对零度下等于[费米能](#^1ec487)
## 三维自由电子气模型
#def 所有电子不受外界电场和相互作用影响
- 能级（由波矢 $\vec{k}$ 标记） $\epsilon_\vec{k} = \frac{\hbar^2}{2m} k^2$
- 费米能 $\epsilon_F = \frac{\hbar^2}{2m} k_F^2$ ，费米温度 $T_F = \frac{\epsilon_F}{k_B}$ ^1ec487
- $k_F = \left(3\pi^2\rho\right)^{1/3},\ \rho = N/V$
- 态密度 $D(\epsilon) = \frac{dN(\epsilon)}{d\epsilon} = \frac{3N(\epsilon)}{2V} = \frac{V}{2\pi^2}\left(\frac{2m}{\hbar^2}\right)^{3/2}\epsilon^{1/2}$
## 电子气比热容
温度升高后，仅能量最高的部分电子（能量在 $\epsilon_F$ 附近*大概* $k_BT$ 的电子）获得能量 $k_BT$ 
当 $k_BT \ll \epsilon_F$ 时，忽略化学势 $\mu$ 的影响：
$$C_el = \frac{1}{2}\pi^2N\frac{k_BT}{\epsilon_F} = \frac{1}{2}\pi^2Nk_B\frac{T}{T_F}$$
> 金属的比热容通常由电子和声子的贡献之和。
## 电导率
与电子输运相关
$\sigma = \frac{ne^2\tau}{m}$，其中 $\tau$ 为平均碰撞间隔时间（通常与杂质、原子、其他电子、声子等等碰撞）
## 霍尔效应
## 导热性
$……$
### 魏德曼-弗兰兹定律 Wiedemann-Franz Law
#prop 温度不太低时，$L = \frac{K}{\sigma T}$ 与 $n, m$ 无关。 $L = \frac{\pi^2}{3}\left(\frac{k_B}{e}\right)^2$ 
# 能带-EnergyBands
## Deep Seek的讲解
#ai 
能带理论（Band Theory）是固体物理学中描述晶体中电子运动的核心理论，它弥补了自由电子气模型的不足，通过考虑晶体中原子的**周期性势场**对电子的影响，解释了导体、半导体和绝缘体的区别，以及材料的电学、光学等性质。以下是来自Deep Seek的能带理论的详细讲解：

---

### **1. 能带理论的基本思想**
- **周期性势场假设**：晶体中原子排列具有周期性，电子在周期性势场 $V(\mathbf{r} + \mathbf{R}) = V(\mathbf{r})$ 中运动（ $\mathbf{R}$ 是晶格矢量）。
- **单电子近似**：忽略电子间的相互作用，但考虑电子与晶格势场的相互作用。
- **量子力学描述**：电子波函数满足**布洛赫定理**（Bloch's Theorem），能量形成**能带**（Energy Bands）和**禁带**（Band Gaps）。

---

### **2. 布洛赫定理（Bloch's Theorem）**
布洛赫定理是能带理论的基础，它指出：  
在周期性势场中，电子的波函数可以表示为平面波与周期性调幅函数的乘积：  
$$\psi_{n\mathbf{k}}(\mathbf{r}) = e^{i\mathbf{k} \cdot \mathbf{r}} u_{n\mathbf{k}}(\mathbf{r})$$
其中：
- $u_{n\mathbf{k}}(\mathbf{r} + \mathbf{R}) = u_{n\mathbf{k}}(\mathbf{r})$ 是周期性函数，与晶格周期性相同。
- $\mathbf{k}$ 是**波矢**，取值范围在第一布里渊区（First Brillouin Zone）。
- $n$ 是能带索引（如导带、价带）。

---

### **3. 能带的形成**
- **原子轨道→分子轨道→能带**：  
  当孤立原子形成晶体时，原子轨道（如s、p轨道）会因原子间的相互作用发生简并分裂，扩展为**能带**。
  - 例如：1个原子的s轨道能级 → N个原子的晶体中形成包含N个能级的s能带（N极大，近似连续）。

- **能带与禁带**：
  - **允带（Allowed Band）**：电子可以存在的能量范围。
  - **禁带（Forbidden Band Gap）**：能量间隔，电子无法占据。

---

### **4. 能带结构的计算**
通过求解周期性势场下的薛定谔方程，得到电子的能量 \( E(\mathbf{k}) \) 与波矢 \( \mathbf{k} \) 的关系，称为**能带结构**。常用方法包括：
1. [**近自由电子近似（Nearly Free Electron Approximation）**](#近自由电子模型)：  
   - 将晶格势场视为微扰，修正自由电子气的能带。
   - 在布里渊区边界出现**能隙**（Bragg反射导致）。
2. **紧束缚近似（Tight-Binding Approximation）**：  
   - 假设电子主要局域在原子附近，原子轨道线性组合形成能带。
   - 适用于半导体和绝缘体。
3. **密度泛函理论（DFT）**：  
   - 现代计算材料学的核心方法，通过电子密度计算能带结构。

---

### **5. 导体、半导体与绝缘体的区别**
能带理论通过**费米能级位置**和**能带填充情况**解释材料的导电性：
- **导体（金属）**：  
  - 价带部分填充，或导带与价带重叠（无禁带）。
  - 费米能级位于允带内，电子可轻易跃迁到邻近能级，形成电流。
  - 例如：Cu、Ag的导带未填满。

- **半导体**：  
  - 禁带宽度较小（约0.1-2 eV），温度升高时，电子可从价带跃迁到导带。
  - 费米能级位于禁带中央附近。
  - 例如：Si（禁带1.1 eV）、GaAs（1.4 eV）。

- **绝缘体**：  
  - 禁带宽度大（>5 eV），电子难以跃迁。
  - 费米能级位于价带顶，导带空。
  - 例如：金刚石（禁带5.5 eV）。

---

### **6. 核心概念**
#### **(1) 有效质量（Effective Mass）**  
电子在晶体中运动时，受晶格势场影响，等效质量 $m^*$ 定义为：  
$$
\frac{1}{m^*} = \frac{1}{\hbar^2} \frac{d^2 E}{dk^2}
$$
- $m^* > 0$：电子行为类似自由电子。
- $m^* < 0$：空穴（Hole）行为。

#### **(2) 直接带隙与间接带隙**  
- **直接带隙**：导带最低点与价带最高点在相同 $\mathbf{k}$ 处（如GaAs），电子跃迁无需声子参与，适合发光器件。
- **间接带隙**：导带最低点与价带最高点 $\mathbf{k}$ 不同（如Si），跃迁需声子协助，发光效率低。

#### **(3) 掺杂与载流子**  
- **n型半导体**：掺入施主杂质（如P掺入Si），提供额外电子。
- **p型半导体**：掺入受主杂质（如B掺入Si），产生空穴。

---

### **7. 能带理论的应用**
1. **半导体器件**：晶体管、二极管、太阳能电池的设计基于能带结构。
2. **光电效应**：光激发电子跨越禁带（如光电探测器）。
3. **超晶格与量子阱**：人工设计能带结构，用于激光器和量子计算。
4. **拓扑绝缘体**：新型材料，体态绝缘，表面态导电（拓扑能带理论）。

---

### **8. 能带理论的局限性**
- **忽略电子关联效应**：强关联材料（如高温超导体）需更复杂的模型。
- **非晶态材料**：周期性势场假设失效，需用其他方法（如迁移率边理论）。
- **动态晶格效应**：未完全考虑电子-声子耦合（需结合多体理论）。

---

### **总结**
能带理论通过引入晶格的周期性势场，成功解释了固体的导电性差异和量子行为，成为现代半导体物理、材料科学的基石。从自由电子气模型到能带理论的发展，体现了从简化模型到更真实物理图像的科学进步。后续的**第一性原理计算**（如DFT）和**拓扑能带理论**进一步扩展了其应用范围。

如果需要具体能带结构图例（如Si、GaAs）或深入讨论某一概念（如拓扑绝缘体），可以继续探讨！

## 近自由电子模型
周期势场作为自由电子模型的微扰项，使能级中出现**能隙**
### 微扰对称性分析-一维情况
**哈密顿算符群**：
- 自由电子： $P_H = \left\{\{R|\mathbf{t}\}|\ R \in \{E,I\},\ \mathbf{t}\in \mathbb{R}\right\}$ 
- 近自由电子：$P_H = \left\{\left\{R|\mathbf{t}\right\}|\ R \in \{E,I\},\ \mathbf{t}=na,n\in \mathbb{Z}\right\}$

波函数由波矢 $\mathbf{k}$ 标记，见[布洛赫定理（Bloch's Theorem）](#**2.%20布洛赫定理（Bloch's%20Theorem）**)
$\mathbf{k}$ 为布里渊区中的波矢，**倒格矢**：
- 自由电子：$\mathbf{G} = \pm\infty$，简单布里渊区为 $k\in\left[0,\infty\right]$
- 近自由电子：$\mathbf{G}_m = m\mathbf{b},\ b = 2\pi/a$，简单布里渊区为 $k \in \left[0,b\right]$


### 微扰计算
……暂略
>[!note] 物理解释
>周期性势场导致电子波函数中出现散射波，散射波波矢 $\mathbf{k'}$ 满足：
>$$\mathbf{k'}=\mathbf{k}+\mathbf{G}$$
>其中，$\mathbf{G}$ 为倒格矢。
>
>
>周期性微扰势场带来的微扰项 $E'$ 在 $2\mathbf{k}=\mathbf{G}$ 时最明显，

## Summary
电子能量由波矢 $k$ 决定，$E$ 是关于 $k$ 的单值函数，其中自变量 $k$ 是
