# Model Application
List three of the supervised learning models above that are appropriate for this problem that you will test on the census data.
- Decision Trees
- Gradient Boosting
- Stochastic Gradient Descent Classifier (SGDC)
------
## 1. Decision Trees
A decision tree is an algorithm that can create both classification and regression models. <br>
Decision trees look like flowcharts, starting at the **root node** with a specific question of data, that leads to branches that hold potential answers. The branches then lead to **decision (internal) nodes**, which ask more questions that lead to more outcomes. This goes on until the data reaches what’s called a **terminal (or “leaf”) node** and ends.

### Decision tree terminology
- **Root node:** The topmost node of a decision tree that represents the entire message or decision
- **Decision (or internal) node:** A node within a decision tree where the prior node branches into two or more variables
- **Leaf (or terminal) node:** The leaf node is also called the external node or terminal node, which means it has no child—it’s the last node in the decision tree and furthest from the root node
- **Splitting:** The process of dividing a node into two or more nodes. It’s the part at which the decision branches off into variables
- **Pruning:** The opposite of splitting, the process of going through and reducing the tree to only the most important nodes or outcomes

### Entropy
Entropy, also called as Shannon Entropy is denoted by H(S) for a finite set S, is the measure of the amount of uncertainty or randomness in data.

$H(S) = -\sum{p_i\log_2{p_i}}$

### Information Gain:
nformation gain is also called as Kullback-Leibler divergence denoted by IG(S,A) for a set S is the effective change in entropy after deciding on a particular attribute A. It measures the relative change in entropy with respect to the independent variables.

$IG(S,A) = H(S) - \sum_{i=0}^{n}  {p(x)} \cdot {H(x)}$

### When to use 

- Classification problems:  For example, they can be used to predict whether a customer is likely to buy a product or not based on their demographic and purchase history.
- Regression problems: For example, they can be used to predict the price of a house based on its size, location, and other features. 
- Decision support systems: For example, they can be used to predict the likelihood of a patient developing a certain disease based on their medical history, or to recommend products to customers based on their past purchases.
- Feature selection: Decision Trees can be used to identify the most important features for predicting the target variable, which can be useful for feature selection and dimensionality reduction.


### Advantages
- DT/CART models are easy to interpret, as "if-else" rules.
- The models can handle categorical and continuous features in the same data set
- The method of construction for DT/CART models means that feature variables are automatically selected, rather than having to use subset selection or similar.
- Non-parametric: Decision Trees are non-parametric, which means they do not make any assumptions about the distribution of the data. 

### Disadvantages
- Poor relative prediction performance compared to other ML models.
- Can overfit and perform poorly on new data.
- DT/CART models suffer from instability, which means they are very sensitive to small changes in the feature space. In the language of the bias-variance trade-off, they are high variance estimators.

### References

- [Decision Trees in Machine Learning: Two Types](https://www.coursera.org/articles/decision-tree-machine-learning)
- [Beginner's Guide to Decision Trees for Supervised Machine Learning](https://www.quantstart.com/articles/Beginners-Guide-to-Decision-Trees-for-Supervised-Machine-Learning/)
- [Decision Trees for Classification: A Machine Learning Algorithm](https://www.xoriant.com/blog/decision-trees-for-classification-a-machine-learning-algorithm)
----
## 2. Gradient Boosting
### Boosting
Boosting is a technique to combine weak learners and convert them into strong ones with the help of Machine Learning algorithms. It uses ensemble learning to boost the accuracy of a model. 

Gradient Boosting enables us to combine the predictions from various learner models and build a final predictive model having the correct prediction.

Gradient boosting machines consist 3 elements as follows:

- Loss function
- Weak learners
- Additive model

### When to use 

- Gradient Boosting can handle large datasets with a large number of features, as it works well with both continuous and categorical features.
- Gradient Boosting is particularly effective when the data has complex, non-linear relationships that are difficult to model with simpler algorithms like linear regression.
- Gradient Boosting combines the strengths of multiple decision trees, reducing the variance of the model, while also addressing the issue of high bias with the use of boosting.

### Advantages
- Gradient Boosting is known for its high accuracy, as it can improve the performance of weak models by combining them into a strong ensemble model.
- Gradient Boosting provides a measure of feature importance, which can be helpful in understanding the relationship between the input variables and the target variable.
- Gradient Boosting is robust to outliers and noisy data, as it can handle them by assigning low weights to them.
- Gradient Boosting has built-in regularization methods that help to prevent overfitting, such as the use of shrinkage, early stopping, and tree depth limitations.

### Disadvantages
- Gradient Boosting can be computationally expensive.
- While Gradient Boosting is interpretable to some extent, it can be difficult to understand how the algorithm arrives at its final predictions, particularly when using a large number of trees.
- Gradient Boosting can be prone to overfitting, particularly when using a large number of trees or when the learning rate is set too high.
### References

- [GBM in Machine Learning](https://www.javatpoint.com/gbm-in-machine-learning)
- [Boosting Algorithms as Gradient Descent ](https://proceedings.neurips.cc/paper/1999/file/96a93ba89a5b5c6c226e49b88973f46e-Paper.pdf)

----
## 3. Stochastic Gradient Descent Classifier (SGDC).
SGDC works by iteratively updating the parameters of a linear classifier model to minimize a cost function, which measures the difference between the predicted class labels and the actual class labels in the training data. The algorithm updates the parameters in small increments by computing the gradients of the cost function with respect to the parameters, and then updating the parameters in the direction of the negative gradient.

Stochastic Gradient Descent, abbreviated as SGD, is used to calculate the cost function with just one observation. We go through each observation one by one, calculating the cost and updating the parameters.

### When to use 

- SGDC is particularly effective when dealing with large datasets that have many features, as it can efficiently update the model parameters on small batches of data.
- SGDC is commonly used for text classification tasks, as it can handle large text datasets with many features and achieve good classification performance.
- SGDC is a fast algorithm that can quickly update the model parameters, making it well-suited for real-time prediction tasks.
- SGDC can handle high-dimensional data, such as image or audio data, by using non-linear transformations of the input features, such as polynomial or radial basis function kernels.

### Advantages
- Since the network processes just one training sample, it is easy to put into memory.
- It can converge quicker for bigger datasets since the parameters are updated more often.
- Only one sample is processed at a time, hence, it is computationally efficient.
- The steps made towards the minima of the loss function include oscillations that can assist get out of the local minimums of the loss function due to frequent updates.

### Disadvantages
- The steps made towards the minima of the loss function include oscillations that can assist get out of the local minimums of the loss function due to frequent updates.-
- Furthermore, due to noisy steps, convergence to the loss function minima may take longer.
- Since it only interacts with one sample at a time, it lacks the benefit of vectorized operations.
- All resources are used to analyze one training sample at a time, frequent updates are computationally costly.
### References

- [Stochastic Gradient Descent](https://www.simplilearn.com/tutorials/scikit-learn-tutorial/stochastic-gradient-descent-scikit-learn)
- [Introduction to SGD Classifier ](https://michael-fuchs-python.netlify.app/2019/11/11/introduction-to-sgd-classifier/)


