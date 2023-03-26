---
title: 两道有意思的微积分题目
layout: posts
tags: math notes
---

![](https://c.1ovv.com/2023/03/24/n8jkU.jpeg)

相当于在近似y=1/x在n到2n的曲线下方面积, 所以结果是 $\ln{2n}-\ln{n}=\ln{2}$

![](https://c.1ovv.com/2023/03/24/n8H38.jpeg)

$$
\begin{aligned}
原式&=\lim_{n \to \infty}{\sqrt{n}(\sum_{i=1}^{n}{\frac{\sqrt{i}}{n^2+n\sqrt{i}}})} 说明：1拆成n个1/n各自相减得到\\
&=\lim_{n \to \infty}{\sqrt{n}(\sum_{i=1}^{n}{\frac{i^{\frac{1}{2}}}{n^2}})} 说明：n趋于无穷，n^2增长快过n\sqrt{i}\\
&=\lim_{n \to \infty}{n^{\frac{1}{2}}{\frac{\frac{2}{3}n^{\frac{3}{2}}}{n^2}}} 说明：n趋于无穷，求和相当于积分\\
&=\frac{2}{3}
\end{aligned}
$$
