# 全同粒子
#def 所有内禀属性都相同的例子
全同粒子在波函数有重叠的情况下会出现不可区分的特性，这在经典情形下是不会出现的。
***
## 体系波函数

>[!faq] Question
>如何描述含有全同粒子体系的波函数？

- 对于一个多粒子体系，体系的右矢空间为所有粒子右矢空间的直积。
- 对于全同粒子体系，为了避免概率的不唯一性，其体系右矢必为交换对称或交换反对称。
### 全同粒子交换
#### 交换算符
#def $N$ 个粒子，$N$ 个态，交换算符 $P_{a_1a_2...a_N}:\ P_{a_1a_2...a_N}\ket{\psi_{1}}\ket{\psi_{2}}...\ket{\psi_{N}} = \left|\psi_{a_1}\right>\left|\psi_{a_2}\right>...\left|\psi_{a_N}\right>$
#denote $\alpha = a_1a_2...a_N,\ \epsilon_\alpha=\begin{cases} +1,\ &\text{if }\alpha\text{ 为偶排列}\\ -1,,\ &\text{if }\alpha\text{ 为奇排列}\end{cases}$
#prop 所有交换算符 $P_\alpha$ 构成一个群，所有 $\epsilon_\alpha P_\alpha$ 也构成一个群
#### 完全对称与完全反对称
#def 
完全对称投影算符 $S=\sum_{\forall a_1a_2...a_N} P_{a_1a_2...a_N}$
完全反对称投影算符 $A=\sum_{\forall \alpha=a_1a_2...a_N} \epsilon_\alpha P_\alpha$
#prop $S, A$ 的本征右矢分别记为 $\left|\psi_S\right>, \left|\psi_A\right>$ ，表示的是总体系的态，且可以有多个本征右矢,有
$$\begin{align}
&P_\alpha \left|\psi_S\right> = \left|\psi_S\right>,\ 
&V_S = span\left\{\left|\psi_{Si}\right>\right\}\\
&P_\alpha \left|\psi_A\right> = \epsilon_\alpha \left|\psi_A\right>,\ 
&V_A = span\left\{\left|\psi_{Ai}\right>\right\}\end{align}
$$
- 对于玻色子而言，$\left|\psi\right> \in V_S$
- 对于费米子而言，$\left|\psi\right> \in V_A$
#prop $SA = AS = 0$，即投影到两个相互正交的子空间，但不一定互补
#prop 
$\forall \alpha,\ P_\alpha S = SP_\alpha = S$
$\forall \alpha,\ P_\alpha A = AP_\alpha = \epsilon_\alpha A$

> #proof 见[重排定理](群论-GroupTheory.md#重排定理)
#### 物理右矢——实际体系的右矢
#def 多全同粒子体系的态矢可以由几个单粒子态矢组合而成，对于玻色子满足完全对称性，对于费米子满足完全反对称性。
#property 物理右矢可能的空间只是整个直积空间的一部分，存在某些态不满足对称性的情况，如费米子的泡利不相容原理。
#prop 投影算符可以将单粒子态的直积投影到实际物理态上，即
- $S\left|\psi_1\right>\left|\psi_2\right>...\left|\psi_N\right>$ 为完全对称态
- $A\left|\psi_1\right>\left|\psi_2\right>...\left|\psi_N\right>$ 为完全反对称态


>*需要归一化*。
## 干涉
**我们可以说，全同粒子之间存在干涉。**
>对于两个粒子分别处在态 $\left|\psi_1\right>,\left|\psi_2\right>$，测量的目标本征态为 $\left|u\right>,\left|u'\right>$
>这里第一个波函数对应第一个粒子，第二个波函数对应第二个粒子
>这里的不干涉指的是测量的结果无法区分两个粒子，但不是全同粒子
>测量的本征态为 $\left|u\right>\left|u'\right>$ 和 $\left|u'\right>\left|u\right>$，对于全同粒子而言这两种情况一致
>这里没有做归一化
>
> ||不干涉|干涉|
> |:--:|:--:|:--:|
> |波函数（概率幅）|$\ket{\psi_{1}}\ket{\psi_{2}}$|$(P_{12}+\epsilon P_{21})\ket{\psi_{1}}\ket{\psi_{2}}$|
> |概率|$(P_{12}+P_{21})\left\|\braket{ u \| \psi_{1} }\braket{ u' \| \psi_{2} }\right\|^2$|$\left\|(P_{12}+\epsilon_{21} P_{21})\braket{ u \| \psi_{1} }\braket{ u' \| \psi_{2} }\right\|^2$|
> 
> 这里不干涉情况也可以写为 $(P_{12}+\epsilon_{21}^2P_{21})\|\left<u\|\psi_1\right>\left<u'\|\psi_2\right>\|^2$
> 
> 与光的结果非常类似，且同样可以解释光的干涉行为，与电磁波有同样的结果
> *P.S. 不同频率的光子也为全同粒子，只是因为相位不稳定所以干涉条纹不可见*

>[!note] 概率干涉项（即平方时的交叉项）为：
>$$2Re\left(\left<\psi_1|u\right>\left<u|\psi_2\right>\left<\psi_2|u'\right>\left<u'|\psi_1\right>\right)$$
>波函数重叠越多，干涉效果越强
> 
> **干涉会影响实际测量粒子时的概率分布，例如最简单的交换力 $\left<\left(x_1-x_2\right)^2\right>_{\pm} = \left<\left(x_1-x_2\right)^2\right>_{distinguishable} \pm 2 \left|\left<\psi_a|x|\psi_b\right>\right|^2$ **

多粒子类似，$Proj$ 表示对应投影算符，$P_\alpha$ 表示置换为 $\alpha$ 次序的置换算符，

||不干涉|干涉|
|:--:|:--:|:--:|
|波函数|$\prod_{i=1}^N\otimes\left\|\psi_i\right>$|$\sum_\alpha \epsilon_\alpha P_\alpha\left(\prod_{i=1}^{N}\otimes\left\|\psi_i\right>\right) = Proj\left(\prod_{i=1}^N\otimes\left\|\psi_i\right>\right)$|
|概率|$\sum_\alpha \|\epsilon_\alpha P_\alpha \left(\prod_{i=1}^N\left<u^{(i)}\|\psi_i\right>\right)\|^2$|$\|\sum_\alpha \epsilon_\alpha P_\alpha \left(\prod_{i=1}^N\left<u^{(i)}\|\psi_i\right>\right)\|^2$|

- **🖊总结**：
	- 对于某个测量量，当多个全同粒子的单粒子态测量结果之间有重叠时，对应多粒子态的测量结果会相对单粒子态出现偏移，测量值越接近，偏移越明显。
		- 玻色子：测量结果间差异更小；波函数接近时，倾向于出现相同的测量结果，表现为凝聚态
		- 费米子：测量结果间差异更大；波函数接近时，测量值仍然倾向于离散分布，而不是得到相同测量值