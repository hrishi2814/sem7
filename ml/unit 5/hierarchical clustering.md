**Hierarchical Clustering**

Hierarchical clustering is an **unsupervised learning** technique used to group similar data points into clusters arranged in a **tree-like structure** called a **dendrogram**. Unlike k-means, it does not require the number of clusters to be specified in advance.

---

### Types of Hierarchical Clustering

1. **Agglomerative (Bottom-Up) Clustering**
    

- Starts with each data point as an individual cluster.
    
- Repeatedly merges the two closest clusters until only one cluster remains.
    
- Most commonly used approach.
    

2. **Divisive (Top-Down) Clustering**
    

- Starts with all data points in a single cluster.
    
- Recursively splits clusters until each point forms its own cluster.
    
- Computationally more expensive and less common.
    

---

### Steps in Hierarchical Clustering (Agglomerative)

1. Treat each data point as a separate cluster.
    
2. Compute the distance matrix between all clusters.
    
3. Merge the two closest clusters.
    
4. Update the distance matrix.
    
5. Repeat until one cluster remains.
    
6. Cut the dendrogram at a desired level to obtain clusters.
    

---

### Linkage Methods

Linkage defines how distance between clusters is computed:

- **Single Linkage:** Minimum distance between points  
    (may cause chaining effect)
    
- **Complete Linkage:** Maximum distance between points  
    (produces compact clusters)
    
- **Average Linkage:** Average distance between all points
    
- **Ward’s Method:** Minimizes variance within clusters
    

---

### Example

Consider student data based on **marks and attendance**.  
Hierarchical clustering groups students with similar performance together.  
By cutting the dendrogram at a chosen height, clusters such as **high**, **medium**, and **low performers** can be obtained.

---

### Advantages

- No need to predefine number of clusters.
    
- Produces a visual dendrogram for interpretation.
    
- Works well for small datasets.
    

---

### Disadvantages

- High time and space complexity ((O(n^2))).
    
- Sensitive to noise and outliers.
    
- Not suitable for very large datasets.
    

---

### Conclusion

Hierarchical clustering is a powerful technique for exploratory data analysis, especially when cluster structure and relationships need to be visualized and interpreted clearly.