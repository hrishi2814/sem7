**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**

DBSCAN is an **unsupervised, density-based clustering algorithm** that groups data points based on **data density**. Unlike k-means, it does **not require the number of clusters in advance** and can identify **arbitrarily shaped clusters** while detecting noise.

---

## Key Concepts

1. **ε (Epsilon)**  
    Radius that defines the neighborhood around a data point.
    
2. **MinPts**  
    Minimum number of points required within ε to form a dense region.
    
3. **Core Point**  
    A point that has at least **MinPts** points (including itself) within ε.
    
4. **Border Point**  
    A point that lies within ε of a core point but has fewer than MinPts neighbors.
    
5. **Noise (Outlier)**  
    A point that is neither core nor border.
    

---

## Algorithm Steps

1. Select an unvisited data point.
    
2. Find all points within ε-neighborhood.
    
3. If the point is a **core point**, create a new cluster.
    
4. Expand the cluster by recursively adding density-reachable points.
    
5. If the point is not a core point, label it as noise (may later become a border point).
    
6. Repeat until all points are visited.
    

---

## Example

Consider GPS locations of people in a city:

- Dense regions correspond to **crowded places** like malls or stations.
    
- Sparse points are treated as **noise**.  
    DBSCAN correctly identifies clusters of arbitrary shapes and ignores isolated points.
    

---

## Advantages

- No need to specify number of clusters.
    
- Detects **noise and outliers** effectively.
    
- Finds **non-spherical clusters**.
    
- Works well with spatial data.
    

---

## Disadvantages

- Struggles with **varying density** clusters.
    
- Sensitive to choice of ε and MinPts.
    
- Less effective in high-dimensional data.
    

---

## Applications

- Geospatial analysis
    
- Image segmentation
    
- Anomaly detection
    
- Customer behavior analysis
    

---

## Comparison with K-Means

|Feature|DBSCAN|K-Means|
|---|---|---|
|Cluster shape|Arbitrary|Spherical|
|Noise handling|Yes|No|
|Number of clusters|Not required|Required|
|Outlier sensitivity|Low|High|

---

## Conclusion

DBSCAN is a powerful clustering algorithm for discovering dense regions and identifying noise, making it ideal for real-world data with irregular cluster shapes and outliers.