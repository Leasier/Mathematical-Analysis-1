# 第十四讲 Cauchy 中值定理与 L'Hôpital 法则

### 洛必达 L'Hôpital 法则

我们有时需要确定形如 $\dfrac{0}{0}, \dfrac{\infty}{\infty}$ 的不定式。

#### 柯西 Cauchy 中值定理

- 由有限增量公式可知 $\exists \xi_1 \in (a, b), \text{s.t. } f(a) - f(b) = f'(\xi_1) (a - b), \exists \xi_2 \in (a, b), \text{s.t. } g(a) - g(b) = g'(\xi_2) (a - b)$。
- 于是 $\dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi_1)}{g'(\xi_2)}$。
- 那么，能不能构造 $\xi \in (a, b)$，使得 $\dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi)}{g'(\xi)}$ 呢？

条件：

- (1) $f, g$ 在 $[a, b]$ 上连续，在 $(a, b)$ 上可导。
- (2) $\forall x \in (a, b), g'(x) \neq 0$。

结论：$\exists \xi \in (a, b), \text{s.t. } \dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi)}{g'(\xi)}$。

- 这里有一个小问题：为什么不要求 $g(a) \neq g(b)$？
- 如果 $g(a) = g(b)$，由罗尔定理可知 $\exists \xi \in (a, b), \text{s.t. } g'(\xi) = 0$，与 $g$ 在 $(a, b)$ 上的导数非零矛盾。

内容：

- _Motivation：能不能仿照拉格朗日定理的证明构造函数呢？_
- 考虑在 $[a, b]$ 上构造函数 $F$，使得 $\forall x \in (a, b), F'(x) = (g(b) - g(a)) f'(x) - (f(b) - f(a)) g'(x)$。
- 不难发现令 $\forall x \in [a, b], F(x) = (g(b) - g(a)) f(x) - (f(b) - f(a)) g(x)$ 即可。
- 注意到 $F(a) = F(b) = g(b) f(a) - f(b) g(a)$，故由罗尔定理可知 $\exists \xi \in (a, b), \text{s.t. } F'(\xi) = 0 \Rightarrow \dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi)}{g'(\xi)}$。

#### 定理 1：$\check{U}(\infty)$ 上的 $\dfrac{\infty}{\infty} = \infty$ 型极限

条件：

- (1) $f, g$ 在 $\check{U}(\infty)$ 上可导。
- (2) $\forall x \in \check{U}(\infty), g'(x) \neq 0$。
- (3) $\displaystyle\lim_{x \to \infty} g(x) = \infty$。
- (4) $\displaystyle\lim_{x \to \infty} \frac{f'(x)}{g'(x)} = \infty$。

结论：$\displaystyle\lim_{x \to \infty} \frac{f(x)}{g(x)} = \infty$。

证明：

- 下面只证 $x \to +\infty$ 的情况，$x \to -\infty$ 是同理的。
- 由条件 (4) 可知：$\forall M_1 > 0, \exists \Delta_1 \in \check{U}(+\infty), \text{s.t. } \forall x > \Delta_1, |\dfrac{f'(x)}{g'(x)}| > M_1$。
- $\forall \Delta_1 \leq a < b$，由柯西中值定理可知 $\exists \xi \in (a, b), \text{s.t. } \dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi)}{g'(\xi)}$。
- _Motivation：我们能通过 $\xi$ 表出目标形式 $\dfrac{f(b)}{g(b)}$ 吗？_
- 由上式可知 $\dfrac{f(b)}{g(b)} = \dfrac{f'(\xi)}{g'(\xi)} (1 - \dfrac{g(a)}{g(b)}) + \dfrac{f(a)}{g(b)}$。
- _Motivation：$\dfrac{f'(\xi)}{g'(\xi)}$ 的绝对值随 $\xi$ 增大呈现出增大的趋势，$\dfrac{g(a)}{g(b)}, \dfrac{f(a)}{g(b)}$ 的绝对值随 $b$ 增大呈现出减小的趋势。这样看来，是否可以考虑让加和中前一项占主导？_
- _Motivation：但问题在于 $\dfrac{g(a)}{g(b)}$ 的绝对值随 $a$ 增大也呈现出增大的趋势，我们甚至不知道 $\dfrac{f(a)}{g(b)}$ 的绝对值随 $a$ 增大时的变化趋势。为便讨论，是否需要对 $a$ 的范围加以限制，使得 $f(a), g(a)$ 是“可控”的？或者更大胆地，令 $a = \Delta_1$？_
- 令 $a = \Delta_1$，由条件 (3) 可知：令 $M_2 = \max(3 |g(a)|, \dfrac{3 |f(a)|}{M_1})$，则 $\exists \Delta_2 \in \check{U}(+\infty), \text{s.t. } \forall x > \Delta_2, |g(x)| > M_2$。
- 令 $M_0 = \dfrac{1}{3} M_1, \Delta_0 = \max(\Delta_1, \Delta_2)$，则 $\forall b > \Delta_0, |\dfrac{g(a)}{g(b)}| < \dfrac{1}{3}, |\dfrac{f(a)}{g(b)}| < \dfrac{1}{3} M_1$，而与之对应的 $\xi$ 满足 $|\dfrac{f'(\xi)}{g'(\xi)}| > M_1$，故 $|\dfrac{f(b)}{g(b)}| \geq ||\dfrac{f'(\xi)}{g'(\xi)}| \cdot |1 - \dfrac{g(a)}{g(b)}| - |\dfrac{f(a)}{g(b)}||$。
- 由于 $|\dfrac{f'(\xi)}{g'(\xi)}| \cdot |1 - \dfrac{g(a)}{g(b)}| > \dfrac{2}{3} M_1 > \dfrac{1}{3} M_1 > |\dfrac{f(a)}{g(b)}|$，可知 $|\dfrac{f(b)}{g(b)}| > \dfrac{2}{3} M_1 - \dfrac{1}{3} M_1 = M_0$。
- 故 $\displaystyle\lim_{x \to \infty} \frac{f(x)}{g(x)} = \infty$。

#### 定理 2：$\check{U}(a)$ 上的 $\dfrac{\infty}{\infty} = \infty$ 型极限

- _Motivation：我们想要将其转化为定理 1 的情形。_

考虑 $\displaystyle\lim_{x \to a} \dfrac{f(x)}{g(x)}$，令 $\tilde{f}(x) = f(\dfrac{1}{x - a}), \tilde{g}(x) = g(\dfrac{1}{x - a})$，则只需求 $\displaystyle\lim_{x \to \infty} \dfrac{\tilde{f}(x)}{\tilde{g}(x)}$。

求得 $\tilde{f}'(x) = -\dfrac{f'(\frac{1}{x - a})}{(x - a)^2}, \tilde{g}'(x) = -\dfrac{g'(\frac{1}{x - a})}{(x - a)^2}$，此时要求：

- (1) $\tilde{f}, \tilde{g}$ 在 $\check{U}(\infty)$ 上可导 $\Rightarrow f, g$ 在 $\check{U}(a)$ 上可导。
- (2) $\forall x \in \check{U}(\infty), \tilde{g}'(x) \neq 0 \Rightarrow \forall x \in \check{U}(a), g'(x) \neq 0$。
- (3) $\displaystyle\lim_{x \to \infty} \tilde{g}(x) = \infty \Rightarrow \lim_{x \to \infty} g(x) = \infty$。
- (4) $\displaystyle\lim_{x \to \infty} \frac{\tilde{f}'(x)}{\tilde{g}'(x)} = \infty \Rightarrow \lim_{x \to a} \frac{f'(x)}{g'(x)} = \infty$。

因此，在满足上面四条对 $f, g$ 的限制的情况下，通过定理 1 即可得到结论：

- $\displaystyle\lim_{x \to \infty} \frac{\tilde{f}(x)}{\tilde{g}(x)} = \infty \Rightarrow \lim_{x \to a} \frac{f(x)}{g(x)} = \infty$。

------

事实上，洛必达法则一共有 $8$ 种情况，可以这样分类：

- 自变量是趋向 $\infty$ 还是 $a \in \mathbb{R}$？（注：这里不区分 $(\pm) \infty$。）
- 形式是 $\dfrac{\infty}{\infty}$ 还是 $\dfrac{0}{0}$？（注：$0 \cdot \infty$ 可以转化为另外两种情况。）
- 导函数极限是趋于 $\infty$ 还是 $A \in \mathbb{R}$？

下面给出自变量趋向 $\infty$、形式为 $\dfrac{0}{0}$、导函数趋于 $A \in \mathbb{R}$ 的情况。

#### 定理 3：$\check{U}(\infty)$ 上的 $\dfrac{0}{0} = A$ 型极限

条件：

- (1) $f, g$ 在 $\check{U}(\infty)$ 上可导。
- (2) $\forall x \in \check{U}(\infty), g'(x) \neq 0$。
- (3) $\displaystyle\lim_{x \to \infty} f(x) = \lim_{x \to \infty} g(x) = 0$。
- (4) $\displaystyle\lim_{x \to \infty} \frac{f'(x)}{g'(x)} = A$。

结论：$\displaystyle\lim_{x \to \infty} \frac{f(x)}{g(x)} = A$。

证明：

- 下面还是只证 $x \to +\infty$ 的情况，$x \to -\infty$ 依然是同理的。
- $\forall \epsilon > 0, \exists \Delta_1 \in \check{U}(+\infty), \text{s.t. } \forall x > \Delta_1, |\dfrac{f'(x)}{g'(x)} - A| < \epsilon$。
- $\forall \Delta_1 \leq a < b$，由柯西中值定理可知 $\exists \xi \in (a, b), \text{s.t. } \dfrac{f(a) - f(b)}{g(a) - g(b)} = \dfrac{f'(\xi)}{g'(\xi)}$。
- ~~由上式可知 $\dfrac{f(b)}{g(b)} = \dfrac{f'(\xi)}{g'(\xi)} (1 - \dfrac{g(a)}{g(b)}) + \dfrac{f(a)}{g(b)}$。~~
- _Motivation：此时 $\dfrac{f'(\xi)}{g'(\xi)}$ 已经离 $A$ “很近”了，我们期待 $\dfrac{g(a)}{g(b)}, \dfrac{f(a)}{g(b)}$ “很小”。_
- _Motivation：但这里与定理 1 恰好反过来了，$b$ 越大，它带来的影响就越难以估量，感觉需要反过来？
- 由上式可知 $\dfrac{f(a)}{g(a)} = \dfrac{f'(\xi)}{g'(\xi)} (1 - \dfrac{g(b)}{g(a)}) + \dfrac{f(b)}{g(a)}$，则 $|\dfrac{f(a)}{g(a)} - A| = |-A \cdot \dfrac{g(b)}{g(a)} + (\dfrac{f'(\xi)}{g'(\xi)} - A) (1 - \dfrac{g(b)}{g(a)}) + \dfrac{f(b)}{g(a)}| < A |\dfrac{g(b)}{g(a)}| + (1 + |\dfrac{g(b)}{g(a)}|) \epsilon + |\dfrac{f(b)}{g(a)}|$。
- 对于**取定**的 $a > \Delta_1$：
- (1) 由 $\displaystyle\lim_{x \to +\infty} f(x) = 0$ 可知：$\exists \Delta_2 > a, \text{s.t. } \forall b > \Delta_2, |f(b)| < |g(a)| \epsilon$。
- (2) 由 $\displaystyle\lim_{x \to +\infty} g(x) = 0$ 可知：$\exists \Delta_3 > a, \text{s.t. } \forall b > \Delta_3, |g(b)| < \min(|g(a)|, \dfrac{|g(a)| \epsilon}{A})$。
- 故任取 $b > \max(\Delta_2, \Delta_3)$，可知 $|\dfrac{f(a)}{g(a)} - A| < \epsilon + (1 + 1) \epsilon + \epsilon = 4 \epsilon$。
- 即 $\forall \epsilon > 0, \exists \Delta_1 \in \check{U}(+\infty), \text{s.t. } \forall a > \Delta_1, |\dfrac{f(a)}{g(a)} - A| < 4 \epsilon$，故 $\displaystyle\lim_{x \to \infty} \frac{f(x)}{g(x)} = A$。

------

余下情形的证明略去，最后给出完整的洛必达法则：

#### 形式 1

条件：

- (1) $a \in \mathbb{R}$ 或 $a = (\pm) \infty$，$f, g$ 在 $\check{U}(a)$ 上可导。
- (2) $\forall x \in \check{U}(a), g'(x) \neq 0$。
- (3) $\displaystyle\lim_{x \to a} g(x) = (\pm) \infty$。
- (4) $A \in \mathbb{R}$ 或 $A = (\pm) \infty$，$\displaystyle\lim_{x \to a} \frac{f'(x)}{g'(x)} = A$。

结论：$\displaystyle\lim_{x \to a} \frac{f(x)}{g(x)} = A$。

#### 结论 2

条件：

- (1) $a \in \mathbb{R}$ 或 $a = (\pm) \infty$，$f, g$ 在 $\check{U}(a)$ 上可导。
- (2) $\forall x \in \check{U}(a), g'(x) \neq 0$。
- (3) $\displaystyle\lim_{x \to a} f(x) = \lim_{x \to a} g(x) = 0$。
- (4) $A \in \mathbb{R}$ 或 $A = (\pm) \infty$，$\displaystyle\lim_{x \to a} \frac{f'(x)}{g'(x)} = A$。

结论：$\displaystyle\lim_{x \to a} \frac{f(x)}{g(x)} = A$。

------

实践中，为了求出一个极限，有时我们需要应用多次洛必达法则。

- **注意：每一步都要看是否满足洛必达法则的条件！**

[例 1] 求 $\displaystyle\lim_{x \to 0} \dfrac{x - \sin x}{x^3}$。

- $f(x) = x - \sin x, g(x) = x^3$，为 $\dfrac{0}{0}$ 型，且满足条件。
- $f'(x) = 1 - \cos x, g'(x) = 3x^2$，为 $\dfrac{0}{0}$ 型，且满足条件。
- $f''(x) = \sin x, g''(x) = 6x$，由 $\displaystyle\lim_{x \to 0} \dfrac{\sin x}{x} = 1$ 立即可得 $\displaystyle\lim_{x \to 0} \dfrac{f''(x)}{g''(x)} = \dfrac{1}{6}$。
- 故 $\displaystyle\lim_{x \to 0} \dfrac{f(x)}{g(x)} = \lim_{x \to 0} \dfrac{f'(x)}{g'(x)} = \lim_{x \to 0} \dfrac{f''(x)}{g''(x)} = \dfrac{1}{6}$。

[例 2] 求 $\displaystyle\lim_{x \to 0} \dfrac{x - \sin x}{x^2 \sin x}$。

- **注意：不要看到极限就直接开始使用洛必达法则！这可能会让问题变复杂！**

注意到 $\dfrac{x - \sin x}{x^2 \sin x} = \dfrac{x - \sin x}{x^3} \cdot \dfrac{x}{\sin x}$，则 $\displaystyle\lim_{x \to 0} \dfrac{x - \sin x}{x^2 \sin x} = (\lim_{x \to 0} \dfrac{x - \sin x}{x^3}) (\lim_{x \to 0} \dfrac{x}{\sin x}) = \dfrac{1}{6}$。

[例 3] 求 $\displaystyle\lim_{x \to +\infty} x (\dfrac{\pi}{2} - \arctan x)$。

- _Motivation：对于这个 $0 \cdot \infty$，如果把较复杂的 $\dfrac{\pi}{2} - \arctan x$ 放到分母上去变成 $\dfrac{1}{\frac{\pi}{2} - \arctan x}$，求导后会变得很复杂。_
- $f(x) = \dfrac{\pi}{2} - \arctan x, g(x) = \dfrac{1}{x}$，为 $\dfrac{0}{0}$ 型，且满足条件。
- $f'(x) = -\dfrac{1}{x^2 + 1}, g'(x) = -\dfrac{1}{x^2}$。
- 故 $\displaystyle\lim_{x \to +\infty} \dfrac{f(x)}{g(x)} = \lim_{x \to +\infty} \dfrac{f'(x)}{g'(x)} = \lim_{x \to +\infty} \dfrac{x^2}{x^2 + 1} = \lim_{x \to +\infty} \dfrac{1}{1 + \frac{1}{x^2}} = 1$。
