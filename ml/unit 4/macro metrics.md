
# **Multi-Class Classification Evaluation (Macro Averages)**

When you have **more than two classes**, you compute **Precision, Recall, and F1-score for each class separately**, and then take an **average**.

---

# 1. **Precision for Class i**

Treat **Class i** as "Positive" and all other classes as "Negative" (one-vs-rest method).

![[Pasted image 20251209155409.png]]

---

# 2. **Recall for Class i**

![[Pasted image 20251209155423.png]]

---

# 3. **F1-score for Class i**

![[Pasted image 20251209155435.png]]

---

# **Macro Average**

Macro = **Unweighted mean** of the metric across all classes.

### **Macro Average Precision**

![[Pasted image 20251209155455.png]]

### **Macro Average Recall**

![[Pasted image 20251209155512.png]]

### **Macro Average F1-score**

![[Pasted image 20251209155529.png]]

Where K = number of classes.

---

# **Important Points (Exam-Safe)**

- **Macro average treats all classes equally**, even if some classes have very few samples.
    
- It is useful when **class imbalance exists**, because it does not get dominated by majority classes.
    
- Macro average is different from **micro average**, which aggregates all TP, FP, FN globally before computing scores.
    

---

# **Small Example (Very Useful for Exams)**

![[Pasted image 20251209155603.png]]


---

If you want, I can take a **real confusion matrix**, calculate **all macro metrics** step-by-step, and give you a solved numerical example.