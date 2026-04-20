# 🚚 Warehouse Location and Fleet Routing Optimization

This project presents a logistics optimization pipeline that addresses two core problems:

- Warehouse (Depot) placement
- Fleet sizing and delivery route optimization

The solution combines clustering, capacity-aware reassignment, and route optimization using a Genetic Algorithm to simulate a realistic delivery system.

## Objectives
- Group delivery locations into clusters served by individual vehicles
- Ensure that each cluster satisfies vehicle capacity constraints
- Introduce higher-level hub structures for better regional control
- Determine optimal depot placement
- Optimize delivery routes within each cluster (TSP)

## Methodology
The pipeline consists of the following stages:

Data -> Clustering -> Capacity check -> Reassignment -> Hub formation -> Depot assignment -> Route optimization

1. **Clustering**
    - Applied KMeans to group delivery points based on spatial proximity.
    - Number of clusters determined from total demand and vehicle capacity.

2. **Capacity constraint handling**
    - Identified overloaded clusters
    - Reassigned delivery points between clusters within the same hub
    - Created new clusters when necessary

3. **Hub formation**
    - Clusters are grouped into hubs (delivery regions)
    - Enables localized optimization and scalability

4. **Depot placement**
    - Introduced a multi-depot strategy
    - Depots positioned using centroid-based approximation
    - Hubs assigned to the nearest depot

5. **Route optimization**
    - Solved Traveling Salesman Problem (TSP) for each cluster
    - Implemented a Genetic Algorithm
    - Objective: minimize total route distance

---

## 🛠️ Tech Stack
- Python
- Pandas
- NumPy
- Scikit-learn (KMeans)
- Matplotlib / Seaborn
- Custom Genetic Algorithm

## Project Structure

All code and modeling steps are contained in a single file - `Vehicle_routing_optimization.ipynb`.
```
Vehicle_routing_optimization.ipynb/
├── Import Libraries and Data Loading
├── Exploratory Data Analysis
├── Clustering and Logistics Calculations
├── Constraint Handling via Cluster Reassignment and Hub Formation
├── Vehicle Route Optimization via Genetic Algorithm
│ ├── Depot placement
│ ├── Genetic Algorithm
│ └── Visualization of constructed routes
└── Project Conclusion
```

---

## 📊 Key Results
Constructed a full logistics pipeline from raw data to optimized routes.
Generated:
- capacity-feasible clusters
- hub-based delivery structure
- multi-depot allocation
- route sequences for each vehicle

## Limitations
1. Cluster reassignment does not consider spatial distance, leading to mixed geographic regions
2. GA-based routing may produce non-smooth routes (direction switching, inefficiencies)
3. No real-world constraints:
    - road networks
    - travel time
    - traffic conditions

## Future Improvements
1. Distance-aware reassignment - minimize(distance + capacity_penalty)
2. Upgrade to Vehicle Routing Problem (VRP) formulation
3. Multi-objective optimization:
    - distance
    - capacity
    - route smoothness
4. Replace GA with advanced heuristics

---

## 💡 Key Insight
This project can be viewed as a simplified implementation of a multi-depot Vehicle Routing Problem (VRP) with capacity constraints and heuristic optimization.