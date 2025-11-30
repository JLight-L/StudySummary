# 量子力学框架
**基本假设**：
- 粒子状态用一个 Hilbert 空间（称为态空间）中的一个**态矢**来表示
- 粒子的各种性质（如位置、动量、能量、自旋等等）各自对应作用在态空间上的一个**算符**
	- 称为可观测量
	- ……

## 态矢
### 测量概率

……
### 态矢的相位
……

## 算符 
### 作用算符
强调**映射关系**

### 测量算符——可观测量
强调**本征值**与**本征态**
#### 期望值

- **定义**：期望值 $\left< A \right> =\bra{\psi}A\ket{\psi}$ 
- 期望值随时间的变化 $\frac{d\left<A\right>}{dt}=\frac{i}{\hbar} \left< [H,A] \right>+\left< \frac{dA}{dt} \right>$ 
	- 特殊地，$\frac{d\left<H\right>}{dt}=\left< \frac{dH}{dt} \right>$ 
- **定义**：方差 $\sigma_{A}^{2}=\left< (A-\left< A \right>)^{2} \right> =\left< A^{2} \right>-\left< A \right>^{2}$ 
- **定理**：不确定关系 $\sigma_{A}^{2}\sigma_{B}^{2}\geq \left(\frac{1}{2i}\bra{\psi}[A,B]\ket{\psi}\right)^{2}$ 

## 算符的数学结构

**前提条件**：厄米算符
- **拓展**：非厄米算符的物理含义： #？？？ 
#### 本征值与本征矢

$A\ket{a_{i}}=a_{i}\ket{a_{i}}$ 
$N$ 维算符 $\hat{A}$ ，会有 $N$ 个本征值 $a_{i}$ ；对于*厄米算符*，可以找到 $N$ 个本征矢 $\ket{a_{i}}$ 
**本征值简并**：$n_{a_{i}}$ 个本征值相等，这时对应一个 $n_{a_{i}}$ 维本征子空间，其中任意一个矢量都可以作为本征矢
- **定理**：正交性：对于厄米算符，不同本征子空间的本征矢之间相互正交


#### 对易性

- **定义**：对易子 $[A,B]=AB-BA$ ，若 $A,B$ 对易，则 $AB=BA$ 
- **定理**：$A$ 的所有本征子空间都是 $B$ 的不变子空间
- **定理**：对易 $\leftrightarrow$ 可以找到一组共同本征矢
	- 或说 $A,B$ 对应的矩阵可以*同时*对角化
	- **证明**：
		- 对于 $A$ 的所有本征子空间 $V$ ，$V$ 同时是 $B$ 的不变子空间；即 $B$ 可以从原本的作用空间限制到 $V$ 上，仍然是一个厄米算符，故一定可以找到一组 $B$ 的正交本征矢

##### 对称性
$[A,H]=0$ 时， $A$ 称为体系的对称算符，即 $AHA^{-1}=H$ ，如 $T(a)\psi(r)=\psi(r+a)\implies T(a)H(r)T(a)^{-1}=H(r+a)$ 

标记本征态的量子数都对应一种对称性

##### 态矢的标记
用若干个算符的本征值来标记一个矢量，这些本征值称为**量子数**（有时是离散的，有时是连续的）
- **定义**：若几个算符的本征值可以恰好完全确定一个矢量（即简并态之间可以相互区分），则这些算符构成的集合叫**对易算符完全集**（Complete Set of Commuting Observables，CSCO，法语缩写 ECOC）
- **性质**：标记态的算符间一定两两对易！

在求解问题时，可以通过寻找相互对应的算符来寻找哈密顿量的本征值与本征态

### 变分法与本征值

- **定理**：（里兹定理）算符的期望值在且仅在本征值附近稳定，即 $\left< H \right> =\frac{\bra{\psi}H\ket{\psi}}{\braket{ \psi | \psi }}$ 在 $\ket{\psi}\to \ket{\psi}+\delta \ket{\psi}$ 下不变时，即取到本征值
- **应用**：可以通过猜测一些试探右矢（用一些参数来表示不同试探右矢）来尝试逼近真实本征值；选取的试探右矢形式与实际本征矢越接近，得到的能量越准确。

## 时间演化


- **（哈密顿算符的）本征态**
	- $H\ket{\psi}=\varepsilon \ket{\psi}$ 
	- **性质**（ $H$ 不变时）：$\ket{\psi}(t)=e^{ i \frac{\varepsilon}{\hbar}t }\ket{\psi}(t=0)$ ，即随时间演化只是附加一个整体相位，不改变内部结构

- **理解**：附加的相位会改变粒子的概率分布
	- 根据傅里叶变换， $x$ 算符附加的相位对应 $p$ 的改变， $p$ 算符附加的相位对应 $x$ 的改变，与经典哈密顿方程完全相同

# 哈密顿算符与本征态
 #？？？ 以位置为基矢时，本征态中可能会有 $\psi(r)=0$ 的点（节点），节点数量有什么含义？（eg. 无限深势阱）

# 角动量
## 角动量算符的关系

**描述角动量的算符**：
	$\vec{n}$ 方向的角动量分量： $J_{\vec{n}}$ 
	角动量模方（大小的平方）： $J^{2}$ 

$J_{x},J_{y},J_{z},J^{2}$ 的**对易关系**：
$$
\begin{cases}
\left[J_{i},J_{j}\right] = \sum\epsilon_{ijk}J_{k} \\
\left[ J^{2},J_{i} \right] = 0
\end{cases}
$$
只需要两个算符就可以完整描述一个角动量，通常取为 $J_{z},J^{2}$ ，对应量子数 $m,l$ ，即：
$$
\begin{cases}
J_{z}\psi_{m,l}=m\hbar \psi_{m,l} \\
J^{2}\psi_{m,l}=l(l+1)\hbar \psi_{m,l} 
\end{cases}
$$
- *注*：量子力学中，$J^{2}=J_{x}^{2}+J_{y}^{2}+J_{z}^{2}$ 依然拥有非负的本征值

升降阶算符
	是什么
	 #？？？ 除了作用在态上可以改升降阶之外，还有什么特殊的含义吗？
	为什么要引入，有什么用
	 #？？？ 

$m,l$ 的关系：



# 自旋
## ……
## 含自旋哈密顿量的求解
波函数在基 $\ket{x,m_{s}}$ 下展开：
$$
\psi(x)=\begin{pmatrix}
\psi_{m_{s}=s}(x) \\
\psi_{m_{s}=s-1}(x) \\
\dots \\
\psi_{m_{s}=-s}(x)
\end{pmatrix}
$$
其中，$\psi_{m_{s}}$ 称为“旋量”。这个形式也是本征态的形式。
则哈密顿方程为：
$$
\begin{pmatrix}
H_{m_{s}=s,m_{s}=s} & H_{m_{s}=s,m_{s}=s-1} & \dots  \\
H_{m_{s}=s-1,m_{s}=s} & \dots \\
\dots
\end{pmatrix}\begin{pmatrix}
\psi_{m_{s}=s}(x) \\
\psi_{m_{s}=s-1}(x) \\
\dots
\end{pmatrix}=E\begin{pmatrix}
\psi_{m_{s}=s}(x) \\
\psi_{m_{s}=s-1}(x) \\
\dots
\end{pmatrix}
$$
解法：先对角化H （ #？？？ 一定能对角化吗？求导之类的怎么办？） →  
## 自旋轨道耦合

# 量子力学与经典对应
## 对易算符
## xp关系
## 波包

# 近似方法
## 微扰论
### 定态微扰理论
$$\begin{align}
 & H=H_{0}+\lambda W \\
 & \psi_{0}\to \psi_{i} \\
 & \varepsilon_{0}\to\varepsilon_{i}
\end{align}
$$

当 $\lambda$ 很小时（即  $\lambda W$ 的所有矩阵元都很小时），本征态和本征能量怎么变化？

对 $\lambda$ 在 $0$ 附近展开（前提条件：能量、波函数均保持收敛）：
$$
\begin{align}
 & \varepsilon_{i}=\varepsilon_{i;0}+\lambda\varepsilon_{i;1}+\lambda^{2}\varepsilon_{i;2}+\dots \\
 & \psi_{i}=\psi_{i;0}+\lambda \psi_{i;1}+\lambda^{2}\psi_{i;2}+\dots
\end{align}
$$

**q阶项**
$$
(H-\varepsilon_{i;0})\psi_{i;q}+(W-\varepsilon_{i;1})\psi_{i;q-1}-\varepsilon_{i;2}\psi_{i;q-2}-\dots-\varepsilon_{i;q}\psi_{i;0}=0
$$

#### 非简并能级的微扰
能级 $\varepsilon_{0}$ 只有一个态，$\psi_{0}=\psi_{i;0}$ 
$$
H_{0}\psi_{i;0}=\varepsilon_{i;0}\psi_{i;0}
$$
$\psi_{i}$ 在 $\psi_{i}^{0}$ 附近发生偏移。

- **一级微扰**
	- $\varepsilon_{i;1}=\bra{\psi_{i}^{0}}W\ket{\psi_{i}^{0}}$ 
	- **解释**：相当于考虑**对角**矩阵元
	- $\braket{\psi_{n}^{p}|\psi_{i;1}}=\sum_{p,\psi_{i}\neq \psi_{0}}  \frac{\bra{\psi_{n}^{p}}W\ket{\psi_{0}}}{\varepsilon_{n}-\varepsilon_{0}}$  
		- *注*：态发生**小偏移**还要求 $W$ 的 非对角元 $\ll$ 对应的能级差
- 二级微扰
	- $\varepsilon_{i;2}=\sum_{p,\psi_{i}\neq \psi_{0}}  \frac{\left|\bra{\psi_{n}^{p}}W\ket{\psi_{0}}\right|^{2}}{\varepsilon_{n}-\varepsilon_{0}}$ 
	- **解释**：考虑**同行、同列**的矩阵元的影响
- **🖊总结**：微扰会使能级发生偏移
#### 简并能级的微扰
记 $\varepsilon_{0}$ 对应的态为 $\psi_{0}^{p}$ ，有 $\psi_{i;0}=\sum_{p}c_{p}\psi_{0}^{p}$ 
$\psi_{i}$ 由对 $W$ 限制在 $\psi_{0}^{p}$ 基下进行对角化得到；对角元为 $W_{pq}=\bra{\psi_{0}^{p}}W\ket{\psi_{0}^{q}}$ 
对角化后再在*新的基*下对哈密顿量做微扰计算（此时微扰中的简并项对应矩阵元为零，$\begin{pmatrix}\varepsilon & 0  & \dots\\ 0 & \varepsilon & \dots \\ \dots & \dots & \dots\end{pmatrix}$ 形式，不影响计算）  #？？？ 真的不影响吗？这是一阶的微扰，那高阶的微扰不会有影响吗？
 #？？？ 高阶微扰如何计算？（牵扯到其它对角元）
 #？？？ 同样是对角化，为什么在对角元相等的时候会出现奇异？（或者问 简并微扰的处理上和非简并有什么区别？为什么）

- *注*：简并的消除也可以在非简并微扰的公式中看出，即分母为 $0$ （能量的*二阶近似*中可以看出）；但此时该公式是错误的
- 简并破缺的情况*不会在一阶微扰中*体现；对角化后的对角项可以近似为…… #？？？ 
- 

- **🖊总结**：微扰可能使原本简并的能级发生劈裂；与对称性相关，见[量子力学中的群论](量子力学中的群论-GroupTheoryInQuantumMechanics.md) 

## 变分法


## WKB近似（半经典近似）
处理**势场V(x)缓变**的情况


## 含时微扰


### 光的发射与吸收


 #？？？ 如何理解电子跃迁对光的影响？
#### 自发辐射
真空涨落/背景辐射，多频率多方向叠加（非相干）

#### 选择定则
$m'-m=\begin{cases}\pm 1, & \text{x, y;} \\ 0, & \text{z.}\end{cases}$ ，可由对易关系 $[L_{i},r_{j}]=i\hbar\epsilon_{ijk}r_{k}$ 推出；
$l'-l=\pm 1$ ，可由对易关系 $[L^{2}[L^{2},r_{i}]]=2\hbar^{2}(r_{i}L^{2}+L^{2}r_{i})$ 推出。
 #？？？ 有没有可能有更加严苛的条件？这里的推导只是给出可能可以的情况