+++
name = "Differential Equations"
subject = "Math"
order = 1
tags = ["math", "differential-equations", "ode", "introduction", "ivp", "slope-field"]
+++

# Differential Equations — Introduction

## 1.1 What is a Differential Equation?

Q: Why do differential equations arise so often in science and engineering?
A: Most natural laws describe rates of change rather than quantities directly. Newton's second law relates acceleration (a rate) to force; population growth depends on current population; heat flow depends on temperature gradients. Whenever a law constrains how a quantity changes rather than its value, the resulting equation involves derivatives and is therefore a differential equation.

Q: Why is solving a differential equation fundamentally different from solving an algebraic equation?
A: An algebraic equation like $x^2 = 4$ asks for unknown numbers. A differential equation asks for an unknown function $y(x)$ whose derivatives satisfy a given relationship. The unknown lives in an infinite-dimensional space of functions, so solutions typically come in families parameterized by arbitrary constants rather than a finite list of numbers.

C: A [differential equation] is an equation relating an unknown function to one or more of its derivatives.

C: In the ODE $y' = f(x, y)$, the symbol $y$ denotes the [unknown function] of the independent variable $x$.

Q: What does it mean to "solve" a differential equation?
A: It means to find every function $y(x)$ that, when substituted together with its derivatives into the equation, reduces it to an identity on some interval of the independent variable.

## 1.2 Order of a Differential Equation

C: The [order] of a differential equation is the order of the highest derivative that appears in it.

Q: What is the order of $y'' + 3y' + 2y = \sin x$, where $y = y(x)$ is the unknown function?
A: The order is 2, because the highest derivative appearing is $y'' = \frac{d^2 y}{dx^2}$.

Q: What is the order of $\left(y'\right)^3 + y = x$, where $y = y(x)$?
A: The order is 1. Order counts the highest derivative that appears, not the power to which a derivative is raised; only $y'$ appears, so the order is 1.

## 1.3 Ordinary vs Partial

Q: Why distinguish ordinary differential equations from partial differential equations?
A: The distinction reflects how many independent variables the unknown function depends on. An ODE describes a function of one variable (like $y(x)$ or $y(t)$), while a PDE describes a function of several variables (like $u(x, t)$ or $u(x, y, z, t)$). Techniques and solution behaviors differ dramatically between the two.

C: An [ordinary differential equation (ODE)] involves derivatives of an unknown function of a single independent variable.

C: A [partial differential equation (PDE)] involves partial derivatives of an unknown function of two or more independent variables.

Q: Is the heat equation $\frac{\partial u}{\partial t} = k \frac{\partial^2 u}{\partial x^2}$ an ODE or a PDE, where $u = u(x, t)$?
A: It is a PDE. The unknown $u(x, t)$ depends on two independent variables ($x$ and $t$), and the equation uses partial derivatives with respect to each.

## 1.4 Linear vs Nonlinear

Q: Why is linearity such an important property for a differential equation?
A: Linear equations obey the superposition principle: sums and scalar multiples of solutions are again solutions. This structure makes linear ODEs dramatically more tractable than nonlinear ones and is the reason entire chapters are devoted to linear theory.

C: A linear ODE of order $n$ has the form $a_n(x) y^{(n)} + \cdots + a_1(x) y' + a_0(x) y = g(x)$, where the [coefficients $a_i(x)$ and forcing term $g(x)$] depend only on the independent variable $x$, not on $y$.

C: In a [linear] ODE, the unknown function $y$ and each of its derivatives appear only to the first power and never multiplied by one another.

Q: Why is $y y' = x$ nonlinear, where $y = y(x)$?
A: Because the term $y y'$ is a product of the unknown function $y$ with its derivative $y'$. Linearity requires that $y$ and its derivatives appear only to the first power and never multiplied together, so this product violates linearity.

Q: Why is $y' + \sin(y) = 0$ nonlinear, where $y = y(x)$?
A: Because $\sin(y)$ is a nonlinear function of the unknown $y$. In a linear ODE, $y$ may appear only to the first power multiplied by a coefficient depending on $x$; $\sin(y)$ expands to a power series in $y$ with terms $y, y^3, y^5, \ldots$, violating this requirement.

Q: Is $y' + x^2 y = e^x$ linear, where $y = y(x)$?
A: Yes. The unknown $y$ and its derivative $y'$ each appear to the first power, they are not multiplied together, and the coefficient $x^2$ of $y$ and the forcing term $e^x$ depend only on the independent variable $x$.

## 1.5 Homogeneous vs Nonhomogeneous

C: A linear ODE $a_n(x) y^{(n)} + \cdots + a_0(x) y = g(x)$ is called [homogeneous] when the forcing term $g(x)$ is identically zero.

C: A linear ODE $a_n(x) y^{(n)} + \cdots + a_0(x) y = g(x)$ is called [nonhomogeneous] when $g(x)$ is not identically zero.

Q: Why does the homogeneous/nonhomogeneous distinction only apply to linear ODEs?
A: The distinction hinges on separating terms involving the unknown $y$ from a "forcing" term that does not. In a nonlinear ODE, products like $y y'$ or $\sin(y)$ cannot be cleanly split into a left-hand "operator on $y$" and a right-hand "source," so the classification loses its meaning.

Q: Is $y'' - 4y = 0$ homogeneous or nonhomogeneous, where $y = y(x)$?
A: Homogeneous. The right-hand side is zero, meaning the forcing term $g(x) \equiv 0$.

## 1.6 Solutions

C: A [solution] of an ODE on an interval $I$ is a function $y(x)$ which, together with its derivatives, satisfies the equation for every $x \in I$.

Q: Why must a solution be specified together with an interval?
A: A function can satisfy an ODE on one interval and fail on another (for example, by becoming undefined or losing differentiability). Naming the interval makes the claim of "being a solution" unambiguous, and many existence theorems guarantee solutions only locally.

## 1.7 General vs Particular Solutions

C: A [general solution] of an $n$-th order ODE is a family of solutions containing $n$ arbitrary constants, from which (under mild conditions) every solution can be obtained by choosing the constants.

C: A [particular solution] is obtained from the general solution by assigning specific numerical values to the arbitrary constants.

Q: Why does the general solution of an $n$-th order ODE contain $n$ arbitrary constants?
A: Integrating a derivative introduces a constant of integration. An $n$-th order equation requires effectively $n$ integrations to recover $y$ from its $n$-th derivative, producing $n$ independent constants. Each constant is fixed by one additional condition, matching the $n$ conditions typically needed to single out a particular solution.

## 1.8 Explicit vs Implicit Solutions

C: An [explicit solution] of an ODE is a solution given in the form $y = \phi(x)$, with the dependent variable isolated.

C: An [implicit solution] of an ODE is a relation $F(x, y) = 0$ that defines $y$ as a function of $x$ (at least locally) satisfying the ODE, without solving for $y$ explicitly.

Q: Why do implicit solutions arise naturally in practice?
A: Many integration techniques (especially separation of variables) yield a relation between $x$ and $y$ that cannot be algebraically solved for $y$, such as $y + \ln y = x + C$. Rather than force an explicit form, we accept the implicit relation because it still uniquely determines $y$ on a suitable interval.

## 1.9 Initial Value Problems

C: An [initial value problem (IVP)] consists of an ODE together with one or more conditions specifying $y$ (and possibly its derivatives) at a single point $x = x_0$.

Q: Why does an initial condition convert a family of solutions into a single solution?
A: The general solution of an $n$-th order ODE contains $n$ arbitrary constants. Specifying values of $y$ and its first $n-1$ derivatives at a single point $x_0$ produces $n$ equations in those $n$ constants, which (under standard hypotheses) has a unique solution.

Q: For a first-order ODE $y' = f(x, y)$, what form does a typical initial condition take?
A: A single condition $y(x_0) = y_0$, prescribing the value $y_0$ the solution must take at the point $x_0$. This pins down the one arbitrary constant in the general solution.

## 1.10 Boundary Value Problems

C: A [boundary value problem (BVP)] for an ODE specifies conditions on $y$ (or its derivatives) at two or more distinct points.

Q: How does a boundary value problem differ in character from an initial value problem?
A: An IVP specifies all conditions at a single point $x_0$, and standard theorems guarantee existence and uniqueness under mild hypotheses. A BVP specifies conditions at separated points, and existence/uniqueness is far more delicate — solutions may fail to exist, or may exist in infinite families, depending on the coefficients and boundary data.

Q: Give an example of a boundary value problem for a second-order ODE.
A: $y'' + y = 0$ with $y(0) = 0$ and $y(\pi/2) = 1$. Conditions are imposed at the two distinct points $x = 0$ and $x = \pi/2$ rather than at a single point.

## 1.11 Direction Fields (Slope Fields)

Q: Why is a direction field useful for a first-order ODE $y' = f(x, y)$?
A: The ODE assigns a slope $f(x, y)$ to every point $(x, y)$ in the plane. Plotting short line segments with those slopes produces a picture of how solutions flow, letting us visualize qualitative behavior (monotonicity, equilibria, asymptotes) without finding a formula for $y(x)$.

C: A [direction field] (or slope field) for $y' = f(x, y)$ is a plot in the $xy$-plane showing short segments of slope $f(x, y)$ at a grid of points.

Q: How do you read a solution curve from a slope field?
A: Starting at any point $(x_0, y_0)$, you follow the drawn segments, always moving in the direction they point. The resulting curve is tangent to the field everywhere and represents the solution of the IVP $y' = f(x, y)$, $y(x_0) = y_0$.

## 1.12 Qualitative Analysis

C: An [equilibrium solution] (or constant solution) of $y' = f(x, y)$ is a constant function $y(x) = c$ for which $f(x, c) = 0$ for all relevant $x$; its derivative vanishes, so it satisfies the ODE trivially.

Q: For the autonomous ODE $y' = y(1 - y)$, what are the equilibrium solutions, where $y = y(x)$?
A: The constants $y = 0$ and $y = 1$. These are the values of $y$ that make the right-hand side zero, so $y'$ vanishes and $y$ remains constant.

Q: Why can qualitative information about solutions often be extracted directly from a slope field without solving the ODE?
A: The slope field encodes the rule $y' = f(x, y)$ geometrically. Regions where $f > 0$ show solutions increasing, regions where $f < 0$ show them decreasing, and zeros of $f$ mark equilibria. By inspecting sign changes and flow direction, we can determine monotonicity, locate equilibria, and predict long-term behavior (asymptotes, blow-up) without any closed-form solution.

## 1.13 Verifying a Proposed Solution

Q: Why is "differentiate and substitute" the canonical method for verifying a proposed solution?
A: A function $y(x)$ is a solution precisely when it and its derivatives reduce the ODE to a true identity on the relevant interval. Computing the needed derivatives of the candidate and plugging them into both sides of the ODE directly tests this definition — no cleverness required.

P: Verify that $y = e^{-x}$ is a solution of $y' + y = 0$, where $y = y(x)$.

S:
**IDENTIFY**: Verification of a proposed explicit solution to a first-order linear homogeneous ODE.

**PLAN**:
- Compute the derivative $y'$ of the candidate $y = e^{-x}$.
- Substitute $y$ and $y'$ into the left-hand side of $y' + y = 0$.
- Check that the result simplifies to the right-hand side (here, $0$) for all $x$.

**EXECUTE**:
1. Differentiate: $y' = \frac{d}{dx}\left(e^{-x}\right) = -e^{-x}$.
2. Substitute into the left-hand side: $y' + y = -e^{-x} + e^{-x}$.
3. Simplify: $-e^{-x} + e^{-x} = 0$, which equals the right-hand side.

**EVALUATE**: The equation reduces to $0 = 0$ for every $x \in \mathbb{R}$, so $y = e^{-x}$ is a solution on all of $\mathbb{R}$. No arbitrary constant was involved, so this is a particular solution, not the general one.

## 1.14 Worked IVP: General Solution and Initial Condition

P: Verify that $y = C e^{2x}$ solves the ODE $y' - 2y = 0$ for every constant $C$, and then find the particular solution satisfying the initial condition $y(0) = 3$. Here $y = y(x)$ and $C \in \mathbb{R}$ is an arbitrary constant.

S:
**IDENTIFY**: A two-part task: (i) verify a one-parameter family is the general solution of a first-order linear homogeneous ODE, and (ii) solve the IVP by selecting the constant $C$ that matches the initial condition $y(0) = 3$.

**PLAN**:
- To verify: differentiate $y = C e^{2x}$ with respect to $x$, substitute $y$ and $y'$ into $y' - 2y$, and check the result is $0$ for all $x$ and all $C$.
- To solve the IVP: substitute $x = 0$ into the general solution, set the result equal to $3$, and solve for $C$. Then write the particular solution with $C$ replaced.

**EXECUTE**:
1. Differentiate: $y' = \frac{d}{dx}\left(C e^{2x}\right) = 2 C e^{2x}$ (the constant $C$ passes through the derivative, and $\frac{d}{dx} e^{2x} = 2 e^{2x}$ by the chain rule).
2. Substitute into the ODE: $y' - 2y = 2 C e^{2x} - 2 \left( C e^{2x} \right) = 2 C e^{2x} - 2 C e^{2x} = 0$.
3. Since the equation holds for every $x$ and every $C$, the family $y = C e^{2x}$ is a valid one-parameter family of solutions; it is the general solution (the ODE is first order, and the family has one arbitrary constant).
4. Apply the initial condition $y(0) = 3$: substitute $x = 0$ into $y = C e^{2x}$ to get $y(0) = C e^{0} = C$.
5. Set $C = 3$ to match $y(0) = 3$.
6. Write the particular solution: $y = 3 e^{2x}$.

**EVALUATE**: Check the particular solution against both requirements. First, $y' - 2y = 6 e^{2x} - 6 e^{2x} = 0$, so the ODE holds. Second, $y(0) = 3 e^{0} = 3$, matching the initial condition. Qualitatively, $y = 3 e^{2x}$ is positive and grows exponentially, consistent with the ODE $y' = 2y$, which says the rate of change is proportional to $y$ with positive constant $2$.
