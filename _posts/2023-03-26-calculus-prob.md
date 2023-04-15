---
title: 两道有意思的微积分题目
layout: posts
tags: math notes
---

![](https://c.1ovv.com/2023/03/24/n8jkU.jpeg)

相当于在近似$y=\frac{1}{x}$在$n$到$2n$的曲线下方面积, 所以结果是 $\ln{2n}-\ln{n}=\ln{2}$

![](https://c.1ovv.com/2023/03/24/n8H38.jpeg)

$$
\begin{aligned}
原式&=\lim_{n \to \infty}{\sqrt{n}(\sum_{i=1}^{n}{\frac{\sqrt{i}}{n^2+n\sqrt{i}}})} && \text{说明：}1{拆成}n{个}\frac{1}{n}{各自相减得到}\\\\
&=\lim_{n \to \infty}{\sqrt{n}(\sum_{i=1}^{n}{\frac{i^{\frac{1}{2}}}{n^2}})} && \text{说明：}n{趋于无穷，}n^2{增长快过}n\sqrt{i}\\\\
&=\lim_{n \to \infty}{n^{\frac{1}{2}}{\frac{\frac{2}{3}n^{\frac{3}{2}}}{n^2}}} && \text{说明：}n{趋于无穷，求和相当于积分}\\\\
&=\frac{2}{3}
\end{aligned}
$$
