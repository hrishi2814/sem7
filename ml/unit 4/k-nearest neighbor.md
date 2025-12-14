# **K-Nearest Neighbor (KNN) – Detailed Explanation**

## **Definition**

K-Nearest Neighbor (KNN) is a **supervised machine learning algorithm** used for **classification and regression**.  
It is a **lazy learning** and **instance-based** method.

KNN predicts the output for a new data point by looking at the **K closest training samples**.

---

# **How KNN Works**

### **Step 1: Choose K**

- K = number of nearest neighbors to consider
    
- Example: K = 3 → look at 3 nearest data points
    

### **Step 2: Calculate Distance**

Find the distance between the new point and all training points using a **distance metric**.

### **Step 3: Select Nearest Neighbors**

Pick the K points with the smallest distance.

### **Step 4: Make Prediction**

- **Classification:** Choose the class that appears most among the K neighbors (majority vote).
    
- **Regression:** Take the **average** of K neighbors.
    

---

# **Importance of Choosing K**

- **K too small (like 1):**
    
    - Very sensitive to noise
        
    - High variance → **overfitting**
        
- **K too large:**
    
    - Boundary becomes smoother
        
    - High bias → **underfitting**
        

Common choice: K = √n (where n = number of samples)

---

# **Distance Metrics in KNN**

### **1. Euclidean Distance (most common)**

```math
  d = \sqrt{\sum (x_i - y_i)^2}  
  ```

### **2. Manhattan Distance**

[  
d = \sum |x_i - y_i|  
]

### **3. Minkowski Distance**

Generalized form:  
[  
d = \left(\sum |x_i - y_i|^p \right)^{1/p}  
]

- p = 1 → Manhattan
    
- p = 2 → Euclidean
    

### **4. Hamming Distance**

- Used for **categorical** or **binary** data
    
- Counts number of mismatches
    

### **5. Cosine Similarity**

- Measures angle between vectors
    
- Used in text mining
    

---

# **Advantages of KNN**

1. **Simple to understand and implement**
    
2. **No training time** (lazy learner)
    
3. Works well for **small datasets**
    
4. Naturally handles **multi-class classification**
    
5. Works with any number of features
    
6. No assumptions about data distribution (non-parametric)
    

---

# **Disadvantages of KNN**

1. **Very slow at prediction time**  
    Must compute distance to all training points.
    
2. **High memory usage**  
    Must store entire training dataset.
    
3. Sensitive to **irrelevant features**  
    Needs feature scaling (min-max or standardization).
    
4. Sensitive to **noise and outliers**.
    
5. Performance decreases with **high-dimensional data** (curse of dimensionality).
    

---

# **Applications of KNN**

- Recommender systems
    
- Pattern recognition
    
- Handwritten digit recognition
    
- Medical diagnosis
    
- Credit risk analysis
    
- Spam detection
    

---

# **Example (For understanding)**

If K = 5 and among the 5 nearest neighbors:

- 3 belong to class A
    
- 2 belong to class B
    

Prediction = **Class A**

---

# **Summary (Short answer for exams)**

K-Nearest Neighbor (KNN) is a supervised learning algorithm that predicts the output of a new instance based on the K closest training samples. It uses distance metrics such as Euclidean, Manhattan, or Minkowski to measure closeness. KNN is simple and effective but slow at prediction time and sensitive to high-dimensional data. It is commonly used for classification, regression, and pattern recognition.

---

If you want, I can also give you a **diagram** to draw in your exam for full marks.