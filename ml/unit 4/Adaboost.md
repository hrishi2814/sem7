
# **AdaBoost (Adaptive Boosting) – Detailed Explanation**

## **Definition**

AdaBoost is a **boosting ensemble technique** that combines many **weak learners** (usually decision stumps) to form a **strong classifier**.  
It focuses more and more on the misclassified samples during training.

The term **Adaptive** means:

> The algorithm _adapts_ by increasing weights of incorrectly predicted samples so the next model focuses on them.

---

# **Key Idea**

1. Train a weak classifier
    
2. Increase the weight of misclassified samples
    
3. Train next classifier on updated weights
    
4. Combine all classifiers with weighted voting
    

This reduces bias and improves accuracy.

---

# **How AdaBoost Works (Step-by-Step)**

### **1. Initialize weights**

Every training sample is given equal weight initially.

### **2. Train a weak learner**

Most commonly: **Decision stump** (a one-level decision tree).

### **3. Calculate error**

Error = weighted sum of misclassified samples.

### **4. Compute classifier weight (α)**

A classifier with lower error gets higher influence.

![[Pasted image 20251209155147.png]]

### **5. Update sample weights**

- Increase weight of misclassified samples
    
- Decrease weight of correctly classified samples
    

![[Pasted image 20251209155220.png]]

Normalize weights so they sum to 1.

### **6. Repeat**

Train next weak learner with updated weights.

### **7. Final prediction**

Classification: **weighted majority vote**  
Regression: **weighted sum**

---

# **Why AdaBoost Works**

- Focuses on hard-to-learn points
    
- Sequential learning improves the overall model
    
- Weak learners become strong by correcting each other’s mistakes
    

---

# **Example (Simple Understanding)**

1. First stump misclassifies some points
    
2. AdaBoost increases weight of those misclassified points
    
3. Next stump tries harder to classify those points
    
4. After many rounds, the boosted model becomes very accurate
    

---

# **Advantages of AdaBoost**

1. **High accuracy** compared to a single tree
    
2. Works well even with **simple weak learners**
    
3. Less prone to overfitting than other algorithms (with correct parameters)
    
4. Easy to implement
    
5. Automatically selects important features during training
    

---

# **Disadvantages of AdaBoost**

1. **Sensitive to noise and outliers**  
    Because misclassified points get higher weight.
    
2. Can overfit if weak learners are too complex.
    
3. Requires careful tuning of the number of learners.
    
4. Slow when dataset is very large.
    

---

# **Applications of AdaBoost**

- Face detection (one of the earliest applications)
    
- Spam filtering
    
- Fraud detection
    
- OCR (Optical Character Recognition)
    
- Customer churn prediction
    

---

# **Bagging vs Boosting vs AdaBoost (Quick Exam Table)**

|Method|Training Style|Focus|Type of Learners|Risk|
|---|---|---|---|---|
|**Bagging**|Parallel|Reduce variance|Strong trees|Low overfitting|
|**Boosting**|Sequential|Reduce bias|Weak learners|Can overfit|
|**AdaBoost**|Sequential|Focus on misclassified samples|Decision stumps|Sensitive to noise|

---

# **Short Exam-Ready Definition**

AdaBoost (Adaptive Boosting) is a boosting algorithm that combines many weak classifiers into a strong one by iteratively giving more weight to incorrectly classified samples and combining classifiers through weighted voting. It improves accuracy by forcing each new learner to focus on the errors of the previous one.

---

If you want, I can also explain **Gradient Boosting vs AdaBoost** or provide a **diagram** for your exam notes.