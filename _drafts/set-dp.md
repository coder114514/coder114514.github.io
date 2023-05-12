---
title: 集合DP
category: OI笔记
tags: OI OI笔记
last_modified_at: 2023/04/17
---

适用于能在子集上合并的东西: $x(A+B)=x(A)+x(B)$ 若 $AB=\empty$

$f[msk][p]$ msk改变后p位能形成的msk子集/超集的结果

以加法为例,

子集dp: $f[msk][p]=f[msk][p-1]+f[msk \oplus 2^{p-1}][p-1]$若 msk 的第p位是1,否则 $f[msk][p]=f[msk][p-1]$

超集dp: $f[msk][p]=f[msk][p-1]+f[msk \oplus 2^{p-1}][p-1]$若 msk 的第p位是0,否则 $f[msk][p]=f[msk][p-1]$

外层循环p,内层循环msk,p这一维可以滚动,且枚举p的循环枚举顺序可以任意

