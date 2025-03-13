# Problem 1

# **Investigating Projectile Motion: Dependence of Range on Launch Angle**  

Projectile motion, the movement of an object thrown at an angle to the horizontal, is a fundamental concept in physics. Understanding how the range of a projectile depends on the launch angle is not only mathematically intriguing but also has numerous real-world applications. This principle is widely used in various fields, from analyzing the flight of a soccer ball to calculating the trajectory of a spacecraft.  

---

## **1. Theoretical Foundation**  

In projectile motion, an object moves under the influence of gravity, following a parabolic path. The key parameters include:  

- **Initial velocity $ v_0 $** – the speed at which the object is launched.  
- **Launch angle $ \theta $** – the angle between the initial velocity vector and the horizontal plane.  
- **Acceleration due to gravity $ g $** – approximately $ 9.81 $ m/s² on Earth.  

The motion can be decomposed into two components:  

### **Equations of Motion**  
- **Horizontal motion (constant velocity):**  
  $$
  x = v_0 \cos\theta \cdot t
  $$  
- **Vertical motion (accelerated motion due to gravity):**  
  $$
  y = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
  $$  
- **Time of flight (when the projectile returns to the ground, $ y = 0 $):**  
  $$
  t = \frac{2 v_0 \sin\theta}{g}
  $$  
- **Range (horizontal distance traveled before landing):**  
  $$
  R = \frac{v_0^2 \sin(2\theta)}{g}
  $$  
This equation reveals that the range depends on the square of the initial velocity, the sine of twice the launch angle, and the gravitational acceleration.  

---

## **2. Range Analysis Based on Launch Angle**  

Key observations:  

- **Maximum range** occurs at $ \theta = 45^\circ $ (assuming no air resistance).  
- **Symmetry of trajectory:** The same range is achieved at complementary angles (e.g., $ 30^\circ $ and $ 60^\circ $ result in the same range).  
- **Dependence on velocity:** Since $ R \propto v_0^2 $, doubling the initial velocity quadruples the range.  
- **Effect of gravity:** On planets with lower gravity (e.g., the Moon, where $ g \approx 1.62 $ m/s²), projectiles travel much farther than on Earth.  

---

## **3. Practical Applications of Projectile Motion**  

Projectile motion plays a crucial role in various fields:  

1. **Sports:** Optimizing kick angles in soccer, basketball shots, and long jumps.  
2. **Ballistics:** Calculating bullet and missile trajectories.  
3. **Engineering:** Designing structures resistant to impact forces.  
4. **Space Exploration:** Determining launch trajectories for satellites and landers.  

However, real-world factors complicate the idealized model:  
- **Air resistance** reduces the range.  
- **Uneven terrain** affects the landing position.  
- **Magnus effect (object spin)** alters the trajectory (e.g., in soccer or tennis).  

---

## **4. Implementation and Visualization with Code**  

To gain a deeper understanding of projectile motion, Python can be used to compute and visualize the relationship between launch angle and range.  

```python
import numpy as np
import matplotlib.pyplot as plt

def range_of_projectile(v0, theta, g=9.81):
    theta_rad = np.radians(theta)
    return (v0**2 * np.sin(2 * theta_rad)) / g

# Variable
v0 = 20  # м/с
angles = np.linspace(0, 90, 100) 
ranges = [range_of_projectile(v0, theta) for theta in angles]

# Graph
plt.figure(figsize=(8, 5))
plt.plot(angles, ranges, label=f'v0 = {v0} м/с')
plt.xlabel('Launch Angle (degrees)')
plt.ylabel('Range (m)')
plt.title('Projectile Range vs. Launch Angle')
plt.legend()
plt.grid()
plt.show()
```

### **What does the provided script do?**  
✅ Computes the range for angles from $ 0^\circ $ to $ 90^\circ $.  
✅ Simulates the effect of different initial velocities.  
✅ Plots a graph of range vs. launch angle.  

If additional factors such as air resistance or variable gravity (e.g., Mars) need to be considered, the code can be extended. Would you like to incorporate such enhancements? 🚀  
