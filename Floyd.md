### 1.Floyd

令 $f_{k,i,j}$ 表示从$i$号结点到$j$号结点只经过编号为$1$~$k$的结点的路径中最短的路程

则 $f_{k,i,j}=\min\{f_{k-1,i,j},f_{k-1,i,k}+f_{k-1,k,j}\}$

而当 $f_{k-1,k,k} \geq 0$ 时， $f_{k,i,k}=f_{k,k,i}=f_{k-1,i,k}$，$f_{k,i,j}$也只依赖于$f_{k-1,i,k}$， $f_{k-1,k,j}$和$f_{k,i,j}$，因此可以使用滚动优化把第一维优化掉

代码：
```cpp
// f[i][j]初始为邻接矩阵
for (int k = 1; k <= n; k++) {
    for (int i = 1; i <= n; i++) {
        for (int k = 1; k <= n; k++) {
            f[i][j] = min(f[i][j], f[i][k] + f[k][j]);
        }
    }
}
```

### 2.倍增Floyd
对邻接矩阵定义矩阵运算：$(A*B)_{i,j}=\min\limits_{1\leq k \leq n}
\{A_{i,k}+B_{k,j}\}$

可以证明这个运算是满足结合律的

记$F^p$表示$\underbrace{F*F*\dots *F}_{p \text{个F}}$

若$F是邻接矩阵$，则$(F^p)_{i,j}$表示从结点$i$到结点$j$**恰好**走$p$步的最短的路程

因为这个运算满足结合律，所以可以用快速幂来求$F^p$

代码：
```cpp
// f[p][i][j]表示从i到j恰好走2^p步的最短路
for (int p = 1; (1 << p) <= nStep; p++) {
    // 里面三层循环可以任意交换顺序
    for (int k = 1; k <= nV; k++) {
        for (int i = 1; i <= nV; i++) {
            for (int j = 1; j <= nV; j++){
                f[p][i][j] = min(f[p][i][j], f[p-1][i][k] + f[p-1][k][j]);
            }
        }
    }
}
```

Floyd和倍增Floyd也能够用在最长路问题上