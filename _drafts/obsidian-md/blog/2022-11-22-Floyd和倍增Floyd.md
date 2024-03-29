### 1.Floyd

能解决没有负环的图上的多源多汇的最短/最长路问题

修改之后能用来计算连通性（传递闭包），找无向图最小环和检测负环

令 $f_{k,i,j}$ 表示从 $i$ 号结点到 $j$ 号结点只经过 $i$ , $j$ 和 $1$ 到 $k$ 号结点的最短路径

初始状态
$$
\begin{cases}
f_{0,i,i}=0\\
f_{0,i,j}=w&如果i到j有一条权值为w的边（重边就选最小的）\\
f_{0,i,j}=+\infty&如果i到j没有边
\end{cases}
$$

转移方程
$$ f_{k,i,j}=\min\{f_{k-1,i,j},f_{k-1,i,k}+f_{k-1,k,j}\} $$

可以证明第一维是可以被滚动优化掉的

代码：
```cpp
// 关于k的循环必须在最外层（因为第一维被滚动掉了）
for (int k = 1; k <= n; k++) {
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            f[i][j] = min(f[i][j], f[i][k] + f[k][j]);
        }
    }
}
```

显然最长路就是把 min 变成 max

### 2.倍增Floyd

用来解决限定步数的最短/最长路问题

定义矩阵运算：$(A*B)_{i,j}=\min\limits_{1 \leq k \leq n}\{A_{i,k}+B_{k,j}\}$

单位元是除了对角线上是 $0$ 其余位置都是 $\infty$ 的矩阵

可以证明这个运算是满足结合律的

令 $F^p$ 表示 $\underbrace{F*F* \dots *F}_{p\text{个F}}$ (因为满足结合律所以无论怎么加括号结果都是一样的)

若 $F$ 是邻接矩阵，则 $(F^p)_{i,j}$ 表示从结点 $i$ 到结点 $j$ **恰好** 走 $p$ 步的最短路径

可以用快速幂计算 $F^p$

最长路就是把 min 变成 max，单位元变成除了对角线上是 $0$ 其余位置都是 $-\infty$ 的矩阵

代码：
```cpp
// f[p][i][j]表示从i到j恰好走2^p步的最短路
// 初值：f[0][i][j]=infinity, 如果(i,j)没有边，否则f[0][i][j]=w(i,j)
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

// 计算走恰好nStep的最短路，结果存在G数组里面
memset(G, 0x3f, sizeof(G));
for (int i = 1; i <= nV; i++) {
    G[i][i]=0;
}

for (int p = 0; (1<<p) <= nStep; p++) { // 和快速幂一样
    if (((1<<p) & nStep) == 0) {
        continue;
    }
    memset(F, 0x3f, sizeof(F));
    for (int k = 1; k <= nV; k++) {
        for (int i = 1; i <= nV; i++) {
            for (int j = 1; j <= nV; j++) {
                F[i][j] = min(F[i][j], G[i][k] + f[p][k][j]);
            }
        }
    }
    memcpy(G, F, sizeof(F));
}
```
