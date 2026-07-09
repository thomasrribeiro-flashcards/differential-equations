+++
order = 2
subject = "Math"
tags = ["math", "differential-equations", "ode", "separable", "integrating-factor", "first-order"]
+++

# Differential Equations — First-Order Separable and Linear Equations

## 2.1 Separable Equations

Q: Why is the separable form $\frac{dy}{dx} = g(x)h(y)$ special among first-order ODEs?
A: Its right-hand side factors cleanly into a part depending only on $x$ and a part depending only on $y$. This structural separation is what lets us move each variable to its own side of the equation and reduce solving an ODE to computing two ordinary integrals.

C: A first-order ODE is called [separable] when it can be written in the form $\frac{dy}{dx} = g(x)h(y)$, where $g$ depends only on the independent variable $x$ and $h$ depends only on the dependent variable $y$.

Q: Why does "separating variables" work as a solution method?
A: Because $g(x)$ and $h(y)$ depend on disjoint variables, we can rewrite the equation so that all $y$-dependence sits with $dy$ and all $x$-dependence sits with $dx$. Once each side is a function of only one variable, standard integration recovers an antiderivative on each side, linked by a single constant.

Q: Is $\frac{dy}{dx} = x + y$ separable?
A: No. The right-hand side is a sum of a function of $x$ and a function of $y$, not a product $g(x)h(y)$, so it cannot be factored into the separable form. It requires a different technique (it is actually linear in $y$).

Q: Is $\frac{dy}{dx} = xy + x$ separable?
A: Yes. Factoring gives $\frac{dy}{dx} = x(y+1) = g(x)h(y)$ with $g(x) = x$ and $h(y) = y+1$, so it is separable even though it did not appear so at first glance.

## 2.2 Solution Technique for Separable Equations

C: To solve $\frac{dy}{dx} = g(x)h(y)$, rewrite it as $\frac{dy}{h(y)} = g(x)\,dx$ and then [integrate both sides].

Q: What are the two steps of the separable solution method?
A: First, algebraically separate the variables so one side contains only $y$ and $dy$ and the other only $x$ and $dx$. Second, integrate both sides to obtain an equation relating $y$ and $x$, which implicitly or explicitly defines the solution.

Q: Before dividing by $h(y)$ to separate variables, what must you check?
A: You must check where $h(y) = 0$, because dividing by $h(y)$ is invalid at those points. Any $y$ values that make $h(y) = 0$ give constant (equilibrium) solutions that can be lost by the division step and must be restored at the end.

## 2.3 Implicit vs Explicit Solutions

Q: Why does integration of a separable ODE often produce an implicit rather than explicit solution?
A: After integrating $\int \frac{dy}{h(y)} = \int g(x)\,dx$, the left side is a function $H(y)$ and the right a function $G(x)$. The resulting equation $H(y) = G(x) + C$ relates $y$ and $x$ implicitly, and inverting $H$ to isolate $y$ may be algebraically impossible or messy.

C: A solution expressed as an equation relating $x$ and $y$ without isolating $y$ is called an [implicit] solution, while one of the form $y = f(x)$ is called an [explicit] solution.

Q: When should you prefer to leave a separable solution in implicit form?
A: When solving for $y$ requires a non-elementary inverse, introduces extraneous branches, or obscures the structure of the relationship. The implicit form $H(y) = G(x) + C$ is often cleaner and still fully determines $y$ locally.

## 2.4 The Constant of Integration

Q: Why does the separable method produce only one arbitrary constant, not two?
A: Integrating the left side gives $H(y) + C_1$ and the right gives $G(x) + C_2$. Moving both to one side yields $H(y) - G(x) = C_2 - C_1$, and the difference of two arbitrary constants is itself a single arbitrary constant $C$. So one constant absorbs both.

C: When integrating both sides of a separated equation, the two constants of integration combine into a [single] arbitrary constant $C$.

## 2.5 Singular Solutions and Equilibria

Q: What is a singular solution in the context of separable ODEs?
A: A solution that cannot be recovered by assigning any value to the constant $C$ in the general solution family. Such solutions are typically lost when we divide by $h(y)$ during separation, because division assumed $h(y) \ne 0$.

C: An [equilibrium] solution of $\frac{dy}{dx} = g(x)h(y)$ is a constant solution $y = y_0$ where $h(y_0) = 0$, making $\frac{dy}{dx} = 0$.

Q: Why must you separately check values where $h(y) = 0$ after solving a separable ODE?
A: Dividing by $h(y)$ excludes those values, so constant solutions $y = y_0$ with $h(y_0) = 0$ may not appear in the general solution family. They are genuine solutions (since $y' = 0 = g(x) \cdot 0$) and must be reported alongside the general solution.

Q: For $\frac{dy}{dx} = y(1-y)$, what are the equilibrium solutions?
A: The equilibria occur where $h(y) = y(1-y) = 0$, giving $y = 0$ and $y = 1$. These are constant functions that satisfy the ODE but would be lost when dividing by $y(1-y)$ during separation.

## 2.6 First-Order Linear ODE

C: A first-order ODE is called [linear] when it can be written in the standard form $y' + P(x)y = Q(x)$, where $P$ and $Q$ are functions of $x$ alone.

Q: What distinguishes a linear first-order ODE from the general linear $n$-th order form introduced previously?
A: Specializing $a_n(x)y^{(n)} + \cdots + a_0(x)y = g(x)$ to $n = 1$ gives $a_1(x)y' + a_0(x)y = g(x)$. Dividing by $a_1(x)$ (where nonzero) yields the standard form $y' + P(x)y = Q(x)$ with $P(x) = a_0(x)/a_1(x)$ and $Q(x) = g(x)/a_1(x)$.

Q: Why is the form $y' + P(x)y = Q(x)$ called "standard form"?
A: Because the coefficient of $y'$ has been normalized to $1$ by dividing through. This normalization is required for the integrating factor formula $\mu = e^{\int P\,dx}$ to be correct, since the derivation assumes $y'$ has coefficient $1$.

C: In the standard form $y' + P(x)y = Q(x)$, the ODE is called [homogeneous] when $Q(x) = 0$ and [nonhomogeneous] when $Q(x) \ne 0$.

## 2.7 Why Linear Equations Need a Different Technique

Q: Why can't the separation of variables method solve a general linear equation $y' + P(x)y = Q(x)$?
A: Rearranging gives $\frac{dy}{dx} = Q(x) - P(x)y$, which is a difference of a function of $x$ and a mixed $x,y$ term, not a product $g(x)h(y)$. Because the right side does not factor into separate $x$- and $y$-dependent pieces, variables cannot be separated when $Q(x) \ne 0$.

Q: When $Q(x) = 0$, why does a linear ODE become separable?
A: The equation reduces to $y' = -P(x)y$, which has the factored form $g(x)h(y)$ with $g(x) = -P(x)$ and $h(y) = y$. So every homogeneous linear first-order ODE is automatically separable.

## 2.8 The Integrating Factor

C: For the linear ODE $y' + P(x)y = Q(x)$, the [integrating factor] is $\mu(x) = e^{\int P(x)\,dx}$, where $P(x)$ is the coefficient of $y$ in standard form.

Q: Before deriving the integrating factor, predict: what property should $\mu(x)$ have so that $\mu y' + \mu P y$ becomes the derivative of a single product?
A: By the product rule, $(\mu y)' = \mu y' + \mu' y$. Matching this to $\mu y' + \mu P y$ requires $\mu' = \mu P$, i.e., $\mu$ must grow at rate $P$, which is exactly the differential equation $\mu' / \mu = P$ solved by $\mu = e^{\int P\,dx}$.

Q: Why does the constant of integration inside $\int P(x)\,dx$ not matter when computing $\mu$?
A: Any additive constant $C$ inside the integral becomes a multiplicative factor $e^C$ in $\mu$. Multiplying the ODE through by a nonzero constant does not change the equation's solutions, so we conventionally choose the constant to be zero.

## 2.9 Why the Integrating Factor Works

Q: Why does multiplying $y' + P(x)y = Q(x)$ by $\mu(x) = e^{\int P\,dx}$ help?
A: The left side becomes $\mu y' + \mu P y$, which by the product rule equals $(\mu y)'$ exactly — precisely because $\mu$ was chosen so $\mu' = \mu P$. The ODE then reads $(\mu y)' = \mu Q$, so a single integration on each side recovers $\mu y$ and hence $y$.

C: After multiplying by the integrating factor $\mu$, the left-hand side of a linear ODE collapses into the exact derivative [$(\mu y)'$].

Q: Why is turning the left-hand side into an exact derivative the key step in solving linear ODEs?
A: Once $(\mu y)' = \mu Q$, both sides can be integrated directly: the left side integrates to $\mu y$, and the right side to $\int \mu Q\,dx + C$. The ODE has been reduced to evaluating one integral, which is always solvable in principle.

## 2.10 The Solution Formula

C: The general solution of the linear ODE $y' + P(x)y = Q(x)$ is $y = [\frac{1}{\mu(x)}\left(\int \mu(x)Q(x)\,dx + C\right)]$, where $\mu(x) = e^{\int P(x)\,dx}$ is the integrating factor and $C$ is an arbitrary constant.

Q: Where does the $\frac{1}{\mu(x)}$ factor in the linear solution formula come from?
A: After integrating $(\mu y)' = \mu Q$ we obtain $\mu y = \int \mu Q\,dx + C$. Dividing both sides by $\mu$ isolates $y$, producing the factor $\frac{1}{\mu}$ multiplying the integrated right-hand side.

Q: In the solution formula $y = \mu^{-1}\left(\int \mu Q\,dx + C\right)$, what role does the constant $C$ play?
A: It encodes the one-parameter family of solutions arising from the undetermined constant of integration. Each choice of $C$ corresponds to a different solution curve; a specific value is pinned down by an initial condition.

## 2.11 Applying an Initial Condition

Q: How do you use an initial condition $y(x_0) = y_0$ to determine $C$ in a linear ODE solution?
A: Substitute $x = x_0$ and $y = y_0$ into the general solution $y(x) = \mu^{-1}(x)\left(\int \mu Q\,dx + C\right)$, then solve the resulting algebraic equation for $C$. The particular solution is then the general formula with that specific $C$ value.

C: Once the general solution of a linear first-order ODE is known, an initial condition $y(x_0) = y_0$ selects the [particular solution] by fixing the value of the constant $C$.

## 2.12 When a Linear Equation Is Also Separable

Q: Under what condition is a linear first-order ODE also separable?
A: When it is homogeneous, i.e., $Q(x) = 0$. The equation $y' + P(x)y = 0$ rearranges to $\frac{dy}{y} = -P(x)\,dx$, a separable form. For any $Q(x) \ne 0$, the ODE is linear but not separable.

Q: Is $y' + 3y = 0$ separable, linear, both, or neither?
A: Both. It is linear with $P(x) = 3$, $Q(x) = 0$, and since $Q = 0$ it is also separable: $\frac{dy}{y} = -3\,dx$, giving $y = Ce^{-3x}$. Either method yields the same answer.

Q: Is $y' + 3y = \sin x$ separable, linear, both, or neither?
A: Linear only. It has the standard form with $P(x) = 3$ and $Q(x) = \sin x \ne 0$, so the integrating factor method applies, but the $\sin x$ term prevents separation of variables.

## 2.13 Choosing the Right First-Order Technique

Q: Given a first-order ODE, what is the flowchart for choosing between the separable and linear techniques?
A: First, try to write it as $\frac{dy}{dx} = g(x)h(y)$; if that works, use separation of variables. Otherwise, try to rearrange into standard form $y' + P(x)y = Q(x)$; if that works, use the integrating factor method. If both work, either is fine — separation is usually faster.

Q: Why check for separability before applying the integrating factor method?
A: Separation of variables typically requires only two direct integrations, while the integrating factor method requires computing $\mu$, then $\int \mu Q\,dx$, then dividing. When both apply, separation is usually computationally lighter.

## 2.14 Worked Problems

P: Solve the initial value problem $y' + 2xy = x$ with $y(0) = 2$ using the integrating factor method.

S:
**IDENTIFY**: First-order linear ODE in standard form $y' + P(x)y = Q(x)$ with $P(x) = 2x$ and $Q(x) = x$; nonhomogeneous (since $Q \ne 0$), so not separable. Initial condition $y(0) = 2$ requests a particular solution.

**PLAN**:
- Compute integrating factor $\mu(x) = e^{\int P\,dx} = e^{\int 2x\,dx}$.
- Multiply the ODE by $\mu$ and recognize the left side as $(\mu y)'$.
- Integrate both sides, solve for $y$, then apply $y(0) = 2$ to find $C$.

**EXECUTE**:
1. $\int 2x\,dx = x^2$, so $\mu(x) = e^{x^2}$.
2. Multiplying: $e^{x^2}y' + 2x e^{x^2}y = x e^{x^2}$, i.e., $\left(e^{x^2}y\right)' = x e^{x^2}$.
3. Integrate: $e^{x^2}y = \int x e^{x^2}\,dx = \tfrac{1}{2} e^{x^2} + C$ (using substitution $u = x^2$).
4. Solve for $y$: $y(x) = \tfrac{1}{2} + C e^{-x^2}$.
5. Apply $y(0) = 2$: $2 = \tfrac{1}{2} + C \cdot 1$, so $C = \tfrac{3}{2}$.
6. Particular solution: $y(x) = \tfrac{1}{2} + \tfrac{3}{2} e^{-x^2}$.

**EVALUATE**:
- Check the IC: $y(0) = \tfrac{1}{2} + \tfrac{3}{2} = 2$. ✓
- Check the ODE: $y' = -3x e^{-x^2}$, and $y' + 2xy = -3x e^{-x^2} + 2x\left(\tfrac{1}{2} + \tfrac{3}{2}e^{-x^2}\right) = -3x e^{-x^2} + x + 3x e^{-x^2} = x$. ✓
- As $x \to \infty$, $y \to \tfrac{1}{2}$, the equilibrium of the associated "forced" balance $P y = Q$ at large $x$, which is reasonable.

P: Solve the initial value problem $\frac{dy}{dx} = xy^2$, $y(0) = 1$.

S:
**IDENTIFY**: First-order ODE with right-hand side factoring as $g(x)h(y) = x \cdot y^2$, so it is separable. Initial condition $y(0) = 1$ requests a particular solution. Note $h(y) = y^2 = 0$ when $y = 0$, so $y \equiv 0$ is an equilibrium (but does not satisfy the IC).

**PLAN**:
- Separate variables: $\frac{dy}{y^2} = x\,dx$.
- Integrate both sides and combine constants.
- Solve for $y$ explicitly, then apply $y(0) = 1$ to find $C$.

**EXECUTE**:
1. Divide by $y^2$ (valid since $y(0) = 1 \ne 0$): $y^{-2}\,dy = x\,dx$.
2. Integrate: $-y^{-1} = \tfrac{1}{2}x^2 + C$, i.e., $-\tfrac{1}{y} = \tfrac{x^2}{2} + C$.
3. Solve for $y$: $y = \dfrac{-1}{\tfrac{x^2}{2} + C} = \dfrac{-2}{x^2 + 2C}$. Let $K = -2C$: $y = \dfrac{2}{K - x^2}$.
4. Apply $y(0) = 1$: $1 = \dfrac{2}{K}$, so $K = 2$.
5. Particular solution: $y(x) = \dfrac{2}{2 - x^2}$.

**EVALUATE**:
- Check the IC: $y(0) = \tfrac{2}{2} = 1$. ✓
- Check the ODE: $y' = \dfrac{2 \cdot 2x}{(2 - x^2)^2} = \dfrac{4x}{(2-x^2)^2}$, and $xy^2 = x \cdot \dfrac{4}{(2-x^2)^2} = \dfrac{4x}{(2-x^2)^2}$. ✓
- The solution blows up as $x \to \sqrt{2}$, so the solution exists only on $(-\sqrt{2}, \sqrt{2})$ — a reminder that nonlinear ODEs may have finite intervals of existence even when the ODE itself looks harmless.
