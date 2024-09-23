# An analysis of Irish Census data to determine the effect of different features on the value of median household income

## Basic overview
This analysis considers data referring to the citizens of Ireland. It collects various metrics from the different Electoral Divisions in the county. This analysis will combine the available data and create machine learning models to determine the effect of different features on the value of median household income.  

## Table of Contents
1. [Basic Overview](#basic-overview)
2. [Installation and Set-Up](#installation-and-set-up)
   
   2.1 [Python Installation](#python-installation)
   
   2.2 [Running Jupyter Notebooks](#running-jupyter-notebooks)
   
   2.3 [Required Packages](#required-packages)

   
3. [Notebooks](#notebooks)

   3.1 [ML Cleaning](#ml-cleaning)
   
   3.2 [ML Dimension Reduction](#ml-dimension-reduction)
   
   3.3 [ML PCA](#ml-pca)
   
   3.4 [ML Regression](#ml-regression)
   
   3.5 [ML Clustering](#ml-clustering)
   
   3.6 [ML Classification Data Prep](#ml-classification-data-prep)
   
   3.7 [ML Classification](#ml-classification)


## Installation and Set-Up

1. **Python Installation**: This project requires Python. Ensure you have Python installed on your system. You can download Python from the [official Python website](https://www.python.org/downloads/).

2. **Running Jupyter Notebooks**: The Python files for this project are in `.ipynb` format, which can be executed using Jupyter Notebook or Google Colab. To use Jupyter Notebook locally, you can install it via Anaconda or directly using pip:
   - **Using Anaconda**: Install Anaconda from [Anaconda's website](https://www.anaconda.com/products/distribution) and launch Jupyter Notebook from the Anaconda Navigator.
   - **Using pip**: Install Jupyter Notebook with the command:
     ```bash
     pip install notebook
     ```
     
3. **Required Packages**: This analysis requires several Python packages. You can install these packages using pip. The list of packages and their installation commands are provided below. 

      - 'pip install pandas'
      - 'pip install numpy'
      - 'pip install scikit-learn'
      - 'pip install matplotlib'
      - 'pip install bioinfokit'
      - 'pip install seaborn'
      - 'pip install xgboost'
      - 'pip install shap'
      - 'pip install interpret'
      
      
Once these packages have been installed all import statements should run.

## Notebooks
The analysis is performed through several notebooks, each focusing on a specific stage. These notebooks are designed to be run in order with data being defined in earlier notebooks and imported for use in later ones:

### ML Cleaning
Data is read in from the relevant datasets, skipping rows in some instances to ensure clean data collection. Non_uniform data at the end of dataframes are dropped. Columns are split to ensure one data entry per dataframe cell. Data columns are renamed for simplicity. The dataframes are then merged. 

The census data is then prepared for merging with the above dataset. Age columnbs are grouped i.e. in groups of 5 years in order to reduce the number of columns. These columns are added back to the original dataframe. This leaves a single dataframe containing all of the records for each of the metrics collected. 

### ML Dimension Reduction
After cleaning and combining the data in the previous notebook the data contains 785 columns. This will cause significant run-times in later analysis. To tackle this problem the dimensions are reduced through a variety of methods.

Any features with a variance of lower than 10% are dropped as they are unlikely to have a significant effect on the target variable. Features that have a correlation with another metric of > 0.5 are dropped to reduce data redundancy. 

This process leaves a dataframe containing 2992 rows and 18 columns.

### ML PCA
Principal Component Analysis is performed on the data to further reduce data dimensionality. The first 10 principal components are retained. The principal components are visualised to show their key features. 

### ML Regression
The first 5 principla components are used to train the regression model. A range of models are trained and tested and the results are stored. The strongest model (Gradient Boost) is then optimized using Grid Search Cross Validation and the optimum hyperparameters are found. 

SHAP (Feature Importance tool) is run using this optimized model. The Second, First and Third Principal Components contributed the most to the target variable. The features in principal component 1 that correlate positively with median household income are:

Households, nationality, population by sex/marital status, families, and languages.  

Features in principal component 1 that correlate negatively with median household income are:

Agriculture, Forestry and Fishing; Construction; Industry; GEOGID and area code.

### ML Clustering
K-means, Mean-Shift and Hierarchical clustering algorithms were executed. The key takeaway from clustering was that when records were grouped by cluster, the first principal component having a negative value seemed to lead to lower income values.

### ML Classification Data Prep
The categorical features are retrieved from the previously cleaned data. The target variable is added to the dataframe. A column is dropped to reduce data redundancy. The variable 'gross income' is then binned into 5 levels of 'High' to 'Low'. 

### ML Classification
The categorical data created in the previous notebook is split into training and testing X and Y sets. A number of classification algorithms are imported and the data is encoded. Each of the models are run on the data. Logistic Regression is the strongest performing model. This model is then tuned using Grid Search Cross Validation in an attempt to find imprved performance. The optimum model reached an accuracy level of 71.8475%.
