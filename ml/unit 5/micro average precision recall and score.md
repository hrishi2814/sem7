
# **Micro Average Precision, Recall, and F1-score**

Micro averaging is used when you want to **give equal importance to each individual sample**, not each class. It aggregates all true positives, false positives, and false negatives across all classes **before** calculating precision and recall.

---



![[Pasted image 20251209164349.png]]


---



![[Pasted image 20251209164407.png]]

---

![[Pasted image 20251209164435.png]]

---

# **Important Concept (Exam Point)**

### **Macro vs Micro**

|Metric Type|What It Averages|Weighting|Use Case|
|---|---|---|---|
|**Macro Average**|Average of per-class metrics|All classes equal|Good for imbalanced datasets|
|**Micro Average**|Global TP/FP/FN across all classes|All samples equal|Good when classes have similar importance|

---

![[Pasted image 20251209164508.png]]

---

# **Short Exam-Ready Definition**

Micro average aggregates all true positives, false positives, and false negatives across classes before computing precision, recall, and F1-score. It gives equal importance to each sample and is useful for multi-class problems with balanced datasets.

---

