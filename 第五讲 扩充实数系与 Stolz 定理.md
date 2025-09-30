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

内容：

- 条件：(1) $\{x_n\}$ 每项大于零且严格单调递增；(2) $\{x_n\}$ 发散于正无穷；(3) $\exists a \in \mathbb{R}, \displaystyle\lim_{n \to +\infty} \frac{y_{n + 1} - y_n}{x_{n + 1} - x_n} = a$。
- 结论：$\displaystyle\lim_{n \to +\infty} \frac{y_n}{x_n} = a$。

[例] 已知 $\displaystyle\lim_{n \to +\infty} x_n = a \in \mathbb{R}$，求证：$\displaystyle\lim_{n \to +\infty} \frac{\sum_{i = 1}^n i x_i}{n^2} = \frac{a}{2}$。

- 由 Stolz 定理，只需考察 $\dfrac{(n + 1) x_{n + 1}}{(n + 1)^2 - n^2} = \dfrac{n + 1}{2n + 1} x_{n + 1}$。
- $\displaystyle\lim_{n  \to +\infty} \frac{n + 1}{2n + 1} x_{n + 1} = (\lim_{n \to +\infty} \frac{n + 1}{2n + 1})(\lim_{n \to +\infty} x_{n + 1}) = \frac{a}{2}$，进而可推知结论。

------

如果差分一次后仍不能确定其收敛性，可以试着继续差分。