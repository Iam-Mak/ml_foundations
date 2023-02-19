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

## Disadvantages
- Poor relative prediction performance compared to other ML models.
- Can overfit and perform poorly on new data.
- DT/CART models suffer from instability, which means they are very sensitive to small changes in the feature space. In the language of the bias-variance trade-off, they are high variance estimators.

### References

- [Decision Trees in Machine Learning: Two Types](https://www.coursera.org/articles/decision-tree-machine-learning)
- [Beginner's Guide to Decision Trees for Supervised Machine Learning](https://www.quantstart.com/articles/Beginners-Guide-to-Decision-Trees-for-Supervised-Machine-Learning/)
- [Decision Trees for Classification: A Machine Learning Algorithm](https://www.xoriant.com/blog/decision-trees-for-classification-a-machine-learning-algorithm)
----