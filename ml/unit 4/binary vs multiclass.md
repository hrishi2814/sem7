
# **Binary vs Multi-Class Classification**

## **1. Binary Classification**

### **Definition**

Binary classification involves predicting **one of two possible classes** (2 categories).

Examples:

- Spam vs Not Spam
    
- Disease vs No Disease
    
- Fraud vs Not Fraud
    
- Yes vs No
    

### **Characteristics**

- Only **two labels**: positive and negative
    
- Uses **sigmoid**, **logistic regression**, **SVM**, **binary decision trees**, etc.
    
- Evaluation metrics: Accuracy, Precision, Recall, F1, ROC-AUC
    

### **Confusion Matrix (2 × 2)**

||Predicted +|Predicted –|
|---|---|---|
|Actual +|TP|FN|
|Actual –|FP|TN|

---

## **2. Multi-Class Classification**

### **Definition**

Multi-class classification involves predicting **one of more than two classes** (3 or more categories).

Examples:

- Classifying images of cats, dogs, horses
    
- Handwritten digit recognition (0–9)
    
- Iris flower dataset (Setosa, Versicolor, Virginica)
    

### **Characteristics**

- K classes where K > 2
    
- Algorithms: Softmax regression, Decision Tree, Random Forest, SVM (one-vs-all), Neural Networks
    
- Evaluation metrics: Macro/Micro Precision, Recall, F1, Confusion Matrix (K × K)
    

### **Confusion Matrix (K × K)**

Rows = Actual classes  
Columns = Predicted classes  
Diagonal values show correct predictions.

---

# **Binary vs Multi-Class (Comparison Table)**

|Feature|Binary Classification|Multi-Class Classification|
|---|---|---|
|**Number of Classes**|2|More than 2|
|**Examples**|Spam/Not Spam|Digit 0–9, animal types|
|**Decision Boundary**|Simple|More complex|
|**Evaluation Metrics**|TP, TN, FP, FN|Macro/micro avg metrics|
|**Confusion Matrix**|2×2|K×K|
|**Output Layer (NN)**|Sigmoid|Softmax|
|**Algorithms**|Logistic Regression, Binary SVM|Softmax SVM, Decision Tree, Random Forest|
|**Handling**|Easier|More computationally expensive|
|**Interpretability**|Easier|Harder|

---

# **Short Exam-Ready Answer**

Binary classification predicts one of two classes, such as yes/no or spam/not spam, using a 2×2 confusion matrix and evaluation metrics like precision, recall, and ROC-AUC. Multi-class classification predicts one of more than two classes, such as digits 0–9, using algorithms like softmax regression or multi-class SVM and a K×K confusion matrix. Multi-class problems are more complex and use macro/micro averaging to evaluate performance.

---

If you want, I can also explain **multi-label classification** (often confused with multi-class).