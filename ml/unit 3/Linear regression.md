
# **Linear Regression (Detailed Explanation)**

![[Pasted image 20251209092646.png]]

# **Types of Linear Regression**

### **1. Simple Linear Regression**

Uses **one independent variable**.

### **2. Multiple Linear Regression**

Uses **two or more independent variables**.

---

# **Goal of Linear Regression**

To find the **best-fit line** that minimizes the difference between actual values and predicted values.

This is done by adjusting weights to minimize an objective function called **Cost Function**.

---



![[Pasted image 20251209092503.png]]

---

![[Pasted image 20251209092549.png]]

---

# **Assumptions of Linear Regression (Important for Exams)**

1. **Linearity**  
    Relationship between features and target must be linear.
    
2. **Independence of errors**  
    Errors should not depend on each other.
    
3. **Homoscedasticity**  
    Constant variance of errors.
    
4. **Normality of residuals**  
    Errors should follow a normal distribution.
    
5. **No multicollinearity** (for multiple LR)  
    Features should not be highly correlated.
    

---

# **Advantages**

- Simple and easy to implement
    
- Fast training and prediction
    
- Works well for linearly related data
    
- Easy to interpret coefficients
    

---

# **Disadvantages**

- Fails if relationship is non-linear
    
- Sensitive to outliers
    
- Assumes independence and constant variance
    
- Multicollinearity can make model unstable
    

---

# **Applications**

- Price prediction (housing, stocks)
    
- Sales forecasting
    
- Risk assessment
    
- Demand estimation
    

---

# **Final Summary (Short Notes)**

Linear Regression is a model that predicts a continuous output using a linear equation. It learns weights by minimizing Mean Squared Error using Gradient Descent. Works well when data shows linear patterns and assumptions hold.

---
