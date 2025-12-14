## **Bias**

Bias is the error that comes from making the model too simple.  
High bias means the model is **not learning enough** from the data.

**Example:**  
Using a straight line to fit a highly curved pattern.

**Effect:**  
Model makes **systematic errors** → poor performance on training data.

---

## **Variance**

Variance is the error that comes from the model being too sensitive to the training data.  
High variance means the model **learns even noise** in the data.

**Example:**  
A very complex decision tree perfectly fitting training points.

**Effect:**  
Model performs well on training data but poorly on new/unseen data.

---

## **Underfitting**

Underfitting happens when the model is **too simple** and cannot capture the underlying pattern.

**Causes:**

- High bias
    
- Not enough features
    
- Too few parameters
    
- Too short training
    

**Symptoms:**

- Low accuracy on training data
    
- Low accuracy on test data
    

**Solution:**

- Increase model complexity
    
- Reduce regularization
    
- Train longer
    
- Add useful features
    

---

## **Overfitting**

Overfitting happens when the model is **too complex** and learns noise along with the actual pattern.

**Causes:**

- High variance
    
- Too many parameters
    
- Not enough data
    
- Training for too long
    

**Symptoms:**

- High accuracy on training data
    
- Low accuracy on test data
    

**Solution:**

- Reduce model complexity
    
- Use regularization (L1/L2)
    
- Get more data
    
- Use dropout (for neural nets)
    
- Early stopping
    

---

## **Bias–Variance Tradeoff**

There is a balance between bias and variance.

- **High bias → Underfitting**
    
- **High variance → Overfitting**
    
- Good models find the **right balance**: not too simple, not too complex.
    

Graphically:

- Bias decreases as model complexity increases
    
- Variance increases as model complexity increases
    
- Error is minimized at an optimal point in between
    



