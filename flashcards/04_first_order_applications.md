+++
order = 4
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "applications", "mixing", "cooling", "population", "rc-circuit"]
+++

# Differential Equations — Applications of First-Order ODEs

## 4.1 Modeling with ODEs

Q: Why do so many real-world phenomena lead naturally to first-order ODEs?
A: Many physical, biological, and engineering processes are described by statements about *rates of change* rather than about absolute values. Since a derivative $dy/dt$ is literally an instantaneous rate of change, translating a rate statement into math produces an ODE. First-order ODEs appear whenever the rate depends only on the current state (and possibly time), which is the simplest and most common modeling assumption.

Q: How do you translate the English phrase "the rate of change of $y$ is proportional to $y$" into a differential equation?
A: "Rate of change of $y$" is $dy/dt$, and "proportional to $y$" means "equal to a constant times $y$". Combining them gives $dy/dt = ky$, where $k$ is the proportionality constant. The sign of $k$ determines whether $y$ grows ($k>0$) or decays ($k<0$).

C: The phrase "the rate of change of $y$ is proportional to $y$" becomes the ODE [$dy/dt = ky$], where $k$ is the proportionality constant.

Q: What are the three basic ingredients of any ODE model?
A: (1) A dependent variable representing the quantity of interest (e.g., population, temperature, charge). (2) An independent variable, usually time $t$. (3) A rate law describing how the dependent variable changes, expressed in terms of the current state and, possibly, external inputs.

## 4.2 Exponential Growth and Decay

C: The exponential growth/decay ODE $dy/dt = ky$ has the general solution [$y(t) = y_0 e^{kt}$], where $y_0 = y(0)$ is the initial value and $k$ is the growth ($k>0$) or decay ($k<0$) rate.

Q: Why does $dy/dt = ky$ produce exponential behavior rather than, say, polynomial growth?
A: The equation says the rate of change at every instant is proportional to the current amount. So whenever $y$ doubles, its growth rate also doubles, which is the defining property of exponential functions. Separating variables gives $\int dy/y = \int k\,dt$, yielding $\ln|y| = kt + C$, i.e. $y = y_0 e^{kt}$.

Q: In the model $dy/dt = ky$, what does the sign of $k$ tell you physically?
A: If $k>0$, $y$ grows without bound (unrestricted population, compound interest, chain reactions). If $k<0$, $y$ decays toward zero (radioactive decay, cooling toward zero, discharging capacitor into a short). If $k=0$, $y$ is constant.

## 4.3 Half-Life and Doubling Time

C: The half-life $t_{1/2}$ of a decaying quantity is the time required for it to fall to half its current value, and for $dy/dt = ky$ with $k<0$ it satisfies [$t_{1/2} = \ln 2 / |k|$].

C: The doubling time $t_d$ of an exponentially growing quantity satisfies [$t_d = \ln 2 / k$], where $k>0$ is the growth rate in $dy/dt = ky$.

Q: Why is the half-life of an exponentially decaying quantity independent of the starting amount?
A: Because the decay is multiplicative: after one half-life, any amount shrinks by the same factor $1/2$. Algebraically, $y(t_{1/2})/y(0) = e^{kt_{1/2}} = 1/2$ gives $t_{1/2} = \ln 2 / |k|$, which does not involve $y_0$.

P: A radioactive sample decays from $100$ g to $75$ g in $5$ years. Find the decay constant $k$ and the half-life.

S:
**IDENTIFY**: Exponential decay model $dy/dt = ky$ with $k<0$; given two data points.

**PLAN**:
- Use $y(t) = y_0 e^{kt}$ with $y_0 = 100$, $y(5) = 75$.
- Solve for $k$, then use $t_{1/2} = \ln 2 / |k|$.

**EXECUTE**:
1. $75 = 100 \, e^{5k}$, so $e^{5k} = 0.75$.
2. $k = \ln(0.75)/5 \approx -0.0575$ per year.
3. $t_{1/2} = \ln 2 / 0.0575 \approx 12.05$ years.

**EVALUATE**: $k<0$ as expected for decay. A half-life of ~12 years is reasonable: after 5 years only 25% has been lost, so we expect the half-life to exceed 5 years.

## 4.4 Newton's Law of Cooling

C: Newton's Law of Cooling states that the rate of change of an object's temperature $T$ is proportional to the difference between $T$ and the ambient temperature $T_\text{env}$: [$dT/dt = -k(T - T_\text{env})$], with $k>0$.

Q: Why is Newton's Law of Cooling written with a minus sign in $dT/dt = -k(T - T_\text{env})$?
A: The sign ensures the object always approaches the ambient temperature. If $T > T_\text{env}$, then $T - T_\text{env} > 0$ and $dT/dt < 0$ (the object cools). If $T < T_\text{env}$, the sign of $T - T_\text{env}$ flips and $dT/dt > 0$ (the object warms). The constant $k>0$ controls how fast this approach happens.

Q: How do you derive the solution to Newton's Law of Cooling $dT/dt = -k(T - T_\text{env})$?
A: Let $u = T - T_\text{env}$; since $T_\text{env}$ is constant, $du/dt = dT/dt = -ku$. This is exponential decay with solution $u(t) = u_0 e^{-kt}$. Substituting back, $T(t) = T_\text{env} + (T_0 - T_\text{env}) e^{-kt}$, where $T_0 = T(0)$.

C: The solution to Newton's Law of Cooling is [$T(t) = T_\text{env} + (T_0 - T_\text{env}) e^{-kt}$], where $T_0$ is the initial temperature, $T_\text{env}$ is the ambient temperature, and $k>0$ is the cooling rate.

Q: What is the long-time behavior ($t \to \infty$) of an object obeying Newton's Law of Cooling, and why?
A: $T(t) \to T_\text{env}$. The exponential term $e^{-kt}$ decays to zero, leaving only the ambient temperature. Physically, the object eventually reaches thermal equilibrium with its surroundings.

P: A cup of coffee at $90^\circ\text{C}$ is placed in a $20^\circ\text{C}$ room. After $10$ minutes it has cooled to $60^\circ\text{C}$. When will the coffee reach $30^\circ\text{C}$?

S:
**IDENTIFY**: Newton's Law of Cooling with $T_\text{env} = 20$, $T_0 = 90$, $T(10) = 60$; find $t$ such that $T(t) = 30$.

**PLAN**:
- Use $T(t) = T_\text{env} + (T_0 - T_\text{env}) e^{-kt} = 20 + 70 e^{-kt}$.
- Use the $t=10$ data to find $k$, then solve for the target time.

**EXECUTE**:
1. $60 = 20 + 70 e^{-10k} \;\Rightarrow\; e^{-10k} = 40/70 = 4/7$.
2. $k = -\tfrac{1}{10} \ln(4/7) = \tfrac{1}{10}\ln(7/4) \approx 0.0560$ per minute.
3. Set $30 = 20 + 70 e^{-kt}$: $e^{-kt} = 10/70 = 1/7$, so $t = \ln 7 / k \approx 1.9459/0.0560 \approx 34.8$ min.

**EVALUATE**: Since the temperature gap shrinks exponentially, each equal *multiplicative* step takes the same time. The gap went from 70 to 40 in 10 min (factor 4/7); reaching 30$^\circ$C requires the gap to drop to 10, a factor of $1/7$. Because $(4/7)^n = 1/7$ gives $n \approx 3.48$, we expect $\approx 34.8$ min. Consistent.

## 4.5 Mixing Problems

Q: What is the fundamental balance law behind every mixing problem?
A: The rate of change of the amount of solute in the tank equals the rate at which solute enters minus the rate at which it leaves: $dQ/dt = (\text{rate in}) - (\text{rate out})$. Each rate is "concentration $\times$ flow rate" for that stream.

C: For a well-mixed tank, $dQ/dt = $ [$c_\text{in} r_\text{in} - (Q/V)\, r_\text{out}$], where $Q$ is the amount of solute, $V$ is the current volume, $c_\text{in}$ is the inflow concentration, and $r_\text{in}, r_\text{out}$ are the inflow/outflow rates.

Q: Why is the outflow concentration in a well-mixed tank equal to $Q/V$ rather than some other value?
A: The "well-mixed" assumption means the solute is uniformly distributed throughout the tank at every instant. So any volume element leaving the tank carries the same concentration as the bulk: $Q(t)/V(t)$. This is what lets us write the outflow rate as $(Q/V)\, r_\text{out}$.

Q: Why is the standard mixing ODE first-order linear?
A: Writing it as $dQ/dt + (r_\text{out}/V)\, Q = c_\text{in} r_\text{in}$ shows it has the form $Q' + p(t)Q = g(t)$, which is the definition of a first-order linear ODE. This is why integrating factors are the natural tool for mixing problems.

P: A $100$ L tank initially contains $5$ kg of salt dissolved in water. Pure water enters at $2$ L/min, and the well-mixed solution leaves at $2$ L/min. Find $Q(t)$, the amount of salt at time $t$.

S:
**IDENTIFY**: Mixing problem with inflow = outflow (constant volume), zero inflow concentration.

**PLAN**:
- Volume is constant: $V = 100$ L.
- Rate in: $c_\text{in} r_\text{in} = 0 \cdot 2 = 0$ kg/min.
- Rate out: $(Q/100)(2) = Q/50$ kg/min.
- Set up and solve the resulting ODE.

**EXECUTE**:
1. $dQ/dt = 0 - Q/50$, i.e. $dQ/dt = -Q/50$.
2. Separable/linear with decay rate $k = 1/50$: $Q(t) = Q_0 e^{-t/50}$.
3. With $Q_0 = 5$: $Q(t) = 5 e^{-t/50}$ kg.

**EVALUATE**: As $t \to \infty$, $Q \to 0$, which matches intuition: continually flushing with pure water eventually removes all salt. The time constant is $50$ min, so after one time constant ($t=50$) about $37\%$ of the salt remains, which is reasonable.

## 4.6 Constant vs Varying Volume Mixing

Q: Why does the tank volume $V$ become time-dependent when the inflow and outflow rates differ?
A: Volume changes at the net flow rate: $dV/dt = r_\text{in} - r_\text{out}$. If $r_\text{in} \neq r_\text{out}$, this integrates to $V(t) = V_0 + (r_\text{in} - r_\text{out})\, t$ — a linear function of time rather than a constant.

C: When the inflow and outflow rates differ, the tank volume varies linearly as [$V(t) = V_0 + (r_\text{in} - r_\text{out})\, t$], where $V_0$ is the initial volume.

Q: How does the mixing ODE change when the volume varies with time?
A: The outflow term becomes $(Q/V(t))\, r_\text{out}$, and since $V(t)$ is a linear function of $t$, the coefficient of $Q$ is now time-dependent: $dQ/dt + [r_\text{out}/V(t)]\, Q = c_\text{in} r_\text{in}$. It is still first-order linear, but the integrating factor is no longer a simple exponential in $t$ — it involves $\ln V(t)$.

Q: When the tank is being filled faster than it drains, what happens if we wait long enough, and how does this constrain the model?
A: The tank eventually overflows. The model is only valid while $V(t) \leq V_\text{max}$; beyond that point, either the problem ends or a new equation (with different boundary conditions) takes over. Always check the physical domain of validity when volumes change.

## 4.7 Logistic Population Model

Q: Why does the simple exponential model $dP/dt = rP$ fail as a long-term model of real populations?
A: It predicts unlimited exponential growth, but real populations are constrained by finite resources (food, space, predators). For small $P$, exponential growth is a good local approximation, but as $P$ gets large, per-capita growth must slow and eventually reach zero when the environment is saturated.

C: The [logistic equation] models a population with limited resources: $dP/dt = rP(1 - P/K)$, where $r>0$ is the intrinsic per-capita growth rate and $K>0$ is the carrying capacity.

Q: In the logistic equation $dP/dt = rP(1 - P/K)$, what is the physical meaning of the carrying capacity $K$?
A: $K$ is the equilibrium population that the environment can support indefinitely. When $P=K$, the factor $(1 - P/K) = 0$, so $dP/dt = 0$ and the population is stable. For $P<K$ the population grows; for $P>K$ it declines toward $K$.

Q: Why does the logistic equation reduce to exponential growth when $P \ll K$?
A: When $P \ll K$, the term $P/K \approx 0$, so $1 - P/K \approx 1$ and $dP/dt \approx rP$. Hence logistic growth behaves exactly like unrestricted exponential growth while the population is much smaller than the carrying capacity; the nonlinear term only matters as $P$ approaches $K$.

## 4.8 Logistic Solution

C: The solution of the logistic equation $dP/dt = rP(1 - P/K)$ with $P(0) = P_0$ is [$P(t) = K/(1 + A e^{-rt})$], where $A = (K - P_0)/P_0$.

Q: Why does the logistic solution $P(t) = K/(1 + A e^{-rt})$ approach $K$ as $t \to \infty$?
A: The term $A e^{-rt}$ decays to $0$ for any $r>0$, so the denominator tends to $1$, giving $P(t) \to K$. Physically, no matter the starting value $P_0 > 0$, the population is drawn to the carrying capacity.

Q: What does the logistic curve's inflection point tell us biologically, and where does it occur?
A: The inflection point is where growth rate $dP/dt$ is maximal — the population is growing fastest. Setting $d^2P/dt^2 = 0$ gives $P = K/2$: the fastest growth occurs when the population is at half the carrying capacity, a key insight for harvesting and conservation.

## 4.9 RC Circuit

Q: Using Kirchhoff's voltage law, why does a series RC circuit with a source $V_s$ obey $RC\, dV/dt + V = V_s$, where $V$ is the capacitor voltage?
A: KVL gives $V_s = V_R + V_C = iR + V$. The current charging the capacitor satisfies $i = C\, dV/dt$. Substituting, $V_s = RC\, dV/dt + V$, i.e. $RC\, dV/dt + V = V_s$. This is first-order linear in $V(t)$.

C: For a series RC circuit driven by a constant source $V_s$, the capacitor voltage $V(t)$ satisfies $RC\, dV/dt + V = V_s$ with [time constant $\tau = RC$].

Q: What is the step response of an RC circuit with capacitor initially uncharged, and why?
A: Solving $RC\, dV/dt + V = V_s$ with $V(0)=0$ gives $V(t) = V_s (1 - e^{-t/RC})$. The capacitor charges exponentially toward $V_s$, reaching ~63% of $V_s$ after one time constant $\tau = RC$ and essentially all of $V_s$ after about $5\tau$.

Q: Physically, why does the RC time constant $\tau = RC$ set the charging speed?
A: $R$ limits how much current can flow for a given voltage difference, while $C$ measures how much charge is needed per volt of capacitor voltage. A larger $R$ throttles the current; a larger $C$ demands more charge. Both increase the time needed to charge, so $\tau = RC$ has units of seconds and sets the natural time scale.

## 4.10 RL Circuit

Q: Using Kirchhoff's voltage law, why does a series RL circuit with source $V_s$ satisfy $L\, dI/dt + RI = V_s$?
A: KVL: $V_s = V_R + V_L = IR + L\, dI/dt$. Rearranging, $L\, dI/dt + RI = V_s$, a first-order linear ODE for the current $I(t)$.

C: The series RL circuit obeys $L\, dI/dt + RI = V_s$ with [time constant $\tau = L/R$].

Q: Why does the RL time constant have the form $\tau = L/R$ rather than $LR$?
A: Dimensionally, inductance is volts per amp-per-second and resistance is volts per amp, so $L/R$ has units of seconds. Physically, larger $L$ opposes changes in current (slower response), while larger $R$ damps current more strongly and reaches steady state faster — hence $R$ in the denominator.

Q: What is the step response of an RL circuit with zero initial current, and what is its long-time limit?
A: Solving $L\, dI/dt + RI = V_s$ with $I(0) = 0$ gives $I(t) = (V_s/R)(1 - e^{-Rt/L})$. As $t \to \infty$, $I \to V_s/R$: the inductor behaves like a plain wire and the current is set by Ohm's law on $R$ alone.

## 4.11 Falling Object with Linear Air Resistance

Q: Applying Newton's second law, why does an object falling with linear air resistance obey $m\, dv/dt = mg - kv$?
A: Two forces act: gravity $+mg$ (downward, taken positive) and drag $-kv$ (opposing motion, proportional to velocity for low speeds/small objects). Newton's second law $F = ma = m\, dv/dt$ gives $m\, dv/dt = mg - kv$.

C: A falling object with linear drag obeys [$m\, dv/dt = mg - kv$], where $m$ is mass, $g$ is gravitational acceleration, $v$ is velocity (taken positive downward), and $k$ is the linear drag coefficient.

Q: What is the terminal velocity of an object under linear drag, and why does it emerge?
A: Setting $dv/dt = 0$ in $m\, dv/dt = mg - kv$ gives $v_t = mg/k$. At this velocity, drag exactly balances gravity, so there is no net force and no further acceleration. Any object released from rest accelerates toward this $v_t$, asymptotically.

C: The terminal velocity of an object falling under linear drag is [$v_t = mg/k$], where $m$ is mass, $g$ is gravitational acceleration, and $k$ is the linear drag coefficient.

Q: Starting from rest, how does the velocity approach terminal velocity over time?
A: Solving $m\, dv/dt = mg - kv$ with $v(0)=0$ gives $v(t) = v_t(1 - e^{-kt/m})$, where $v_t = mg/k$. The velocity rises exponentially toward $v_t$ with time constant $\tau = m/k$: heavier objects or weaker drag make the approach slower.

## 4.12 Dimensional Analysis and Units

Q: Why is a dimensional (units) check essential when writing an ODE model?
A: Every term in a valid equation must share the same units. A mismatch reveals a missing factor, a misplaced constant, or a conceptual error. Units also assign physical meaning to proportionality constants (e.g., $k$ in Newton's cooling has units of $1/\text{time}$, so $1/k$ is a time scale).

Q: In $dy/dt = ky$, what are the units of $k$, and why?
A: $dy/dt$ has units of $[y]/\text{time}$, and $ky$ has units of $[k]\cdot[y]$. For these to match, $[k] = 1/\text{time}$. So $k$ is a rate (per second, per year, per minute), and $1/k$ is the characteristic time scale of the process.

Q: What are the units of the drag coefficient $k$ in $m\,dv/dt = mg - kv$, and why?
A: $kv$ must have units of force (same as $mg$). Since $v$ has units of m/s and force has units of kg·m/s², $k$ must have units of kg/s. Equivalently, this matches $v_t = mg/k$ having units of m/s as required.

Q: Why does $\tau = RC$ in an RC circuit have units of seconds?
A: Resistance has units of $V/A = V\cdot s/C$ (since 1 A = 1 C/s), and capacitance has units of $C/V$. Multiplying, $R\cdot C$ has units of $(V\cdot s/C)\cdot(C/V) = s$. So $\tau$ is genuinely a time, consistent with appearing inside $e^{-t/\tau}$.
