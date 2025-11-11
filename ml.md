## 🧠 ML Practical - 1: Uber Fare Amount Prediction (Regression)

### 1. Uber database details

A typical Uber fare dataset contains information about individual trips. Key columns (features) usually include:

- `key` or `trip_id`: A unique identifier for the trip.
    
- `pickup_datetime`: The date and time when the ride started.
    
- `pickup_longitude`, `pickup_latitude`: GPS coordinates for the pickup location.
    
- `dropoff_longitude`, `dropoff_latitude`: GPS coordinates for the dropoff location.
    
- `passenger_count`: The number of passengers.
    
- `fare_amount`: The cost of the ride (this is the **target variable** we want to predict).
    

### 2. Details of features and shape of database

- **Features (Columns):** These are the independent variables (like `pickup_latitude`, `passenger_count`) used to make a prediction.
    
- **Target (Output):** This is the dependent variable (like `fare_amount`) that you are trying to predict.
    
- **Shape:** This refers to the dimensions of the dataset, expressed as **(rows, columns)**. For example, a shape of (100000, 7) means the dataset has 100,000 rows (trips) and 7 columns (features).
    

### 3. Preprocessing steps- null values

- **Null Values Identification:** Finding empty or missing entries in the dataset (often shown as `NaN`). Models cannot process these.
    
- **Filling (Imputation):** We must replace them.
    
    - **Mean:** Use the average value of the column (e.g., `df['column'].mean()`). Best for data that is normally distributed (a bell curve).
        
    - **Median:** Use the middle value of the column (e.g., `df['column'].median()`). Best for data that is **skewed** (has many outliers), as the median is not affected by extreme values.
        
    - You can also **drop** rows with null values, but only if you have a very large dataset and the missing data is a small percentage.
        

### 4. What are outliers, identifying outliers, removal of outliers

- **Outliers:** Data points that are significantly different from other observations. They can be due to errors (e.g., a latitude of 200) or be genuine (e.g., a $1000 fare for a very long trip). They can skew the model's training.
    
- **Identifying Outliers:**
    
    - **Box Plot:** A visual tool. Points falling outside the "whiskers" are potential outliers.
        

![Image of a box plot with outliers](https://encrypted-tbn1.gstatic.com/licensed-image?q=tbn:ANd9GcRB9l3FnA8hpRS6zznVerAPDhrDbxnSQvy3s-3HA37F0odvLXxL_aU-r51zhv-ecAzDPnrgmYfk2L210sOBKD4jXzT_NuB5ZueQ18clZu0iyS1XlKM)

Shutterstock

```
* **IQR (Interquartile Range) Method:** A statistical method.
    1.  Find $Q_1$ (the 25th percentile).
    2.  Find $Q_3$ (the 75th percentile).
    3.  Calculate $IQR = Q_3 - Q_1$.
    4.  The "fences" are $Q_1 - 1.5 \times IQR$ (lower) and $Q_3 + 1.5 \times IQR$ (upper).
    5.  Any data point outside these fences is considered an outlier.
```

- **Removal:** You can filter the dataset to remove these rows, e.g., `df = df[df['fare_amount'] < 100]`.
    

### 5. Scaling - what is it, necessity, how to implement

- **What is it:** The process of transforming numerical features to a common scale.
    
- **Necessity:** Many ML algorithms (like Linear Regression, SVM, KNN) are sensitive to the _magnitude_ of features. A feature with a large range (e.g., `distance` from 0 to 100) might dominate a feature with a small range (e.g., `passenger_count` from 1 to 5), leading to poor performance. Scaling ensures all features contribute equally.
    
- **Implementation (Python `sklearn`):**
    
    - **StandardScaler:** Transforms data to have a mean of 0 and standard deviation of 1. (Most common).
        
    - **MinMaxScaler:** Rescales data to a specific range, usually [0, 1].
        

### 6. Train test split, what is it, how to implement, what is cross validation

- **Train Test Split:** The process of dividing your dataset into two parts:
    
    - **Training Set (e.g., 80%):** The data the model _learns_ from.
        
    - **Test Set (e.g., 20%):** The data the model is _evaluated_ on. This data is "unseen" by the model during training.
        
- **Why:** This is crucial to check for **overfitting**. If a model performs perfectly on training data but poorly on test data, it has only _memorized_ the training set, not _learned_ the general pattern.
    
- Implementation: from sklearn.model_selection import train_test_split
    
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
    
- **Cross Validation (CV):** A more robust evaluation method. Instead of one split, **K-Fold CV** splits the data into 'K' (e.g., 5 or 10) "folds." It then trains and tests the model K times, using a different fold as the test set each time. The final performance is the average of all K runs. This gives a more reliable measure of model performance.
    

### 7. Algorithms used

- **Linear Regression (LR):** A simple algorithm that finds a "best-fit" line to describe the relationship between the features and the target.
    
- **Random Forest (RF):** A more complex, powerful algorithm that builds hundreds of "decision trees" and averages their predictions.
    

### 8. All details of LR

- **Linear vs. Logistic Regression:**
    
    - **Linear Regression:** Predicts a **continuous value** (e.g., fare amount, price, temperature).
        
    - **Logistic Regression:** Predicts a **probability** that is then used for **classification** (e.g., Spam/Not Spam, Yes/No). It uses a sigmoid function to "squash" the output between 0 and 1.
        
- **Classification vs. Regression:**
    
    - **Regression:** The output is a number (e.g., 50.75). The problem is "How much?"
        
    - **Classification:** The output is a category (e.g., "Spam", "Class B"). The problem is "Which one?"
        

### 9. What is Random forest, drawbacks of decision tree, need of random forest, bagging boosting

- **Random Forest (RF):** An **ensemble** algorithm. It trains many individual **Decision Trees** on different random subsets of the data and features. The final prediction is the average (for regression) or majority vote (for classification) of all the trees.
    
- **Drawbacks of Decision Tree:** A single decision tree is highly prone to **overfitting**. It will keep splitting branches to perfectly fit the training data, capturing noise instead of the underlying trend.
    
- **Need for Random Forest:** By combining hundreds of trees (each one "weak" and slightly overfit to different data), RF averages out the noise and errors, resulting in a robust, accurate, and generalized model.
    
- **Bagging (Bootstrap Aggregating):** This is the technique RF uses. It involves training each model (tree) on a random sample (a "bootstrap" sample) of the training data, drawn _with replacement_.
    
- **Boosting:** A different ensemble technique (e.g., XGBoost, AdaBoost). It builds trees **sequentially**, where each new tree's job is to correct the errors made by the previous trees.
    

### 10. What is haversine distance, why haversine

- **Haversine Distance:** A formula that calculates the shortest distance between two points on the surface of a **sphere** (like the Earth) using their latitude and longitude.
    
- **Why Haversine:**
    
    - **Not Euclidean:** Euclidean distance ($sqrt((x_2-x_1)^2 + (y_2-y_1)^2)$) calculates the straight-line distance on a **flat plane**. This is very inaccurate for GPS coordinates because the Earth is curved.
        
    - **Not Hamming:** Hamming distance is used for comparing strings, measuring how many characters are different. It is completely irrelevant for geographical coordinates.
        

### 11. Use of heat map and explanation about correlation of features

- **Correlation:** A statistical measure (from -1 to +1) that shows how strongly two features are related.
    
    - **+1:** Perfect positive correlation (as X increases, Y increases).
        
    - **0:** No correlation.
        
    - **-1:** Perfect negative correlation (as X increases, Y decreases).
        
- **Heatmap:** A visual representation of this correlation matrix. It uses colors (e.g., dark red for +1, dark blue for -1) to show the relationships between all pairs of features at a glance. It's excellent for identifying which features are strongly related to the target (`fare_amount`) and which features are redundant (highly correlated with each other).
    

### 12. Use of all libraries and packages

- `pandas`: For loading and manipulating data (DataFrames).
    
- `numpy`: For numerical operations (math, arrays).
    
- `sklearn.model_selection.train_test_split`: To split the data.
    
- `sklearn.preprocessing.StandardScaler`: To scale data.
    
- `sklearn.linear_model.LinearRegression`: The LR model.
    
- `sklearn.ensemble.RandomForestRegressor`: The RF model.
    
- `sklearn.metrics`: To access performance metrics.
    
    - `mean_squared_error` (MSE)
        
    - `r2_score` (R2)
        

### 13. What is performance metrics

- **MSE (Mean Squared Error):** The average of the _squared_ errors. It heavily penalizes large errors.
    
- **RMSE (Root Mean Squared Error):** The square root of MSE. This is the most common metric for regression as it is interpretable in the _same units_ as the target (e.g., an RMSE of 5.0 means the model is, on average, wrong by about $5.00).
    
- **MAE (Mean Absolute Error):** The average of the _absolute_ errors. It's less sensitive to outliers than MSE/RMSE.
    
- **R2 Score (Coefficient of Determination):** A value between 0 and 1 that measures the _proportion of the variance_ in the target variable that is explained by the model. An R2 of 0.75 means the model explains 75% of the "signal" in the data. Higher is better.
    
- **Adjusted R2 Score:** A modified R2 that _penalizes_ you for adding useless features. R2 will always increase if you add more features, but Adjusted R2 will only increase if the new feature _actually improves_ the model.
    

### 14. Linear Regression equation for multidimensional data

For one feature: $y = \beta_0 + \beta_1x_1$

For multiple features (multidimensional):

$$y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \beta_3x_3 + ... + \beta_nx_n + \epsilon$$

Where:

- $y$ is the predicted value (e.g., fare).
    
- $\beta_0$ is the intercept (the base fare, when all features are 0).
    
- $\beta_1, \beta_2, ... \beta_n$ are the coefficients (the "weight" or importance) for each feature.
    
- $x_1, x_2, ... x_n$ are the feature values (e.g., distance, passenger_count).
    
- $\epsilon$ is the error term.
    

### 15. What is best fit line

In Linear Regression, this is the line (or hyperplane in multi-dimensions) that **minimizes the sum of the squared residuals**. A "residual" is the vertical distance between an actual data point and the line. This method is called "Ordinary Least Squares" (OLS).

![Image of a linear regression best fit line](https://encrypted-tbn3.gstatic.com/licensed-image?q=tbn:ANd9GcT1jua9L5mLfA0bfp0-MNcXiMgktmTRL3YnxwdjISz4l92JyhPhWS9mFC1ywzOuCn4rvNEd9aFk7NKqJ80esZhzz-6Q26DC5-sFikQaR3CAi9OCxsI)

Shutterstock

### 16. What is dependent and independent parameter

- **Independent Parameter (or Variable, Feature):** The **input** to the model, which you use to make a prediction (e.g., `distance`, `time_of_day`).
    
- **Dependent Parameter (or Variable, Target):** The **output** you are trying to predict (e.g., `fare_amount`). Its value _depends_ on the independent variables.
    

### 17. Theoretical concepts

- **AI (Artificial Intelligence):** The broad concept of creating "intelligent" machines that can perform tasks that typically require human intelligence.
    
- **ML (Machine Learning):** A **subset of AI**. It's the process of "training" a machine by feeding it data and letting it learn patterns, rather than explicitly programming the rules.
    
- **Supervised Learning:** Training a model on a **labeled dataset** (input-output pairs). The model's job is to learn the mapping from input (X) to output (y). (e.g., Regression, Classification).
    
- **Unsupervised Learning:** Training a model on an **unlabeled dataset**. The model's job is to find hidden structures or patterns in the data (e.g., Clustering, Dimensionality Reduction).
    
- **Model Training:** The process of feeding the training data to the algorithm (e.g., Linear Regression) so it can find the optimal parameters (e.g., the $\beta$ coefficients) that minimize the error (e.g., MSE).
    
- **Actual and Predicted Output:**
    
    - **Actual:** The true value from the dataset (e.g., the `fare_amount` was $12.50).
        
    - **Predicted:** The model's guess (e.g., the model predicted $12.75). The difference is the error.
        
- **Bias-Variance Tradeoff:**
    
    - **Bias:** The error from a model's simplifying assumptions. High bias = **Underfitting** (the model is too simple, e.g., using a straight line for a complex curve).
        
    - **Variance:** The error from a model's sensitivity to small changes in training data. High variance = **Overfitting** (the model is too complex; it "memorized" the training data noise).
        
- **Underfit:** High bias, low variance. Poor performance on _both_ training and test data.
    
- **Overfit:** Low bias, high variance. Great performance on training data, poor performance on test data.
    
- **Good Fit (Generalized):** Low bias, low variance. Good performance on _both_ training and test data. This is the goal.
    

---

## 🔒 ML Practical - 2: Classification of Email as Spam or not Spam

### 1. Email database details - features

For spam classification, the dataset is typically a matrix where:

- **Rows:** Each row is a single email.
    
- **Columns (Features):** These are numerical representations of the email content. A common method is **"Bag of Words"** or **"TF-IDF"**, where each column represents the _frequency_ or _importance_ of a specific word (e.g., "free", "money", "report", "viagra").
    
- **Target:** A binary column (0 for "Not Spam" / "Ham", 1 for "Spam").
    

### 2. What is one hot encoding

**One-Hot Encoding (OHE)** is a technique to convert **categorical variables** into a numerical format. It creates a new binary (0 or 1) column for each unique category.

- Example: `Color = [Red, Green, Blue]`
    
- `Red` becomes `[1, 0, 0]`
    
- `Green` becomes `[0, 1, 0]`
    
- Blue becomes [0, 0, 1]
    
    As your note says: if the dataset already provides word frequencies (which are numerical), you do not need OHE. You would only need it if a feature was categorical, e.g., Email_Provider = [gmail, yahoo, hotmail].
    

### 3. Concepts of Preprocessing, scaling, train test split

These are the same as in Practical 1. **Scaling** is extremely important for both KNN and SVM, as they are "distance-based" algorithms and are highly sensitive to features with different ranges.

### 4. Algorithms used detailed understanding - KNN and SVM

- **KNN (K-Nearest Neighbors):** A simple, "lazy" algorithm. To classify a new email, it finds the 'K' (e.g., K=5) _closest_ emails to it in the training data (based on their feature vectors). It then takes a **majority vote** of those 5 neighbors. If 4 are "Spam" and 1 is "Ham", the new email is classified as "Spam".
    
- **SVM (Support Vector Machine):** A powerful classification algorithm. It finds the **optimal hyperplane** (a line or plane) that best separates the two classes (Spam vs. Not Spam) in the high-dimensional feature space. It does this by maximizing the **margin** (the distance) between the hyperplane and the closest data points (the "support vectors") from each class.
    

### 5. Difference in KNN and K means

|**Feature**|**KNN (K-Nearest Neighbors)**|**K-Means**|
|---|---|---|
|**Type**|**Supervised** (Classification)|**Unsupervised** (Clustering)|
|**Goal**|Predicts a class for a new data point.|Finds natural groups (clusters) in data.|
|**Data**|Needs **labeled** data (X and y).|Only needs **unlabeled** data (X).|
|**'K'**|Number of _neighbors_ to poll.|Number of _clusters_ to create.|

### 6. Difference in classification and clustering

- **Classification (Supervised):** You have pre-defined labels (e.g., Spam, Not Spam). The goal is to learn a rule to assign new data to these _known_ labels.
    
- **Clustering (Unsupervised):** You have _no_ labels. The goal is to _discover_ hidden groupings in the data. You don't know what the groups mean until you inspect them.
    

### 7. How to choose correct/ optimum value of k (in KNN)

You use **cross-validation**. You test a range of 'K' values (e.g., K=1, 3, 5, ... 21) and see which K value results in the highest performance (e.g., best accuracy or F1-score) on the validation data.

### 8. What is elbow method, explain

The **Elbow Method** is used for **K-Means** (not KNN) to find the optimal number of clusters (K).

1. You run K-Means for a range of K values (e.g., K=1 to 10).
    
2. For each K, you calculate the **inertia** (or WCSS - Within-Cluster Sum of Squares). This is the sum of squared distances of samples to their closest cluster center.
    
3. You plot K vs. Inertia. The plot will look like an arm.
    
4. The "elbow" is the point where the inertia stops decreasing rapidly. This point is considered the optimal K, as adding more clusters beyond this point gives diminishing returns.
    

### 9. SVM as a classifier and regressor

- **SVM Classifier (SVC):** Finds a hyperplane to _separate_ classes.
    
- **SVM Regressor (SVR):** Finds a hyperplane, but fits a "tube" (defined by a margin $\epsilon$) around it. It tries to fit as many data points as possible _inside_ this tube. It's used for continuous value prediction (regression).
    

### 10. How to classify data which is non linear using SVM

Using the **Kernel Trick**. SVM can use a "kernel" to project the data from its original, non-linear feature space into a much **higher-dimensional space** where the data _becomes_ linearly separable.

### 11. What is RBF radial basis function

The **RBF kernel** is the most popular kernel for SVM. It's a non-linear kernel that can create complex, non-linear decision boundaries. It essentially maps data into an _infinite_-dimensional space. It's the default choice for SVM when you don't know the data structure.

### 12. What is the performance metrics used

For classification, especially with imbalanced data (like spam), **Accuracy** is not enough. We use:

- **Confusion Matrix**
    
- **Precision**
    
- **Recall**
    
- **F1-Score**
    

### 13. What is confusion matrix

A table that summarizes a classification model's performance by showing the counts of correct and incorrect predictions for each class.

### 14. Details of TP, TN, FP, FN

Let's assume **Positive = Spam**, **Negative = Not Spam (Ham)**.

- **TP (True Positive):** Actual: Spam, Predicted: Spam. (Correctly caught spam).
    
- **TN (True Negative):** Actual: Ham, Predicted: Ham. (Correctly identified good email).
    
- **FP (False Positive):** Actual: Ham, Predicted: Spam. (**Type I Error**. This is **BAD** - a good email lands in the spam folder).
    
- **FN (False Negative):** Actual: Spam, Predicted: Ham. (**Type II Error**. This is annoying - spam gets into your inbox).
    

### 15. What is precision, recall, F - score, what is beta in F score

- **Precision:** "Of all emails we _predicted_ as Spam, what percentage was _actually_ Spam?"
    
    - $Precision = \frac{TP}{TP + FP}$
        
    - High precision means a low False Positive (FP) rate.
        
- **Recall:** "Of all _actual_ Spam emails, what percentage did we _catch_?"
    
    - $Recall = \frac{TP}{TP + FN}$
        
    - High recall means a low False Negative (FN) rate.
        
- **F1-Score:** The **harmonic mean** of Precision and Recall. It provides a single score that balances both. Use it when both FPs and FNs are important.
    
    - $F_1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}$
        
- **Beta in F-score ($F_\beta$):** This is a generalized F-score. The $\beta$ parameter controls the trade-off.
    
    - $\beta = 1$: This is the F1-Score (Precision and Recall are equally important).
        
    - $\beta > 1$ (e.g., $F_2$): Gives _more_ weight to Recall.
        
    - $\beta < 1$ (e.g., $F_{0.5}$): Gives _more_ weight to Precision.
        

### 16. What is macro and micro precision or recall

These are used in **multi-class** classification (e.g., classifying news as Sports, Politics, or Tech).

- **Macro Average:** Calculate the metric (e.g., Precision) for _each class_ independently, then take the unweighted average. This treats all classes equally, regardless of how many samples they have.
    
- **Micro Average:** Calculate the metric globally by summing all individual TPs, FPs, and FNs across all classes. This gives more weight to classes with more samples.
    

### 17. When to use F score

Use the F1-Score when you have an **imbalanced dataset** (e.g., 99% Ham, 1% Spam). In this case, a model could get 99% accuracy by just predicting "Ham" every time. The F1-score will be very low for such a model and will give a much better sense of its true performance.

### 18. Under what conditions precision or recall would be significant

- **Prioritize Precision** when False Positives are very costly.
    
    - **Spam Filtering:** You _never_ want a good email to go to spam (high FP cost).
        
    - **Legal:** Convicting an innocent person (FP) is worse than letting a guilty person go free (FN).
        
- **Prioritize Recall** when False Negatives are very costly.
    
    - **Medical Diagnosis:** Missing a disease (FN) is far worse than a false alarm (FP).
        
    - **Fraud Detection:** Missing a fraudulent transaction (FN) is the main problem.
        

### 19. What is error and accuracy

- **Accuracy:** The percentage of _all_ predictions that were correct.
    
    - $Accuracy = \frac{TP + TN}{Total \ Population}$
        
- **Error Rate:** The percentage of _all_ predictions that were wrong.
    
    - $Error = \frac{FP + FN}{Total \ Population} = 1 - Accuracy$
        

### 20. Is the dataset balanced?

A dataset is **balanced** if all classes have a roughly equal number of samples. Most real-world datasets (like spam, fraud, or medical) are **imbalanced**.

---

## 📉 ML Practical - 3: Gradient Descent Algorithm

### 1. What is Gradient descent algorithm

Gradient Descent is the core **optimization algorithm** used in most of machine learning. Its goal is to find the **minimum** of a function (like a Cost Function). It works by:

1. Starting at a random point.
    
2. Calculating the **gradient** (the slope) at that point.
    
3. Taking a small "step" in the **opposite** direction of the gradient (i.e., downhill).
    
4. Repeating steps 2-3 until it reaches the bottom (the minimum).
    

### 2. Explain the expression $y = (x+3)^2$

- **Goal:** Find the value of $x$ that gives the minimum value of $y$.
    
- **Cost Function:** $J(x) = (x+3)^2$.
    
- **Gradient:** The derivative of the cost function with respect to $x$:
    
    - $\frac{dJ}{dx} = 2(x+3) \cdot 1 = 2(x+3)$
        
- **Algorithm (Update Rule):** The new value of $x$ is the old value, minus a step in the downhill direction.
    
    - $x_{new} = x_{old} - \alpha \cdot \frac{dJ}{dx}$
        
    - **$x_{new} = x_{old} - \alpha \cdot [2(x_{old}+3)]$** (where $\alpha$ is the learning rate).
        

### 3. What is the global minima or local minima value for $y = (x+3)^2$

- The minimum possible value for $y$ is **0**.
    
- This occurs when $x+3 = 0$, which means **$x = -3$**.
    
- This function is **convex** (a perfect bowl shape), so it has only one minimum. This minimum is the **global minimum**.
    

### 4. In general what is global and local minima

- **Local Minimum:** A point that is lower than all of its _immediate neighbors_.
    
- **Global Minimum:** The _absolute lowest point_ across the entire function.
    
- A complex, non-convex function can have many local minima that "trap" the algorithm, but only one global minimum.
    

### 5. What is cost function

A function that measures the **error** or "cost" of the model. For example, **MSE** is the cost function for Linear Regression. The goal of training is to find the model parameters (e.g., $\theta_1$) that **minimize** this cost function.

### 6. How to choose the optimum value of theta 1

You _don't_ choose the optimum value of $\theta_1$ (a model parameter or weight). The **Gradient Descent algorithm's entire job is to _find_ it**. You just choose a _starting_ value for $\theta_1$, and the algorithm iteratively updates it until it finds the optimal one that minimizes the cost.

### 7. What is learning rate

The **learning rate ($\alpha$)** is a hyperparameter that controls the **size of the step** you take at each iteration of Gradient Descent.

### 8. What is the optimum value of learning rate

There is no single "optimum" value. It's a critical hyperparameter you must **tune** (find by experimentation). Common values to try are 0.1, 0.01, 0.001.

### 9. What happens if the value of learning rate is too large or too small

- **Too Large:** The algorithm will "overshoot" the minimum. It will bounce back and forth wildly and **fail to converge**, or even diverge (the cost will get _worse_).
    
- **Too Small:** The algorithm will converge, but it will be **extremely slow**, requiring many, many iterations to reach the minimum.
    

### 10. What is stochastic and batch gradient descent

- **Batch Gradient Descent:** Calculates the gradient using the **entire** training dataset for one step. It's very accurate but computationally _very slow_ on large datasets.
    
- **Stochastic Gradient Descent (SGD):** Calculates the gradient using **one single** training sample at a time. It's much faster, but the path to the minimum is "noisier" (it bounces around a lot).
    
- **Mini-Batch Gradient Descent:** The compromise. Calculates the gradient using a small "batch" (e.g., 32 or 64 samples) at a time. This is the **most common method** used in deep learning.
    

### 11. What do you mean by gradient

The gradient is a vector (a list of numbers) containing the **partial derivatives** of the cost function with respect to each parameter. It points in the direction of the **steepest ascent** (the "uphill" direction). We move in the _negative_ gradient's direction to go downhill.

### 12. Explain the concave shape curve obtained

The curve for $y=(x+3)^2$ is **convex** (a U-shape or bowl-shape), not concave (an n-shape or upside-down bowl).

- **X-axis:** The parameter $x$.
    
- **Y-axis:** The Cost $J(x)$ (or $y$).
    
- **Minima:** The very bottom of the bowl, at $x = -3$.
    
- **How it reaches the minimum:**
    
    - **If you start on the right side** (e.g., $x=5$): The gradient $2(5+3)$ is **positive** (slope is uphill to the right). The algorithm moves in the negative direction (to the **left**), toward the minimum.
        
    - **If you start on the left side** (e.g., $x=-10$): The gradient $2(-10+3)$ is **negative** (slope is uphill to the left). The algorithm moves in the negative-gradient direction (to the **right**), toward the minimum.
        

---

## 💻 ML Practical - 4: Bank Customer Churn (Deep Learning)

### 1. Details of dataset- its features, shape etc

The dataset typically contains customer information from a bank.

- **Features (X):** `CreditScore`, `Geography` (e.g., France, Spain), `Gender`, `Age`, `Tenure` (years with bank), `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`.
    
- **Target (y):** `Exited` (1 if the customer left/churned, 0 if they stayed).
    
- **Shape:** e.g., (10000, 11), meaning 10,000 customers and 11 features (including the target).
    

### 2. Choice of x- input features and y- output or target feature

- **X (Input):** All the features _except_ `Exited` and non-predictive features like `CustomerID` or `Surname`.
    
- **y (Output):** The `Exited` column. This is what we are trying to predict.
    

### 3. Is feature engineering implemented, if no why

**Yes, it is absolutely required.** The model cannot understand text.

- Categorical features like `Geography` (France, Spain, Germany) and `Gender` (Male, Female) must be converted to numbers.
    
- `Gender` can be **Label Encoded** (0 for Female, 1 for Male).
    
- `Geography` must be **One-Hot Encoded** because there is no order (e.g., France=[1,0,0], Spain=[0,1,0], Germany=[0,0,1]).
    
- All features must also be **Scaled** (e.g., with `StandardScaler`) for the ANN to train properly.
    

### 4. What are Deep Learning algorithms

Deep Learning (DL) is a subfield of ML that uses **Artificial Neural Networks (ANNs)**—algorithms inspired by the structure of the human brain. "Deep" refers to networks that have _multiple layers_ (at least one hidden layer).

### 5. When and why is DL preferred over ML

- **When:** DL is preferred when you have **massive amounts of data** (e.g., millions of images) and for **unstructured data** (images, audio, text).
    
- **Why:** Traditional ML (like SVM, RF) relies on "feature engineering" (you telling the model what's important). DL models can _learn_ the important features and complex patterns _automatically_ from the raw data. On tabular data (like the bank dataset), DL and ML (like XGBoost) are often competitive.
    

### 6. What are various DL networks

- **ANN (Artificial Neural Network) / MLP (Multi-Layer Perceptron):** The "standard" network, made of densely-connected layers. Best for **tabular data** (like the bank dataset).
    
- **CNN (Convolutional Neural Network):** Specialized for **image** and grid-data. Uses "convolution" and "pooling" layers to "see" patterns, edges, and shapes.
    
- **RNN (Recurrent Neural Network):** Specialized for **sequential data** (text, time series, stock prices). It has a "memory" (a feedback loop) that allows information to persist from one step to the next.
    

### 7. Compare biological network with ANN

|**Biological Neuron**|**Artificial Neuron (Perceptron)**|
|---|---|
|Dendrites|Inputs|
|Cell Nucleus|Weighted Sum + Activation Function|
|Synapse|Weight (strength of connection)|
|Axon|Output|

### 8. What is sum of weighted inputs

This is the first step inside a neuron. It multiplies each input value ($x_i$) by its corresponding weight ($w_i$), sums them all up, and adds a bias ($b$).

$$\text{Weighted Sum} = (x_1 \cdot w_1) + (x_2 \cdot w_2) + ... + (x_n \cdot w_n) + b$$

This sum is then passed to the activation function.

### 9. What are activation functions

A function applied to the weighted sum of a neuron.

### 10. Why are activation functions necessary

They introduce **non-linearity** into the network. Without them, an ANN with 100 layers would just be a simple (and weak) linear regression model. Non-linearity is what allows the network to learn complex, non-linear relationships in the data.

### 11. Details of sigmoid, ReLU, soft max and tanh

- **Sigmoid:** $f(x) = \frac{1}{1 + e^{-x}}$. Squashes output to **(0, 1)**.
    
    - **Use:** Output layer for **binary classification** (to get a probability).
        
- **ReLU (Rectified Linear Unit):** $f(x) = max(0, x)$.
    
    - **Use:** The most popular choice for **hidden layers**. It's fast and helps prevent the "vanishing gradient" problem.
        
- **Tanh (Hyperbolic Tangent):** Squashes output to **(-1, 1)**.
    
    - **Use:** A (less common) alternative to ReLU in hidden layers.
        
- **Softmax:** $f(x_i) = \frac{e^{x_i}}{\sum e^{x_j}}$. Takes a vector of numbers and turns it into a probability distribution (all outputs sum to 1).
    
    - **Use:** Output layer for **multi-class classification** (e.g., [Cat: 0.1, Dog: 0.8, Fish: 0.1]).
        

### 12. What is vanishing gradient

A problem in deep networks, especially when using Sigmoid or Tanh. As the error is "back-propagated" through many layers, the gradient (the update signal) can get multiplied by small numbers over and over, becoming so small it "vanishes." This means the first few layers of the network **stop learning** or learn _extremely_ slowly.

### 13. Why is ReLU popularly used

It **solves the vanishing gradient problem** (for positive inputs, the gradient is a constant 1). This allows for much deeper and more stable networks. It is also very fast to compute.

### 14. Justify used of sigmoid for binary classification

Because its output range is (0, 1), which can be perfectly interpreted as a **probability**. For churn, an output of 0.75 means a "75% probability that this customer will churn."

### 15. Justify used of softmax for multi class classification

Because its output is a **probability distribution** across all classes, summing to 1. This tells you the model's confidence for _each_ class, and the highest probability is the prediction.

### 16. What is Multi layer perceptron (MLP)

An ANN with at least **one hidden layer** (a layer of neurons between the input layer and the output layer). This is the standard ANN architecture.

### 17. Explain the implementation of MLP in python

Using the **Keras** library (part of TensorFlow):

Python

```
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# 1. Define the model
model = Sequential()

# 2. Add layers
# Input layer (inferred) and first hidden layer
model.add(Dense(units=6, activation='relu')) 
# Second hidden layer
model.add(Dense(units=6, activation='relu'))
# Output layer (binary classification)
model.add(Dense(units=1, activation='sigmoid')) 

# 3. Compile the model
model.compile(optimizer='adam', 
              loss='binary_crossentropy', 
              metrics=['accuracy'])

# 4. Train the model
model.fit(X_train, y_train, batch_size=32, epochs=100)
```

### 18. Is the data imbalanced

**Yes, almost certainly.** In a bank churn dataset, you will have _far more_ customers who **stay** (0) than customers who **leave** (1). This imbalance can bias the model.

### 19. How to balance the data

You can use **sampling techniques** (see below) or you can **adjust class weights** during training (telling the model to "pay more attention" to the rare class).

### 20. Over sampling and under sampling

- **Under-sampling:** Reducing the number of samples from the **majority class** (e.g., randomly deleting 'stay' customers) until the classes are balanced. This is fast but you risk **losing important information**.
    
- **Over-sampling:** Increasing the number of samples from the **minority class** (e.g., duplicating 'churn' customers). This is better but can lead to overfitting on the duplicated samples.
    

### 21. Implementation of over sampling

The best method is **SMOTE (Synthetic Minority Over-sampling Technique)**. Instead of just duplicating minority samples, SMOTE _creates new, synthetic samples_ by:

1. Finding a minority sample.
    
2. Looking at its K-nearest minority neighbors.
    
3. Creating a new sample on the line connecting the original sample and one of its neighbors.
    

This is implemented in the imbalanced-learn library:

from imblearn.over_sampling import SMOTE

smote = SMOTE()

X_resampled, y_resampled = smote.fit_resample(X, y)