**Isolation Factor Model (Isolation Forest)**

The **Isolation Factor Model**, commonly known as **Isolation Forest**, is an **unsupervised anomaly (outlier) detection technique** based on the principle that **anomalies are easier to isolate than normal data points**.

---

### Core Idea

- Normal data points are **dense and similar**, so they require many splits to isolate.
    
- Outliers are **few and different**, so they get isolated **quickly**.
    
- Instead of modeling normal behavior, the model **directly isolates anomalies**.
    

---

### Working Principle

1. **Random Subsampling**  
    Randomly select a subset of data.
    
2. **Isolation Trees (iTrees)**
    
    - Build trees by randomly selecting:
        
        - a feature
            
        - a split value
            
    - Recursively split data until each point is isolated.
        
3. **Path Length**
    
    - Path length = number of splits needed to isolate a point.
        
    - **Shorter path → more anomalous**
        
    - **Longer path → normal**
        
4. **Isolation Factor / Anomaly Score**
    
    - Calculated using the **average path length** across all trees.
        
    - Higher isolation factor indicates higher likelihood of being an outlier.
        

---

### Example

In a credit card transaction dataset:

- Normal transactions cluster densely.
    
- Fraudulent transactions are rare and isolated.  
    Isolation Forest detects fraud by isolating these rare points quickly.
    

---

### Advantages

- Efficient for large datasets
    
- No distance or density calculation
    
- Works well in high-dimensional data
    
- Explicitly designed for outlier detection
    

---

### Limitations

- Less interpretable than rule-based methods
    
- Requires tuning number of trees and subsample size
    

---

### Conclusion

The Isolation Factor Model detects outliers by **measuring how easily a data point can be isolated** using random partitioning. Its efficiency and effectiveness make it widely used in **fraud detection, intrusion detection, and anomaly detection tasks**.