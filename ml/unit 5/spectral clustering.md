**Spectral Clustering**

Spectral clustering is an **unsupervised machine learning** technique that uses **graph theory and linear algebra** to cluster data based on the **eigenvalues (spectrum)** of a similarity matrix. It is especially effective for **non-linearly separable** and complex-shaped clusters.

---

### Key Idea

- Data points are treated as **nodes of a graph**.
    
- Similarity between points is represented as **edges with weights**.
    
- Clustering is performed using the **eigenvectors of the graph Laplacian**.
    

---

![[Pasted image 20251214160144.png]]

---

### Example

Points forming **two concentric circles** cannot be clustered correctly using k-means.  
Spectral clustering separates them effectively by using graph connectivity instead of distance alone.

---

### Advantages

- Handles complex, non-convex cluster shapes.
    
- Works well when clusters are connected but not spherical.
    
- Strong theoretical foundation using graph cuts.
    

---

### Disadvantages

- Computationally expensive (eigen decomposition).
    
- Requires choosing similarity parameters carefully.
    
- Not ideal for very large datasets.
    

---

### Applications

- Image segmentation
    
- Social network analysis
    
- Bioinformatics (gene clustering)
    

---

### Conclusion

Spectral clustering is a powerful clustering technique that transforms data using graph Laplacians, enabling accurate clustering of complex and non-linear data structures.