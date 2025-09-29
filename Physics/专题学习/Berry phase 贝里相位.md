## 定义
Berry相位（Berry phase），又称贝里相位，是量子力学中的一种几何相位，由英国物理学家Michael Berry于1984年系统提出。它描述的是量子系统在参数空间经历绝热循环演化时波函数积累的额外相位，与系统的几何性质密切相关，而非动力学过程的时间积累。
## 数学描述
$$\begin{align} \\
 H= & H(R), \text{with a eigenstate } \ket{n}  \\
 R\to  & R+dR \\
 \implies  & \begin{cases}
H(R)\to H(R)+\nabla_{R}H\cdot dR \\
 \ket{n} \to \ket{n}+\nabla_{R}\ket{n}dR=\ket{n} e^{ -id\gamma _{n} }
\end{cases}  \\
 \implies & \text{Phase change: }  d\gamma_{n}=-\mathrm{Im}\ln(\braket{ n(R) | n(R+dR) } )=\bra{n} i\nabla_{R}\ket{n}  
\end{align}$$
- **拓展**：量子力学中的规范变换：给态附加相位
	-  #？？？ 
- *注*：全局规范变换不会影响 $d\gamma_{n}$ ，但局域规范变换会影响

- **定义**：Berry connection
$$
A_{n}=\frac{d\gamma_{n}}{dR}=\bra{n} i\nabla_{R}\ket{n}
$$

- **例**：……  【 #推导 】
# 贝里曲率

Berry connection 的 **“旋度”**，表示的是 *经过一个微小的变化回到原位之后，较之前的相位变化*。