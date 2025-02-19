#ai
# 群表示-GroupRepresentation-Kimi

## 群表示的定义
#def 群表示是将抽象群与线性变换群建立同态映射关系，利用矩阵的计算特点来研究群的结构。
#denote 设有群 $G$，如存在一个从 $G$ 到 $n$ 维线性空间 $V$ 上的线性变换群 $L(V, C)$ 的同态映射 $A$，则称 $A$ 是群 $G$ 的一个线性表示，$V$ 为表示空间，$n$ 是表示的维数。记为：$A : G \to V$，$\forall g \in G$, 有$A(g) \in L$，$\forall g_\alpha, g_\beta \in G$，有$A(g_\alpha) A(g_\beta) = A(g_\alpha g_\beta)$ 。

## 等价表示与不可约表示
### 等价表示
#def 设群 $G = \{g_\alpha\}$ 在表示空间 $V$ 上的一个表示 $A$ 是 $\{A(g_\alpha)\}$，也就是说对每个 $g_\alpha$ 有个非奇异变换与之对应，在一组基 $(e_1, e_2, \cdots, e_n)$ 下，$A(g_\alpha)$ 为 $g_\alpha$ 对应的非奇异矩阵。设 $P$ 是 $V$ 上的一个非奇异矩阵，则相似矩阵集合 $\{P^{-1}A(g_\alpha) P\}$ 也给出群 $G$ 的一个表示，这个表示 $\{P^{-1}A(g_\alpha) P\}$ 称为 $\{A(g_\alpha)\}$ 的等价表示。
#prop 等价表示保持乘法规律不变。

### 不可约表示
#def 设 $A$ 是群 $G$ 在表示空间 $V$ 上的一个表示，如果 $V$ 存在一个 $G$ 不变的真子空间 $W$（“真”指的是这个空间不能为 $V$ 本身或只包含零向量），则称 $A$ 是可约表示。其中 $G$ 不变的真子空间 $W$，是指对 $\forall y \in W$，$\forall g_\alpha \in G$，有 $A(g_\alpha) y \in W$。相对的，如果群 $G$ 表示 $A$ 的表示空间 $V$ 不存在 $G$ 不变的真子空间，则称 $A$ 是 $G$ 的不可约表示。

## 特征标
#def 设 $A = \{A(g_\alpha)\}$ 是群 $G = \{g_\alpha\}$ 的一个表示，这个表示的特征标定义为 $\{\chi(g_\alpha)\}$，其中 $\chi(g_\alpha) = \text{tr}A(g_\alpha) = \sum_\mu A_{\mu\mu}(g_\alpha)$ 。
#prop 等价表示的特征标相同。
#prop 同一个表示中，共轭元素的特征标相同。
#prop 特征标是类的函数。
#prop 单位元自成一类，特征标等于表示维度。

## 酉表示
#def 群 $G$ 到内积空间 $V$ 中的酉变换群 $L$ 上的同态映射 $A$，称为群 $G$ 的酉表示。
#prop 酉表示的矩阵具有 $U^\dagger U = UU^\dagger = I$ 的性质，即 $A(g_\alpha)^\dagger = A(g_\alpha)^{-1} = A(g_\alpha^{-1})$。

## 群代数与群函数
### 群空间
#def 以群元的线性组合为向量构成的线性空间，称为群空间。
#denote 群空间记为 $V_G$。

### 群代数
#def 在群空间的基础上定义乘法规则，形成的代数称为群代数。
#denote 群代数记为 $R_G$。

### 群函数
#def 以群为定义域、以复数域为值域的函数称为群函数。
#denote 群函数记为 $f(g_\alpha) = x_\alpha \in \mathbb{C}$。

## 正则表示
### 左正则表示
#def 取群 $G$ 的群代数空间 $R_G$ 为群 $G$ 的表示空间，定义 $G$ 到 $R_G$ 上的线性变换群 $L(G)$ 的映射为 $L: G \to L(G)$，线性变换 $L(g_i) \in L(G)$ 定义为：$L(g_i)x = g_ix$，则映射 $L$ 保持了群的乘法结构不变，为同构映射，$L(G)$ 称为群 $G$ 的左正则表示。
#denote 左正则表示记为 $L(G)$。

### 右正则表示
#def 同上，定义 $G$ 到 $R_G$ 上的线性变换群 $R(G)$ 的映射为 $R: G \to R(G)$，线性变换 $R(g_i) \in R(G)$ 定义为：$R(g_i)x = xg_i^{-1}$，则 $R(G)$ 称为群 $G$ 的右正则表示。
#denote 右正则表示记为 $R(G)$。

## 有限群表示理论
### 舒尔引理一
#def 设 $A$ 是群 $G$ 在有限维复空间 $V$ 上的不可约表示，若 $V$ 上的线性变换 $M$ 满足 $MA(g_\alpha) = A(g_\alpha)M$ 对 $\forall g_\alpha \in G$ 成立，则 $M = \lambda E$，其中 $\lambda$ 为数域上的数，$E$ 为单位变换。

### 舒尔引理二
#def 设群 $G$ 在有限维向量空间 $V_A$ 与 $V_B$ 有不可约表示 $A$ 与 $B$，若对 $\forall g_\alpha \in G$，有将 $V_A$ 映入 $V_B$ 的线性变换 $M$，满足：$B(g_\alpha)M = MA(g_\alpha)$，则:
  - 当表示 $A$ 与 $B$ 不等价时，$M \equiv 0$（为零矩阵）；
  - 当 $M$ 不为零时，$A$ 与 $B$ 必等价。

### 正交性定理
#def 设有限群 $G = \{g_\alpha\}$ 有不等价不可约酉表示 $A_1, A_2, \cdots, A_p, \cdots, A_r, \cdots$，其维数分别为：$S_1, S_2, \cdots, S_p, \cdots, S_r, \cdots$。这些不等价不可约酉表示矩阵元，作为群函数，在群函数空间这个内积空间有如下性质：$\langle A_p^{\mu\nu} | A_r^{\mu'\nu'} \rangle = \frac{1}{S_p}\delta_{pr}\delta_{\mu\mu'}\delta_{\nu\nu'}$，写成求和的形式为 $\sum_{i=1}^n A_p^{*\mu\nu}(g_i) A_r^{\mu'\nu'}(g_i) = \frac{n}{S_p}\delta_{pr}\delta_{\mu\mu'}\delta_{\nu\nu'}$。

### Burnside 定理
#def 有限群的所有不等价不可约酉表维数的平方和等于群的阶。

## 特征标理论
### 特征标第一定理
#def 有限群不可约表示的特征标满足：$(\chi_p | \chi_r) = \frac{1}{n}\sum_{i=1}^n \chi_p^*(g_i) \chi_r(g_i) = \delta_{pr}$。

### 特征标第二定理
#def 有限群 $G$ 有类 $K_1, K_2, \cdots, K_q$，$n_i$ 为第 $i$ 个类的元素个数，则有：$\frac{1}{n}\sum_{p=1}^q n_i \chi_p^*(K_i) \chi_p(K_j) = \delta_{ij}$。

## 新表示的构成
### 直积表示
#def 群 $G$ 有两个表示 $A$ 与 $B$，作表示矩阵的直积 $C(g_\alpha) = A(g_\alpha) \otimes B(g_\alpha)$，这个直积矩阵群 $C$ 保持群的乘法规律不变，也是群 $G$ 的一个表示。这个表示称为 $A$ 表示与 $B$ 表示的直积表示。
#denote 直积表示记为 $C(g_\alpha) = A(g_\alpha) \otimes B(g_\alpha)$。

### 直积群的表示
#def 设群 $G = G_1 \otimes G_2$ 是群 $G_1, G_2$ 的直积，$A$ 与 $B$ 分别是 $G_1$ 与 $G_2$ 的表示，令 $C(g_{1\alpha}, g_{2\beta}) = A(g_{1\alpha}) \otimes B(g_{2\beta})$，则 $C$ 构成直积群 $G$ 的一个表示。
#denote 直积群的表示记为 $C(g_{1\alpha}, g_{2\beta}) = A(g_{1\alpha}) \otimes B(g_{2\beta})$。

### 诱导表示
#def 设群 $G$ 有子群 $H$，则有子群的表示 $B$ 诱导出的群 $G$ 的表示称为诱导表示。诱导表示 $HU_B$ 的构造方式如下：将群 $G$ 作右陪集分割 $Hg_1, Hg_2, \cdots, Hg_l$，设子群 $H$ 的表示 $B$ 的维数为 $d$，定义映射如下：$\forall g \in G$，$\sigma(g) = \begin{cases} B(g), & \text{if } g \in H \\ 0, & \text{if } g \notin H \end{cases}$，利用映射 $\sigma$ 可构造由子群 $H$ 的表示 $B$ 诱导的群 $G$ 的表示 $HU_B$：$\forall g \in G$，$HU_B(g)$ 为 $ld$ 维表示矩阵，其中 $l = |G| / |H|$ 为子群 $H$ 的指数，矩阵元为 $[HU_B(g)]_{ij} = \sigma(g_i g g_j^{-1})$，$g_i, g_j$ 为陪集代表元。
# 群表示-GroupRepresentation-Kimi删减版

## 群表示的定义
#def 群表示是抽象群与线性变换群的同态映射。
#denote $A: G \to V$，$A(g_\alpha) A(g_\beta) = A(g_\alpha g_\beta)$。

## 等价表示与不可约表示
### 等价表示
#def 通过相似变换联系的群表示。
#prop 保持乘法规律不变。

### 不可约表示
#def 不存在非平凡不变子空间的表示。

## 特征标
#def 表示矩阵的迹。
#prop 等价表示的特征标相同。
#prop 特征标是类的函数。

## 酉表示
#def 保持内积不变的群表示。
#prop $A(g_\alpha)^\dagger = A(g_\alpha)^{-1}$。

## 群代数与群函数
### 群空间
#def 群元的线性组合构成的空间。
#denote $V_G$。

### 群代数
#def 群空间上的乘法规则构成的代数。
#denote $R_G$。

### 群函数
#def 群到复数域的函数。
#denote $f(g_\alpha)$。

## 正则表示
### 左正则表示
#def 群代数空间上的线性变换。
#denote $L(G)$。

### 右正则表示
#def 群代数空间上的线性变换。
#denote $R(G)$。

## 有限群表示理论
### 舒尔引理一
#def 不可约表示下的线性变换。
#prop $M = \lambda E$。

### 舒尔引理二
#def 不等价不可约表示间的线性变换。
#prop $M \equiv 0$ 或表示等价。

### 正交性定理
#def 不等价不可约酉表示矩阵元的正交关系。
#prop $\langle A_p^{\mu\nu} | A_r^{\mu'\nu'} \rangle = \frac{1}{S_p}\delta_{pr}\delta_{\mu\mu'}\delta_{\nu\nu'}$。

### Burnside 定理
#def 不等价不可约酉表示维数平方和等于群阶。

## 特征标理论
### 特征标第一定理
#def 不可约表示特征标的正交关系。
#prop $(\chi_p | \chi_r) = \delta_{pr}$。

### 特征标第二定理
#def 类函数空间中特征标的正交关系。
#prop $\frac{1}{n}\sum_{p=1}^q n_i \chi_p^*(K_i) \chi_p(K_j) = \delta_{ij}$。

## 新表示的构成
### 直积表示
#def 两个表示的矩阵直积。
#denote $C(g_\alpha) = A(g_\alpha) \otimes B(g_\alpha)$。

### 直积群的表示
#def 直积群的表示构造。
#denote $C(g_{1\alpha}, g_{2\beta}) = A(g_{1\alpha}) \otimes B(g_{2\beta})$。

### 诱导表示
#def 子群表示诱导出的群表示。
#denote $HU_B(g)$。
## 
# 群表示理论-GroupRepresentationTheory-DeepSeek

## 2.1 群表示的基本概念
### 线性空间
#def 数域 $K$ 上的向量集合 $V$，满足加法与数乘的封闭性及线性空间公理  
- **例**：多项式空间 $\mathbb{P}_n$，正实数空间 $\mathbb{R}^+$（定义 $x+y=xy$，$tx=x^t$）

### 线性变换
#def 映射 $A: V \to V$，满足 $A(ax+by) = aA(x)+bA(y)$  
#property 在基矢 $\{e_i\}$ 下，线性变换由矩阵 $[A]$ 表示，满足 $[y] = [A][x]$  
#property 基变换下，矩阵关系为 $[A'] = [P^{-1}][A][P]$（相似变换）

### 群表示
#def 群 $G$ 到线性变换群 $L(V, \mathbb{C})$ 的同态映射 $A$，满足：  
$$
A(g_\alpha g_\beta) = A(g_\alpha)A(g_\beta)
$$
#denote 忠实表示：同态为同构（单射+满射）  
#example 
1. **恒等表示**：所有群元映射为单位矩阵  
2. **$D_3$ 在 $\mathbb{R}^3$ 中的表示**：  
$$
A(d) = \begin{pmatrix}
-\frac{1}{2} & -\frac{\sqrt{3}}{2} & 0 \\
\frac{\sqrt{3}}{2} & -\frac{1}{2} & 0 \\
0 & 0 & 1
\end{pmatrix}
$$

---

## 2.2 等价表示与不可约表示
### 等价表示
#def 若存在相似变换 $P$ 使得 $A'(g_\alpha) = P^{-1}A(g_\alpha)P$，则 $A$ 与 $A'$ 等价  
#property 等价表示的特征标相同  

### 不可约表示
#def 若表示空间 $V$ 无真不变子空间，则称为不可约表示  
#prop **完全可约性**：有限群的表示可分解为不可约表示的直和  
$$
A(g_\alpha) = \bigoplus_p m_p A_p(g_\alpha)
$$
#example 
1. **$C_2$ 群的 $\mathbb{R}^3$ 表示**：分解为 $A_1 \oplus 2A_2$  
2. **$SO(2)$ 的表示**：二维旋转矩阵分块对角化  

---

## 2.3 酉表示与正交性定理
### 酉表示
#def 表示矩阵满足 $A(g_\alpha)^\dagger = A(g_\alpha)^{-1}$  
#property 酉表示可约则完全可约  

### 正交性定理
#prop 对不等价不可约酉表示 $A^p$ 和 $A^r$，有：  
$$
\frac{1}{|G|} \sum_{g \in G} A_{\mu\nu}^p(g) A_{\mu'\nu'}^{r*}(g) = \frac{1}{d_p} \delta_{pr} \delta_{\mu\mu'} \delta_{\nu\nu'}
$$
#prop **Burnside 定理**：有限群不等价不可约表示的维数平方和等于群阶  
$$
\sum_p d_p^2 = |G|
$$

---

## 2.4 特征标理论
### 特征标
#def $\chi^p(g) = \operatorname{tr} A^p(g)$，是类的函数  
#property **正交性**：  
$$
\frac{1}{|G|} \sum_{g \in G} \chi^{p*}(g) \chi^r(g) = \delta_{pr}
$$
#denote 特征标表：以类的个数为列，不可约表示为行的正交表  

### 例：$D_3$ 群特征标表
| $D_3$ | $\{e\}$ | $2\{C_3\}$ | $3\{C_2\}$ |
|-------|---------|------------|------------|
| $A_1$ | 1       | 1          | 1          |
| $A_2$ | 1       | 1          | -1         |
| $A_3$ | 2       | -1         | 0          |

---

## 2.5 新表示的构造
### 直积表示
#def 若 $A$ 和 $B$ 是群 $G_1$ 和 $G_2$ 的表示，则 $C(g_1, g_2) = A(g_1) \otimes B(g_2)$ 是 $G_1 \otimes G_2$ 的表示  
#property 直积群的不可约表示由因子群的不可约表示直积生成  

### 诱导表示与分导表示
#def **诱导表示**：从子群 $H$ 的表示构造群 $G$ 的高维表示  
#def **分导表示**：将群 $G$ 的表示限制到子群 $H$ 上  
#prop **弗罗宾尼斯互易定理**：诱导表示与分导表示的重复度相等  

---

## 2.6 应用示例
### 正四面体群 $T$ 与正八面体群 $O$
#example 
- **$T$ 群**：12 个元素，特征标表含 1 个三维表示  
- **$O$ 群**：24 个元素，特征标表含 2 个三维表示（见表 2.5）  

### 晶体对称性
#example 正方体沿体对角线拉伸后，对称群退化为 $D_3$，其表示分解为：  
$$
A_4|_{D_3} = B_2 \oplus B_3, \quad A_5|_{D_3} = B_1 \oplus B_3
$$

---

**关键公式总结**  
- 正交性定理：  
$$
\frac{1}{|G|} \sum_{g \in G} \chi^{p*}(g) \chi^r(g) = \delta_{pr}
$$
- Burnside 定理：  
$$
\sum_p d_p^2 = |G|
$$