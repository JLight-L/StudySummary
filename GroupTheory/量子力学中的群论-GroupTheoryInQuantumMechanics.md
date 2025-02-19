#important 
体系对称性抽象为变换算符与哈密顿算符对易：$P_gH = HP_g \Rightarrow$ $g$为对称操作
# 简并-Degeneracy
#important  $H$ 拥有一套完整的本征函数，作为承载 $P_g$ 的基函数。
对于所有 $P_g$ ，函数空间可约化为几个空间的直和，通过：
- 承载的不可约表示 $A^\alpha$
- 该空间中函数的序号 $i$
- 在承载相同不可约表示的所有空间里的序号 $m$，用于区分承载相同不可约表示的函数空间

来标记函数，即
$$
\begin{align}
H\psi^{\alpha,m}_i &= E^{\alpha,m}_i\psi^{\alpha,m}_i\\
P_g\psi^{\alpha,m}_j &= \sum_i A^\alpha_{ij}\psi^{\alpha,m}_i
\end{align}
$$
## 对称性导致的简并
#prop 构成哈密顿算符群的不可约表示的本征函数必属于同一能级，即
$$
E^{\alpha,m}_i \equiv E^{\alpha,m}
$$
哈密顿量相同能级的本征态至少承载（furnish）一个不可约表示，若简并态承载多于一个不可约表示，则简并能级为偶然简并。
> *P.S. 偶然简并是由一些隐藏对称性导致的，很多时候这些对称性并不重要* 

## 承载不可约表示的基函数
#def $P^\alpha_{ij} = \frac{s_\alpha}{n}\sum_{g\in G}A^\alpha_{ij}(g)P_g$，其中 $s_\alpha$ 为 $A^\alpha$ 的维数
#prop $P^\alpha_{ij}P^\beta_{kl} = \delta_{\alpha\beta}\delta_{jk}P_{il}$
#prop $P^\alpha_{ij}\psi^{\beta,m}_k = \delta_{\alpha\beta}\delta_{jk}\psi^{\beta,m}_i$，即$P^\alpha_{ij}\psi^{\alpha,m}_j = \psi^{\alpha,m}_i$
#prop $P^\alpha_{jj}$ 为投影算符，将函数投影到所有承载 $A^\alpha$ 的第 $j$ 个函数组成的空间上，即 $$P^\alpha_{jj}:\ V \rightarrow span\left\{\psi^{\alpha,1}_j,\ \psi^{\alpha,2}_j,...\right\}$$
### 特征标投影算符
#def $P^\alpha= \sum_j P^\alpha_{jj} = \frac{s_\alpha}{n}\sum_{g\in G}\chi^\alpha_{ij}(g)P_g$，将函数投影到所有承载 $A^\alpha$ 的空间上
## 正交性定理
#prop $\left<\psi^{\alpha,m}_i|\psi^{\beta,n}_j\right> = \delta_{\alpha\beta}\delta_{ij}f^\alpha_{mn}$，其中 $f^\alpha_{mn}$ 与 $i,j$ 无关
# 微扰-Perturbation
微扰可能会引起能级分裂，是因为对称性遭到破坏
……
## 根据初末态
## 根据微扰项
# 固体物理中的对称性-SymmetryInSolidStatePhysics
## 晶体对称性
### 晶体点群
……
### 晶体空间群
- **定义**：$G = \{\left\{ R|\mathbf{t} \right\}|\left\{ R|\mathbf{t} \right\}\mathbf{r}=R\mathbf{r}+\mathbf{t}\text{，保持晶体结构不变}\}$ 
- **性质**：所有平移部分构成空间群的不变子群 $T = \{\mathbf{t}|\exists \left\{ R|\mathbf{t} \right\}\in G\}$
#### 空间群的点群
- **定义**：$G_{0}$ 为所有空间群中的转动元素组成
- **定理**：$G/T = G_{0}$
### ……
# 自旋轨道耦合-SpinOrbitCoupling
## 自旋与双群
在半整数自旋（费米子）情况下，粒子波函数在空间变换下不满足 $SO(3)$ 群的变换规律，自旋波函数在旋转 $2\pi$ 后并不是回到本身，而是会多一个 $-1$ 的相位，所以**自旋空间的变换满足** $SU(2)$ **群**

> $\exp(2\pi im)$ 在 $m$ 为半整数时会产生一个 $-1$ 的相位

- **定义**：由 $SO(3)$ 出发，引入代表旋转 $2\pi$ 的元素 $\bar{E}$ ，将原本取值在 $[0,2\pi)$ 的转角增大为 $[0,4\pi)$，并重新定义乘法规则，满足 $\bar{E}\bar{E}=E$ （该乘法下 $SO(3)$ 不封闭），组成 $SO(3)$ 的双群（Double Group） $SO^D(3)$。
- **性质**：$SO^D(3) \cong SU(2)$ 

> 注：$SO^D(3) / \{E,\bar{E}\} \cong SO(3),\ SO^D(3)=SO(3)\cup \bar{E}SO(3)$，但 $SO(3)$ 不是 $SO^D(3)$ 的子群

## 双点群
## 自旋轨道耦合
空间对称性为群 $G$，为 $O(3)$ 群或其有限子群
- **没有耦合项时**：哈密顿算符群为 $G\otimes SU(2)$
- **有耦合项时**：……
# 时间反演-TimeReversal
