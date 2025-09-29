XRD测结构
DFT算能带
ARPES（利用光电效应）测能带

# DFT 简介

$H=K+\text{elec-nucl}+\text{elec-elec}+\text{nucl-nucl}$ 
通常忽略原子运动
## Hohenberg-Kohn Theory
将 $H$ 进行拆分 $H=\sum T_{i}+\sum V_{ext}(r_{i})+\sum V_{int}(r_{i},r_{j})$ 
- *粒子数密度确定* $V_{ext}$ 
 → 考虑能量泛函 $E[n]$ 
- 基态粒子数密度——能量极小值
 #没懂 
## Kohn-Sham Variational Eq.

 $\left( -\frac{1}{2}\nabla^{2} +V_{n}+V_{H}+V_{xc}\right)\psi_{i}=\varepsilon_{i}\psi_{i}$ ，$V_{xc}$ : Exchange and Correlation potential，

# VASP 计算
## Files
### Input
#### INCAR
计算方式

- 描述电子在能级附近的分布，$f(E)$ ，用于避免数值计算的不稳定性（通常是通过用连续的分布代替不连续分布，即“smearing”）
	- Kimi：控制电子能量分布的平滑处理方式，用于处理能带填充问题。
	- ISMEAR：分布类型
		- 对于半导体和绝缘体体系，ISMEAR的值取绝对不能大于0， 一般用0；
		- K 点少，半导体或者绝缘体，那么只能用 ISMEAR = 0；
		- 在DOS能带计算中，使用ISMEAR= -5 用于获取精确的信息。
		- 对于金属来说，ISMEAR的取值一般为>=0 的数值（0,1,2）；
		- 保守地说，ISMEAR = 0 (Gaussian Smearing) 可以满足大部分的体系（金属，导体，半导体，分子）；
	- SIGMA：分布宽度
		- 如果用了ISMEAR = -5； SIGMA的值可以忽略，也可以不管
		- 对于金属：ISMEAR = 1 或 0、非金属: ISMEAR= 0 的时候，一般取 SIGMA = 0.10 即可，默认值是0.20。不放心的话，用0.05。
		- 对于气体分子，原子体系（也就是你把分子或者原子放到一个box里面）： ISMEAR = 0; SIGMA = 0.01。
		- **标准是**： SIGMA的取值要保证OUTCAR 中的 `entropy T*S` 这一项，平均到每个原子上，要小于 1-2 meV 
- 自旋极化
    - ISPIN=1：无自旋极化
    - ISPIN=2：共线自旋极化
    - INONCOLLINEAR=.T.：非共线（记得使用 vasp_ncl）
    - *注*：For noncollinear calculations ISPIN is ignored.


#### KPOINTS
- 第3行：k空间网格类型
	- G：Gamma-Centered Grid，包含布里渊区中心点（Γ点）
	- M：Monkhorst-Pack Grid，围绕Γ点（相当于平移一段距离）
- 第四行：k点（网格格点）分割数（ #？？？ 对第一布里渊区的分割）
	- 对于原子或者分子的计算，K点取一个点就够了（1 1 1）
	- 如果你要用 `ISMEAR = -5` 来计算的时候，需要至少大于 2 2 2或者3 3 3
		- 四面体积分法需要在k空间中划分多个四面体单元，每个四面体由相邻的k点连接而成。如果只有 **1×1×1**（即仅Γ点），无法形成任何四面体，导致方法失效。
- 第五行：k点偏移量

#### POSCAR
原子位点信息

#### POTCAR
赝势文件

- 依个人的学习经验，VRHFIN， LEXCH，TITEL，ZVAL，ENMAX是用到最多的几个参数。
	- VRHFIN 用来看元素的价电子排布，如果你元素周期表倒背如流，可以忽略这个参数；
	- LEXCH 表示这个POTCAR对应的是GGA-PBE泛函；如果INCAR中不设定泛函，则默认通过这个参数来设定。
	- TITEL 就不用说了，指的是哪个元素，以及POTCAR发布的时间；
	- ZVAL 指的是实际上POTCAR中价电子的数目，尤其是做Bader电荷分析的时候，极其重要。
	- ENMAX 代表默认的截断能。与INCAR中的ENCUT这个参数相关
- POTCAR检查常用的Linux命令：

	查看POTCAR中的元素:
	
	```bash
	grep  TIT POTCAR
	```
	
	查看POTCAR的截断能:
	
	```bash
	grep  ENMAX POTCAR
	```
	
	查看POTCAR中元素的价电子数目：
	
	```bash
	grep  ZVAL POTCAR
	```
- *交换关联泛函* 
	- 在 LDA 中，交换能量密度是电子密度的函数，其形式为 $E_x^{LDA}[\rho] = \int \epsilon_x(\rho(\mathbf{r})) \rho(\mathbf{r}) d\mathbf{r}$，其中 $\epsilon_x(\rho)$ 是均匀电子气中的交换能量密度。
	- GGA 是对 LDA 的改进，它考虑了电子密度的梯度信息，能够更好地描述电子密度变化较快的区域。GGA 的交换相关能量泛函形式为 $E_{xc}^{GGA}[\rho] = \int \epsilon_{xc}(\rho(\mathbf{r}), \nabla\rho(\mathbf{r})) \rho(\mathbf{r}) d\mathbf{r}$ ，其中 $\epsilon_{xc}(\rho, \nabla\rho)$ 是交换相关能量密度，它不仅依赖于电子密度，还依赖于电子密度的梯度。
		- 常用的 GGA 泛函有 PBE 泛函等
- 赝势选择
	- 
#### 一定要检查输入文件！
参数名
计算体系需求
计算任务需求

### 交换关联泛函
好的，那我来详细讲讲交换相关泛函。

在 DFT 中，交换相关能量泛函是一个关键部分，因为它直接决定了计算精度。交换相关能量泛函由交换能量泛函和相关能量泛函两部分组成。

交换能量泛函描述了电子之间的交换相互作用，它来源于泡利不相容原理，导致同自旋电子之间相互排斥。在 LDA 中，交换能量密度是电子密度的函数，其形式为 \( E_x^{LDA}[\rho] = \int \epsilon_x(\rho(\mathbf{r})) \rho(\mathbf{r}) d\mathbf{r} \)，其中 \( \epsilon_x(\rho) \) 是均匀电子气中的交换能量密度。

相关能量泛函描述了电子之间的相关运动带来的能量变化。在 LDA 中，相关能量密度也是电子密度的函数，形式为 \( E_c^{LDA}[\rho] = \int \epsilon_c(\rho(\mathbf{r})) \rho(\mathbf{r}) d\mathbf{r} \)，其中 \( \epsilon_c(\rho) \) 是均匀电子气中的相关能量密度。LDA 的优点是计算简单，但缺点是对非均匀电子密度体系的描述不够准确。

GGA 是对 LDA 的改进，它考虑了电子密度的梯度信息，能够更好地描述电子密度变化较快的区域。GGA 的交换相关能量泛函形式为 \( E_{xc}^{GGA}[\rho] = \int \epsilon_{xc}(\rho(\mathbf{r}), \nabla\rho(\mathbf{r})) \rho(\mathbf{r}) d\mathbf{r} \)，其中 \( \epsilon_{xc}(\rho, \nabla\rho) \) 是交换相关能量密度，它不仅依赖于电子密度，还依赖于电子密度的梯度。常用的 GGA 泛函有 PBE 泛函等，PBE 泛函在描述材料的结构和性质方面表现出较好的精度。

在 VASP 计算中，选择合适的交换相关泛函对计算结果的准确性至关重要。对于大多数固体材料，GGA 泛函（如 PBE）是一个较好的选择，因为它在计算精度和计算成本之间取得了较好的平衡。在实际应用中，需要根据具体的研究体系和计算目的来选择合适的交换相关泛函。在 VASP 的输入文件 INCAR 中，可以通过设置参数 IXC 或 PRECAL 来选择不同的交换相关泛函，例如 IXC=1 表示 LDA，PRECAL=PBE 表示 PBE 泛函。

如果有其他问题，欢迎继续提问。

## SSAFM（自旋劈裂反铁磁）的计算
### KPOINTS
第四行分割数一般的标准：每个方向：分割数 × 晶格常数 > 45
	保证k空间取点间距足够近


