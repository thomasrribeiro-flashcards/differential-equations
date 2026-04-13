+++
order = 5
tags = ["math", "differential-equations", "ode", "existence-uniqueness", "picard", "lipschitz"]
+++

# Differential Equations — Existence and Uniqueness

## 5.1 Why Existence and Uniqueness Matter

Q: Why should you check existence and uniqueness before attempting to solve an IVP?
A: If no solution exists, any method you apply is chasing a non-thing and will produce garbage or a contradiction. If multiple solutions exist, a single method may find only one of them and mislead you about the behavior of the system. Knowing existence and uniqueness holds tells you the IVP is well-posed, so the solution you compute is THE solution.

Q: What does it mean for an initial value problem to be "well-posed"?
A: A solution exists, the solution is unique, and (ideally) it depends continuously on the initial data. Well-posed problems are the ones for which standard solution techniques give trustworthy answers.

C: An initial value problem is [well-posed] when a solution exists, is unique, and depends continuously on the initial data.

C: Without a [uniqueness] guarantee, a solution technique may find one solution while missing others.

## 5.2 The Picard-Lindelöf Theorem

Q: What IVP does the Picard-Lindelöf theorem address?
A: The first-order IVP $y' = f(x,y)$ with initial condition $y(x_0) = y_0$, where $f(x,y)$ is a given function of the independent variable $x$ and the unknown $y$, and $(x_0, y_0)$ is a specified point in the $xy$-plane.

C: Picard-Lindelöf concerns the IVP [$y' = f(x,y)$, $y(x_0) = y_0$], where $f$ is a given function and $(x_0, y_0)$ is a specified point.

Q: What hypotheses does Picard-Lindelöf require on $f(x,y)$?
A: Both $f$ and its partial derivative $\partial f/\partial y$ must be continuous on some closed rectangle $R$ containing the point $(x_0, y_0)$ in its interior. Here $x$ is the independent variable and $y$ is the unknown function's value.

C: Picard-Lindelöf requires $f$ and [$\partial f/\partial y$] to be continuous on a rectangle around $(x_0, y_0)$.

Q: What does Picard-Lindelöf conclude when its hypotheses hold?
A: There exists some open interval containing $x_0$ on which a unique solution $y(x)$ to the IVP $y' = f(x,y)$, $y(x_0) = y_0$ is defined. The theorem guarantees existence and uniqueness simultaneously on that interval.

C: If the Picard-Lindelöf hypotheses hold, a [unique] solution exists on some interval containing $x_0$.

Q: Why does Picard-Lindelöf require continuity of $\partial f/\partial y$ and not just continuity of $f$?
A: Continuity of $f$ alone guarantees existence (Peano's theorem) but not uniqueness. The extra smoothness from $\partial f/\partial y$ continuous lets you bound how fast $f$ can change as $y$ varies, which is exactly what is needed to rule out two solutions splitting apart from the same initial point.

## 5.3 Local Nature of the Theorem

Q: Why is Picard-Lindelöf called a "local" existence theorem?
A: It only guarantees a solution on some (possibly small) interval around $x_0$, not on the entire real line or even the full $x$-range of the rectangle. The size of that interval depends on $f$ and the rectangle, and the theorem does not tell you what it is.

C: Picard-Lindelöf is a [local] existence theorem — it guarantees a solution only on some neighborhood of $x_0$.

Q: Why can't Picard-Lindelöf give a global existence result for general $f(x,y)$?
A: Even with $f$ and $\partial f/\partial y$ smooth everywhere, the solution itself can blow up (go to infinity) at a finite $x$. Once the solution leaves every rectangle, there is nothing left for the theorem to control.

C: A solution to $y' = f(x,y)$ may [blow up] at a finite $x$ even when $f$ is smooth everywhere.

## 5.4 Non-Uniqueness Example

Q: What IVP is the standard example of non-uniqueness?
A: The IVP $y' = y^{1/3}$, $y(0) = 0$. Here $f(x,y) = y^{1/3}$, which is continuous everywhere, but its partial derivative with respect to $y$ fails to be bounded near $y = 0$.

Q: Why does $y' = y^{1/3}$, $y(0) = 0$ fail the Picard-Lindelöf hypotheses?
A: The partial derivative $\partial f/\partial y = \tfrac{1}{3} y^{-2/3}$ becomes unbounded as $y \to 0$, so it is not continuous on any rectangle containing $(0,0)$ in its interior. The theorem's hypothesis is violated exactly at the initial point.

C: For $f(x,y) = y^{1/3}$, the derivative $\partial f/\partial y = $ [$\tfrac{1}{3} y^{-2/3}$] is unbounded near $y = 0$.

Q: What are two distinct solutions of the IVP $y' = y^{1/3}$, $y(0) = 0$?
A: The zero solution $y(x) = 0$ and the nontrivial solution $y(x) = (2x/3)^{3/2}$ (for $x \ge 0$). Both satisfy the ODE and pass through $(0,0)$, demonstrating that the IVP has more than one solution.

C: The IVP $y' = y^{1/3}$, $y(0) = 0$ has solutions $y = 0$ and $y = $ [$(2x/3)^{3/2}$].

Q: What does the non-uniqueness example $y' = y^{1/3}$, $y(0) = 0$ teach conceptually?
A: Continuity of $f$ alone is not enough for uniqueness; you need control on how $f$ changes with $y$. At points where $f$ is continuous but $\partial f/\partial y$ blows up, multiple solutions can emerge from the same initial point.

## 5.5 Blow-Up in Finite Time

Q: What is the standard example of a solution that blows up at a finite $x$?
A: The IVP $y' = y^2$, $y(0) = 1$ has the unique solution $y(x) = 1/(1 - x)$, which is smooth on $(-\infty, 1)$ but tends to $+\infty$ as $x \to 1^-$. So even though $f(x,y) = y^2$ is as smooth as possible, the solution exists only on a bounded interval to the right of $x_0 = 0$.

C: The IVP $y' = y^2$, $y(0) = 1$ has solution $y = $ [$1/(1-x)$], which blows up at $x = 1$.

Q: Why does $y' = y^2$, $y(0) = 1$ still satisfy Picard-Lindelöf's hypotheses despite blowing up?
A: Picard-Lindelöf only claims a solution exists on SOME interval around $x_0 = 0$, not all of $\mathbb{R}$. The solution $1/(1-x)$ exists on $(-\infty, 1)$, consistent with the local conclusion. Blow-up at $x = 1$ does not contradict the theorem; it illustrates why the theorem is local.

C: Blow-up in finite time shows why Picard-Lindelöf can only be a [local] theorem.

## 5.6 Lipschitz Condition

Q: What is a Lipschitz condition in $y$ for $f(x,y)$?
A: $f$ satisfies a Lipschitz condition in $y$ on a region if there exists a constant $L > 0$ such that $|f(x, y_1) - f(x, y_2)| \le L |y_1 - y_2|$ for all $(x, y_1)$ and $(x, y_2)$ in the region. Here $L$ is the Lipschitz constant, $y_1, y_2$ are any two values of the dependent variable, and $x$ is fixed.

C: $f$ is [Lipschitz] in $y$ on a region if $|f(x,y_1) - f(x,y_2)| \le L|y_1 - y_2|$ for some constant $L > 0$.

Q: How is Lipschitz continuity related to the hypothesis "$\partial f/\partial y$ continuous"?
A: If $\partial f/\partial y$ is continuous on a closed rectangle, it is bounded there, and the mean value theorem gives $|f(x,y_1) - f(x,y_2)| \le L|y_1 - y_2|$ with $L = \max |\partial f/\partial y|$. So "continuous $\partial f/\partial y$" on a rectangle implies Lipschitz in $y$, but not conversely.

Q: Why is the Lipschitz version of Picard-Lindelöf useful?
A: Lipschitz continuity is weaker than having a continuous $\partial f/\partial y$, so the Lipschitz form applies to more functions (e.g. $|y|$, which has no derivative at $0$ but is Lipschitz). It gives the same existence-and-uniqueness conclusion under a more flexible hypothesis.

## 5.7 Linear First-Order: Global Existence

Q: State the existence-uniqueness theorem for the linear first-order IVP.
A: For the IVP $y' + P(x) y = Q(x)$, $y(x_0) = y_0$, if $P(x)$ and $Q(x)$ are continuous on an open interval $I$ containing $x_0$, then a unique solution $y(x)$ exists on ALL of $I$. Here $P, Q$ are the given coefficient and forcing functions.

C: For a linear first-order IVP with $P, Q$ continuous on interval $I$ containing $x_0$, a unique solution exists on [all of $I$] (global).

Q: How does the linear existence-uniqueness theorem differ from Picard-Lindelöf?
A: Picard-Lindelöf is local: it guarantees a solution only on some unspecified neighborhood. The linear theorem is global: the solution exists on the entire interval where $P$ and $Q$ are continuous, with no blow-up possible inside $I$.

C: The linear first-order existence theorem is [global], while Picard-Lindelöf is local.

## 5.8 Why Linear Equations Give Global Solutions

Q: Why can linear first-order ODEs achieve global existence while nonlinear ones cannot?
A: The integrating-factor formula $y(x) = \tfrac{1}{\mu(x)}\left(\int \mu(x) Q(x)\,dx + C\right)$, with $\mu(x) = \exp(\int P(x)\,dx)$, produces an explicit solution defined wherever $P$ and $Q$ are continuous. There is no nonlinearity in $y$ to cause finite-time blow-up — the solution grows at most as fast as the integrating factor allows.

C: Linear first-order ODEs avoid finite-time blow-up because there is no [nonlinearity in $y$] to drive the solution to infinity.

Q: What is the role of the integrating factor in proving global existence for linear first-order ODEs?
A: The integrating factor $\mu(x) = e^{\int P(x)\,dx}$ reduces the ODE to $(\mu y)' = \mu Q$, which integrates directly. Whenever $P$ is continuous, $\mu$ is defined and nonzero on $I$; whenever $Q$ is continuous, the integral exists on $I$. So the formula produces a solution on all of $I$.

## 5.9 Picard Iteration

Q: What is Picard iteration?
A: An iterative method for constructing the solution of $y' = f(x,y)$, $y(x_0) = y_0$: define $y_0(x) = y_0$ and recursively $y_{n+1}(x) = y_0 + \int_{x_0}^x f(t, y_n(t))\,dt$. Under Picard-Lindelöf's hypotheses, the sequence $y_n(x)$ converges uniformly on a small interval to the unique solution.

C: Picard iteration is defined by $y_{n+1}(x) = $ [$y_0 + \int_{x_0}^x f(t, y_n(t))\,dt$].

Q: Why is Picard iteration valuable beyond just proving existence?
A: It is a constructive proof — it does not just assert a solution exists; it builds one as a limit of computable approximations. In principle you can carry out a finite number of iterations to get an approximate solution with controlled error, and the same estimates feed into the uniqueness argument.

C: Picard iteration gives a [constructive] proof of existence — it builds the solution as a limit of explicit approximations.

## 5.10 What the Theorem Does NOT Tell You

Q: What does Picard-Lindelöf NOT tell you about the solution?
A: It does not give a formula for $y(x)$, does not tell you the length of the interval of existence (only that some interval exists), does not describe behavior outside the rectangle, and says nothing about solutions to IVPs that violate its hypotheses (they may or may not exist or be unique).

C: Picard-Lindelöf does NOT tell you the [formula] for the solution, only that one exists.

C: Picard-Lindelöf does NOT tell you the [interval of existence] — only that some neighborhood of $x_0$ works.

Q: If an IVP violates Picard-Lindelöf's hypotheses, what can you conclude?
A: Nothing automatic. The theorem is a sufficient condition, not a necessary one. A solution may still exist and be unique, or existence may hold while uniqueness fails (as with $y' = y^{1/3}$), or existence itself may fail. You must analyze the specific equation.

## 5.11 Application: Checking Well-Posedness

Q: Given an IVP, what is the first diagnostic question to ask before solving?
A: Are the hypotheses of an existence-uniqueness theorem satisfied at the initial point? For a general $y' = f(x,y)$, check that $f$ and $\partial f/\partial y$ are continuous near $(x_0, y_0)$. For a linear equation, check that $P$ and $Q$ are continuous on an interval containing $x_0$.

Q: Why does checking $\partial f/\partial y$ near $(x_0, y_0)$ catch the non-uniqueness trap?
A: Non-uniqueness in first-order ODEs typically arises when $\partial f/\partial y$ blows up at the initial point, as in $y' = y^{1/3}$ at $y = 0$. A quick sanity check on $\partial f/\partial y$ at $(x_0, y_0)$ flags exactly those pathological initial conditions.

P: For the IVP $y' = \sqrt{y}$, $y(0) = 4$, determine a region where a unique solution is guaranteed, and explain why uniqueness might fail if instead $y(0) = 0$.

S:
**IDENTIFY**: Application of Picard-Lindelöf to $y' = f(x,y)$ with $f(x,y) = \sqrt{y} = y^{1/2}$. We must check continuity of $f$ and $\partial f/\partial y$ on a rectangle around the initial point, and interpret what happens when the initial point sits on the boundary $y = 0$.

**PLAN**:
- Compute $f$ and $\partial f / \partial y$ explicitly.
- Identify the set where both are continuous.
- For $y(0) = 4$, build a rectangle staying strictly above $y = 0$ and conclude local existence-uniqueness.
- For $y(0) = 0$, check whether the initial point lies in the region of continuity; if not, the theorem does not apply and non-uniqueness becomes possible.

**EXECUTE**:
1. $f(x,y) = y^{1/2}$ is defined and continuous for $y \ge 0$.
2. $\partial f/\partial y = \tfrac{1}{2} y^{-1/2}$ is continuous for $y > 0$ but unbounded as $y \to 0^+$.
3. Case $y(0) = 4$: the point $(0, 4)$ lies in the open region $y > 0$. Choose any rectangle $R = \{|x| \le a, |y - 4| \le b\}$ with $b < 4$ so that $R$ stays in $y > 0$. On $R$, both $f$ and $\partial f/\partial y$ are continuous, so Picard-Lindelöf guarantees a unique solution on some interval around $x_0 = 0$.
4. Case $y(0) = 0$: the point $(0, 0)$ is on the boundary $y = 0$. Every rectangle around $(0,0)$ intersects $y < 0$ (where $f$ is undefined) and contains points where $\partial f/\partial y$ is unbounded. Picard-Lindelöf's hypotheses fail, so uniqueness is not guaranteed.
5. Indeed, $y(0) = 0$ admits both $y(x) = 0$ and $y(x) = x^2/4$ (for $x \ge 0$), confirming non-uniqueness (this mirrors the $y' = y^{1/3}$ example).

**EVALUATE**:
- For $y(0) = 4$, the conclusion is local: Picard-Lindelöf does not tell us how far the interval extends, just that one exists.
- For $y(0) = 0$, the failure mode is exactly the one seen in 5.4: $\partial f/\partial y$ unbounded at the initial point allows solutions to "split." So the well-posedness diagnostic correctly flags $y(0) = 0$ as a dangerous initial condition while approving $y(0) = 4$.

## 5.12 Summary Comparisons

Q: Contrast Picard-Lindelöf with the linear first-order existence-uniqueness theorem in one line.
A: Picard-Lindelöf gives LOCAL existence-uniqueness for general $y' = f(x,y)$ under continuity of $f$ and $\partial f/\partial y$; the linear theorem gives GLOBAL existence-uniqueness for $y' + P(x)y = Q(x)$ on any interval where $P, Q$ are continuous.

C: General nonlinear ODEs: [local] existence-uniqueness. Linear first-order ODEs: [global] existence-uniqueness on intervals of coefficient continuity.

Q: What are the three classic "warning signs" that an IVP might be non-unique or have a short interval of existence?
A: (1) $\partial f/\partial y$ unbounded at $(x_0, y_0)$ — risk of non-uniqueness; (2) $f$ growing faster than linearly in $y$ (like $y^2$) — risk of finite-time blow-up; (3) $P$ or $Q$ in a linear equation having a discontinuity near $x_0$ — limits the interval on which the global theorem applies.
