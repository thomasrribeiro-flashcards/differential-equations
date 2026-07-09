+++
order = 8
subject = "Mathematics"
tags = ["math", "differential-equations", "ode", "vibrations", "damping", "resonance", "rlc-circuit"]
+++

# Differential Equations — Applications of Second-Order Equations

## 8.1 Why Second-Order ODEs Model Physical Systems

Q: Why do so many physical systems lead naturally to second-order linear ODEs?
A: Newton's second law $F = ma$ relates force to acceleration, and acceleration is the second derivative of position with respect to time, so any mechanical law written in terms of position is automatically second-order. Similarly, Kirchhoff's voltage law applied to a circuit containing an inductor produces a second-order equation in charge, because the voltage across an inductor is proportional to $dI/dt$ and the current is itself $dQ/dt$. The prevalence of "force = stiffness + friction + inertia" relationships is what makes the second-order linear ODE a universal template.

C: Newton's second law $F = ma$ is [second-order] in position because $a = \ddot{x}$.

C: Kirchhoff's voltage law applied to an RLC circuit yields a second-order ODE in the [charge] $Q(t)$.

## 8.2 The Mass-Spring-Damper Equation

Q: What equation governs a mass on a spring with linear damping and an external driving force?
A: Newton's second law gives $m\ddot{x} + b\dot{x} + kx = F(t)$, where $m$ is the mass, $b$ is the damping coefficient, $k$ is the spring constant, $x$ is displacement from equilibrium, and $F(t)$ is the external driving force. The $kx$ term is the restoring force from Hooke's law, and the $b\dot{x}$ term represents a velocity-proportional drag (e.g., a dashpot).

C: The mass-spring-damper equation is $[m\ddot{x} + b\dot{x} + kx = F(t)]$, where $m$ is mass, $b$ damping, $k$ spring constant, $x$ displacement, and $F(t)$ the driving force.

Q: Why is $x$ measured from the equilibrium position rather than from the natural length of the spring?
A: Measuring from equilibrium absorbs the constant gravitational force into the definition of equilibrium, so gravity drops out of the equation of motion. The resulting ODE is homogeneous in $x$ with the same spring constant $k$, which makes the linear structure visible and the analysis cleaner.

## 8.3 Undamped Free Vibration

Q: What ODE describes a mass-spring system with no damping and no driving force?
A: Setting $b = 0$ and $F = 0$ in $m\ddot{x} + b\dot{x} + kx = 0$ and dividing by $m$ gives $\ddot{x} + \omega_0^2 x = 0$, where $\omega_0 = \sqrt{k/m}$ is the natural angular frequency. This is simple harmonic motion: the mass oscillates sinusoidally forever because there is no mechanism to dissipate energy.

C: The undamped free vibration equation is $[\ddot{x} + \omega_0^2 x = 0]$, with $\omega_0 = \sqrt{k/m}$.

C: The general solution of $\ddot{x} + \omega_0^2 x = 0$ can be written as $x(t) = [A\cos(\omega_0 t - \phi)]$, where $A$ is amplitude, $\omega_0$ natural frequency, and $\phi$ phase.

## 8.4 Natural Frequency and Period

C: The natural angular frequency of an undamped mass-spring system is $\omega_0 = [\sqrt{k/m}]$, where $k$ is the spring constant and $m$ is the mass.

C: The period of undamped free vibration is $T = [2\pi/\omega_0]$, where $\omega_0 = \sqrt{k/m}$.

Q: Why does a stiffer spring oscillate at a higher frequency, while a heavier mass oscillates at a lower frequency?
A: Because $\omega_0 = \sqrt{k/m}$: increasing $k$ raises the restoring force per unit displacement, so the mass is pulled back faster, while increasing $m$ raises inertia, so the mass responds more slowly to the same force. The square root moderates both effects.

## 8.5 Amplitude-Phase Form

Q: Why is it useful to rewrite $c_1\cos(\omega t) + c_2\sin(\omega t)$ in amplitude-phase form $A\cos(\omega t - \phi)$?
A: The amplitude-phase form exposes the two physically meaningful quantities directly: $A$ is the amplitude of oscillation (maximum displacement) and $\phi$ is the phase shift (where in the cycle the motion starts). The raw $c_1, c_2$ combination hides both behind a trigonometric identity.

C: To convert $c_1\cos(\omega t) + c_2\sin(\omega t)$ to $A\cos(\omega t - \phi)$, use $A = [\sqrt{c_1^2 + c_2^2}]$.

C: In the conversion $c_1\cos(\omega t) + c_2\sin(\omega t) = A\cos(\omega t - \phi)$, the phase satisfies $\tan\phi = [c_2/c_1]$.

P: Express $x(t) = 3\cos(2t) + 4\sin(2t)$ in the amplitude-phase form $A\cos(2t - \phi)$.

S:
**IDENTIFY**: Conversion from linear combination of sine and cosine to single cosine with phase shift.

**PLAN**: Use $A = \sqrt{c_1^2 + c_2^2}$ and $\tan\phi = c_2/c_1$ with $c_1 = 3$ and $c_2 = 4$.

**EXECUTE**:
1. $A = \sqrt{3^2 + 4^2} = \sqrt{25} = 5$.
2. $\tan\phi = 4/3$, so $\phi = \arctan(4/3) \approx 0.927$ rad.
3. Therefore $x(t) = 5\cos(2t - 0.927)$.

**EVALUATE**: Check at $t = 0$: $5\cos(-0.927) = 5 \cdot (3/5) = 3$, matching $c_1 = 3$; derivative at $t = 0$ gives $5 \cdot 2 \cdot \sin(0.927) = 10 \cdot (4/5) = 8$, matching $c_2 \omega = 4 \cdot 2 = 8$.

## 8.6 Damped Free Vibration: Three Cases

Q: Why does damped free vibration split into exactly three qualitatively different behaviors?
A: The homogeneous equation $m\ddot{x} + b\dot{x} + kx = 0$ has characteristic equation $mr^2 + br + k = 0$, whose discriminant is $b^2 - 4mk$. The sign of this discriminant determines whether the roots are complex conjugates (oscillation), repeated real (borderline), or distinct real (no oscillation), producing three distinct physical regimes.

C: The three damping regimes are classified by the sign of the discriminant $[b^2 - 4mk]$ of the characteristic equation $mr^2 + br + k = 0$.

## 8.7 Underdamped Motion

C: A mass-spring-damper system is [underdamped] when $b^2 < 4mk$, and it oscillates with decaying amplitude.

Q: What is the general solution of an underdamped free vibration?
A: The characteristic roots are complex conjugates $r = -\gamma \pm i\omega_d$, where $\gamma = b/(2m)$ is the decay rate and $\omega_d = \sqrt{\omega_0^2 - \gamma^2}$ is the damped angular frequency. The solution is $x(t) = Ae^{-\gamma t}\cos(\omega_d t - \phi)$, a sinusoid of frequency $\omega_d$ whose amplitude envelope $Ae^{-\gamma t}$ decays exponentially.

C: For an underdamped system, the decay rate is $\gamma = [b/(2m)]$, where $b$ is the damping coefficient and $m$ the mass.

C: For an underdamped system, the damped angular frequency is $\omega_d = [\sqrt{\omega_0^2 - \gamma^2}]$, where $\omega_0 = \sqrt{k/m}$ and $\gamma = b/(2m)$.

Q: Why is the damped frequency $\omega_d$ always lower than the natural frequency $\omega_0$?
A: Because $\omega_d = \sqrt{\omega_0^2 - \gamma^2}$, and $\gamma^2 > 0$ whenever damping is present. Physically, damping removes energy in each cycle, slowing the mass down relative to its undamped motion, so the oscillation takes longer — a lower frequency.

## 8.8 Critically Damped Motion

C: A mass-spring-damper system is [critically damped] when $b^2 = 4mk$, the borderline between oscillation and monotonic decay.

Q: Why is critical damping the fastest return to equilibrium without oscillation?
A: At critical damping the characteristic equation has a repeated real root $r = -b/(2m)$, giving solutions of the form $(c_1 + c_2 t)e^{-\gamma t}$. Any slightly smaller damping produces oscillation (overshoots equilibrium), while any larger damping produces two distinct negative roots whose slower one dominates the long-term decay. Critical damping sits precisely at the boundary and minimizes the settling time.

Q: In engineering, when do you design for critical damping?
A: When you want a system to reach its target state as quickly as possible without overshooting or oscillating — e.g., automatic door closers, analog meter needles, vehicle suspensions tuned to stop bouncing after a bump.

## 8.9 Overdamped Motion

C: A mass-spring-damper system is [overdamped] when $b^2 > 4mk$, and it decays to equilibrium without oscillating.

Q: Why does an overdamped system return to equilibrium more slowly than a critically damped one?
A: Overdamping yields two distinct negative real roots $r_1, r_2$, and the long-term behavior is dominated by the root closer to zero (the slower exponential). Excess damping resists motion so strongly that the mass creeps back to equilibrium instead of snapping to it; critical damping is the sweet spot where the slowest decay rate is as large as possible.

## 8.10 Forced Vibration (Undamped)

C: The undamped forced vibration equation with sinusoidal forcing is $[\ddot{x} + \omega_0^2 x = F_0\cos(\omega t)]$, where $\omega_0$ is the natural frequency and $\omega$ is the driving frequency.

Q: When the driving frequency $\omega$ differs from $\omega_0$, what is the form of the particular solution to $\ddot{x} + \omega_0^2 x = F_0\cos(\omega t)$?
A: Try $x_p = C\cos(\omega t)$; substituting gives $(-\omega^2 + \omega_0^2)C = F_0$, so $C = F_0/(\omega_0^2 - \omega^2)$. The particular solution $x_p = \frac{F_0}{\omega_0^2 - \omega^2}\cos(\omega t)$ oscillates at the driving frequency with amplitude that blows up as $\omega \to \omega_0$.

## 8.11 Beats

Q: What are beats, and when do they occur in an undamped forced oscillator?
A: Beats are a slow periodic rise and fall in the amplitude envelope of the total response, caused when the driving frequency $\omega$ is close to but not equal to the natural frequency $\omega_0$. The sum of two cosines of nearly equal frequency can be rewritten as a product: a fast oscillation at $(\omega + \omega_0)/2$ modulated by a slow envelope at $(\omega_0 - \omega)/2$, which is audible as a throbbing "beat" pattern.

C: Beats arise in an undamped forced oscillator when the driving frequency $\omega$ is [close to but not equal to] the natural frequency $\omega_0$.

## 8.12 Resonance

Q: What is resonance in an undamped forced oscillator?
A: Resonance is the phenomenon where the driving frequency exactly matches the natural frequency, $\omega = \omega_0$, and the particular solution's amplitude formula $F_0/(\omega_0^2 - \omega^2)$ diverges. The correct particular solution then has the form $x_p = \frac{F_0}{2m\omega_0} t \sin(\omega_0 t)$, whose amplitude grows linearly in $t$ without bound.

C: In an undamped forced oscillator, resonance occurs when $\omega = [\omega_0]$, and the particular solution's amplitude grows like $[t]$.

## 8.13 Why Resonance Occurs Physically

Q: Why does resonance cause the amplitude to grow without bound in an undamped system?
A: When the driving force oscillates in phase with the mass's natural motion, every push occurs exactly when the mass is moving in the direction of the push. Each cycle the force does positive work on the mass, pumping energy into the system, and because no damping dissipates it, the kinetic plus potential energy — and thus the amplitude — increases without limit.

Q: Why does adding even a small amount of damping prevent unbounded resonance?
A: Damping dissipates energy at a rate proportional to $\dot{x}^2$, which grows with amplitude. As the amplitude rises, the dissipation rate eventually matches the rate at which the driver pumps energy in, and the system settles into a finite steady-state oscillation rather than growing forever.

## 8.14 Damped Forced Vibration

Q: What is the steady-state amplitude of a damped, sinusoidally driven oscillator?
A: For $m\ddot{x} + b\dot{x} + kx = F_0\cos(\omega t)$, the steady-state particular solution has amplitude $A(\omega) = F_0/\sqrt{(k - m\omega^2)^2 + b^2\omega^2}$, where $F_0$ is the forcing amplitude, $\omega$ the driving frequency, $m$ mass, $b$ damping, and $k$ spring constant. The amplitude is finite for all $\omega$ because the $b^2\omega^2$ term keeps the denominator positive even at $\omega_0$.

C: The steady-state amplitude for $m\ddot{x} + b\dot{x} + kx = F_0\cos(\omega t)$ is $A(\omega) = [F_0/\sqrt{(k - m\omega^2)^2 + b^2\omega^2}]$.

Q: Near what driving frequency is the steady-state amplitude $A(\omega)$ largest for a lightly damped system?
A: Near the natural frequency $\omega_0 = \sqrt{k/m}$. The factor $(k - m\omega^2)^2$ in the denominator vanishes at $\omega_0$, so only the damping term $b^2\omega^2$ limits the peak. For small $b$ the amplitude peaks sharply just below $\omega_0$.

## 8.15 Transient vs Steady-State Response

Q: What is the difference between the transient and steady-state parts of a damped forced response?
A: The transient is the homogeneous solution of the damped system, which always contains the decay factor $e^{-\gamma t}$ and therefore dies out as $t \to \infty$. The steady-state is the particular solution — a sinusoid at the driving frequency $\omega$ — which persists indefinitely. The transient captures the system's memory of its initial conditions; the steady-state captures its long-run response to the driver.

C: In a damped forced oscillator, the [transient] response decays exponentially, while the [steady-state] response is a sustained sinusoid at the driving frequency.

Q: Why do the initial conditions only affect the transient and not the steady-state?
A: The general solution is $x = x_h + x_p$, and initial conditions are absorbed into the two free constants of $x_h$ (the homogeneous part). The particular solution $x_p$ depends only on the forcing and system parameters, so once the transient decays the motion forgets its starting position and velocity.

## 8.16 RLC Series Circuit

Q: What ODE governs the charge on the capacitor in a series RLC circuit driven by a voltage $V(t)$?
A: Kirchhoff's voltage law gives $L\ddot{Q} + R\dot{Q} + Q/C = V(t)$, where $L$ is the inductance, $R$ the resistance, $C$ the capacitance, $Q(t)$ the charge on the capacitor, and $V(t)$ the source voltage. The $Q/C$ term is the voltage across the capacitor (from $V = Q/C$), $R\dot{Q}$ is the resistor voltage (from $V = IR$ with $I = \dot{Q}$), and $L\ddot{Q}$ is the inductor voltage ($V = L\,dI/dt$).

C: The series RLC circuit equation in terms of charge is $[L\ddot{Q} + R\dot{Q} + Q/C = V(t)]$, where $L$ is inductance, $R$ resistance, $C$ capacitance, and $Q$ charge.

Q: What is the mass-spring ↔ RLC analogy?
A: Comparing $m\ddot{x} + b\dot{x} + kx = F(t)$ with $L\ddot{Q} + R\dot{Q} + Q/C = V(t)$: inductance $L$ plays the role of mass (inertia), resistance $R$ plays the role of damping $b$ (dissipation), reciprocal capacitance $1/C$ plays the role of spring constant $k$ (restoring stiffness), and source voltage $V(t)$ plays the role of driving force $F(t)$. Every mechanical result (natural frequency, damping regimes, resonance) transfers directly.

C: In the mass-spring ↔ RLC analogy, $L \leftrightarrow [m]$ (inertia).

C: In the mass-spring ↔ RLC analogy, $R \leftrightarrow [b]$ (damping/dissipation).

C: In the mass-spring ↔ RLC analogy, $1/C \leftrightarrow [k]$ (restoring stiffness).

Q: What is the natural angular frequency of an undriven, undamped LC circuit?
A: By direct analogy with $\omega_0 = \sqrt{k/m}$ and the substitutions $k \to 1/C$, $m \to L$: $\omega_0 = \sqrt{1/(LC)} = 1/\sqrt{LC}$, where $L$ is inductance and $C$ capacitance. This is the frequency at which the LC "tank" circuit oscillates, exchanging energy between the inductor's magnetic field and the capacitor's electric field.

## 8.17 Quality Factor

C: The quality factor of a damped oscillator is $Q_f = [m\omega_0/b]$, where $m$ is mass, $\omega_0 = \sqrt{k/m}$ is the natural frequency, and $b$ is the damping coefficient.

Q: What does the quality factor $Q_f$ physically describe?
A: $Q_f$ measures the sharpness of the resonance peak in the amplitude response $A(\omega)$: large $Q_f$ (small damping) gives a narrow, tall peak and a system that rings for many cycles before decaying; small $Q_f$ (heavy damping) gives a broad, shallow peak and a system that barely oscillates. Roughly, $Q_f \approx 2\pi \times (\text{energy stored}) / (\text{energy lost per cycle})$.

Q: For an RLC circuit, what is the quality factor by analogy?
A: Using $m \to L$, $b \to R$, $\omega_0 = 1/\sqrt{LC}$, the circuit quality factor is $Q_f = L\omega_0/R = (1/R)\sqrt{L/C}$, where $L$ is inductance, $R$ resistance, and $C$ capacitance. High-$Q_f$ circuits (small $R$) are used as frequency-selective filters in radio receivers because they respond strongly only to a narrow band near $\omega_0$.

## 8.18 Worked Classification and Solution

P: A 1 kg mass hangs on a spring with spring constant $k = 4$ N/m and damping coefficient $b = 5$ N·s/m. At $t = 0$ the mass is displaced 1 m below equilibrium and released from rest. Classify the damping regime and find $x(t)$.

S:
**IDENTIFY**: Damped free vibration — need to classify the damping regime using the discriminant $b^2 - 4mk$, then solve the resulting homogeneous ODE subject to $x(0) = 1$, $\dot{x}(0) = 0$.

**PLAN**:
- Write the ODE $m\ddot{x} + b\dot{x} + kx = 0$ with $m = 1$, $b = 5$, $k = 4$.
- Compute discriminant $b^2 - 4mk$ and compare to zero: positive → overdamped (distinct real roots), zero → critically damped (repeated root), negative → underdamped (complex roots).
- Solve the characteristic equation for the roots $r_1, r_2$.
- Apply initial conditions $x(0) = 1$, $\dot{x}(0) = 0$ to determine the two constants.

**EXECUTE**:
1. ODE: $\ddot{x} + 5\dot{x} + 4x = 0$.
2. Discriminant: $b^2 - 4mk = 25 - 16 = 9 > 0$, so the system is **overdamped**.
3. Characteristic equation: $r^2 + 5r + 4 = 0 \Rightarrow (r + 1)(r + 4) = 0$, giving $r_1 = -1$, $r_2 = -4$.
4. General solution: $x(t) = c_1 e^{-t} + c_2 e^{-4t}$.
5. Apply $x(0) = 1$: $c_1 + c_2 = 1$.
6. Compute $\dot{x}(t) = -c_1 e^{-t} - 4c_2 e^{-4t}$ and apply $\dot{x}(0) = 0$: $-c_1 - 4c_2 = 0 \Rightarrow c_1 = -4c_2$.
7. Substitute: $-4c_2 + c_2 = 1 \Rightarrow c_2 = -1/3$, so $c_1 = 4/3$.
8. Solution: $x(t) = \tfrac{4}{3}e^{-t} - \tfrac{1}{3}e^{-4t}$.

**EVALUATE**:
- Check $x(0) = 4/3 - 1/3 = 1$ ✓ and $\dot{x}(0) = -4/3 + 4/3 = 0$ ✓.
- Both exponentials decay, so $x(t) \to 0$ as $t \to \infty$ — consistent with overdamped free motion.
- The slower mode $e^{-t}$ (root closer to zero) dominates the long-term return, confirming that overdamping returns to equilibrium more slowly than critical damping would.
- Physically: $b^2 = 25$ while $4mk = 16$, so the damping strongly exceeds the critical value — the mass creeps back to equilibrium without oscillating, as expected.
