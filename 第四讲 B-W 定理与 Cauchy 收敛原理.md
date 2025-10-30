# 第四讲 B-W 定理与 Cauchy 收敛原理

[例 1] 当 $\alpha \in \mathbb{R}_{\geq 2}$，求证：$x_n = \displaystyle\sum_{k = 1}^n \dfrac{1}{k^{\alpha}}$ 收敛。

注意到 $x_n$ **单调递增**，且当 $k \in \mathbb{N}_{\geq 2}$，均有 $\dfrac{1}{k^{\alpha}} \leq \dfrac{1}{k^2} \leq \dfrac{1}{(k - 1) k} = \dfrac{1}{k - 1} - \dfrac{1}{k}$，则 $x_n \leq 2 - \dfrac{1}{n}$。

故 $\{x_n\}$ 有界为 $2$。运用**确界定理**即可。

[例 2] _见第三讲例 7。_

------

### 闭区间套定理

内容：我们称 $\{[a_n, b_n]\}$ 为一个闭区间套，当且仅当 $\forall n \in \mathbb{N}, [a_{n + 1}, b_{n + 1}] \subseteq [a_n, b_n]$。

下设 $\displaystyle\lim_{n \to +\infty} a_n = a^*, \displaystyle\lim_{n \to +\infty} b_n = b^*$。

- 若 $a^* < b^*$，则 $\cap_{n = 0}^{+\infty} [a_n, b_n] = [a^*, b^*]$。
- 若 $a^* = b^*$，则 $\cap_{n = 0}^{+\infty} [a_n, b_n] = \{a^*\}$。

证明（只考虑前者）：分别考虑 $\cap_{n = 0}^{+\infty} [a_n, b_n] \subseteq [a^*, b^*], [a^*, b^*] \subseteq \cap_{n = 0}^{+\infty} [a_n, b_n]$ 即可。

------

[例 3] 对于常数 $a \in \mathbb{R}_+$，求 $\displaystyle\lim_{n \to +\infty} \dfrac{a^n}{n!}$。

- _Motivation：当 $n$ 充分大，$n$ 每增大 $1$，序列单调递减。_

令 $x_n = \dfrac{a^n}{n!}$，则 $x_0 = 1$，$x_{n + 1} = \dfrac{a}{n + 1} x_n$。

1. 证明 $\{x_n\}$ 收敛

当 $n \geq \max(a - 1, 0)$，有 $x_{n + 1} \leq x_n$，且 $x_n$ 有下界为 $0$，则 $\{x_n\}$ 存在极限为 $x^*$（只有前面的**有限**项不单调递减）。

- **注意：类似情况下，极限为去掉不单调递减部分后的下确界！**

2. 求 $x^*$

考虑**递推**式：$\displaystyle\lim_{n \to +\infty} x_{n + 1} = x^*$，$\displaystyle\lim_{n \to +\infty} \dfrac{a}{n + 1} = 0$，则 $x^* = 0 \cdot x^*$，则 $x^* = 0$，即 $\displaystyle\lim_{n \to +\infty} \frac{a^n}{n!} = 0$。 

### B-W 定理

子序列：$\{n_k\}$ 是 $\mathbb{N}$ 中的严格单调递增序列，对 $\{x_n\}$ 而言，称 $\{x_{n_k}\}$ 为其一个子序列。

内容：有界序列一定存在一个收敛子序列。

证明（**构造法**）：

- 设 $a_0, b_0$ 为 $\{x_n\}$ 的上下界。
- 取中点 $c_0 = \dfrac{a_0 + b_0}{2}$，则 $[a_0, c_0], [c_0, b_0]$ 中至少一个区间内包含了 $\{x_n\}$ 的**无限项**。
- 不妨取 $[a_0, c_0]$ 满足条件，令 $a_1 = a_0, b_1 = c_0$，取 $n_0$ 满足 $x_{n_0} \in [a_1, b_1]$。
- 再取中点 $c_1 = \dfrac{a_1 + b_1}{2}$，则 $[a_1, c_1], [c_1, b_1]$ 中至少一个区间内包含了 $\{x_n\}_{n > n_0}$ 的**无限项**。
- 不妨取 $[a_1, c_1]$ 满足条件，令 $a_2 = a_1, b_2 = c_1$，取 $n_1$ 满足 $n_1 > n_0, x_{n_1} \in [a_2, b_2]$。
- 如此续行，可以构造出**闭区间套** $\{[a_n, b_n]\}$，使得 $\{n_k\}$ 严格单调递增，且 $\forall k \in \mathbb{N}, x_{n_k} \in [a_{k + 1}, b_{k + 1}]$。
- 由 $b_{n + 1} - a_{n + 1} = \dfrac{b_n - a_n}{2}$ 可知 $\displaystyle\lim_{n \to +\infty} (b_n - a_n) = 0$ 即 $a^* = b^*$（定义同前）。
- 由夹挤原理可知 $\displaystyle\lim_{n \to +\infty} x_{n_k} = a^*$。

#### 推论

内容：若 $\displaystyle\lim_{n \to +\infty} x_n = x^*$，则对于其任意子序列 $\{x_{n_k}\}$，均有 $\displaystyle\lim_{k \to +\infty} x_{n_k} = x^*$。

证明：考虑 $\displaystyle\lim_{k \to +\infty} n_k = +\infty$，具体过程略。

### 柯西 Cauchy 收敛原理

内容：$\{x_n\}$ 收敛 $\Leftrightarrow \forall \epsilon > 0, \exists N \in \mathbb{N}, \text{s.t. } \forall n, m > N, |x_n - x_m| < \epsilon$，另一表述为 $\forall \epsilon > 0, \exists N \in \mathbb{N}, \text{s.t. } \forall n > N, p \in \mathbb{N}, |x_{n + p} - x_n| < \epsilon$。

证明：

- $\Rightarrow$：$\exists x^* \in \mathbb{R}, \text{s.t. } \displaystyle\lim_{n \to +\infty} x_n = x^*$，且 $\forall \epsilon > 0, \exists N \in \mathbb{N}, \text{s.t. } \forall n, m > N, |x_n - x^*| < \epsilon, |x^* - x_m| < \epsilon$，则 $|x_n - x_m| \leq |x_n - x^*| + |x^* - x_m| < \epsilon$。
- $\Leftarrow$：考虑先证明其有界。

取 $\epsilon = 1$，则 $\exists N \in \mathbb{N}, \text{s.t. } \forall n > N + 1, |x_n - x_{N + 1}| < 1$，则 $|x_n| < |x_{N + 1}| + 1$。

取 $M = \max\{|x_0|, |x_1|, \cdots, |x_N|, |x_{N + 1}| + 1\}$，则 $\forall n \in \mathbb{N}, |x_i| \leq M$，即 $\{x_n\}$ 有界。

接下来根据 B-W 定理考察其收敛子序列。

$\exists$ 收敛子序列 $\{x_{n_k}\}$，$\text{s.t. } \displaystyle\lim_{k \to +\infty} x_{n_k} = a$。
$$
\forall \epsilon > 0, \begin{cases}
\exists K \in \mathbb{N}, \text{s.t. } \forall k > K, |x_{n_k} - a| < \dfrac{\epsilon}{2} \\
\exists N_0 \in \mathbb{N}, \text{s.t. } \forall n, m > N_0, |x_n - x_m| < \dfrac{\epsilon}{2}
\end{cases}
$$
由 $\displaystyle\lim_{k \to +\infty} n_k = +\infty$ 可知：
$$
\exists K_0 > K, \text{s.t. } n_{K_0} > N_0
$$
取 $N = n_{K_0}$，则：
$$
\forall n > N, |x_n - a| < |x_n - x_N| + |x_N - a| < \dfrac{\epsilon}{2} + \dfrac{\epsilon}{2} = \epsilon
$$
故 $\displaystyle\lim_{n \to +\infty} x_n = a$，即 $\{x_n\}$ 收敛。

[例 4] 求证：$x_n = \displaystyle\sum_{i = 1}^n \frac{1}{i}$ **不**收敛。

- 欲证 $\exists \epsilon > 0, \text{s.t. } \forall N \in \mathbb{N}_+, \exists n > N, p \in \mathbb{N}, \text{s.t. } |x_{n + p} - x_n| \geq \epsilon$。

$|x_{n + p} - x_n| = \displaystyle\sum_{i = 1}^p \frac{1}{n + i} \geq \frac{p}{n + p}$，取 $\epsilon = \dfrac{1}{2}, n = p = N + 1$，可知满足不收敛的叙述。

[例 5] 求证：$x_n = \displaystyle\sum_{i = 1}^n \frac{1}{i^2}$ 收敛。

$|x_{n + p} - x_n| = \displaystyle\sum_{i = 1}^p \frac{1}{(n + i)^2} \leq \sum_{i = 1}^p \frac{1}{(n + i - 1)(n + i)} = \sum_{i = 1}^p (\frac{1}{n + i - 1} - \frac{1}{n + i}) = \frac{1}{n} - \frac{1}{n + p} \leq \frac{1}{n}$，则 $\forall \epsilon > 0$，取 $N = \lceil \dfrac{1}{\epsilon} \rceil$ 即可。

------

我们称实数是**完备**的，因为在实数中定义的柯西序列收敛，但在其他数域中未必。

- e.g. 在 $\mathbb{Q}$ 中定义 $x_n = \dfrac{\lfloor 10^n \pi \rfloor}{10^n}$，则 $\{x_n\}$ 在 $\mathbb{Q}$ 中不收敛。

实数完备的原因在于其上有 **B-W 定理**，进一步来自**闭区间套定理**，再进一步来自**确界定理**，最终来自**确界原理**。

------

[例 6] 求证：$\{\tan(n)\}$ 不收敛。

法一：注意到 $\forall k \in \mathbb{N}$，在 $(k \pi + \dfrac{\pi}{6}, k \pi + \dfrac{\pi}{2}), (k \pi + \dfrac{\pi}{2}, k \pi + \dfrac{5 \pi}{6})$ 中总是各能抓出 $n_1, n_2 \in \mathbb{N}$（因为区间长度 $\dfrac{\pi}{3} > 1$），且 $\tan(n_1) > \dfrac{\sqrt{3}}{3}, \tan(n_2) < -\dfrac{\sqrt{3}}{3}$，则 $\{\tan(n)\}$ 不收敛。

法二：（**一阶递推对应的函数必须有不动点**）$\displaystyle\lim_{n \to +\infty} \tan(n) = \lim_{n \to +\infty} \tan(n + 1)$，假设极限存在，令之为 $A$，则 $A = \dfrac{A + \tan(1)}{1 - A \tan(1)} \Rightarrow A^2 = -1$，显然在 $\mathbb{R}$ 上无解，则 $\{\tan(n)\}$ 不收敛。

法三：（**证明其不是柯西序列**）

- 欲证 $\exists \epsilon > 0, \text{s.t. } \forall N \in \mathbb{N}, \exists n > N, p > 0, \text{s.t. } |\tan(n + p) - \tan(n)| \geq \epsilon$。
- 化简一下，要求 $\dfrac{\tan(p) (\tan^2(n) + 1)}{1 - \tan(n) \tan(p)} \geq \epsilon$。
- 稍微放缩一下，令 $p = 13$，只要 $\tan(n) \in (0, \dfrac{1}{\tan(13)})$ 即可令 $\epsilon = \tan(13)$。
- 这要求 $\exists k \in \mathbb{N}, \text{s.t. } n \in (k \pi, k \pi + (\dfrac{9}{2} \pi - 13))$。由于 $\dfrac{9}{2} \pi - 13 > 1$，任取一个 $k$，其中一定包含一个 $n$，则 $\{\tan(n)\}$ 不收敛。
