---
layout: default
title:  数论学习笔记 -> exEuler
---

<script>
  MathJax = {
    tex: { inlineMath: [['$', '$'], ['\\(', '\\)']] }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# 数论学习笔记 —— exEuler

Euler定理可以很快速地求出在特定情境下, 在模意义下的幂. 但是, 这个算法有一个很大的局限: 底数与模数必须相等 (即 $a^b(\mod m)$ 中, $\gcd(a, m)=1$ ). 此时, 为了使得一般的情形能够被求出, 我们考虑使用 exEuler定理.

### 核心公式: 对于 $a^b(\mod m)$ , 当 $b\ge \varphi(m)$ 时, 有: $a^b\equiv a^{b\mod \varphi(m)+\varphi(m)}(\mod m)$

[证明](/exEuler_proof)比较繁琐, 不在此展开.