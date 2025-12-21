# 《The affine and Euclidean normalizers of the subperiodic groups》文档解读总结

## 一、文档基础信息



| 项目   | 内容                                                                                                    |
| ---- | ----------------------------------------------------------------------------------------------------- |
| 论文标题 | The affine and Euclidean normalizers of the subperiodic groups（亚周期群的仿射正规化子与欧几里得正规化子）                  |
| 作者   | Brian Kevin VanLeeuwen、Pedro Valentı́n De Jesu´s、Daniel B. Litvin、Venkatraman Gopalana                |
| 作者单位 | a 美国宾夕法尼亚州立大学材料科学与工程系；b 美国宾夕法尼亚州立大学 Eberly 科学学院物理系                                                    |
| 发表期刊 | Acta Crystallographica Section A: Foundations and Advances                                            |
| 发表时间 | 2015 年                                                                                                |
| DOI  | 10.1107/S2053273314024395                                                                             |
| 关键词  | 亚周期群（subperiodic groups）、正规化子（normalizers）、仿射正规化子（affine normalizers）、欧几里得正规化子（Euclidean normalizers） |

## 二、研究背景与动机



1. **正规化子概念**

* 非正式定义：正规化子可理解为 “对称模式的对称性”，是将对称群映射到自身的变换集合。例如，点群 222 的正交正规化子群是 m$\overline{3}$m，因为绕其二重轴的 90° 旋转、垂直于二重轴平面的镜像等操作均不改变 222 群。

* 正式定义：给定群 S 和其子群 G，G 在 S 中的正规化子群$N_{S}(G)$是 S 中满足$G = sGs^{-1}$（s∈S）的所有元素 s 构成的子群，即$N_{S}(G)=\{s \in S: G = sGs^{-1}\}$，无需群 G 中每个元素 g 满足$g = sgs^{-1}$，只需群 G 整体满足该等式。

1. **相关群定义**

* 仿射变换群（A）：由线性变换和平移构成，线性部分无需保距。

* 欧几里得运动群（E）：由保距线性变换和平移构成，是仿射变换群的子集（$E \subset A$）。

* 亚周期群：包含饰带群（frieze groups）、杆群（rod groups）和层群（layer groups），是介于点群（0 个周期维度）和空间群（3 个周期维度）之间的对称群，周期维度 p 满足 0 < p < d（d 为空间总维度）。

1. **研究动机**

* 此前研究建议扩展双反对称亚周期群的列表，但因双反对称亚周期群类型未知，且 VanLeeuwen 等人（2014）提出的评估真仿射等价性方法需用到仿射正规化子，故开展本研究以推导亚周期群的仿射正规化子。

* 虽欧几里得正规化子对上述方法非必需，但具有一定研究价值，因此也将结果扩展至欧几里得正规化子。

## 三、核心理论与方法

### （一）亚周期群的平移子群仿射正规化子



1. **基本关系推导**

* 欧几里得运动群中的群 G（含平移子群$\Lambda$）满足：若 s∈$N_{A}(G)$（G 的仿射正规化子），则 s∈$N_{A}(\Lambda)$（$\Lambda$的仿射正规化子），即$N_{A}(G) \subset N_{A}(\Lambda)$。这是因为仿射变换共轭纯平移仍为纯平移，$G = sGs^{-1}$可推出$\Lambda = s\Lambda s^{-1}$。

* 平移子群$\Lambda$的定义：$\Lambda \equiv \{ \{1|t\} \in G \}$，其中 {1|t} 表示线性部分为单位矩阵、平移向量为 t 的仿射变换（Seitz 符号）。

1.  $N_{A}(\Lambda)$ **的矩阵形式**

* 基于广义原始基，$N_{A}(\Lambda)$中的元素用增广矩阵表示，形式为$\left\{ \begin{array}{cc} n & r_{\|} \\ 0 & r_{\perp} \end{array} | x \right\}$，各参数约束如下：


  * n：p×p 整数子矩阵，行列式$|n| = \pm 1$（保证亚周期单胞体积守恒）。

  * $r_{\|}$：p×(d-p) 实矩阵。

  * $r_{\perp}$：(d-p)×(d-p) 实矩阵，行列式$|r_{\perp}| \neq 0$（保证矩阵可逆）。

  * x：d 维实平移向量。

1. **不同亚周期群的** $N_{A}(\Lambda)$ **具体形式**
    1. 饰带群（d=2, p=1）
    
    $$
    N_A(\Lambda) = \left\{
    \left( \begin{array}{cc|c}
    \pm 1 & r_{12} & x_1 \\
    0 & r_{22} & x_2
    \end{array} \right)
    : \ r_{22} \neq 0,\ r_{ij}, x_i \in \mathbb{R}
    \right\}.
    $$
    
    2. 杆群（d=3, p=1，平移沿 \[001\]）
    
    $$
    N_A(\Lambda) = \left\{
    \left( \begin{array}{ccc|c}
    r_{11} & r_{12} & 0 & x_1 \\
    r_{21} & r_{22} & 0 & x_2 \\
    r_{31} & r_{32} & \pm 1 & x_3
    \end{array} \right)
    : \ \det\begin{pmatrix} r_{11} & r_{12} \\ r_{21} & r_{22} \end{pmatrix} \neq 0,\ r_{ij}, x_i \in \mathbb{R}
    \right\}.
    $$
    
    3. 层群（d=3, p=2）
    
    $$
    N_A(\Lambda) = \left\{
    \left( \begin{array}{ccc|c}
    n_{11} & n_{12} & r_{13} & x_1 \\
    n_{21} & n_{22} & r_{23} & x_2 \\
    0 & 0 & r_{33} & x_3
    \end{array} \right)
    : \ \det\begin{pmatrix} n_{11} & n_{12} \\ n_{21} & n_{22} \end{pmatrix} = \pm 1,\ r_{33} \neq 0,\ r_{ij}, x_i \in \mathbb{R},\ n_{ij} \in \mathbb{Z}
    \right\}.
    $$

### （二）亚周期群的仿射正规化子



1. **核心思路**

* 将群 G 按平移子群$\Lambda$分解为陪集：$G/\Lambda = \{g_{1}\Lambda, g_{2}\Lambda, ..., g_{i}\Lambda\}$（i 为 G 的点群大小，有限）。

* 仿射变换 s∈$N_{A}(G)$的充要条件：s 对陪集的共轭作用是$G/\Lambda$的自同构（$\sigma \in Aut(G/\Lambda)$），即$(sg_{1}s^{-1}\Lambda, sg_{2}s^{-1}\Lambda, ..., sg_{i}s^{-1}\Lambda) = \sigma(g_{1}\Lambda, g_{2}\Lambda, ..., g_{i}\Lambda)$。

1. **求解步骤**


   1. 将 G 分解为关于$\Lambda$的有限陪集集合。

   2. 分析$N_{A}(\Lambda)$中元素对这些陪集的置换方式。

   3. 求解同时属于$N_{A}(\Lambda)$和$N_{A}(G)$的元素，得到$N_{A}(G)$。

4. **示例：层群 L23（pmm2）的** $N_{E}(G)$ 

* $G/\Lambda = \{ \{1|0\}\Lambda, \{2_{001}|0\}\Lambda, \{m_{100}|0\}\Lambda, \{m_{010}|0\}\Lambda \}$，仅需考虑恒等置换和交换$\{m_{100}|0\}\Lambda$与$\{m_{010}|0\}\Lambda$的置换。

* 最终$N_{A}(pmm2)$的矩阵形式：$\left\{ \left\{ \begin{array}{ccccc} \pm 1 & 0 & 0 & x_{1}/2 \\ 0 & \pm 1 & 0 & x_{2}/2 \\ 0 & 0 & r_{33} & x_{3} \end{array} \right\}, \left\{ \begin{array}{cccc} 0 & \pm 1 & 0 & x_{1}/2 \\ \pm 1 & 0 & 0 & x_{2}/2 \\ 0 & 0 & r_{33} & x_{3} \end{array} \right\} : r_{33} \neq 0, r_{33}, x_{3} \in \mathbb{R}, x_{1}, x_{2} \in \mathbb{Z}\right\}$。

### （三）亚周期群的欧几里得正规化子



1. **定义与关系**

* 欧几里得正规化子$N_{E}(G)$是仿射正规化子$N_{A}(G)$的子集，需额外满足保距条件：对距离度量矩阵 M，有$a^{T}Ma = M$（a 为仿射变换的线性部分），即$N_{E}(G) = \{ \{a|t\} \in N_{A}(G) : a^{T}Ma = M \}$。

* 距离定义：列向量 v 的欧几里得长度$d = (v^{T}Mv)^{1/2}$。

1. **示例：层群 L1（p1）的** $N_{E}(G)$ 

* 一般斜交度量 M：$\left( \begin{array}{ccc} a^{2} & ab\cos\gamma & 0 \\ ab\cos\gamma & b^{2} & 0 \\ 0 & 0 & 1 \end{array} \right)$（a、b 为单胞向量长度，γ 为夹角），此时$N_{E}(p1)$含 4 类变换，Hermann-Mauguin（HM）符号为$P^{3}112/m$。

* 特殊正方形度量（γ=90°，a=b）：M 为对角矩阵$\left( \begin{array}{ccc} a^{2} & 0 & 0 \\ 0 & a^{2} & 0 \\ 0 & 0 & 1 \end{array} \right)$，$N_{E}(p1)$的 HM 符号为$P^{3}4/mmm$（因正方形格子对 4 重旋转不变）。

## 四、研究结果：正规化子表格

### （一）饰带群的欧几里得正规化子（Table 1）



* 涵盖 7 种饰带群，包含群编号、HM 符号、单胞度量、$N_{E}(G)$的符号与基向量、额外生成元（平移、二重旋转、其他生成元）、G 在$N_{E}(G)$中的指数等信息。

* 示例：饰带群 1（HM 符号$\mathscr{p}1$，一般度量）的$N_{E}(G)$符号为$p^{2}2mm$，基向量为$\varepsilon_{1}a, \varepsilon_{2}b$，额外生成元含平移（$x_{1},0;0,x_{2}$）、二重旋转（-x,-y）和进一步生成元（-x,y），指数为$(\infty_{\|} \cdot \infty_{\perp}) \cdot 2 \cdot 2$。

### （二）层群的欧几里得正规化子（Table 2）



* 涵盖 80 种层群，除饰带群表格的信息外，还考虑了特殊度量（如 a=b、γ=90°/120°、2cosγ=-a/b 等）对$N_{E}(G)$的影响。

* 示例：层群 1（p1）在不同度量下$N_{E}(G)$不同，如 a=b、γ=120° 时，$N_{E}(G)$符号为$P^{3}6/mmm$，额外生成元含平移（$x_{1},0,0;0,x_{2},0;0,0,x_{3}$）、反演（(0,0,0)）和进一步生成元（-y,x-y,z；-x,-y,z），指数为$(\infty_{\perp}\infty_{\|}^{2}) \cdot 2 \cdot 12$。

### （三）杆群的欧几里得正规化子（Table 3）



* 涵盖 75 种杆群，部分$N_{E}(G)$含连续旋转生成元（标注 “Continuous rotation”），指数中含$\infty$（因连续变换）。

* 示例：杆群 1（HM 符号$\mathscr{p}1$，一般度量）的$N_{E}(G)$符号为$P^{3}\infty/mmm$，额外生成元含连续旋转和 (-x,y,z)，指数为$(\infty_{\perp}^{2}\infty_{\|}) \cdot 2 \cdot \infty$。

## 五、数据与工具支持



1. **机器可读文件**：支持信息中提供 “SubperiodicGroupNormalizersMachineReadableFiles.zip”，含各亚周期群仿射 / 欧几里得正规化子元素的矩阵表示文本文件，格式规则如下：

* 首行：亚周期群编号（层群欧几里得正规化子含度量描述）。

* 后续行：增广矩阵展平为一行，饰带群对应 3×3 矩阵（9 个元素），层群 / 杆群对应 4×4 矩阵（16 个元素）。

* 符号含义：“r + 数字” 表示任意实数，“n + 数字” 表示任意整数，“x + 数字” 表示 \[0,1) 内实数。

1. **Mathematica 文件**：提供 “SubperiodicGroupNormalizersMachineReadableFiles.nb”，可直接解析上述 zip 文件中的正规化子数据。

## 六、研究意义与致谢



1. **研究意义**

* 填补双反对称亚周期群研究的空白，为评估亚周期群的真仿射等价性提供关键工具（仿射正规化子）。

* 系统推导并列出亚周期群的仿射 / 欧几里得正规化子，为晶体学、材料科学等领域的对称分析提供基础数据。

1. **致谢**：感谢宾夕法尼亚州立大学纳米级科学中心（NSF-MRSEC DMR #0820404）和 DMR-1210588 项目的资金支持。

> （注：文档部分内容可能由 AI 生成）