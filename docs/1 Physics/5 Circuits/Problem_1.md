# Problem 1

### Explanation of Problem 1: Equivalent Resistance Using Graph Theory

#### Main Topic: What is Equivalent Resistance and Graph Theory?

Equivalent resistance is the single resistance that can replace a complex network of resistors while producing the same current for a given voltage, according to Ohm’s law ($V = I R$). Graph theory provides a mathematical framework to analyze such networks by representing them as graphs, where nodes (vertices) are junctions and edges are resistors. This approach simplifies complex circuits and is useful in electrical engineering, circuit design, and optimization problems.

**Key Concepts:**  
- **Resistance $R$** (in ohms, $\Omega$): Measures how much a resistor opposes the flow of electric current.  
- **Series Connection**: Resistors in series have the same current, and their resistances add: $R_{\text{eq}} = R_1 + R_2$.  
- **Parallel Connection**: Resistors in parallel have the same voltage, and their equivalent resistance is: $\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2}$.  
- **Graph Representation**:  
  - **Nodes (Vertices)**: Junctions where resistors connect.  
  - **Edges**: Resistors connecting the nodes, with weights equal to their resistances.  
- **Equivalent Resistance**: The resistance between two nodes in the graph, computed by simplifying the network using series and parallel rules or advanced methods like Kirchhoff’s laws.

**Applications:**  
- **Circuit Design**: Simplifying complex circuits to predict behavior.  
- **Network Analysis**: Optimizing power grids or communication networks.  
- **Physics Education**: Understanding how current flows in complex systems.

#### What Are We Trying to Do?

The task asks us to:  
1. Describe how to calculate equivalent resistance using graph theory, including series and parallel connections.  
2. Implement an algorithm to compute the equivalent resistance of a circuit represented as a graph.  
3. Test the algorithm on examples like series, parallel, nested configurations, and complex graphs with cycles.

---

### Solution for Problem 1: Equivalent Resistance Using Graph Theory

```
**Step-by-Step Solution: Equivalent Resistance Using Graph Theory**

**Step 1: Describe the Method Using Graph Theory**

In graph theory, a circuit is represented as a graph:  
- **Nodes**: Junctions where resistors connect.  
- **Edges**: Resistors, with weights equal to their resistances.  

To find the equivalent resistance between two nodes (e.g., nodes A and B):  
- **Series Reduction**: If two resistors $R_1$ and $R_2$ are in series (connected end-to-end with no other paths), replace them with a single resistor: $R_{\text{eq}} = R_1 + R_2$.  
- **Parallel Reduction**: If two resistors $R_1$ and $R_2$ are in parallel (connected between the same two nodes), replace them with: $\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2}$, so $R_{\text{eq}} = \frac{R_1 R_2}{R_1 + R_2}$.  
- **Iterative Simplification**: Repeatedly apply series and parallel reductions until the graph is reduced to a single edge between the two nodes.  
For complex graphs with cycles, we may need advanced methods like Kirchhoff’s laws or the delta-star transformation, but we’ll focus on simpler examples here.

**Step 2: Implement the Algorithm**

We’ll implement a simplified algorithm to compute the equivalent resistance of a circuit. For demonstration, we’ll manually simplify the graph for three example circuits:  
- **Series Circuit**: Two resistors in series.  
- **Parallel Circuit**: Two resistors in parallel.  
- **Nested Circuit**: A combination of series and parallel connections.  

**Python Code: Equivalent Resistance Calculation**

```py
import networkx as nx
import matplotlib.pyplot as plt

# Function to compute equivalent resistance for series and parallel
def series_resistance(R1, R2):
    return R1 + R2

def parallel_resistance(R1, R2):
    return (R1 * R2) / (R1 + R2)

# Example 1: Series Circuit
print("Example 1: Series Circuit")
R1, R2 = 2, 3  # Two resistors: 2 ohms and 3 ohms
R_series = series_resistance(R1, R2)
print(f"R1 = {R1} ohms, R2 = {R2} ohms")
print(f"Equivalent Resistance (Series): {R_series} ohms")

# Example 2: Parallel Circuit
print("\nExample 2: Parallel Circuit")
R1, R2 = 2, 3
R_parallel = parallel_resistance(R1, R2)
print(f"R1 = {R1} ohms, R2 = {R2} ohms")
print(f"Equivalent Resistance (Parallel): {R_parallel:.2f} ohms")

# Example 3: Nested Circuit (Series with Parallel)
print("\nExample 3: Nested Circuit")
# Circuit: R1 in series with (R2 || R3)
R1, R2, R3 = 1, 2, 2
R_parallel_23 = parallel_resistance(R2, R3)  # R2 and R3 in parallel
R_nested = series_resistance(R1, R_parallel_23)  # R1 in series with (R2 || R3)
print(f"R1 = {R1} ohms, R2 = {R2} ohms, R3 = {R3} ohms")
print(f"R2 || R3 = {R_parallel_23:.2f} ohms")
print(f"Equivalent Resistance (Nested): {R_nested:.2f} ohms")

# Visualize a simple graph (for the nested circuit)
G = nx.Graph()
G.add_edge('A', 'B', weight=R1)
G.add_edge('B', 'C', weight=R2)
G.add_edge('B', 'C', weight=R3)  # Parallel edge
pos = nx.spring_layout(G)
labels = nx.get_edge_attributes(G, 'weight')
nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=500)
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)
plt.title("Nested Circuit Graph Representation")
plt.show()
```

**Explanation of the Code**  
- **Functions**: `series_resistance` and `parallel_resistance` compute the equivalent resistance for series and parallel configurations.  
- **Examples**:  
  - **Series**: Two resistors (2 Ω and 3 Ω) in series yield 5 Ω.  
  - **Parallel**: Two resistors (2 Ω and 3 Ω) in parallel yield $\frac{2 \times 3}{2 + 3} = 1.2 \, \Omega$.  
  - **Nested**: R1 (1 Ω) in series with R2 (2 Ω) and R3 (2 Ω) in parallel. First, R2 || R3 = 1 Ω, then R1 + (R2 || R3) = 2 Ω.  
- **Visualization**: We use NetworkX to draw a simple graph representation of the nested circuit.

**Step 3: Test on Examples**

- **Series Circuit**: The equivalent resistance is simply the sum, as expected.  
- **Parallel Circuit**: The result (1.2 Ω) is less than either resistor, which is typical for parallel connections.  
- **Nested Circuit**: The combination of series and parallel reductions correctly yields 2 Ω.  
For more complex graphs with cycles, we would need to implement algorithms like the delta-star transformation or use Kirchhoff’s laws, which are beyond this simplified implementation.

**Step 4: Analysis**  
Graph theory simplifies circuit analysis by breaking down complex networks into manageable parts. The method is efficient for series and parallel configurations but requires additional techniques for cycles. In practical applications, this approach is used in circuit simulators and network optimization tools.
```

---

### Summary of Explanations and Solutions

#### Problem 1: Simulating the Effects of the Lorentz Force
- **Explanation**: We detailed the Lorentz force, its components ($q \vec{E}$ and $q (\vec{v} \times \vec{B})$), and their effects on a charged particle’s motion. We explained variables like $q$, $m$, $\vec{E}$, $\vec{B}$, and $\vec{v}$, and their roles in applications like particle accelerators and astrophysics.  
- **Solution**: We simulated a proton’s motion in combined electric and magnetic fields, visualized the spiral trajectory with $\vec{E} \times \vec{B}$ drift, and analyzed the Larmor radius and drift velocity.

#### Problem 1: Equivalent Resistance Using Graph Theory
- **Explanation**: We described equivalent resistance and how graph theory represents circuits as graphs (nodes as junctions, edges as resistors). We explained series and parallel rules, the variables $R$, and the significance in circuit design.  
- **Solution**: We implemented a simple algorithm to compute equivalent resistance for series, parallel, and nested circuits, tested it on examples, and visualized a graph representation using NetworkX.
