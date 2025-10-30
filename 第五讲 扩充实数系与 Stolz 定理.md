# 第五讲 扩充实数系与 Stolz 定理

### 扩充实数系

#### 定义

将集合 $\mathbb{R} \cup \{+\infty, -\infty\}$ 称作扩充实数系，记作 $\overline{\mathbb{R}}$。

- 注意：$+\infty, -\infty$ 仅仅是一种**记号**，我们不认为它们是数。

#### 一些简化记号

$\{x_n\}$ 发散到正、负无穷分别可以记作 $\displaystyle\lim_{n \to +\infty} x_n = \pm \infty$。

$\{x_n\}$ 为无穷大序列可以记作 $\displaystyle\lim_{n \to +\infty} x_n = \infty$。

非空集合 $E \subseteq R$ 无上、下界分别可记作 $\sup R = +\infty, \inf E = -\infty$。

$x$ 为有限实数可记作 $-\infty < x < +\infty$。

实数序列在扩充实数系中**至多**只有一个极限。

- 注意：这里不能说一个序列的极限**是 / 收敛到** $\pm \infty$。

#### 一些定理在无穷处的扩展

夹挤原理：

- 条件：对于实数序列 $\{x_n\}, \{y_n\}$，假设 $\exists N \in \mathbb{N}, \text{s.t. } \forall n > N, -\infty < x_n \leq y_n < +\infty$。
- 内容：(1) 若 $\displaystyle\lim_{n \to +\infty} x_n = +\infty$，则 $\displaystyle\lim_{n \to +\infty} y_n = +\infty$；(2) 若 $\displaystyle\lim_{n \to +\infty} y_n = -\infty$，则 $\displaystyle\lim_{n \to +\infty} x_n = -\infty$。

B-W 定理的推论（**无穷大序列的子序列也是无穷大序列**）：

- 若 $\displaystyle\lim_{n \to +\infty} x_n = (\pm) \infty$，则对于其任意子序列 $\{x_{n_k}\}$，均有 $\displaystyle\lim_{k \to +\infty} x_{n_k} = (\pm) \infty$。

#### 收敛序列与无穷大序列的四则运算（略）

### Stolz 定理

#### Stolz 定理的内容

- 条件：(1) $\{x_n\}$ 每项大于零且严格单调递增；(2) $\{x_n\}$ 发散于正无穷；(3) $\exists a \in \mathbb{R}, \displaystyle\lim_{n \to +\infty} \frac{y_{n + 1} - y_n}{x_{n + 1} - x_n} = a$。
- 结论：$\displaystyle\lim_{n \to +\infty} \frac{y_n}{x_n} = a$。

如果差分一次后仍不能确定其收敛性，可以试着继续差分。

[例] 已知 $\displaystyle\lim_{n \to +\infty} x_n = a \in \mathbb{R}$，求证：$\displaystyle\lim_{n \to +\infty} \frac{\displaystyle\sum_{i = 1}^n i x_i}{n^2} = \frac{a}{2}$。

- 由 Stolz 定理，只需考察 $\dfrac{(n + 1) x_{n + 1}}{(n + 1)^2 - n^2} = \dfrac{n + 1}{2n + 1} x_{n + 1}$。
- $\displaystyle\lim_{n  \to +\infty} \frac{n + 1}{2n + 1} x_{n + 1} = (\lim_{n \to +\infty} \frac{n + 1}{2n + 1})(\lim_{n \to +\infty} x_{n + 1}) = \frac{a}{2}$，进而可推知结论。

------

#### Toeplitz 变换

构造一个“三角形数表”，$\forall i \in \mathbb{N}_+$，第 $i$ 行有 $i$ 个数 $t_{i, 1}, t_{i, 2}, \cdots, t_{i, i}$，满足：

- $t_{i, j} \geq 0$。
- $\displaystyle\sum_{j = 1}^i t_{i, j} = 1$。
- $\forall j \in \mathbb{N}_+, \displaystyle\lim_{i \to +\infty} t_{i, j} = 0$。

此时，我们将 $\{a_n\}$ 变换为 $\{b_n\}$，满足 $b_n = \displaystyle\sum_{i = 1}^n t_{n, i} a_i$。这一过程称作 Toeplitz 变换。

一个先前讨论过的特例是 $t_{i, j} = \dfrac{1}{i}$，即 $\{b_n\}$ 每项为 $\{a_n\}$ 的前缀均值。

#### 引理 1

内容：若 $\displaystyle\lim_{n \to +\infty} a_n = 0$，则 $\displaystyle\lim_{n \to +\infty} b_n = 0$。

证明（**拆分，一部分利用极限定义，另一部分有限，可以继续操作**）：

- $\forall \epsilon > 0, \exists N \in \mathbb{N}_+, \text{s.t. } \forall n > N, |a_n| < \dfrac{\epsilon}{2} \Rightarrow \displaystyle\sum_{i = N + 1}^n t_{n, i} |a_i| < \sum_{i = N + 1}^n t_{n, i} \cdot \frac{\epsilon}{2} \leq \frac{\epsilon}{2}$。
- 接下来讨论 $c_n = \displaystyle\sum_{i = 1}^N t_{n, i} a_i$。$\forall i \in \mathbb{N} \cap i \leq N$，由于 $\{t_{n, i}\}_{n \in \mathbb{N}_+}$ 是无穷小序列，有 $\{t_{n, i} a_i\}_{n \in \mathbb{N}_{\geq N}}$ 也为无穷小序列，接着将这 $N$ 个无穷小序列加起来，得到的 $\{c_n\}_{n \in \mathbb{N}_{\geq N}}$ 还是无穷小序列。
- 故 $\exists N' \in \mathbb{N}_{\geq N}, \text{s.t. } \forall n > N', |c_n| < \dfrac{\epsilon}{2}$。
- 进而 $\forall n > N', |b_n| \leq |c_n| + \displaystyle\sum_{i = N + 1}^n t_{n, i} |a_i| < \epsilon$，则 $\displaystyle\lim_{n \to +\infty} b_n = 0$。

#### 引理 2

内容：若 $\displaystyle\lim_{n \to +\infty} a_n = a$，则 $\displaystyle\lim_{n \to +\infty} b_n = a$。

利用引理 1 易证，略去。

#### Stolz 定理的证明

方便起见，不妨令 $x_0 = y_0 = 0$。

令 $a_n = \dfrac{y_n - y_{n - 1}}{x_n - x_{n - 1}}, b_n = \dfrac{y_n}{x_n}, \forall i \in \mathbb{N} \cap i \leq n, t_{n, i} = \dfrac{x_i - x_{i - 1}}{x_n}$。

此时有 $\displaystyle\sum_{i = 1}^n t_{n, i} a_i = \sum_{i = 1}^n \frac{y_i - y_{i - 1}}{x_n} = \frac{y_n}{x_n} = b_n$。

由引理 2 可知 $\displaystyle\lim_{n \to +\infty} b_n = a$。
