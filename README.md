# An analysis of Irish Census data to determine the effect of different features on the value of median household income

## Basic overview
This analysis considers data referring to the citizens of Ireland. It collects various metrics from the different Electoral Divisions in the county. This analysis will combine the available data and create machine learning models to determine the effect of different features on the value of median household income.  

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

### ML_Cleaning
Data is read in from the relevant datasets, skipping rows in some instances to ensure clean data collection. Non_uniform data at the end of dataframes are dropped. Columns are split to ensure one data entry per dataframe cell. Data columns are renamed for simplicity. The dataframes are then merged. 

The census data is then prepared for merging with the above dataset. Age columnbs are grouped i.e. in groups of 5 years in order to reduce the number of columns. These columns are added back to the original dataframe. This leaves a single dataframe containing all of the records for each of the metrics collected. 

### ML_Dimension_Reduction

### ML_PCA

### ML_Regression

### ML_Clustering

### ML_Classification_Data_Prep

### ML_Classification
