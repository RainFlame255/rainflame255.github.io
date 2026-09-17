---
layout: default
title:  数论学习笔记 -> exEuler 证明
---

<script>
  MathJax = {
    tex: { inlineMath: [['$', '$'], ['\\(', '\\)']] }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# 数论学习笔记 —— exEuler 证明



## 命题

对于式子 $a^b(\mod m)$ , 当 $b\ge \varphi(m)$ 时, 有:

$$
a^b \equiv a^{b\mod \varphi(m)+\varphi(m)}(\mod m)
$$




## 证明

先分为以下两种情况讨论:




### Case 1: $a$ 与 $m$ 互质

此时情形退化为euler定理的适用情形, 有:

$$
a^b \equiv a^{b\mod \varphi(m)}(\mod m)
\newline
a^\varphi(m)\equiv 1(\mod m)
$$

两组方程相乘, 有:

$$
a^b \equiv a^{b\mod \varphi(m)+\varphi(m)}(\mod m)
$$

Case 1 讨论结束.





### Case 2: $a$ 与 $m$ 不互质

对 $m$ 进行质因数分解: $m=p_1^{t_1}p_2^{t_2}\cdots p_n^{t_n}$

接下来, 只需证明对于任意 $p_i^{t_i}$ , $a^b$ 与 $a^{b\mod \varphi(m)+\varphi(m)}$ 对这个质数取余的结果相等即可.




#### 简要证明:

质因数分解保证 $p_i^{t_i}$ 对于不同的 $i$ 互质, 因此可以将问题转化为:

###### 若 $a\equiv b(\mod m_1), a\equiv b(\mod m_2), \gcd(m_1, m_2)=1$ , 则 $a\equiv b(\mod m_1m_2)$

证明是容易的. 由上述条件, 可知 $a-b$ 同时是 $m_1$ 和 $m_2$ 的倍数, 又 $m_1, m_2$ 互质, 因此 $a-b$ 是 $m_1m_2$ 的倍数, 命题得证.




回到原命题的证明上.

讨论 $a$ 与 $p_i$ 的关系.




### Case 2-i $a$ 与 $p_i^{t_i}$ 互质

$\varphi(m)是\varphi(p_i^{t_i})$ 的倍数 (因为 $\varphi$ 是积性函数) 
此时也退化到了euler定理的适用情形, 即Case 1. 证明见上面的Case 1.





### Case 2-ii $a$ 与 $p_i{t_i}$ 不互质

此时必有 $p_i|a$ , 即 $a$ 可表示为 $kp_i$ 的形式.

接下来分别考虑 $a^b$ 和 $a^{b\mod \varphi(m)+\varphi(m)}(\mod m)$ 与 $p_i^{t_i}$ 的关系.


由命题的先决约束, 可知 $b\ge\varphi(m)$ , 又因为 $\varphi$ 是积性函数, $\varphi(m)\ge\varphi(p_i^{t_i})$

又 $\varphi(p_i^{t_i})=(p_i-1)p_i^{t_i-1}$ , 可以由此得知 $\varphi(p_i^{t_i})\ge t_i$

又等式的传递, 可知 $b\ge t_i$ 以及 $b\mod \varphi(m)+\varphi(m) \ge t_i$ , 因此可得 $a^b\equiv 0(\mod p_i^{t_i})$ 以及 $a^{b\mod \varphi(m)+\varphi(m)}\equiv 0(\mod p_i^{t_i})$





命题得证.