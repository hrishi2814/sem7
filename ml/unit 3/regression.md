## **What is Regression? (Brief)**

Regression is a machine learning technique used to **predict a continuous numerical value** based on input features.  
It finds the **relationship between independent variables (X)** and a **dependent variable (Y)**.

**Example:** Predicting house prices, temperature, salary, etc.

---

## **Ridge Regression**

Ridge Regression is a type of linear regression that uses **L2 regularization**.  
It adds a penalty equal to the **square of the magnitude of coefficients**.

**Penalty term:**  
[  \lambda \sum w_i^2  ]

**Uses / Advantages:**

- Reduces model complexity
    
- Prevents overfitting
    
- Does **not** reduce coefficients to zero (keeps all features)
    

---

## **Lasso Regression**

Lasso Regression uses **L1 regularization**.  
It adds a penalty equal to the **absolute value of coefficients**.

**Penalty term:**  
[  \lambda \sum |w_i|  ]

**Uses / Advantages:**

- Prevents overfitting
    
- Can make some coefficients **exactly zero**
    
- Helps in **feature selection**
    

---

## **Key Difference (Exam Point)**

|Method|Regularization|Effect|Feature Selection|
|---|---|---|---|
|**Ridge**|L2 (squared weights)|Shrinks weights but doesn’t remove them|❌ No|
|**Lasso**|L1 (absolute weights)|Can shrink some weights to zero|✔️ Yes|

---

