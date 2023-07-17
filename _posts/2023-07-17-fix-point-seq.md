---
title: 不动点法求数列通项
tags: 数学
last_modified_at: 2023/07/17 
---

今天复习数列，碰到了这个东西。

假设我们有这样的一个递推式 $a_{n+1}=f(a_n)$，那么要求它的通项公式。我们可以先求出它的不动点 $x_f=f(x_f)$，然后在递推式两端减去不动点 $a_{n+1}-x_f=f(a_n)-f(x_f)$ 这样有时候能凑出一些特殊的容易处理的结构。

下面是几个例子。

##### 1

$a_{n+1}=\lambda a_n+t$，其中$\lambda\neq 1$

首先求不动点 $x_f=\lambda x_f+t$ 显然是有解的

然后两式相减得 $a_{n+1}-x_f=\lambda(a_n-x_f)$

于是 $a_n=(a_1-x_f)\lambda^{n-1}+x_f$

##### 2

$a_{n+1}=\frac{ka_n+t}{sa_n+p}$，其中对于所有 $n\in\mathbb{N^+}$，$sa_n+p\neq0$ 且 $s\neq0$，$pk\neq st$，$p,k,s,t\in\mathbb{R}$

求不动点
$$
\begin{aligned}
x&=\frac{kx+t}{sx+p}\\\\
&\iff \frac{sx^2+(p-k)x-t}{sx+p}=0\\\\
&\iff sx^2+(p-k)x-t=0&&\text{不会有增根，因为}pk\neq st
\end{aligned}
$$
我们把复数解也考虑进来，那么不动点有1个或者2个

式子两端减去一个不动点 $x_f$
$$
\begin{aligned}
a_{n+1}-x_f&=\frac{ka_n+t}{sa_n+p}-\frac{kx_f+t}{sx_f+p}\\\\
&=\frac{(ka_n+t)(sx_f+p)-(kx_f+t)(sa_n+p)}{(sa_n+p)(sx_f+p)}\\\\
&=\frac{(pk-st)(a_n-x_f)}{(sx_f+p)(sa_n+p)}
\end{aligned}
$$
如果只有一个不动点，那么由 $(p-k)^2+4st=0$ 可得 $pk-st=(sx_f+p)^2$ 由此，对上式两端取倒数，然后进行一定处理后能得到 $\frac{1}{a_n-x_f}$ 形成等差数列(如果$a_n$不是全为$x_f$的常数列)

如果有两个不动点，记为 $x_1,x_2$，那么有
$$
a_{n+1}-x_1=\frac{(pk-st)(a_n-x_1)}{(sx_1+p)(sa_n+p)}\\\\
a_{n+1}-x_2=\frac{(pk-st)(a_n-x_2)}{(sx_2+p)(sa_n+p)}
$$
做商(假设$a_n$不是常数列，那么两式都不为0)
$$
\frac{a_{n+1}-x_1}{a_{n+1}-x_2}=\frac{sx_2+p}{sx_1+p}\frac{a_n-x_1}{a_n-x_2}
$$
于是 $\frac{a_{n}-x_1}{a_n-x_2}$形成等比数列

其中不动点为复数的情况比较有意思，它们对应的是周期数列(证明见参考资料)

##### 3

$$
\begin{aligned}
a_1&=2\\\\
a_{n+1}&=\frac{1}{2}(a_n+\frac{2}{a_n})
\end{aligned}
$$

牛顿迭代法求 $\sqrt{2}$

首先 $x=\frac{1}{2}(x+\frac{2}{x})$ 得 $x_{1,2}=\sqrt{2},-\sqrt{2}$

式子两端各自减去两个不动点，然后再做商可得
$$
\frac{a_{n+1}+\sqrt{2}}{a_{n+1}-\sqrt{2}}=(\frac{a_n+\sqrt{2}}{a_n-\sqrt{2}})^2\\\\
\frac{a_n+\sqrt{2}}{a_n-\sqrt{2}}=(1+\sqrt{2})^{2^n}\\\\
a_n=\frac{(1+\sqrt{2})^{2^n}+1}{(1+\sqrt{2})^{2^n}-1}\sqrt{2}
$$




### 参考资料

1. https://zhuanlan.zhihu.com/p/104544760
2. https://www.zhihu.com/question/566595014/answer/2758066742
