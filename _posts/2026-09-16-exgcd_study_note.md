---
layout: default
title:  数论学习笔记 -> exGcd
---

# 数论学习笔记 —— exGcd

exGcd 是基于 Gcd 的递归运算，计算形如 $ax+by=c$ 形式的不定方程的解的方法.

### 观察1: 如果 $x_1$ , $y_1$ 是不定方程的一组解, 则 $x_1 + k ( b / \gcd(a, b))$ , $y_1 - k ( a / \gcd(a, b))$ 是不定方程的通解

可以发现相邻两组解中, $a\Delta x$ 必为 $b$ 的倍数, 因此易知 $\delta x = b \ gcd(a, b)$ , 对于 $y$ 同理. 自然得证.

因此, 接下来我们只需求出一组特解即可得到全体通解.

### 性质1: $ax+by$ 的最小正值为 $\gcd(a, b)$, 可通过辗转相除得到

接下来, 将会讲解这个解的求法.

我们在求 gcd 时, 会有一个 $(a, b) \mapsto (b, a \mod b)$ 的一个映射过程.

到最后, 我们可以得到一组值 $(g, 0)$ , $g$ 就是所求的 gcd . 此时, $1\times g + 0\times 0$ 即为 $g$ .

之后将前面所求的 $a'x'+b'y'=g$ 的一组解回传, 求出 $ax+by=g$ 的一组解.

因为:

$$ a'=b
\newline
b'=a-\lfloor a/b \rfloor \times b$$

所以:带入前面的方程, 有:

$$ 
bx'+(a-\lfloor a/b \rfloor \times b)y'=g
\newline
ay'+b(x'-\lfloor a/b \rfloor \times b y')=g
$$

比较系数, 于是得到 $ax+by=g$ 的一组解:

$$
x=y'
\newline
y=x'-\lfloor a/b \rfloor \times b \times y'
$$

得到特解后, 可知:

### 性质2: $ax+by=g$ 有解, 当且仅当 $\gcd(a, b) | g$ ,
### 令 $mul=g/\gcd(a, b)$ , 此时, 对于 $ax+by=\gcd(a, b)$ 的一组特解 $(p, q)$ , 有 $ax+by=g$ 的一组特解 $(p\times mul, q\times mul)$

于是,这个问题得到了解决.

# 题目

[luogu P1082 同余方程 (模板)](https://www.luogu.com.cn/problem/P1082)

题目中的 $ax\equiv b (\mod 1)$ 等价于 $ax+by=1$ , 求出一个特解 $x$ 后, 可得通解形式为 $x+kb$ (本题限制了 $gcd(a, b)=1$ ).

接下来, 因为要求最小正整数解, 将答案对 $b$ 取模即可.

但是需要注意的是, 求出来的 $b$ 可能是负的, 此时需要取模之后再加一个 $b$.

[luogu P1516 青蛙的约会](https://www.luogu.com.cn/problem/P1516)

令青蛙的速度分别为 $v_1, v_2$ , 初始位置分别为 $x_1, x_2$ , 一圈长度为 $L$

此时, 青蛙能相遇, 当且仅当路程差 $\Delta s=s_2-s_1$ 满足: $\Delta s=x_2-x_1+kL$

对此建立方程, 有:

$$p(v_2-v_1)=(x_2-x_1)+kL$$

其中, p即为跳跃次数.

移项:

$$p(v_2-v_1)-kL=x_2-x_1$$

转化为标准的形式, 直接求解即可.

<script>
  MathJax = {
    tex: { inlineMath: [['$', '$'], ['\\(', '\\)']] }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>