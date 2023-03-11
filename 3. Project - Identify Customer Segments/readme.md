# Project: Identify Customer Segments

<img src="../images/Customer Seg.png" width="800" height="450" alt="Charity Image" />

### Description
In this project, we will work with real-life data provided to us by Bertelsmann partners AZ Direct and Arvato Finance Solution. The data here concerns a company that performs mail-order sales in Germany. Their main question of interest is to identify *facets* of the population that are most likely to be purchasers of their products for a mailout campaign. Our job as a data scientist will be to use unsupervised learning techniques to organize the general population into clusters, then use those clusters to see which of them comprise the main user base for the company. Prior to applying the machine learning methods, we will also need to assess and clean the data in order to convert the data into a usable form.

#### Check My 
- [Jupyter notebook](https://github.com/Iam-Mak/Udacity-Machine-Learning-Projects/blob/main/3.%20Project%20-%20Identify%20Customer%20Segments/Identify%20Customer%20Segments.ipynb)

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


## Preprocessing
The feature summary file contains a summary of properties for each demographics data column. We will use this file to make cleaning decisions.
- Number of Naturally missing values are `4896838`.

In `AZDIAS_Feature_Summary` Fourth column `missing_or_unknown` contains missing values encoded  as a list (e.g. `[-1,0]`). We need to Convert data that matches a 'missing' or 'unknown' value code into a numpy NaN value. 
- Total number of missing values after conversion is `8373929`

### Missing Data in Each Column
Columns that have more than 20% missing data are considered as outlier columns according to me, and are dropped.<br>
Dropped columns: 
- AGER_TYP
- GEBURTSJAHR
- TITEL_KZ
- ALTER_HH
- KK_KUNDENTYP
- KBA05_BAUMAX

<img src='Images/Columns Missing Values.png' width=700px>

- Dhape of DataFrame `(891221, 79)`.
- Total number of missing values after removing outlier is 5035304


###  Missing Data in Each Row
<img src='Images/Rows Missing Values.png' width=700px>

We observed that nearly 10% of row data has missing more than 20% values which can be ignored to simplify further processing. We will be going ahead with the dataset having below 20% of missing data. Replacing the nan with using most frequent value in each category.
- Rows with missing data above 20 % : 99325 or 11.14 % of all data

## Re-Encode Features
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

**Shape of Data After Cleaning and Encoding :** `797077, 194`

### Mixed-Type Features
- `PRAEGENDE_JUGENDJAHRE` combines information on three dimensions: generation by decade, movement (mainstream vs. avantgarde), and nation (east vs. west).
    - `PRAEGENDE_JUGENDJAHRE_DECADE`
    - `PRAEGENDE_JUGENDJAHRE_MOVEMENT`
- `CAMEO_INTL_2015` combines information on two axes: wealth and life stage.
    - `CAMEO_INTL_2015_WEALTH` 
    - `CAMEO_INTL_2015_LIFE_STAGE`

**Shape of Data After Engineer Mixed-Type Features :** `797077, 196`

## Feature Transformation
- **StandardScaler:** Standardize features by removing the mean and scaling to unit variance.
- **Principal Component Analysis (PCA)** is an unsupervised machine learning technique to reduce the dimensionality of data consisting of a large number of inter-related attributes (or features or variables) but at the same time retaining as much as possible of the variation present in the original data.
<img src='Images/PCA.png' width=700px>
Selecting 60 components for our Analysis.


## Clustering
To Find Optimum Value for K

<img src='Images/AvgDistK.png' width=700px>

- Selecting k = 14 Clusters for our Customer Segmentation.

### Compare Customer Data to Demographics Data
<img src='Images/Customer Comparision.png' width=1000px>

By looking at the graph we can easily find that the cluster points 3, 5 and 7 data points are highly likely customer segments because the larger praportion of customer data is present at these points while data points that are defined by cluster points 0, 4 and 8 are less likely to be turned into customers are general population data dominates these clusters.

- **Cluster 7 is overrepresented** in the customers data compared to general population data, we can describe some segments of the population that are relatively popular with the mail-order company:

    - People with age older than 60 years old is higher (ALTERSKATEGORIE_GROB = 3.07)
    - Males (ANREDE_KZ = 1.483374)
    - People who are socially-minded (average affinity) (SEMIO_SOZ =4.229552)
- **Cluster 0 is underrepresented** in the customers data compared to general population data, we can illustrate some segments of the population that are relatively unpopular with the company:

    - People with age of 30 - 45 years old is lower (ALTERSKATEGORIE_GROB = 1.765125)
    - Females (ANREDE_KZ = 1.987310)
    - People who are socially-minded (high affinity) (SEMIO_SOZ = 3.290106)


