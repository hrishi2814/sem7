# **Gradient Descent (Detailed Explanation)**

## **Definition**

Gradient Descent is an optimization algorithm used to **minimize a cost function** by updating the model’s parameters (weights and bias) in the direction of the **negative gradient**.

The idea is simple:

- Compute how the cost changes when weights change
    
- Move the weights slightly in the direction that **reduces** the cost
    

---

# **Why Gradient Descent?**

In machine learning, we want to find the parameters that give the **lowest possible error (cost)**.

For Linear Regression, cost function = **Mean Squared Error (MSE)**.

---
![[Pasted image 20251209093004.png]]

# **Types of Gradient Descent**

## 1. **Batch Gradient Descent**

Uses the **entire training dataset** to compute the gradient **before every update**.

### **Steps**

1. Take all training samples
    
2. Compute gradient using whole dataset
    
3. Update weights once per epoch
    

### **Advantages**

- Stable convergence
    
- Smooth path to minimum
    
- Good for small datasets
    

### **Disadvantages**

- Very slow for large datasets
    
- Requires a lot of memory
    
- Not suitable for real-time learning
    

### **Use Case**

- Small or medium-sized datasets
    
- Problems where accuracy > speed
    

---

## 2. **Stochastic Gradient Descent (SGD)**

Updates weights **after every single training example**.

### **Steps**

For each training sample:

1. Compute gradient
    
2. Update weight immediately
    

### **Advantages**

- Very fast
    
- Can escape local minima (because updates are noisy)
    
- Good for large datasets
    

### **Disadvantages**

- Very noisy convergence
    
- Loss function fluctuates
    
- Harder to reach exact minimum
    

### **Use Case**

- Large datasets (millions of samples)
    
- Online learning
    

---

## 3. **Mini-Batch Gradient Descent**

A compromise between Batch and Stochastic.

Dataset is divided into **small batches** (e.g., 32, 64, 128 samples).

### **Steps**

1. Split data into batches
    
2. For each batch:
    
    - Compute gradient
        
    - Update weights
        

### **Advantages**

- Faster than Batch GD
    
- Smoother convergence than SGD
    
- Efficient on GPUs
    
- Best for Deep Learning
    

### **Disadvantages**

- Batch size must be chosen carefully
    
- Still some noise
    

### **Use Case**

- Deep learning (standard method)
    
- Large datasets
    

---

# **Comparison Table (Exam-Friendly)**

|Type|Uses Data|Updates Per Epoch|Speed|Convergence|
|---|---|---|---|---|
|**Batch GD**|Full dataset|1|Slow|Smooth, stable|
|**SGD**|1 sample|n updates|Fast|Very noisy|
|**Mini-Batch**|Small batch (like 32)|n/batch updates|Fast & stable|Best balance|

---

# **Graphical Intuition**

- **Batch GD**: Moves in a straight, smooth path toward minimum
    
- **SGD**: Zig-zag path with noise
    
- **Mini-Batch**: Slight zig-zag but generally smooth
    

---

# **Learning Rate Importance**

If ( \alpha ) is:

- **Too small** → slow convergence
    
- **Too big** → overshoots, may diverge
    

---

# **Final Summary (Short Notes)**

Gradient Descent minimizes cost by moving weights opposite to the gradient.  
Three versions:

- Batch: accurate but slow
    
- Stochastic: fast but noisy
    
- Mini-batch: best trade-off, used in deep learning
    

---
