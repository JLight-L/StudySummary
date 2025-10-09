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

[VASP](VASP.md)