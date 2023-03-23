---
title: 2维DP四边形不等式优化（决策单调性优化）
layout: posts
tags: OI notes
---

Knuth-Yao quadrangle inequality speedup

cost满足区间包含单调性+四边形不等式

cost与k也有关，Borchers, Gupta, 1993论文, Extending the quadrangle inequality to speed-up dynamic programming

```cpp

struct Opt {
    int v, k;
} f[N][N];

int F(int i, int j, int k);

void DP() {
    for (int i = 1; i <= n; i++) {
        f[i][i] = (Opt){0, -1};
        for (int j = i + 1; j <= n; j++) {
            f[i][j] = (Opt){1 << 30, -1};
        }
    }
    for (int i = 1; i < n; i++) {
        f[i][i+1] = (Opt){F(i, i+1, i), i};
    }
    for (int len = 3; len <= n; len++) {
        for (int i = 1, j = len; j <= n; i++, j++) {
            int kl = f[i][j - 1].k;
            int kr = f[i + 1][j].k;
            for (int k = kl; k <= kr; k++) {
                int v = F(i, j, k);
                if (v <= f[i][j].v) {
                    f[i][j] = (Opt){v, k};
                }
            }
        }
    }
    printf("%d\n", f[1][n].v);
}
```
