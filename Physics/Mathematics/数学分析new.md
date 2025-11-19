
- d 在x处不连续：左右极限存在-简单不连续（第一类）；else 第二类
    - p 左极限的等价定义（直接用距离而不是点列，其实我觉得没什么区别）$f:(a,b):\quad f(x-) = A \iff \forall \varepsilon > 0, \exists \delta > 0\text{ with } a < x - \delta, \forall t\in (x - \delta, x),|f(t) - A| < \varepsilon$ 
- d 单调函数：$f: X \to \mathbb{R}$，若 $y > x \Rightarrow f(y) \geq f(x)$ 则为单调递增；若 $f(y) > f(x)$ 则为严格单调递增
- p 单调函数在每点都有左右极限
- p （单增为例）sup f（x）＝f（x-）≤ f（x+）＝ inf f（x）
- p 单调函数的不连续点的集合 可数

---
**微分**

- d **导数**：变化率极限，$f'(x) = \lim_{t \to x} \frac{f(t) - f(x)}{t - x}$
- **可微必连续**
- 导数的运算：加乘除，链式法则

- d **（局部）极值**：若 $\exists\delta > 0$ 使得 $f(x)$ 在 $X \cap (x_0 - \delta, x_0 + \delta)$ 上取得最大（小）值，则称 $f$ 在 $x_0$ 处取得局部最大（小）值。
    -  **与一阶导关系（必须在开集）**：若 $f$ 在 $x \in (a, b)$ 处可微且取得局部极值，则 $f'(x) = 0$。
        - 注意：存在鞍点（如 $f(x) = x^3$ 在 $x = 0$）使得 $f'(x) = 0$ 但不是极值点

---
- p **连续函数介值定理：（区间中函数值一定连续变化）** 若 $f$ 在 $[a, b]$ 上连续，且 $f(a) \leq \kappa \leq f(b)$，则存在 $x_0 \in [a, b]$ 使得 $f(x_0) = \kappa$ 
- p **Rolle定理：** 闭区间连续、开区间可微函数：**两端点等高 → 内部存在极值**
    - coro **开区间可微且导数无0 → 严格单调**
- p **广义中值定理**：若 $f, g$ 闭区间连续、开区间可微，则存在 $x \in (a, b)$ 使得 $[f(b) - f(a)] g'(x) = [g(b) - g(a)] f'(x)$ （或 $\frac{f(b)-f(a)}{g(b)-g(a)}=\frac{f'(x)}{g'(x)}$ ）
    - p **中值定理（取g(x)＝x）**：$f(b) - f(a) = (b - a) f'(x)$ 
    - coro **导数范围确定两端函数值差的可能范围**，若 $\mu \leq f'(x) \leq m$ 对所有 $x \in (a, b)$ 成立，则对 $a \leq x_1 \leq x_2 \leq b$ 有 $\mu(x_2 - x_1) \leq f(x_2) - f(x_1) \leq m(x_2 - x_1)$ 
- p **若 $f'(x) \equiv 0$，则 $f$ 为常数函数**
    - 若 $f'(x) \equiv \gamma$，则 $f(x) = \gamma x + c$ 
    - 若 $f' = \gamma f$，则 $f(x) = f(0) e^{\gamma x}$ 
- d **Lipschitz连续**：$|f(x_2) - f(x_1)| \leq M |x_2 - x_1|$ 
- p  **$|f'(x)| \leq \gamma |f(x)|$ 有零点则全为0**
    - coro **一阶常微分方程** $f'(x) = \phi(f(x))$，$\phi$ Lipschitz连续，加边界条件 $f(a) = c$，则解唯一

---
- p **极值与二阶导**：若 $f'(x_0) = 0$，$f''(x_0) > 0$，则 $f$ 在 $x_0$ 处取得严格局部极小值
- p **导数介值定理（Darboux定理）**：若 $f$ 在 $[a, b]$ 上可微，且 $f'(a) < \lambda < f'(b)$，则存在 $x \in (a, b)$ 使得 $f'(x) = \lambda$
    - *注*：这里导数**不一定连续**，如 $f(x)=x^{2}\sin \frac{1}{x^{2}} \text{ if }x\neq 0\text{ else }0$ ，在0处导数不连续（导数震荡）
- p **洛必达法则**：若 $f, g$ 在 \((a, b)\) 上可微，$g'(x) \neq 0$，且 $f(x), g(x) \to 0$（或 $\to \infty$）当 $x \to a$，且 $\frac{f'(x)}{g'(x)} \to A$，则 $\frac{f(x)}{g(x)} \to A$ 
- p **Taylor定理**：若 $f^{(n)}$ 在 $(a, b)$ 上存在，$a<\alpha<\beta<b$ ，则存在 $x \in(\alpha,\beta)$ 使得 $f(\beta) = \sum_{k=0}^{n-1} \frac{f^{(k)}(\alpha)}{k!} (\beta - \alpha)^k + \frac{f^{(n)}(x)}{n!} (\beta-\alpha)^n$ 

---
- d **凹函数（西方国家一般称为 convex（（下）凸），本笔记中对应名词为凹）**：若对任意 $x_0, x_1 \in I$，$t \in [0, 1]$，有 $f((1-t)x_0 + t x_1) \leq (1-t)f(x_0) + t f(x_1)$ 
- p **凹函数与导数（开区间上）的关系**：
    - $f$ 凹 $\iff f'$ 单调不减（不严格的单调增）
    - 若 $f''(x) \geq 0$ 则 $f$ 凹；若 $f''(x) > 0$ 则严格凹 
- p **凹函数的组合的性质**：
    - **一族凹函数的上确界仍凹**，即 $f(x)=\mathrm{sup} \{f_{i}(x)\}$ 凹
    - **正且单增的凹函数的乘积仍凹**，即 $g(x),h(x)>0$ 且单增，则 $g(x)h(x)$ 凹
    - **凹函数与单增凹函数的复合仍凹**，即 $f,g$ 凹且 $g$ 单增，则 $g\circ f$ 凹
- 凹函数的代数性质
    - 凹函数有 $\frac{f(b)-f(a)}{b-a} \le \frac{f(c)-f(b)}{c-b}$ 
    - p **Jensen不等式**：若 $f$ 凹，$\alpha_i \geq 0$，$\sum \alpha_i = 1$，则 $f(\sum \alpha_i x_i) \leq \sum \alpha_i f(x_i)$ 

---
**积分**

- d **分割（partition）** 及其 **细化（refinement）** 
- 积分因子（integrator） $\alpha$ ：单调增
- d **达布上和**（Darboux upper sum，或上积分和）：$U(P,f,\alpha)=\sum_{i=1}^{n} \left(\mathrm{sup}_{[x_{i},x_{i+1}]}f(x)\right)\Delta\alpha_{i}$ 
    - 下和（lower sum）类似
    - p 分割细化后：细化的上和 ≤ 原上和，细化的下和 >= 原下和
- d **黎曼上积分**：$U$ 在取不同分割时的下确界
    - 下积分类似
    - p 下积分 ≤ 上积分
- **黎曼可积**，通常记为 $f \in \mathcal{R}(\alpha)$ ，$\alpha$ 为积分因子
    - $f \in \mathcal{R}(\alpha)\iff$ 上积分 == 下积分
    - p **达布准则**：$\forall\varepsilon,\exists P,U(P,f,\alpha)-L(P,f,\alpha)<\varepsilon$ 
- 积分定理
    - p 连续函数可积
    - p 积分因子连续时，单调函数可积
    - p 积分因子在不连续点连续时，有限不连续点的函数可积
- 函数组合的积分关系：
    - p 连续函数（一定一致连续）和可积函数的复合可积
    - 和、数乘：可积性传递，积分和、数乘
    - 不等关系：积分的不等关系
    - 区间和：积分和
    - 积分因子和、数乘 → 积分和、数乘
- p $\phi:[A,B]\to [a,b]$ 是连续严格增的满射，则 $f\in \mathcal{R}(\alpha)\implies g\in \mathcal{R}(\beta),\int_{A}^{B}gd\beta=\int_{a}^{b}fd\alpha$ 
    - coro 变量代换
- p 分部积分
- **积分与微分的关系** 
    - p 积分 → 微分：$F(x)=\int_{a}^{b}f(x)dx$ 连续；若 $f$ 在 $x_{0}$ 连续，则 $F$ 在 $x_{0}$ 处可微，且 $F'(x_{0})=f(x_{0})$ 
    - p 微分 → 积分：$f \in \mathcal{R}$ ，若 $f=F'$ ，则 $\int_{a}^{b}f(x)dx=F(b)-F(a)$ 
---
- p $f:[a,b]\to \mathbb{R}^{k}$ 的一个不等式：**积分的模 ≤ 模的积分**
- d **曲线（curve）**：连续映射 $\gamma:[a,b]\to \mathbb{R}^{k}$ 
    - $\gamma$ 为单射 ⇒  arc（单射弧）
    - $\gamma(a)=\gamma(b)$ ⇒ 闭合曲线（closed curve）
    - d **可求长**性：$\gamma'$ 连续 ⇔ 可求长，$\Lambda(\gamma)=\int_{a}^{b}\left| \gamma'(t) \right|dt$ 

---
**函数项序列（函数列）**

- d $\left\{ f_{n} \right\},f_{n}:E\to \mathbb{R}$ 
- d **极限函数**：$f(x)=\lim_{ n \to \infty }f_{n}(x)$ ；极限函数存在则**函数列收敛**

> **Question**：函数的性质是否被极限运算保持？（函数的一些运算操作是否可以和极限运算交换）

- **例**：
    - $f_{n}(x)=x^{n}$ 连续，但极限函数不连续
    - $f_{n}(x)=\frac{x^{2}}{(1+x^{2})^{n-1}}$ 连续，但函数项级数不连续

- d **一致收敛**：$\forall\varepsilon,\exists N,$ 使得 $\forall n\geq N,\forall x\in E,\ \left| f_{n}(x)-f(x) \right|<\varepsilon$ 
    - 保证对于**所有 x** ，都有一个**共同的**最低收敛速度
    - **等价定义**：$\forall\varepsilon,\exists N,$ 使得 $\forall m,n>N,\forall x \in E,\ \left| f_{n}(x)-f_{m}(x) \right|<\varepsilon$ 
    - p $f_{n}\to f$ ，记 $M_{n}=\mathrm{sup}_{x \in E}\left| f_{n}(x)-f(x) \right|$ ，若 $M_{n}\to 0$ ，则一致收敛


- d **函数项级数**：$f(x) = \sum_{n=1}^{\infty}f_{n}(x)$ 
- p 函数项级数一致收敛条件：使用函数列一致收敛条件
- ……