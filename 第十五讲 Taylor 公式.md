# 第十五讲 Taylor 公式

### 带 Peano 余项的 Taylor 公式

我们已经学过导数定义导出的无穷小增量公式 $f(x) = f(x_0) + f'(x_0) (x - x_0) + o(x - x_0) \ (x \to x_0)$，这在 $x - x_0$ 的“精度”下近似了 $f(x)$，或者说从一阶导数导出了 $f(x)$ 的一阶近似。

但有时我们可能需要做“精度更高”的近似，即将 $o(x - x_0)$ “拆成更高阶的小量之和“。

不妨设 $f(x) = f(x_0) + f'(x_0) (x - x_0) + A (x - x_0)^2 + o((x - x_0)^2) \ (x \to x_0)$，我们尝试解出 $A$。

当 $f$ 在 $x_0$ 处二阶可导，有：

$$
\begin{aligned}
A &= \lim_{x \to x_0} \dfrac{f(x) - f'(x_0) (x - x_0)}{(x - x_0)^2} \\
&= \lim_{x \to x_0} \dfrac{f'(x) - f'(x_0)}{2 (x - x_0)} \\
&= \frac{f''(x)}{2}
\end{aligned}
$$

- 这里第二个等号用到了洛必达法则。

如此续行，对于在 $x_0$ 处足够高阶可导的 $f$，我们可以给出 $f$ 在 $\check{U}(x_0)$ 上足够高阶的近似。

------

内容：若 $f$ 在 $x_0$ 处 $n$ 阶可导，则 $f(x) = f(x_0) + \displaystyle\sum_{i = 1}^n f^{(i)}(x_0) (x - x_0)^i + o((x - x_0)^n) \ (x \to x_0)$。

证明：仿照求二阶近似的方式做数学归纳法即可，略。

#### 定理（带 Peano 余项的 Taylor 展开式唯一）

内容：若 $f$ 在 $x_0$ 处 $n$ 阶可导，且 $f(x) = \displaystyle\sum_{i = 0}^n a_i (x - x_0)^i + o((x - x_0)^n) \ (x \to x_0)$，则必有 $a_0 = f(x_0), \forall i \in [1, n] \cap \mathbb{N}, a_i = f^{(i)}(x_0)$。

证明：

- _Motivation：能不能一位一位确定啊？_
- 令 $p_n(x) = f(x_0) + \displaystyle\sum_{i = 1}^n f^{(i)}(x_0) (x - x_0)^i, q_n(x) = \displaystyle\sum_{i = 0}^n a_i (x - x_0)^i$。
- 则 $f(x) = p_n(x) + o((x - x_0)^n) = q_n(x) + o((x - x_0)^n) \ (x \to x_0)$，于是 $p_n(x) - q_n(x) = o((x - x_0)^n) \ (x \to x_0)$。
- 首先考察 $a_0$：由于 $\displaystyle\lim_{x \to x_0} (p_n(x) - q_n(x)) = \lim_{x \to x_0} ((f(x_0) - a_0) + o(1)) = f(x_0) - a_0 = 0$，可得 $a_0 = f(x_0)$。
- 接下来考察 $a_1$：由于 $\displaystyle\lim_{x \to x_0} \frac{p_n(x) - q_n(x)}{x - x_0} = \lim_{x \to x_0} ((f'(x_0) - a_1) + o(1)) = f'(x_0) - a_1 = 0$，可得 $a_1 = f'(x_0)$。
- 如此续行（或者说使用数学归纳法），最终可得 $\forall i \in [1, n] \cap \mathbb{N}, a_i = f^{(i)}(x_0)$。

#### 麦克劳林 Maclaurin 公式

内容：若 $f$ 在 $0$ 处 $n$ 阶可导，则 $f(x) = f(0) + \displaystyle\sum_{i = 1}^n f^{(i)}(x) x^i + o(x^n) \ (x \to 0)$。

证明：在泰勒公式中代入 $x_0 = 0$ 立即可得。

[例 1] 对于正偶数 $2n + 2$，求 $f(x) = \sin x$ 的 $2n + 2$ 阶麦克劳林展开式。

$f$ 在 $0$ 处无穷次可导，且有：

$$
\begin{cases}
f^{(4k)}(x) = \sin x \\
f^{(4k + 1)}(x) = \cos x \\
f^{(4k + 2)}(x) = -\sin x \\
f^{(4k + 3)}(x) = -\cos x
\end{cases}
\Rightarrow \begin{cases}
f^{(4k)}(x) = 0 \\
f^{(4k + 1)}(x) = 1 \\
f^{(4k + 2)}(x) = 0 \\
f^{(4k + 3)}(x) = -1
\end{cases}
$$

故 $\sin x = \displaystyle\sum_{i = 0}^n \frac{(-1)^i}{(2i + 1)!} x^{2i + 1} + o(x^{2n + 2}) \ (x \to 0)$。

------

同理，我们可以写出下列 $x \to 0$ 时的常用麦克劳林展开式：

$$
\begin{aligned}
\cos x &= \sum_{i = 0}^{n} \frac{(-1)^i}{(2i)!} x^{2i} + o(x^{2n}) \\
e^x &= \sum_{i = 0}^n \frac{1}{i!} x^i + o(x^n) \\
\ln (1 + x) &= \sum_{i = 1}^n \frac{(-1)^{i - 1}}{i} x^i + o(x^n) \\
\frac{1}{1 - x} &= \sum_{i = 0}^n x^i + o(x^n)
\end{aligned}
$$

灵活运用这些公式有助于简化计算。

[例 2] 求 $f(x) = \arctan x$ 的 $2n + 2$ 阶麦克劳林展开式。

易知 $f'(x) = \dfrac{1}{1 + x^2}$，但若直接继续向下求导就显得有些不便。

但幸运的是，我们知道 $\dfrac{1}{1 - x}$ 的麦克劳林展开式。由于当 $x \to 0$，有 $-x^2 \to 0$，可得：

$$
\begin{aligned}
f'(x) &= \frac{1}{1 - (-x^2)} \\
&= \sum_{i = 0}^{n + 1} (-x^2)^i + o((-x^2)^{n + 1}) \\
&= \sum_{i = 0}^{n + 1} (-1)^i x^{2i} + o(x^{2n + 2})
\end{aligned}
$$

现在，我们尝试通过 $f'$ 的麦克劳林展开式，求出 $f$ 的麦克劳林展开式。

由于 $f'(x) = \displaystyle\sum_{i = 0}^{2n + 2} \frac{(f')^{(i)}(0)}{i!} x^i + o(x^{2n + 2}) = \sum_{i = 1}^{2n + 3} \frac{f^{(i)}(0)}{(i - 1)!} x^{i - 1} + o(x^{2n + 2}) \ (x \to x_0)$，有：

$$
\forall i \in [1, 2n + 3] \cap \mathbb{N}, \frac{f^{(i)}(0)}{(i - 1)!} = \begin{cases} (-1)^{\frac{i - 1}{2}}, &\quad 2 \not\mid i \\ 0, &\quad 2 \mid i\end{cases} \Rightarrow \frac{f^{(i)}(0)}{i!} = \begin{cases} \dfrac{(-1)^{\frac{i - 1}{2}}}{i}, &\quad 2 \not\mid i \\ 0, &\quad 2 \mid i\end{cases}
$$

故有 $f(x) = f(0) + \displaystyle\sum_{i = 1}^{2n + 3} \dfrac{f^{(i)}(0)}{i!} x^i + o(x^{2n + 3}) = \sum_{i = 0}^{n + 1} \frac{(-1)^i}{2i + 1} x^{2i + 1} + o(x^{2n + 3}) = \sum_{i = 0}^n \frac{(-1)^i}{2i + 1} x^{2i + 1} + o(x^{2n + 2})$。

[例 3] 将 $f(x) = e^{\cos x}$ 在 $x = 0$ 处展开至 $x^4$ 项。

- **注意当 $x \to 0$ 有 $\cos x \to 1$，不应直接代入 $\cos x$ 的麦克劳林公式！**

令 $y = \cos x = 1 - \dfrac{1}{2} x^2 + \dfrac{1}{24} x^4 + o(x^4)$，考虑将 $e^y$ 在 $y = 1$ 处展开：

$$
\begin{aligned}
e^{\cos x} &= e^y \\
&= e + (y - 1) + \frac{(y - 1)^2}{2} + o((y - 1)^2) \\
&= e + (-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4)) + \frac{1}{2} (-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4))^2 + o((-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4))^2) \\
&= e - \frac{1}{2} x^2 + \frac{1}{6} x^4 + o(x^4)
\end{aligned}
$$
