**K-Medoids Clustering (Detailed Explanation)**

**K-Medoids** is an **unsupervised clustering algorithm** similar to k-means, but instead of using the mean of points as the cluster center, it uses an **actual data point (medoid)** as the center of each cluster. This makes it more **robust to noise and outliers**.

---

## Key Idea

- A **medoid** is the most centrally located data point in a cluster.
    
- Clustering is done by **minimizing the total dissimilarity** between points and their assigned medoid.
    

---
![[Pasted image 20251214160649.png]]

---
## Algorithm (PAM: Partitioning Around Medoids)

### Step 1: Initialization

- Randomly select **k data points** as initial medoids.
    

### Step 2: Assignment

- Assign each data point to the **nearest medoid** based on distance.
    

### Step 3: Update Medoids

- For each cluster, try swapping the medoid with a non-medoid point.
    
- Compute total cost after swap.
    
- If cost decreases, accept the swap.
    

### Step 4: Repeat

- Repeat assignment and update steps until **no further improvement** is possible.
    

---

## Example

Suppose we want to cluster customers based on **age and annual spending**.

- K-means may place a center at a point where no customer exists.
    
- K-medoids selects an **actual customer** as the cluster representative, making interpretation easier and reducing effect of outliers.
    

---

## Distance Metrics

K-medoids supports **any distance metric**, such as:

- Euclidean distance
    
- Manhattan distance
    
- Hamming distance
    

This makes it more flexible than k-means.

---

## Advantages

- Robust to **outliers and noise**
    
- Works with **non-Euclidean distances**
    
- Cluster centers are **real data points**
    
- More interpretable than k-means
    

---

## Disadvantages

- **Computationally expensive** ( O(k(n-k)^2) )
    
- Slower than k-means
    
- Not suitable for very large datasets
    

---

## K-Means vs K-Medoids

|Feature|K-Means|K-Medoids|
|---|---|---|
|Cluster center|Mean (virtual point)|Actual data point|
|Sensitivity to outliers|High|Low|
|Distance metrics|Mostly Euclidean|Any metric|
|Speed|Faster|Slower|

---

## Applications

- Market segmentation
    
- Medical data analysis
    
- Fraud detection
    
- Social network clustering
    

---

## Conclusion

K-medoids is a powerful clustering algorithm that improves robustness by using real data points as cluster centers. While computationally heavier than k-means, it is preferred when data contains **outliers** or **non-numeric distance measures**.