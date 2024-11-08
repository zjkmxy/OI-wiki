## 描述

给定多项式 $G\left(x, y\right)$，已知有 $x$ 的多项式 $f\left(x\right)$ 满足：

$$
G\left(x, f\left(x\right)\right)\equiv 0\pmod{x^{n}}
$$

且存在数值 $f_0$ 使 $G\left(x, y\right)$ 满足以下条件：

-   $G(0, f_1) = 0$；
-   $\frac{\partial G}{\partial y}(0, f_1) \neq 0$。

求出模 $x^{n}$ 意义下的 $f\left(x\right)$。

## Newton's Method

考虑倍增。

首先当 $n=1$ 时，$\left[x^{0}\right]G\left(x, f\left(x\right)\right)=0$ 的解需要单独求出。假设中的 $f_1$ 满足条件。

假设现在已经得到了模 $x^{\left\lceil\frac{n}{2}\right\rceil}$ 意义下的解 $f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)$，要求模 $x^{n}$ 意义下的解 $f\left(x\right) = f_n\left(x\right)$。

将 $G\left(x, y\right)$ 对 $y$ 在 $y=f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)$ 处进行泰勒展开，有：

$$
\sum_{i=0}^{+\infty}\frac{\frac{\partial^i G}{\partial y^i}\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)}{i!}\left(f\left(x\right)-f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)^{i}\equiv 0\pmod{x^{n}}
$$

因为 $f\left(x\right)-f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)$ 的最低非零项次数最低为 $\left\lceil\frac{n}{2}\right\rceil$，故有：

$$
\forall 2\leqslant i:\left(f\left(x\right)-f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)^{i}\equiv 0\pmod{x^{n}}
$$

则：

$$
\sum_{i=0}^{+\infty}\frac{\frac{\partial^i G}{\partial y^i}\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)}{i!}\left(f\left(x\right)-f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)^{i}\equiv G\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)+\frac{\partial G}{\partial y}\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)\cdot\left[f\left(x\right)-f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right]\equiv 0\pmod{x^{n}}
$$

$$
f_n\left(x\right)\equiv f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)-\frac{G\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)}{\frac{\partial G}{\partial y}\left(x, f_{\left\lceil\frac{n}{2}\right\rceil}\left(x\right)\right)}\pmod{x^{n}}
$$

或者

$$
f_{2n}\left(x\right)\equiv f_n\left(x\right)-\frac{G\left(x, f_n\left(x\right)\right)}{\frac{\partial G}{\partial y}\left(x, f_n\left(x\right)\right)}\pmod{x^{2n}}
$$

## 例题

### [多项式求逆](./elementary-func.md#多项式求逆)

设给定函数为 $h\left(x\right)$，有：

$$
G\left(x, y\right)=\frac{1}{y}-h\left(x\right)
$$

应用 Newton's Method 可得：

$$
\begin{aligned}
    f_{2n}\left(x\right)&\equiv f_{n}\left(x\right)-\frac{\frac{1}{f_{n}\left(x\right)}-h\left(x\right)}{-\frac{1}{f_{n}^{2}\left(x\right)}}&\pmod{x^{2n}}\\
    &\equiv 2f_{n}\left(x\right)-f_{n}^{2}\left(x\right)h\left(x\right)&\pmod{x^{2n}}
\end{aligned}
$$

时间复杂度

$$
T\left(n\right)=T\left(\frac{n}{2}\right)+O\left(n\log{n}\right)=O\left(n\log{n}\right)
$$

### [多项式开方](./elementary-func.md#多项式开方)

设给定函数为 $h\left(x\right)$，有：

$$
G\left(x, y\right)=y^{2}-h\left(x\right)\equiv 0
$$

应用 Newton's Method 可得：

$$
\begin{aligned}
    f_{2n}\left(x\right)&\equiv f_{n}\left(x\right)-\frac{f_{n}^{2}\left(x\right)-h\left(x\right)}{2f_{n}\left(x\right)}&\pmod{x^{2n}}\\
    &\equiv\frac{f_{n}^{2}\left(x\right)+h\left(x\right)}{2f_{n}\left(x\right)}&\pmod{x^{2n}}
\end{aligned}
$$

时间复杂度

$$
T\left(n\right)=T\left(\frac{n}{2}\right)+O\left(n\log{n}\right)=O\left(n\log{n}\right)
$$

### [多项式指数函数](./elementary-func.md#多项式对数函数--指数函数)

设给定函数为 $h\left(x\right)$，有：

$$
G\left(x, y\right)=\ln{y}-h\left(x\right)
$$

应用 Newton's Method 可得：

$$
\begin{aligned}
    f_{2n}\left(x\right)&\equiv f_{n}\left(x\right)-\frac{\ln{f_{n}\left(x\right)}-h\left(x\right)}{\frac{1}{f_{n}\left(x\right)}}&\pmod{x^{2n}}\\
    &\equiv f_{n}\left(x\right)\left(1-\ln{f_{n}\left(x\right)+h\left(x\right)}\right)&\pmod{x^{2n}}
\end{aligned}
$$

时间复杂度

$$
T\left(n\right)=T\left(\frac{n}{2}\right)+O\left(n\log{n}\right)=O\left(n\log{n}\right)
$$

## 手算演示

为了方便理解，这里举几个例子演示一下算法流程。

### 整数模素数幂的平方根

我们先从不涉及多项式的整数开始。假设 $h$ 是一个不被 3 整除的「方便的」整数。（「方便」指「必然有解」，具体条件后文再言）假设要算 $h$ 在模 $3^n$ 意义下的平方根 $f$。有方程（为了避免混淆改成大写 $G$）：

$$
G\left(f\right) = f^2-h \equiv 0\pmod{3^{n}}
$$

Taylor 展开 $G$ 得到：

$$
G(f) = \sum_{i=0}^{+\infty}\frac{G^{\left(i\right)}\left(f_{0}\right)}{i!}\left(f-f_{0}\right)^{i}
= G(f_0) + 2f_0(f-f_0) + (f-f_0)^2
$$

用倍增计算。假设倍增中得到的中间结果是 $f_0, f_1, \ldots, f_j$，或者严谨地说 $f_j$ 是满足 $G(f_j)\equiv 0\pmod{3^{2^j}}$ 的一个整数，且为了唯一性它同时满足以下两个条件：

-   $0 < f_{j} < 3^{2^j}$；
-   $f_{j+k}-f_j\equiv 0\pmod{3^{2^j}}$，对所有 $k$。

把 $f_{j+1}$ 和 $f_j$ 代入上面的式子就有：

$$
G(f_{j+1}) = G(f_j) + 2f_j(f_{j+1}-f_j) + (f_{j+1}-f_{j})^2  \equiv 0 \pmod{3^{2^{j+1}}}
$$

显然 $f_{j+1}-f_j$ 必然是 $3^{2^j}$ 的倍数。于是得到

$$
f_{j+1} \equiv f_j - \frac{f_j^2-h}{2f_j} \equiv \frac{f_j^2 + h}{2f_j} \pmod{3^{2^{j+1}}}
$$

如果 $f_j$ 存在，那么 $2f_j$ 不被 $3$ 整除，所以必然有模 $3^{2^{j+1}}$ 的逆元。因此数列 $f_0,f_1\ldots,f_j$ 存在当且仅当 $f_0$ 存在。不被 3 整除的整数 $h$ 模 $3$ 的平方根要么不存在，要么有两个。所以 $h$ 有模 $3$ 平方根就是整个算法能跑的唯一条件。

这里选 $h=46$ 实际计算示例。

-   $f_0=1$,$f_1=\frac{1^2+46}{2\times 1}\mod 9 = 1$,$f_2=\frac{1^2+46}{2\times 1}\mod 81 = 64$,$f_3=\frac{64^2+46}{2\times 64}\mod 6561 = 955$,$\ldots$
-   $f_0=2$,$f_1=\frac{2^2+46}{2\times 2}\mod 9 = 8$,$f_2=\frac{8^2+46}{2\times 8}\mod 81 = 17$,$f_3=\frac{17^2+46}{2\times 17}\mod 6561 = 5606$,$\ldots$（等于前一个取负）

可以验证一下两个都是正确的模平方根数列。

### 复数多项式模多项式的平方根

假设 $h$ 是一个不被 $x$ 整除（有常数项）的「方便的」复数多项式，求它对模 $x^n$ 的平方根。很容易发现，我们可以几乎照抄上一节的内容，只要把 $3$ 换成 $x$。以下实际演练一下。

我们有方程（为了避免混淆改成大写 $G$）：

$$
G\left(f(x)\right) = f^2(x)-h(x) \equiv 0\pmod{3^{n}}
$$

Taylor 展开 $G$ 得到下式。注意这里是对 $f$ 的展开，所以导数都是对 $f$ 的偏导数，$x$ 在这里是当成常数算的。

$$
G(f(x)) = \sum_{i=0}^{+\infty}\frac{G^{\left(i\right)}\left(f_{0}(x)\right)}{i!}\left(f(x)-f_{0}(x)\right)^{i}
= G(f_0(x)) + 2f_0(x)(f(x)-f_0(x)) + (f(x)-f_0(x))^2
$$

用倍增计算。假设倍增中的中间结果是 $f_0(x), f_1(x), \ldots, f_j(x)$，或者数学严谨地说 $f_j(x)$ 是满足 $G(f_j(x))\equiv 0\pmod{x^{2^j}}$ 的一个复数多项式，且为了唯一性它同时满足以下两个条件：

-   $f_{j}(x)$ 次数不超过 $x^{2^j}$；
-   $f_{j+k}(x)-f_j(x)\equiv 0\pmod{x^{2^j}}$，对所有 $k$。

把 $f_{j+1}(x)$ 和 $f_j(x)$ 代入上面的式子就有：

$$
G(f_{j+1}(x)) = G(f_j(x)) + 2f_j(f_{j+1}(x)-f_j(x)) + (f_{j+1}(x)-f_{j}(x))^2  \equiv 0 \pmod{x^{2^{j+1}}}
$$

显然 $f_{j+1}(x)-f_j(x)$ 必然是 $x^{2^j}$ 的倍数。于是得到

$$
f_{j+1}(x) \equiv f_j(x) - \frac{f_j^2(x)-h(x)}{2f_j(x)} \equiv \frac{f_j(x)^2 + h(x)}{2f_j(x)} \pmod{x^{2^{j+1}}}
$$

如果 $f_j(x)$ 存在，那么 $2f_j(x)$ 不被 $x$ 整除（有常数项），所以必然有模 $x^{2^{j+1}}$ 的逆元。因此数列 $f_0,f_1\ldots,f_j$ 存在当且仅当 $f_0$ 存在。不被 $x$ 整除的复数多项式 $h(x)$ 模 $x$ 的平方根是一定存在的，因为 $h(x)$ 模掉 $x$ 就是个普通非零复数，一定有两个平方根。所以可以对所有有常数项的 $h(x)$ 用这个算法。

选 $h(x)=x+1$ 举例计算如下：

-   $f_0(x)=1$,$f_1(x)=\frac{1^2+x+1}{2\times 1}\mod x^2 = \frac{1}{2}x+1$,$f_2(x)=\frac{\left(\frac{1}{2}x+1\right)^2+x+1}{2\times \left(\frac{1}{2}x+1\right)}\mod x^4 = \frac{1}{16}x^3-\frac{1}{8}x^2+\frac{1}{2}x+1$,$\ldots$
-   $f_0(x)=-1$,$f_1(x)=\frac{(-1)^2+x+1}{2\times (-1)}\mod x^2 = -\frac{1}{2}x-1$,$\ldots$（等于前一个取负）

可以验证两个都是正确的模平方根多项式列。

### 对比思考

那么，为什么我们可以把数字的算法直接复制粘帖给多项式用呢？这需要一点抽象代数的知识。这里把冗长繁琐的定义去掉简单说明一下基本原理。

对一个能做加法和乘法的代数系统（*交换环*），我们可以对其中的非零元素 $a$ 进行如下分类：

-   单位元：存在乘法逆 $b$，即 $ab=ba=1$。
-   素数元：对所有 $x,y$，如果积 $xy$ 能被 $a$ 整除，那么 $x$ 或 $y$ 中的一个必定能被 $a$ 整除。
-   合数元：其他元素。

在一些条件满足的时候，合数元可以唯一写成素数元的乘积再乘上某个单位元。容易发现对足够大的 $N$，整数模 $3^N$ 和复数多项式模 $x^N$ 都满足这个条件：

-   整数模 $3^N$ 中，$3$ 是唯一的素数元，不被 $3$ 整除的都是单位元，而其他所有非 0 元素都可以写成 $3^a$ 乘某个单位元。
    -   这里「唯一」是把它乘以一个单位后变成的其他数也算进去的。
-   复数多项式模 $x^N$ 中，$x$ 是唯一的素数元，不被 $x$ 整除的都是单位元，而其他所有非 0 元素都可以写成 $x^a$ 乘某个单位元。

那么我们可以定义一个映射，把每个元素映射成它其中包括的素元素的次数。这样元素就自然分出了一个层级结构。

???+ abstract "P 进赋值"
    给定有唯一素数元 $p$ 的交换环 $R$，对所有 $x\in R$，令 $\nu_p(x)$ 为 $x$ 中含因子 $p$ 的最高次数：$\exists e\in R, e^{-1}p^{\nu_p(x)} = x$。$\nu_p$ 称为 **P 进赋值**，且 $R$ 称为 **离散赋值环（DVR）**。

P 进赋值高的上层的元素可以通过取模映射到 P 进赋值低的下层。而我们的算法只是逆转了方向，从下层往上走。只要这个层级结构一致，我们的算法就是可行的。
