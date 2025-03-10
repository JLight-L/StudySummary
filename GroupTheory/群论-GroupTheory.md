# 群的基本概念-IntroductionToGroups
#def 集合+乘法（二元运算） with 封闭性，结合律，单位元，逆元
#def #denote  #finite_group 群的阶$|G|$：群的元素个数
## 群之间的关系
### 同态映射
#def 从一个群到另一个群的映射（单射），满足乘法关系不变
$$
\begin{array}{l}
\phi: G_1 \to G_2 \\ satisfies:\\
\hspace{20pt}\phi(g_1 g_2) = \phi(g_1) \phi(g_2)
\end{array}
$$
#denote $G_1 \simeq G_2$
#### 同态核
#def 映射到单位元的子群
##### 同态核定理
#prop 同态核一定为[不变子群](#不变子群)
### 同构映射
#def 满射的同态映射
#denote $G_1 \cong G_2$
### 子群
#def 封闭的子集
#denote $H$为$G$的子群，记为$H<G$
#### 群元的阶
#def #finite_group 由$g$[生成](#生成元)的[循环群](#循环群-C)的[指数](#Lagrange定理)
#denote $|g|$
#### 陪集
#def $gH$（左陪集），$Hg$（右陪集）
##### 陪集定理
#prop 
$$\forall g_1,g_2 \in G,\ 
\begin{cases}
g_1H=g_2H ,&if\ g_1g_2^{-1} \in H\\
g_1H\ \cap\ g_2H=\varnothing ,&else
\end{cases}
$$
##### 陪集的重排定理
#prop $l\in gH \Rightarrow lH=gH$
#### Lagrange定理
#important
#prop #finite_group $H<G\Rightarrow |G|/|H| \in \mathbb Z$
#denote $|G|/|H|$记为$H$的指数（Index）
#coro 素数阶的群一定同构于同阶循环群（没有真子群）
#### Cauchy定理
#prop #finite_group $p\mid (|G|)\Rightarrow \exists g \in G,\ |g|=p$
#### 不变子群
#important 
#def 由几个完整的[类](#类)构成的子群
#denote $H\triangleleft G$
#property $\forall g \in G,\ gHg^{-1}=H$ ^[见[类](#类)]
#coro  指数为2的子群一定为不变子群
##### 商群
#def #denote $H\triangleleft G \Rightarrow$商群$G/H=\{H,g_1H,g_2H,...\}$，即为$H$的陪集串构成的群
#property $G = H \rtimes G/H$，见[半直积](#半直积群)
### 直积
#### 直积群
#def 由$G_1$、$G_2$各自群元组成的有序数对$g_{1\alpha}g_{2\beta}$构成，定义乘法使得 $g_{2\beta}g_{1\alpha} = g_{1\alpha}g_{2\beta}$ ，即**可交换地组合在一起**
#denote $G_1 \otimes G_2$
#### 直积因子
#def $\forall g \in G$可由$G$的两个子群$G_1$、$G_2$的各一个群元唯一组合（相乘）而成
即$g_{\alpha\beta}=g_{1\alpha}g_{2\beta}=g_{2\beta}g_{1\alpha}$
#property $G_1 \triangleleft G,\ G_2 \triangleleft G$
#### 半直积群
#def 由$H$、$G_1$各自群元组成的有序数对$h_\alpha g_{1\beta}$构成，定义乘法使得 $g_{1\beta}H = Hg_{1\beta}$ ，
即 $g_{1\beta}h_\alpha = h_{\alpha'}g_{1\beta}$ ，其中 $h_\alpha, h_{\alpha'} \in H$
#denote $H \rtimes G_1$
#property 记 $G = H \rtimes G_1$ ，有 $H \triangleleft G,\ G_1 < G$
#property 两个群可以有多种半直积的结果，直积是一种特殊的半直积
## 群元之间的关系
### 重排定理
#important 
#prop $g \in G \Rightarrow gG = G$
### 类
#important 
#def 相互[共轭](#共轭)的元素构成的集合
#property  同类元素同阶
#property  单位元自成一类
#### 共轭
#def $\exists g \in G,\ gg_1g^{-1}=g_2 \Rightarrow g_1,\ g_2\ 互为共轭群元$
#property 相互性，传递性
### 生成元
#def 最小可以生成（元素之间运算得到新的元素）整个群的集合（不一定唯一）
## 李群-LieGroup
#def 
## 最简单的群
### 循环群-C
#property Abel
### 二面体群-D
$D_n=\{C_n,\ C_n^2,\ ...,\ C_n^{(n-1)},\ C_2^{(1)},\ C_2^{(2)},\ ...,\ C_2^{(n)}\}$
#property $D_n/C_n \cong C_2$
### 10阶内有限群
[10阶内有限群](10阶内有限群.png)

| 阶数  | 群                                                                                                                                              |
| :-: | :--------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | $C_1 = \{e\}$                                                                                                                                  |
|  2  | $C_2$                                                                                                                                          |
|  3  | $C_3$                                                                                                                                          |
|  4  | $C_4$,    $V_4(D_2) = C_2 \otimes C_2$ \[最小的非循环群\]                                                                                             |
|  5  | $C_5$                                                                                                                                          |
|  6  | $C_6 = C_2 \otimes C_3$,    $D_3 = C_3 \rtimes C_2$ \[最小的非 Abel 群\]                                                                            |
|  7  | $C_7$                                                                                                                                          |
|  8  | $C_8$,    $D_4 = C_4 \rtimes C_2$,    $C_{4h} = C_4 \otimes C_2$,    $D_{2h} = D_2 \otimes C_2 = C_2 \otimes C_2 \otimes C_2$,    $Q$ \[四元数群\] |
|  9  | $C_9$,    $C_3 \otimes C_3$                                                                                                                    |
| 10  | $C_{10} = C_2 \otimes C_5$,    $D_5 = C_5 \rtimes C_2$                                                                                         |

## 变换群
由作用于一个集合的一一映射组成

***
# 群表示-GroupRepresentation
#def 同态矩阵群
# 完全转动群和点群-RotationGroupAndPointGroups

# 晶体对称性-CrystalSymmetry
