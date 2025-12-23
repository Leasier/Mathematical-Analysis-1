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

[例 1] 求 $f(x) = \sin x$ 的 $2n + 2$ 阶麦克劳林展开式。

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

故所求展开式为：

$$
\begin{aligned}
f(x) &= f(0) + \sum_{i = 1}^{2n + 3} \frac{f^{(i)}(0)}{i!} x^i + o(x^{2n + 3}) \\
&= \sum_{i = 0}^{n + 1} \frac{(-1)^i}{2i + 1} x^{2i + 1} + o(x^{2n + 3}) \\
&= \sum_{i = 0}^n \frac{(-1)^i}{2i + 1} x^{2i + 1} + o(x^{2n + 2})
\end{aligned}
$$

[例 3] 对于 $\alpha \in \mathbb{R}$，求 $f(x) = (1 + x)^{\alpha}$ 的 $n$ 阶麦克劳林展开式。

记广义组合数为 $C_{\alpha}^k = \dfrac{1}{k!} \displaystyle\prod_{i = 0}^{k - 1} (\alpha - i)$，则 $f^{(k)}(x) = C_{\alpha}^k (1 + x)^{\alpha - k}$。

故所求展开式为：

$$
f(x) = \sum_{i = 0}^n C_{\alpha}^i x^i + o(x^n)
$$

- 特别地，当 $\alpha \in \mathbb{N}_+$，在 $k > \alpha$ 时有 $f^{(k)}(x) = 0$。

------

结合例 2 和例 3，可以求得 $\arcsin$ 的 $2n + 1$ 阶麦克劳林展开式为：

$$
\begin{aligned}
\arcsin x &= \sum_{i = 0}^n \frac{C_{-\frac{1}{2}}^i (-x^2)^i \cdot x}{2i + 1} + o(x^{2n + 1}) \\
&= x + \sum_{i = 1}^n \frac{(2i - 1)!!}{2^i \cdot i! \cdot (2i + 1)} x^{2i + 1} + o(x^{2n + 1}) \\
&= \sum_{i = 0}^n \frac{(2i)!}{4^i \cdot (i!)^2 \cdot (2i + 1)} x^{2i + 1} + o(x^{2n + 1})
\end{aligned}
$$

[例 3] 将 $f(x) = e^{\cos x}$ 在 $x = 0$ 处展开至 $x^4$ 项。

- **注意当 $x \to 0$ 有 $\cos x \to 1$，不应直接代入 $\cos x$ 的麦克劳林展开式！**

令 $y = \cos x = 1 - \dfrac{1}{2} x^2 + \dfrac{1}{24} x^4 + o(x^4)$，考虑将 $e^y$ 在 $y = 1$ 处展开：

$$
\begin{aligned}
e^{\cos x} &= e^y \\
&= e + (y - 1) + \frac{(y - 1)^2}{2} + o((y - 1)^2) \\
&= e + (-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4)) + \frac{1}{2} (-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4))^2 + o((-\frac{1}{2} x^2 + \frac{1}{24} x^4 + o(x^4))^2) \\
&= e - \frac{1}{2} x^2 + \frac{1}{6} x^4 + o(x^4)
\end{aligned}
$$

[例 4] 将 $f(x) = \tan x$ 在 $x = 0$ 处展开至 $x^4$ 项。

- _Motivation：$\sin x, \cos x$ 的展开式都已知，能否据此求出 $\tan x = \dfrac{\sin x}{\cos x}$ 的展开式？_

$$
\begin{aligned}
x \to 0, f(x) &= \frac{\sin x}{\cos x} \\
&= \frac{x - \frac{x^3}{3!} + o(x^4)}{1 - \frac{x^2}{2!} + \frac{x^4}{4!} + o(x^4)} \\
&= (x - \frac{x^3}{3!} + o(x^4)) (1 + (\frac{x^2}{2!} - \frac{x^4}{4!} + o(x^4)) + (\frac{x^2}{2!} - \frac{x^4}{4!} + o(x^4))^2 + o((\frac{x^2}{2!} - \frac{x^4}{4!} + o(x^4))^2)) \\
&= (x - \frac{x^3}{3!} + o(x^4)) (1 + \frac{x^2}{2!} + \frac{5x^4}{24} + o(x^4)) \\
&= x + \dfrac{x^3}{3} + o(x^4)
\end{aligned}
$$

- 第三个等号的依据是 $\dfrac{x^2}{2!} - \dfrac{x^4}{4!} + o(x^4) \to 0$。
- _这里保留到几次方可能需要一些尝试（_

[例 5] 求 $\displaystyle\lim_{x \to 0} \frac{\sin x - \arctan x}{\tan x - \arcsin x}$。

$$
\begin{aligned}
\text{原式} &= \lim_{x \to 0} \frac{(x - \dfrac{x^3}{6} + o(x^3)) - (x - \dfrac{x^3}{3} + o(x^3))}{(x + \dfrac{x^3}{3} + o(x^3)) - (x + \dfrac{x^3}{6} + o(x^3))} \\
&= \lim_{x \to 0} \frac{\dfrac{x^3}{6} + o(x^3)}{\dfrac{x^3}{6} + o(x^3)} \\
&= 1
\end{aligned}
$$

#### 极值的第三充分条件

内容：若 $f$ 在 $x_0$ 处 $n \geq 2$ 阶可导，且 $f'(x_0) = \cdots = f^{(n - 1)}(x_0) = 0, f^{(n)}(x_0) \neq 0$，则：

- (1) 当 $n$ 为偶数，$f^{(n)}(x_0) > 0 \Rightarrow x_0$ 为严格极小值点，$f^{(n)}(x_0) < 0 \Rightarrow x_0$ 为严格极大值点。
- (2) 当 $n$ 为奇数，$x_0$ 不为极值点。

证明：

- 写出 $f$ 在 $x_0$ 处展开的带 Peano 余项的 Taylor 公式：$f(x) = f(x_0) + f^{(n)}(x_0) (x - x_0)^n + o((x - x_0)^n)$。
- (1) 当 $n$ 为偶数：
- I. 若 $f^{(n)}(x_0) > 0$，则 $\exists \check{U}(x_0), \text{s.t. } \forall x \in \check{U}(x_0), f(x) - f(x_0) = f^{(n)}(x_0) (x - x_0)^n + o((x - x_0)^n) > 0$，故 $x_0$ 为严格极小值点。
- II. 若 $f^{(n)}(x_0) < 0$，同理可得 $x_0$ 为严格极大值点。
- (2) 当 $n$ 为奇数：
- I. 若 $f^{(n)}(x_0) > 0$，则 $\exists \check{U}(x_0), \text{s.t. } \forall x \in \check{U}(x_0), (f(x) - f(x_0))(x - x_0) = f^{(n)}(x_0) (x - x_0)^{n + 1} + o((x - x_0)^{n + 1}) > 0$。
- 进而 $\exists \check{U}^+(x_0), \text{s.t. } \forall x \in \check{U}^+(x_0), f(x) - f(x_0) > 0$ 且 $\exists \check{U}^-(x_0), \text{s.t. } \forall x \in \check{U}^-(x_0), f(x) - f(x_0) < 0$，故 $x_0$ 不为极值点。
- II. 若 $f^{(n)}(x_0) < 0$，同理可得 $x_0$ 不为极值点。
- 综上即可得证。

### 带 Lagrange 余项的 Taylor 公式

有限增量公式指出 $\exists \xi$ 在 $x_0, x$ 之间，$\text{s.t. } f(x) = f(x_0) + f'(\xi) (x - x_0)$，这可以视作在“零阶近似” $f(x) = f(x_0) + o(1) \ (x \to x_0)$ 的基础上将 $o(1)$ 细化、得到“一阶余项”，我们得以更加精确地刻画两者之差。

在此基础上，考虑改写 Taylor 公式的 Peano 余项。一般地，不妨设 $x > x_0$。

令 $p(x) = f(x_0) + \displaystyle\sum_{i = 1}^n \frac{f^{(i)}(x_0)}{i!} (x - x_0)^i, q(x) = f(x) - p(x)$，则有：

$$
\begin{aligned}
\frac{q(x)}{(x - x_0)^{n + 1}} &= \frac{q(x) - q(x_0)}{(x - x_0)^{n + 1} - (x_0 - x_0)^{n + 1}} \\
&= \frac{q'(x_1)}{(n + 1) (x_1 - x_0)^n}, &\quad x_1 \in (x_0, x) \\
&= \frac{q'(x_1) - q'(x_0)}{(n + 1) ((x_1 - x_0)^n - (x_0 - x_0)^n)} \\
&= \frac{q''(x_2)}{(n + 1) n (x_2 - x_0)^{n - 1}}, &\quad x_2 \in (x_0, x_1) \\
&= \frac{q''(x_2) - q''(x_0)}{(n + 1) n ((x_2 - x_0)^{n - 1} - (x_0 - x_0)^{n - 1})} \\
&= \cdots \\
&= \frac{q^{(n + 1)}(x_{n + 1})}{(n + 1)! (x_{n + 1} - x_0)^0}, &\quad x_{n + 1} \in (x_0, x_n) \\
&= \frac{f^{(n + 1)}(x_{n + 1})}{(n + 1)!} \\
\end{aligned}
$$

故 $\exists \xi = x_{n + 1} \in (x_0, x_n) \subset (x_0, x), \text{s.t. } \dfrac{q(x)}{(x - x_0)^{n + 1}} = \dfrac{f^{(n + 1)}(\xi)}{(n + 1)!}$，即 $f(x) = f(x_0) + \displaystyle\sum_{i = 1}^n \frac{f^{(i)}(x_0)}{i!} (x - x_0)^i + \dfrac{f^{(n + 1)}(\xi)}{(n + 1)!} (x - x_0)^{n + 1}$。

当 $x < x_0$，同理而略之。

上面的推导用到了 $n$ 阶 Taylor 公式和 Cauchy 中值定理，下面据此重述公式的条件与内容。

------

条件：

- (1) $f$ 在 $[a, b]$ 上 $n$ 阶可导。
- (2) $f^{(n)}$ 在 $[a, b]$ 上连续。
- (3) 在 $(a, b)$ 上 $n + 1$ 阶可导。

结论：$\forall x_0, x \in [a, b] \land x_0 \neq x, \exists \xi$ 在 $x_0, x$ 之间，$\text{s.t. } f(x) = f(x_0) + \displaystyle\sum_{i = 1}^n \frac{f^{(i)}(x_0)}{i!} (x - x_0)^i + \dfrac{f^{(n + 1)}(\xi)}{(n + 1)!} (x - x_0)^{n + 1}$。

#### 推论（多项式函数判据）

条件：

- (1) $f$ 在 $[a, b]$ 上 $n$ 阶可导。
- (2) $f^{(n)}$ 在 $[a, b]$ 上连续。
- (3) $\forall x \in (a, b), f^{(n + 1)}(x) = 0$。

结论：$f$ 在 $[a, b]$ 上为 $n$ 阶多项式。

证明：在带 Lagrange 余项的 Taylor 公式中代入 $x_0 = a$，令 $x$ 取遍 $(a, b]$ 即可。

------

[例 6] 分别求 $f(x) = \sin x$ 在 $x = 0$ 的 $2n + 1, 2n + 2$ 阶带 Lagrange 余项的 Taylor 展开式。

- (1) $f(x) = \displaystyle\sum_{i = 0}^n \frac{(-1)^i}{(2i + 1)!} x^{2i + 1} + \frac{(-1)^n \cos (\theta x)}{(2n + 1)!} x^{2n + 1}$。
- (2) $f(x) = \displaystyle\sum_{i = 0}^n \frac{(-1)^i}{(2i + 1)!} x^{2i + 1} + \frac{(-1)^{n + 1} \sin (\theta x)}{(2n + 1)!} x^{2n + 2}$。

其中参数 $\theta \in (0, 1)$。

- 有趣的是，上面两个结果并不相同：尽管 $2n + 2$ 阶 Taylor 展开式中的 $x^{2n + 1}$ 项均为 $0$，但 (1)(2) 的 Lagrange 余项却因为精度要求之别产生了不同。

[例 7] 已知 $f$ 在 $[a, b]$ 上二阶可导，且 $f'(a) = f'(b) = 0$，求证：$\exists c \in (a, b), \text{s.t. } |f''(c)| \geq \dfrac{4}{(b - a)^2} |f(b) - f(a)|$。

- _Motivation：我要怎么利用端点一阶导为 $0$ 呢？_
- _Motivation：注意到答案形式中没有一阶导，那是否可以考虑在端点处展开？_

$$
\forall x \in (a, b),
\begin{cases}
\exists \xi_1 \in (a, x), \text{s.t. } f(x) = f(a) + f'(a) (x - a) + \dfrac{f''(\xi_1)}{2} (x - a)^2 = f(a) + \dfrac{f''(\xi_1)}{2} (x - a)^2 \\
\exists \xi_2 \in (x, b), \text{s.t. } f(x) = f(b) + f'(b) (x - b) + \dfrac{f''(\xi_2)}{2} (x - b)^2 = f(b) + \dfrac{f''(\xi_2)}{2} (x - b)^2
\end{cases}
$$

- _Motivation：注意到答案形式中没有内点函数值，那是否可以考虑将两式相减？_
- 将第二式减去第一式，得 $0 = (f(b) - f(a)) + \dfrac{1}{2} (f''(\xi_2) (x - b)^2 - f''(\xi_1) (x - a)^2)$。
- 考虑反证法：假设 $\forall c \in (a, b), |f''(c)| < \dfrac{4}{(b - a)^2} |f(b) - f(a)|$。
- 移项可知 $f(b) - f(a) = f''(\xi_1) (x - a)^2 - f''(\xi_2) (x - b)^2$，两边同时取绝对值可知：

$$
\begin{aligned}
|f(b) - f(a)| &= \frac{1}{2} (|f''(\xi_1)| (x - a)^2 + |f''(\xi_2)| (x - b)^2) \\
&< \frac{2}{(b - a)^2} |f(b) - f(a)| ((x - a)^2 + (x - b)^2)
\end{aligned}
$$

- 注意到 $x$ 的值由我们**自行选定**，为使限制最强（即 $(x - a)^2 + (x - b)^2$ 最小），取 $x = \dfrac{a + b}{2}$ 可得：

$$
\begin{aligned}
|f(b) - f(a)| &< \frac2{(b - a)^2} |f(b) - f(a)| \cdot \frac{1}{2} (b - a)^2 \\
&= |f(b) - f(a)|
\end{aligned}
$$

- 由此推出矛盾，故假设不成立，即 $\exists c \in (a, b), \text{s.t. } |f''(c)| \geq \dfrac{4}{(b - a)^2} |f(b) - f(a)|$。

[例 8] 已知 $f$ 在 $[a, b]$ 上二阶可导，$f(a) = f(b) = 0$，且 $f''$ 在 $[a, b]$ 上能取到最大值，求证：

- (1) $\displaystyle\max_{a \leq x \leq b} |f(x)| \leq \frac{1}{8} (b - a)^2 \max_{a \leq x \leq b} |f''(x)|$。
- (2) $\displaystyle\max_{a \leq x \leq b} |f'(x)| \leq \frac{1}{2} (b - a) \max_{a \leq x \leq b} |f''(x)|$。

第一问：

- _Motivation：这里不涉及 $f'$，考虑在内点展开以将其消去。_
- 取 $x \in (a, b)$，有：

$$
\begin{cases}
\exists \xi_1 \in (a, x), \text{s.t. } 0 = f(a) = f(x) + f'(x) (a - x) + \dfrac{f''(\xi_1)}{2} (a - x)^2 &\quad (1) \\
\exists \xi_2 \in (x, b), \text{s.t. } 0 = f(b) = f(x) + f'(x) (b - x) + \dfrac{f''(\xi_2)}{2} (b - x)^2 &\quad (2)
\end{cases}
$$

- 为消去 $f'(x)$，考虑写出 $\dfrac{1}{x - a} \cdot (1) + \dfrac{1}{b - x} \cdot (2)$：

$$
\begin{aligned}
& 0 = \frac{b - a}{(x - a)(b - x)} f(x) + (\dfrac{f''(\xi_1)}{2} (x - a) + \dfrac{f''(\xi_2)}{2} (b - x)) \\
\Leftrightarrow & f(x) = -\frac{(x - a)(b - x)}{b - a} (\dfrac{f''(\xi_1)}{2} (x - a) + \dfrac{f''(\xi_2)}{2} (b - x))
\end{aligned}
$$

- 两边同时取绝对值可知：

$$
\begin{aligned}
|f(x)| &= \frac{(x - a)(b - x)}{b - a} |\dfrac{f''(\xi_1)}{2} (x - a) + \dfrac{f''(\xi_2)}{2} (b - x)| \\
&\leq \frac{(x - a)(b - x)}{2(b - a)} (|f''(\xi_1)| (x - a) + |f''(\xi_2)| (b - x)) \\
&\leq \frac{(x - a)(b - x)}{2(b - a)} \cdot (b - a) \max_{a \leq x \leq b} |f''(x)| \\
&= \frac{(x - a)(b - x)}{2} \max_{a \leq x \leq b} |f''(x)| \\
&\leq \frac{1}{8} (b - a)^2 \max_{a \leq x \leq b} |f''(x)|
\end{aligned}
$$

- 由 $x$ 的任意性，再特判 $x = a$ 和 $x = b$ 的情况（或利用 $f$ 的连续性），可知 $\displaystyle\max_{a \leq x \leq b} |f(x)| \leq \frac{1}{8} (b - a)^2 \max_{a \leq x \leq b} |f''(x)|$。

第二问：

- _Motivation：这里不涉及 $f$，仍考虑在内点展开以将其消去。_
- 为消去 $f$，考虑写出 $(2) - (1)$：

$$
\begin{aligned}
0 &= f'(x) (b - a) + (\frac{f''(\xi_2)}{2} (b - x)^2 - \frac{f''(\xi_1)}{2} (a - x)^2) \\
\Leftrightarrow f'(x) &= \frac{1}{2 (b - a)} (f''(\xi_1) (a - x)^2 - f''(\xi_2) (b - x)^2)
\end{aligned}
$$

- 两边同时取绝对值可知：

$$
\begin{aligned}
|f'(x)| &= \frac{1}{2 (b - a)} |f''(\xi_1) (a - x)^2 - f''(\xi_2) (b - x)^2| \\
&\leq \frac{1}{2 (b - a)} (|f''(\xi_1)| (a - x)^2 + |f''(\xi_2)| (b - x)^2) \\
&\leq \frac{1}{2 (b - a)} \cdot ((a - x)^2 + (b - x)^2) \max_{a \leq x \leq b} |f''(x)| \\
&< \frac{1}{2 (b - a)} \cdot (b - a)^2 \max_{a \leq x \leq b} |f''(x)| \\
&= \frac{b - a}{2} \max_{a \leq x \leq b} |f''(x)|
\end{aligned}
$$

- 由 $x$ 的任意性，再特判 $x = a$ 和 $x = b$ 的情况（或利用 $f$ 的连续性），可知 $\displaystyle\max{a \leq x \leq b} |f'(x)| \leq \frac{b - a}{2} \max_{a \leq x \leq b} |f''(x)|$。

[例 9] 已知 $f$ 在 $\mathbb{R}$ 上二阶可导，且 $\forall x \in \mathbb{R}, |f(x)| \leq M_0, |f''(x)| \leq M_2$，求证：$\forall x \in \mathbb{R}, |f'(x)| \leq \sqrt{2 M_0 M_2}$。

- _Motivation：结论似乎意味着我们需要通过某种方式卡出 $|f'(x)|$ 的上界，但这个是不是有点均值不等式啊？_
- $\forall x \in \mathbb{R}$，有：

$$
\forall h > 0, \exists \xi \in (x, x + h), \text{s.t. } f(x + h) = f(x) + f'(x) h + \frac{f''(\xi)}{2} h^2 \ (1)
$$

- 整理并取绝对值，化简后可知 $|f'(x)| \leq \dfrac{|f(x + h) - f(x)|}{h} + \dfrac{|f''(\xi)|}{2} h \leq \dfrac{2 M_0}{h} + \dfrac{M_2}{2} h$。
- 可惜的是，直接通过均值不等式只能卡出 $|f'(x)| \leq 2 \sqrt{M_0 M_2}$，但问题是什么？
- _Motivation：诶，这个 $f$ 的部分咋有两个啊？_
- _Motivation：能不能消去与 $f'(x)$ 无关的常数 $f(x)$？_
- 考虑写出 $x - h$ 处的展开式：

$$
\exists \xi' \in (x - h, x), \text{s.t. } f(x - h) = f(x) - f'(x) h + \frac{f''(\xi')}{2} h^2 \ (2)
$$

- 写出 $(1) - (2)$：$f(x + h) - f(x - h) = 2 f'(x) h + \dfrac{1}{2} (f''(\xi) - f''(\xi')) h^2$。
- 整理并取绝对值，化简后可知 $|f'(x)| \leq \dfrac{|f(x + h) - f(x - h)|}{2h} + \dfrac{|f''(\xi) - f''(\xi')|}{4} h \leq \dfrac{M_0}{h} + \dfrac{M_2}{2} h$。
- 接下来，取均值不等式即可卡出 $|f'(x)| \leq \sqrt{2 M_0 M_2}$。

### 插值公式及其余项

#### Lagrange 插值公式

给出 $f$ 在 $n + 1$ 个点 $x_0 < x_1 < \cdots < x_n$ 处的取值 $y_0, y_1, \cdots, y_n$，我们尝试用一个**多项式**“拟合”出 $f$ 在这些位置的表现。

从构造的视角看，一个暴躁的想法是：

- 构造多项式 $\forall i \in [0, n] \cap \mathbb{N}, L_i(x)$，使得 $L_i(x_j) = [i = j]$。
- 此时可以构造多项式 $L(x) = \displaystyle\sum_{i = 0}^n y_i L_i(x)$，则 $\forall i \in [0, n] \cap \mathbb{N}, L(x_i) = y_i$。

下面来构造 $L_i(x)$：

- 由于 $L_i(x)$ 有 $n$ 个零点 $x_0, \cdots, x_{i - 1}, x_{i + 1}, \cdots, x_n$，其应当有因式 $\displaystyle\prod_{j \neq i} (x - x_j)$。
- 为了让 $L_i(x_i) = 1$，考虑将其除以 $\displaystyle\prod_{j \neq i} (x_i - x_j)$。
- 故可令 $L_i(x) = \dfrac{\prod_{j \neq i} (x - x_j)}{\prod_{j \neq i} (x_i - x_j)}$。

因此，我们得到一个满足要求的 $L$：

$$
L(x) = \sum_{i = 0}^n y_i \cdot \frac{\prod_{j \neq i} (x - x_j)}{\prod_{j \neq i} (x_i - x_j)}
$$

这是一个 $n$ 次多项式，反证即得这样的构造唯一。

上面的 $L_i(x)$ 称作 **Lagrange 基函数**，$L(x)$ 称作 **Lagrange 插值多项式**。

------

当我们想要“插值”，要么知道它是一个多项式函数、且想要求出其系数或点值，要么想要用一个“性质较好”的函数（比如多项式函数）去近似原函数、以简化计算等。因此，我们可能需要知道 Lagrange 插值公式与原函数之间的误差。

这看上去似乎不可能做到，因为上面的公式对 $f$ 没有任何要求。不过事实上，若加入一些限制，我们确实能够通过某些“余项”的信息估计误差。

#### 定理（Lagrange 插值公式的余项）

内容：若 $f$ 在 $[a, b]$ 上 $n + 1$ 阶可导，选取 $[a, b]$ 上的 $n + 1$ 个点 $a \leq x_0 < \cdots < x_n \leq b$ 得到 Lagrange 插值多项式 $L$，则：

$$
\forall x \in [a, b], \exists \xi \in (a, b), \text{s.t. } f(x) = L(x) + \frac{f^{(n + 1)}(\xi)}{(n + 1)!} \prod_{i = 0}^n (x - x_i)
$$

证明：

- 由 $\forall i \in [0, n] \cap \mathbb{N}, f(x) = L(x)$ 可知 $f(x) - L(x)$ 有 $n + 1$ 个零点 $x_0, \cdots, x_n$。
- 令 $\omega(x) = \displaystyle\prod_{i = 0}^n (x - x_i)$，则 $f(x) - L(x)$ 可以写成 $r(x) \omega(x)$ 的形式，考虑求出 $r(x)$。
- (1) $\forall x \in \{x_0, \cdots, x_n\}$，由于 $\displaystyle\prod_{i = 0}^n (x - x_i) = 0$，任取 $\xi \in (a, b)$ 并令 $r(x) = \dfrac{f^{(n + 1)}(\xi)}{(n + 1)!}$ 即可。
- (2) $\forall x \in [a, b] \backslash \{x_0, \cdots, x_n\}$，令 $D(t) = f(t) - L(t) - r(x) \omega(t)$，则 $D$ 存在 $n + 2$ 个零点为 $x, x_0, \cdots, x_n$。
- 连续使用 $n + 1$ 次 Rolle 定理，可知 $D^{(n + 1)}(t)$ 存在一个 $(a, b)$ 上的零点，即：

$$
\exists \xi \in (a, b), \text{s.t. } 0 = D^{(n + 1)}(t) = f^{(n + 1)}(\xi) - 0 - r(x) (n + 1)! \Rightarrow r(x) = \frac{f^{(n + 1)}(\xi)}{(n + 1)!}
$$

- 综合 (1)(2) 即可得证。

#### Hermite 插值公式

上面的 Lagrange 插值公式给出的 $L$ 仅仅拟合了 $f$ 的函数值，但没能模仿 $f$ 在高阶导数处的行为。下面我们尝试进行更“光滑”的拟合。

给出 $[a, b]$ 上的 $n$ 个点 $a \leq x_1 < \cdots < x_n \leq b$ 和约束 $k_1, \cdots, k_n \in \mathbb{N}$，我们尝试用一个多项式拟合出 $\forall i \in [1, n] \cap \mathbb{N}, j \in [0, k_i] \cap \mathbb{N}, f^{(j)}(x_i)$ 的值。当然，这里要求 $f$ 在 $[a, b]$ 上 $\displaystyle\max_{i = 1}^n k_i$ 阶可导。

仿照上面的思路，考虑构造多项式 $\forall i \in [1, n] \cap \mathbb{N}, j \in [0, k_i] \cap \mathbb{N}, H_{i, j}(x)$，使得 $\forall p \in ([1, n] \backslash \{i\}) \cap \mathbb{N}, q \in [0, k_p] \cap \mathbb{N}, H_{i, j}^{(q)}(x_p) = [i = p \land j = q]$：

- _Motivation：对于 $i$，我们希望刚好求 $j$ 次导并产生常数。_
- 考虑让 $U_{i, j}(x) = (x - x_i)^j$ 为其因式。
- _Motivation：对于 $p$，我们可能会求 $k_p$ 次导啊！如何制止其产生值？_
- 考虑让 $V_i(x) = \displaystyle\prod_{p \neq i} (x - x_p)^{k_p + 1}$ 为其因式。
- 接下来我们只需选取多项式函数 $R_{i, j}(x)$，并令 $H_{i, j}(x) = U_{i, j}(x) V_i(x) R_{i, j}(x)$，使得 $\forall q \in [0, j) \cap \mathbb{N}, H_{i, j}^{(q)}(x_i) = 0$ 且 $H_{i, j}^{(j)}(x_i) = 1$。
- 令 $W_i(x) = \dfrac{1}{V_i(x)}$，则 $H_{i, j}(x) W_i(x) = U_{i, j}(x) r(x)$。
- 对两边同时求 $j + q$ 次导，得到：

$$
\sum_{r = 0}^{j + q} C_{j + q}^r H_{i, j}^{(r)}(x) W_i^{(j + q - r)}(x) = \sum_{r = 0}^{j + q} C_{j + q}^r U_{i, j}^{(r)}(x) R_{i, j}^{(j + q - r)}(x)
$$

- 令 $x = x_i$，得到 $C_{j + q}^j W_i^{(q)}(x_i) = C_{j + q}^j \cdot j! \cdot R_{i, j}^{(q)}(x_i)$，即 $R_{i, j}^{(q)}(x_i) = \dfrac{1}{j!} W_i^{(q)}(x_i)$。
- 类比 Taylor 展开式，令 $R_{i, j} = \dfrac{1}{j!} \displaystyle\sum_{q = 0}^{?} \frac{W_i^{(q)}(x_i)}{q!} (x - x_i)^q$。
- 令 $m = \displaystyle\sum_{i = 1}^n (k_i + 1)$，仿照 Lagrange 插值公式使 $H$ 为一个 $m - 1$ 次多项式，故求和上限设为 $n_i - j$。

因此，我们得到一个满足要求的 $H$：

$$
H(x) = \sum_{i = 0}^n \sum_{j = 0}^{k_i} f^{(j)}(x_i) \cdot \frac{1}{j!} (x - x_i)^j \cdot V_i(x) \sum_{q = 0}^{n_i - j} \frac{W_i^{(q)}(x_i)}{q!} (x - x_i)^q 
$$

这是一个 $m - 1$ 次多项式，反证即得这样的构造唯一。

上面的 $H_i(x)$ 称作 **Hermite 基函数**，$H(x)$ 称作 **Hermite 插值多项式**。

#### 定理（Hermite 插值公式的余项）

内容：选取 $[a, b]$ 上的 $n$ 个点 $a \leq x_1 < \cdots < x_n \leq b$ 和约束 $k_1, \cdots, k_n \in \mathbb{N}$ 得到 Hermite 插值多项式 $H$，令 $m = \displaystyle\sum_{i = 1}^n (k_i + 1)$，若 $f$ 在 $[a, b]$ 上 $m$ 阶可导，则：

$$
\forall x \in [a, b], \exists \xi \in (a, b), \text{s.t. } f(x) = H(x) + \frac{f^{m}(\xi)}{m!} \prod_{i = 1}^n (x - x_i)^{k_i}
$$

证明：同理构造函数并通过 Rolle 定理处理零点即可，略。

[例 10] 已知 $f$ 在 $[0, 1]$ 上四阶可导，$p$ 为三次多项式且满足 $p(0) = f(0), p'(0) = f'(0), p(1) = f(1), p'(1) = f'(1)$，求证：$\forall x \in [0, 1], |f(x) - p(x)| \leq \dfrac{1}{384} \displaystyle\max_{x \in [0, 1]} |f^{4}(x)|$。

由题意可知 $p$ 为 $f$ 的以 $0, 1$ 为二重节点的 Hermite 插值多项式，则：

$$
\forall x \in [0, 1], \exists \xi \in (0, 1), \text{s.t. } f(x) - p(x) = \dfrac{f^{4}(\xi)}{24} \cdot x^2 (x - 1)^2
$$

故 $|f(x) - p(x)| = \dfrac{1}{24} (x(1 - x))^2 \displaystyle\max_{x \in [0, 1]} |f^{4}(x)| \leq \frac{1}{24} (\frac{1}{4})^2 \max_{x \in [0, 1]} |f^{4}(x)| = \frac{1}{384} \max_{x \in [0, 1]} |f^{4}(x)|$。

### Taylor 级数

若 $f$ 在 $I$ 上任意阶可导，取 $x_0 \in I$，则有：

$$
\forall x \in I, n \in \mathbb{N}, f(x) = f(x_0) + \sum_{i = 1}^n f^{(i)}(x_0) (x - x_0)^i + R_n(x)
$$

其中 $R_n(x)$ 是 $n$ 阶 Taylor 展开的余项。

若 $\forall x \in I, \displaystyle\lim_{n \to +\infty} R_n(x) = 0$，则有：

$$
\forall x \in I, f(x) = \lim_{n \to +\infty} (f(x_0) + \sum_{i = 1}^n f^{(i)}(x_0) (x - x_0)^i) = f(x_0) + \sum_{i = 1}^{+\infty} f^{(i)}(x_0) (x - x_0)^i
$$

此时称 $f$ 在 $I$ 上可以展开为 Taylor 级数。

- **注意：只要 $f$ 在 $I$ 上任意阶可导，就可以给出其在 $a$ 处定义的 $I$ 上的 Taylor 级数，但此时不一定能说可以展开为 Taylor 级数，因为函数值和级数结果不一定能取等！**
- $x_0 = 0$ 时的 Taylor 级数也称 Maclaurin 级数。

[例 11] 求 $f(x) = e^x$ 的 Maclaurin 级数。

写出 $f$ 的带 Lagrange 余项的 Maclaurin 展开式：

$$
\exists \theta \in (0, 1), \text{s.t. } f(x) = \sum_{i = 0}^n \frac{x^i}{i!} + \frac{e^{\theta x}}{(n + 1)!} x^{n + 1}
$$

考察余项 $R_n(x) = \dfrac{e^{\theta x}}{(n + 1)!} x^{n + 1}$，由于 $|R_n(x)| < \dfrac{e^x |x|^{n + 1}}{(n + 1)!}$，而当 $n + 1 \geq C = \lceil 2|x| \rceil$ 时有 $\dfrac{|x|^{n + 1}}{(n + 1)!} \leq \dfrac{1}{2^{n + 1}} \cdot \dfrac{e^x C^C}{C!}$，而 $\{\dfrac{1}{2^{n + 1}} \cdot \dfrac{e^x C^C}{C!}\}$ 显然是无穷小序列，故 $\displaystyle\lim_{n \to +\infty} R_n(x) = 0$。

因此 $f$ 的 Maclaurin 级数为：

$$
e^x = \sum_{i = 0}^{+\infty} \frac{x^i}{i!}
$$

[例 12] 求证：$e$ 为无理数。

考虑反证法，假设 $e$ 可以被表示为既约分数 $\dfrac{M}{N}$。

由 $e^x$ 的带 Lagrange 余项的 Maclaurin 展开式可知：

$$
\forall n \in \mathbb{N}_+, \exists \theta \in (0, 1), \text{s.t. } e = \sum_{i = 0}^n \frac{1}{i!} + \frac{e^{\theta}}{(n + 1)!}
$$

由放缩可知 $e^{\theta} \in (1, 3)$。

- _Motivation：能不能通过某些方式，让余项导出矛盾？_

考虑在展开式两边同时乘上 $n!$，有 $\dfrac{e^{\theta}}{n + 1} = M (N - 1)! - \displaystyle\sum_{i = 0}^n \frac{n!}{i!} \in \mathbb{Z}$。

令 $n = \max(N, 2)$，可知 $\dfrac{e^{\theta}}{n + 1} \in (0, \dfrac{3}{n + 1}) \subseteq (0, 1)$，与其属于整数矛盾。

故假设不成立，即 $e$ 为无理数。

#### 定义：函数的解析性

若 $f$ 在定义域内总是可以展开为 Maclaurin 级数，则称 $f$ 是解析的，如 $e^x, \sin x, \cos x$ 等。

#### 反例：任意阶可导但不解析的函数

考察函数 $f(x) = \begin{cases} e^{-\frac{1}{x}}, &\quad x > 0 \\ 0, &\quad x \leq 0 \end{cases}$。

显然有：

- $\forall x > 0, f'(x) = \dfrac{1}{x^2} e^{-\frac{1}{x}}$。
- $f'_-(0) = 0$。
- $\forall x < 0, f'(x) = 0$。

而 $f'_+(0)$ 的计算如下：

$$
\begin{aligned}
f'_+(0) &= \lim_{x \to 0^+} \frac{e^{-\frac{1}{x}} - 0}{x - 0} \\
&= \lim_{y \to +\infty} \frac{y}{e^y} \\
&= \lim_{y \to +\infty} \frac{1}{e^y} \\
&= 0
\end{aligned}
$$

故 $f'(0) = 0$。

进一步地，通过洛必达法则可以归纳出 $f^{2n}(x) = \begin{cases} P_{2n}(\dfrac{1}{x}) e^{-\frac{1}{x}}, &\quad x > 0 \\ 0, &\quad x \leq 0 \end{cases}$，故 $f$ 任意阶可导。

写出其 Maclaurin 级数，发现结果恒为 $0$，与 $f$ 在 $(0, +\infty)$ 上非零矛盾，故 $f$ 不解析。

### 应用：证明不等式

#### 法一：带 Lagrange 余项的 Taylor 公式 + 放缩余项

[例 13] 求证：$\forall x \in \mathbb{R}, e^x \geq 1 + x$。

由带 Lagrange 余项的 Maclaurin 公式可知：

$$
\begin{aligned}
\exists \theta \in (0, 1), \text{s.t. } e^x &= 1 + x + \dfrac{1}{2} x^2 e^{\theta x} \\
&\geq 1 + x
\end{aligned}
$$

[例 14] 求证：$\forall x > -1, \alpha > 1, (1 + x)^{\alpha} \geq 1 + \alpha x$。

由带 Lagrange 余项的 Maclaurin 公式可知：

$$
\begin{aligned}
\exists \theta \in (0, 1), \text{s.t. } (1 + x)^{\alpha} &= 1 + \alpha x + \frac{\alpha (\alpha - 1)}{2} x^2 (1 + \theta x)^{\alpha} \\
&\geq 1 + \alpha x
\end{aligned}
$$

#### 法二：构造函数并研究其单调性或最值

[例 15] 求证：$\forall x \in (0, \dfrac{\pi}{2}], \dfrac{\sin x}{x} \geq \dfrac{2}{\pi}$。

- 这就是 $y = \sin x$ 连接 $(0, 0), (\dfrac{\pi}{2}, 1)$ 的“割线放缩”。

令 $f(x) = \dfrac{\sin x}{x}$，则 $f'(x) = \dfrac{x \cos x - \sin x}{x^2}$。

由 $\forall x \in (0, \dfrac{\pi}{2}), x < \tan x$，可得 $f'(x) < 0$，故 $f$ 在 $(0, \dfrac{\pi}{2}]$ 上严格单调递减。

故 $\forall x \in (0, \dfrac{\pi}{2}], f(x) \geq f(\dfrac{\pi}{2}) = \dfrac{2}{\pi}$。
