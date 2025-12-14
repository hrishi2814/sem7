Here is an **exam-ready list of techniques to reduce underfitting**, written clearly and concisely.

---

# **Techniques to Reduce Underfitting**

Underfitting occurs when the model is **too simple** to learn the underlying patterns.  
To fix underfitting, we need to **increase model complexity** or allow the model to learn more.

---

## **1. Increase Model Complexity**

- Use a more complex model (e.g., deeper neural network, more tree depth).
    
- Increase polynomial degree in polynomial regression.
    

---

## **2. Train for More Time**

- Increase the number of training epochs/iterations.
    
- Reduce early stopping or disable it temporarily.
    

---

## **3. Reduce Regularization**

- Decrease L1/L2 regularization strength (λ).
    
- In neural networks, reduce dropout rate.  
    Too much regularization makes model too simple.
    

---

## **4. Add More Relevant Features**

- Introduce new features that help the model learn.
    
- Use feature engineering (interaction terms, polynomial features).
    

---

## **5. Reduce Noise in Data**

- Clean the dataset (remove wrong or random values).  
    Cleaner data allows the model to learn patterns better.
    

---

## **6. Hyperparameter Tuning**

Examples:

- Increase number of decision tree splits
    
- Increase number of neurons/layers in neural networks
    
- Increase K in KNN? No → decrease K to make model more flexible
    

---

## **7. Use Better Feature Representations**

- Standardize or normalize data when required
    
- Use encoding techniques for categorical features (one-hot, target encoding)
    

---

## **Short Summary for Exams**

Underfitting is reduced by **increasing model complexity**, **training longer**, **reducing regularization**, and **adding useful features** so the model can learn patterns more effectively.

---

If you want, I can also give techniques to reduce **overfitting** so you can write both together.