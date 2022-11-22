# Dijkstra最短路算法

## 算法过程
1. 初始化：$$ f_{start}=0 $$, $$ f_{other}=\infty $$, 所有点染为蓝色
2. 若没有蓝色点，结束
3. 从蓝色点选出$$ f $$最小的，记为$$ u $$
4. 把$$ u $$染为黑色
5. $$ u $$通过以它为起点的边对周围节点进行松弛(修改$$ f $$)
6. 回到2

## 复杂度分析
2的选最小的操作会执行$$ n $$次

3的松弛操作会执行$$ m $$次

&nbsp;

### 暴力

选f最小的点的复杂度 $$ \mathcal{O}(n^2) $$

松弛复杂度 $$ \mathcal{O}(m) $$

复杂度 $$ \mathcal{O}(n^2+m) = \mathcal{O}(n^2) $$


&nbsp; 


### 堆

选f最小的点的复杂度 $$ \mathcal{O}(n\log{}n) $$

松弛复杂度 $$ \mathcal{O}(m\log{}n) $$

复杂度 $$ \mathcal{O}((n+m)\log{}n) = \mathcal{O}(m\log{}n) $$

&nbsp;


### 优先队列

选f最小的点的复杂度 $$ \mathcal{O}(n\log{}m) $$

松弛复杂度 $$ \mathcal{O}(m\log{}m) $$

复杂度 $$ \mathcal{O}((n+m)\log{}m) = \mathcal{O}(m\log{}m) $$