**Step-by-Step Solution: Theoretical Foundation**

**Step 1: Understand the Given Differential Equation**
The differential equation for a forced damped pendulum is provided as:
$$
\frac{d^2\theta}{dt^2} + \frac{b}{m} \frac{d\theta}{dt} + \frac{g}{l} \sin \theta = A \cos(\omega t)
$$
Where:
- $ \theta $: Angle of the pendulum from the vertical (in radians).
- $ \frac{d^2\theta}{dt^2} $: Angular acceleration.
- $ \frac{b}{m} \frac{d\theta}{dt} $: Damping term, proportional to angular velocity, where $ b $ is the damping coefficient and $ m $ is the mass.
- $ \frac{g}{l} \sin \theta $: Restoring force due to gravity, where $ g $ is the gravitational acceleration and $ l $ is the length of the pendulum.
- $ A \cos(\omega t) $: External periodic forcing with amplitude $ A $ and frequency $ \omega $.

This equation is nonlinear due to the $ \sin \theta $ term, but the task asks for an approximate solution for small angles.

---

**Step 2: Apply the Small-Angle Approximation**
For small angles ($ \theta \ll 1 $), we can approximate:
$$
\sin \theta \approx \theta
$$
Substitute this into the differential equation:
$$
\frac{d^2\theta}{dt^2} + \frac{b}{m} \frac{d\theta}{dt} + \frac{g}{l} \theta = A \cos(\omega t)
$$
Define:
- $ \gamma = \frac{b}{m} $: Damping coefficient.
- $ \omega_0^2 = \frac{g}{l} $, where $ \omega_0 = \sqrt{\frac{g}{l}} $ is the natural frequency of the undamped pendulum.

The equation becomes:
$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
$$
This is now a linear second-order differential equation with constant coefficients and a harmonic forcing term.

---
**Step 3: Solve the Homogeneous Equation**
First, solve the homogeneous part:
$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = 0
$$
The characteristic equation is:
$$
r^2 + \gamma r + \omega_0^2 = 0
$$
Solve for $ r $:
$$
r = \frac{-\gamma \pm \sqrt{\gamma^2 - 4 \omega_0^2}}{2}
$$
The discriminant is:
$$
\Delta = \gamma^2 - 4 \omega_0^2
$$
Assuming weak damping ($ \gamma < 2 \omega_0 $, so $ \Delta < 0 $), the roots are complex:
$$
r = -\frac{\gamma}{2} \pm i \sqrt{\omega_0^2 - \left(\frac{\gamma}{2}\right)^2}
$$
Define the damped frequency:
$$
\omega_d = \sqrt{\omega_0^2 - \left(\frac{\gamma}{2}\right)^2}
$$
The homogeneous solution is:
$$
\theta_h(t) = e^{-\frac{\gamma}{2} t} \left( C_1 \cos(\omega_d t) + C_2 \sin(\omega_d t) \right)
$$
This represents damped oscillations that decay over time.

---

**Step 4: Solve the Particular Solution (Forced Response)**
Now, solve the nonhomogeneous equation:
$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
$$
Assume a particular solution of the form:
$$
\theta_p(t) = B \cos(\omega t) + C \sin(\omega t)
$$
Compute the derivatives:
- $ \frac{d\theta_p}{dt} = -B \omega \sin(\omega t) + C \omega \cos(\omega t) $
- $ \frac{d^2\theta_p}{dt^2} = -B \omega^2 \cos(\omega t) - C \omega^2 \sin(\omega t) $

Substitute into the equation:
$$
(-B \omega^2 \cos(\omega t) - C \omega^2 \sin(\omega t)) + \gamma (-B \omega \sin(\omega t) + C \omega \cos(\omega t)) + \omega_0^2 (B \cos(\omega t) + C \sin(\omega t)) = A \cos(\omega t)
$$
Equate coefficients of $ \cos(\omega t) $ and $ \sin(\omega t) $:
- For $ \cos(\omega t) $:
$$
-B \omega^2 + \gamma C \omega + \omega_0^2 B = A
$$
$$
B (\omega_0^2 - \omega^2) + \gamma C \omega = A \quad (1)
$$
- For $ \sin(\omega t) $:
$$
-C \omega^2 - \gamma B \omega + \omega_0^2 C = 0
$$
$$
C (\omega_0^2 - \omega^2) - \gamma B \omega = 0 \quad (2)
$$
From (2):
$$
C (\omega_0^2 - \omega^2) = \gamma B \omega
$$
$$
C = \frac{\gamma B \omega}{\omega_0^2 - \omega^2}
$$
Substitute $ C $ into (1):
$$
B (\omega_0^2 - \omega^2) + \gamma \left( \frac{\gamma B \omega}{\omega_0^2 - \omega^2} \right) \omega = A
$$
$$
B \left( (\omega_0^2 - \omega^2) + \frac{\gamma^2 \omega^2}{\omega_0^2 - \omega^2} \right) = A
$$
$$
B \left( \frac{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}{\omega_0^2 - \omega^2} \right) = A
$$
$$
B = \frac{A (\omega_0^2 - \omega^2)}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}
$$
Now solve for $ C $:
$$
C = \frac{\gamma \omega}{\omega_0^2 - \omega^2} \cdot \frac{A (\omega_0^2 - \omega^2)}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2} = \frac{A \gamma \omega}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}
$$
The particular solution is:
$$
\theta_p(t) = \frac{A (\omega_0^2 - \omega^2)}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2} \cos(\omega t) + \frac{A \gamma \omega}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2} \sin(\omega t)
$$
Rewrite in amplitude-phase form:
$$
\theta_p(t) = D \cos(\omega t - \phi)
$$
Where:
$$
D = \sqrt{B^2 + C^2} = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}}
$$
$$
\tan \phi = \frac{C}{B} = \frac{\gamma \omega}{\omega_0^2 - \omega^2}
$$

---

**Step 5: General Solution**
The general solution is the sum of the homogeneous and particular solutions:
$$
\theta(t) = e^{-\frac{\gamma}{2} t} \left( C_1 \cos(\omega_d t) + C_2 \sin(\omega_d t) \right) + \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}} \cos(\omega t - \phi)
$$
The first term (homogeneous) decays over time, leaving the steady-state solution (particular) as the dominant behavior.

---

**Step 6: Resonance Conditions**
Resonance occurs when the amplitude $ D $ is maximized:
$$
D = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}}
$$
The denominator is minimized when $ \omega \approx \omega_0 $, i.e., the driving frequency matches the natural frequency. For small damping, this leads to a large amplitude, increasing the system’s energy significantly.

---

**Solution Summary**

**Forced Damped Pendulum: Small-Angle Approximation Solution**

**Step 1: Differential Equation**
The equation is:
$$
\frac{d^2\theta}{dt^2} + \frac{b}{m} \frac{d\theta}{dt} + \frac{g}{l} \sin \theta = A \cos(\omega t)
$$

**Step 2: Small-Angle Approximation**
For small angles, $ \sin \theta \approx \theta $, so:
$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
$$
where $ \gamma = \frac{b}{m} $, $ \omega_0^2 = \frac{g}{l} $.

**Step 3: Homogeneous Solution**
Characteristic equation: $ r^2 + \gamma r + \omega_0^2 = 0 $
Roots: $ r = -\frac{\gamma}{2} \pm i \sqrt{\omega_0^2 - \left(\frac{\gamma}{2}\right)^2} $
Damped frequency: $ \omega_d = \sqrt{\omega_0^2 - \left(\frac{\gamma}{2}\right)^2} $
Solution: $ \theta_h(t) = e^{-\frac{\gamma}{2} t} \left( C_1 \cos(\omega_d t) + C_2 \sin(\omega_d t) \right) $

**Step 4: Particular Solution**
Assume: $ \theta_p(t) = B \cos(\omega t) + C \sin(\omega t) $
Solve to find:
$$
B = \frac{A (\omega_0^2 - \omega^2)}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}, \quad C = \frac{A \gamma \omega}{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}
$$
Amplitude-phase form: $ \theta_p(t) = D \cos(\omega t - \phi) $, where:
$$
D = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}}, \quad \tan \phi = \frac{\gamma \omega}{\omega_0^2 - \omega^2}
$$

**Step 5: General Solution**
$$
\theta(t) = e^{-\frac{\gamma}{2} t} \left( C_1 \cos(\omega_d t) + C_2 \sin(\omega_d t) \right) + \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + \gamma^2 \omega^2}} \cos(\omega t - \phi)
$$

**Step 6: Resonance**
Resonance occurs at $ \omega \approx \omega_0 $, maximizing the amplitude $ D $.

**Python Code: Forced Damped Pendulum Simulation**
``` py
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import odeint

# Parameters
g = 9.81  # Gravitational acceleration (m/s^2)
l = 1.0   # Length of the pendulum (m)
b = 0.5   # Damping coefficient (kg/s)
m = 1.0   # Mass of the pendulum (kg)
A = 1.0   # Amplitude of the driving force
omega = 2.0  # Driving frequency (rad/s)

# Define the system of first-order ODEs
def forced_damped_pendulum(state, t, gamma, omega_0, A, omega):
    theta, theta_dot = state
    dtheta_dt = theta_dot
    dtheta_dot_dt = -gamma * theta_dot - omega_0**2 * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, dtheta_dot_dt]

# Constants
gamma = b / m
omega_0 = np.sqrt(g / l)

# Time array
t = np.linspace(0, 20, 1000)

# Initial conditions: [theta(0), theta_dot(0)]
state0 = [0.1, 0.0]

# Solve the ODE
solution = odeint(forced_damped_pendulum, state0, t, args=(gamma, omega_0, A, omega))
theta = solution[:, 0]
theta_dot = solution[:, 1]

# Plotting
plt.figure(figsize=(12, 8))

# Plot theta vs time
plt.subplot(2, 2, 1)
plt.plot(t, theta, label='θ(t)')
plt.xlabel('Time (s)')
plt.ylabel('Angle θ (rad)')
plt.title('Angle vs Time')
plt.grid(True)
plt.legend()

# Plot theta_dot vs time
plt.subplot(2, 2, 2)
plt.plot(t, theta_dot, label='dθ/dt(t)', color='orange')
plt.xlabel('Time (s)')
plt.ylabel('Angular Velocity (rad/s)')
plt.title('Angular Velocity vs Time')
plt.grid(True)
plt.legend()

# Phase portrait
plt.subplot(2, 2, 3)
plt.plot(theta, theta_dot, label='Phase Portrait')
plt.xlabel('Angle θ (rad)')
plt.ylabel('Angular Velocity dθ/dt (rad/s)')
plt.title('Phase Portrait')
plt.grid(True)
plt.legend()

plt.tight_layout()
plt.show()
```

---

**Explanation of the Code**
- **Parameters**: The script defines physical parameters like $ g $, $ l $, $ b $, $ m $, $ A $, and $ \omega $.
- **ODE System**: The nonlinear equation is converted into a system of first-order ODEs: $ \frac{d\theta}{dt} = \dot{\theta} $, $ \frac{d\dot{\theta}}{dt} = -\gamma \dot{\theta} - \omega_0^2 \sin \theta + A \cos(\omega t) $.
- **Numerical Solution**: The `odeint` function from SciPy uses an adaptive method (similar to Runge-Kutta) to solve the system.
- **Plots**: The script generates three plots: $ \theta(t) $, $ \dot{\theta}(t) $, and a phase portrait ($ \dot{\theta} $ vs. $ \theta $).