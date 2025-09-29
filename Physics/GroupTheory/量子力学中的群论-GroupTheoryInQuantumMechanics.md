#important 
体系对称性抽象为变换算符与哈密顿算符对易：$P_gH = HP_g \Rightarrow$ $g$为对称操作

*注*：作用在函数空间上的操作 $P_{g}$  和 作用在参数空间上的操作 $g$  的关系：$P_{g}\psi(g\mathbf{r})=\psi(\mathbf{r})$ ;
    即 相同的“参数位置”对应相同的函数值

### 对称群与本征空间的关系

> ==算符的本征空间对对称群封闭==（意思是对所有群操作都封闭，即一个本征空间一定可以承载完整的一个或多个表示） → 被任一群元联系在一起的态（更严格地说是承载不可约表示的态，这与本征空间中的基矢（本征态）选取有关）一定处在同一能级，这种简并被该对称性保护

- 找到本征空间承载的表示 → 算特征标，分析是否可约 → 判断必然简并
- 一个本征态可以通过对称算符和另一个态联系起来 → 另一个态一定也是有相同本征值的本征态 ^ae44c1
- 算符的本征态可以通过对称群不可约表示来标记（另一种形式的用对易算符的本征态标记）
    -  $\alpha$ - 标记不可约表示， $k$ - 标记承载相同不可约表示的不同表示空间， $m$ - 标记承载同一不可约表示的不同基矢
- 
# 简并-Degeneracy
#important  $H$ 拥有一套完整的本征函数，作为承载 $P_g$ 的基函数。
对于所有 $P_g$ ，函数空间可约化为几个空间的直和，通过：
- 承载的不可约表示 $A^\alpha$ 
- 该空间中函数的序号 $i$ 
- 在承载相同不可约表示的所有空间里的序号 $m$ ，用于区分承载相同不可约表示的函数空间

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
**离散平移对称性**下的对称性
## 晶体对称性
### 晶体点群
……
### 晶体空间群
- **定义**：$G = \{\left\{ R|\mathbf{t} \right\}|\left\{ R|\mathbf{t} \right\}\mathbf{r}=R\mathbf{r}+\mathbf{t}\text{，保持晶体结构不变}\}$ 
	- *注*：$\left\{ R |\mathbf{t}\right\}=\left\{ E|\mathbf{t} \right\}\left\{ R|0 \right\}=\left\{ R|0 \right\}\left\{ E|R^{-1}\mathbf{t} \right\}$ 
- **性质**：对于任何一个空间群操作 $\left\{ R|\mathbf{t} \right\}$ ，平移部分只有两种可能：
    1. $\mathbf{t}=\mathbf{R}_{m}$ ，称为点式对称性 
    2. $\mathbf{t}=\mathbf{R}_{m}+\frac{L}{n}\mathbf{R}_{0}$ ，$\mathbf{R}_{0}$ 为 n 次转轴方向的单位晶格矢量，$L<n$ 为整数
    - *注*：对于所有操作都是点式操作的群，称作点式空间群
- **性质**：所有平移部分构成空间群的不变子群 $T = \{\mathbf{t}|\exists \left\{ R|\mathbf{t} \right\}\in G\}$
- **定义** 空间群的点群 $G_{0}$ ：所有空间群中的转动元素组成
    - **定理**：$G/T \cong G_{0}$ ，特别的，对于*点式空间群*，$G = T\rtimes G_{0}$（这时所有陪集代表元可取在 $G_{0}$ 中）
- 

#### 点式空间群
所有空间群操作的平移部分是
### ……
## 周期势下的态——由k空间标记

用**倒空间**中的 $\mathbf{k}$ 来标记态（与平移算符的共同本征态），满足 $T(\mathbf{x})\psi_{\mathbf{k}}=e^{ i\mathbf{k}\cdot \mathbf{x} }\psi_{\mathbf{k}}$ ，同时也承载空间平移群的不可约表示
    note：平移群只有一维不可约表示，由本征态承载



点群    平移群
空间群


# 自旋轨道耦合-SpinOrbitCoupling
## 自旋与双群
在半整数自旋（费米子）情况下，粒子波函数在空间变换下不满足 $SO(3)$ 群的变换规律，自旋波函数在旋转 $2\pi$ 后并不是回到本身，而是会多一个 $-1$ 的相位，所以**自旋空间的变换满足** $SU(2)$ **群**

> $\exp(2\pi im)$ 在 $m$ 为半整数时会产生一个 $-1$ 的相位

- **定义**：由 $SO(3)$ 出发，引入代表旋转 $2\pi$ 的元素 $\bar{E}$ ，将原本取值在 $[0,2\pi)$ 的转角增大为 $[0,4\pi)$，并重新定义乘法规则，满足 $\bar{E}\bar{E}=E$ （该乘法下 $SO(3)$ 不封闭），组成 $SO(3)$ 的双群（Double Group） $SO^D(3)$。
- **性质**：$SO^D(3) \cong SU(2)$ 

> 注：$SO^D(3) / \{E,\bar{E}\} \cong SO(3),\ SO^D(3)=SO(3)\cup \bar{E}SO(3)$，但 $SO(3)$ 不是 $SO^D(3)$ 的子群

## 双点群

## 自旋群

**def**  nontrivial SPGs: 不包含纯自旋操作的自旋群： $\left\{ g_{s}=U_{m}(\varphi) | g=C_{n}(\theta)\right\},C_{n}(\theta)\neq E$ 

**def**  spin-only group: 纯自旋群，自旋群的一种子群： $G_{SO}=\left\{ g_{s}|e \right\}$ 
    根据spin-only群的类型对自旋排布进行分类：
        1. Nonmagnetic spin arrangements: $G_{\text{SO}} = O^{s}(3)$ 
        2. Collinear spin arrangements: $G_{\text{SO}} = \text{SO}(2) \rtimes Z_2^K$
        3. Coplanar spin arrangements: $G_{\text{SO}} = Z_2^K = \{E, U_{\boldsymbol{n}}(\pi)T\}$ 
        4. Noncoplanar spin arrangements: $G_{\text{SO}} = \{E\}$

Polychromatic extension
扩展方式原理？

## 自旋轨道耦合
空间对称性为群 $G$，为 $O(3)$ 群或其有限子群
- **没有耦合项时**：哈密顿算符群为 $G\otimes SU(2)$
- **有耦合项时**：……

## 特殊能带结构特征s

- Kramers degeneracy：对于费米子（$T^{2}=-1$），在时间反演对称性保护下能带会出现二重简并

# 时间反演-TimeReversal
