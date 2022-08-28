# Project: Identify Customer Segments


### Description
In this project, we will work with real-life data provided to us by Bertelsmann partners AZ Direct and Arvato Finance Solution. The data here concerns a company that performs mail-order sales in Germany. Their main question of interest is to identify *facets* of the population that are most likely to be purchasers of their products for a mailout campaign. Our job as a data scientist will be to use unsupervised learning techniques to organize the general population into clusters, then use those clusters to see which of them comprise the main user base for the company. Prior to applying the machine learning methods, we will also need to assess and clean the data in order to convert the data into a usable form.

#### Check My 
- [Jupyter notebook](https://github.com/Iam-Mak/Udacity-Machine-Learning-Projects/blob/main/1.%20Project%20-%20Finding%20Donors%20for%20CharityML/Finding%20Donors%20for%20CharityML.ipynb)

### Software and Libraries
This project uses the following software and Python libraries:
- [NumPy](http://www.numpy.org/)
- [Pandas](http://pandas.pydata.org)
- [Matplotlib](http://matplotlib.org/)
- [Seaborn ](https://seaborn.pydata.org/)
- [Scikit-Learn](http://scikit-learn.org/stable/)

## Getting Started
### Data
- **Udacity_AZDIAS_Subset.csv:** Demographic data for the general population of Germany; `891211 persons (rows) x 85 features (columns)`.
- **Udacity_CUSTOMERS_Subset.csv:** Demographic data for customers of a mail-order company; `191652 persons (rows) x 85 features (columns)`.
- **Data_Dictionary.md:** Information file about the features in the provided datasets.
- **AZDIAS_Feature_Summary.csv:** Summary of feature attributes for demographic data.

Each row of the demographics files represents a single person, but also includes information outside of individuals, including information about their household, building, and neighborhood.We will use this information to cluster the general population into groups with similar demographic properties. Then, we will see how the people in the customers dataset fit into those created clusters.
The hope here is that certain clusters are over-represented in the customers data, as compared to the general population; those over-represented clusters will be assumed to be part of the core userbase. This information can then be used for further applications, such as targeting for a marketing campaign.

## Preparing the Data
### Preprocessing
The feature summary file contains a summary of properties for each demographics data column. We will use this file to make cleaning decisions.
- Number of Naturally missing values are `4896838`.
- Total number of missing values after conversion is `8373929`

Columns that have more than 20% missing data are considered as outlier columns according to me, and are dropped.
Dropped columns: 
- AGER_TYP
- GEBURTSJAHR
- TITEL_KZ
- ALTER_HH
- KK_KUNDENTYP
- KBA05_BAUMAX

We observed that nearly 10% of row data has missing more than 25 values which can be ignored to simplify further processing. We will be going ahead with the dataset having below 25% of missing data. Replacing the nan with using most frequent value in each category.
- Rows with missing data above 25 : 93315 or 10.47 % of all data

### Re-Encode Features
For categorical data, we need to encode the levels as dummy variables.Depending on the number of categories, perform one of the following:
- For binary (two-level) categoricals that take numeric values, we can keep them without needing to do anything.
- There is one binary variable that takes on non-numeric values. For this one, we need to re-encode the values as numbers or create a dummy variable.
- For multi-level categoricals (three or more values), we can choose to encode the values using multiple dummy variables (e.g. via [OneHotEncoder](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)), or (to keep things straightforward) just drop them from the analysis.

|Type| Value|
|----|------|
| ordinal  |      49|
|categorical  |  18|
|mixed      |     6|
|numeric     |    6|

**Shape of Data After Cleaning and Encoding :** `797906, 196`

## Feature Transformation
