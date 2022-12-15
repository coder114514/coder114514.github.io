# 洛谷 P1654 OSU

令$$S_i$$表示$$1..i$$的分数（随机变量），$$L_i$$表示从$$i$$往前的连续1的长度（随机变量），$$a_i=0/1$$表示第$$i$$位是否命中，$$p_i$$表示第$$i$$位命中的概率

$$S_0=0$$
$$S_i=\begin{cases}  
S_{i-1} & a_i==0,概率为1-p_i\\
S_{i-1}+3L_{i-1}^2+3L_{i-1}+1 & a_i==1,概率为p_i
\end{cases}$$

$$L_0=0$$
$$L_i=\begin{cases}
0 & a_i==0,概率为1-p_i\\
L_{i-1}+1 & a_i==1,概率为p_i
\end{cases}$$

$$L_i^2=\begin{cases}
0 & a_i==0,概率为1-p_i\\
L_{i-1}^2+2L{i-1}+1 & a_i==1,概率为p_i
\end{cases}$$

E[L[0]]=0
E[L[i]]=p[i]*(E[L[i-1]]+1)

E[L[0]^2]=0
E[L[i]^2]=p[i]*(E[L[i-1]^2]+2*E[L[i-1]]+1)

E[score[0]]=0
E[score[i]]=E[score[i-1]]+p[i]*(3*E[L[i-1]^2]+3*E[L[i-1]]+1)