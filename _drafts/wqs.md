---
title: wqs二分
layout: posts
tags: OI notes
---

https://pufanyi.github.io/%E7%94%9F%E6%88%90%E6%A0%91%E5%85%A5%E9%97%A8/Train2012-sol-wqs.pdf

Lagrange sufficiency theorem: 对于问题$P$：使 $f(x)$ 最小化，其中 $g(x)=b, x\in X$ 那么若无限制问题 $P'$：使 $f(x)-\lambda g(x)$ 最小化， 若解为 $x_*$ 满足 $g(x_*) = b$，那 $x_*$ 也是原问题的一个解

这时候，如果 $g(x_*)$ 关于 $\lambda$ 有单调性，就可以通过二分 $\lambda$ 和解决 $P'$ （比 $P$ 简单）来找到答案，这也意味着 $P(b)$ 具有凸性

经典题目：

最小黑白生成树
