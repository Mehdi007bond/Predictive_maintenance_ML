# ML Predictive Maintenance

## Project Overview
This project applies machine learning to predictive maintenance using the well-known AI4I 2020 Kaggle dataset. The goal is to anticipate equipment failures, optimize maintenance operations, and minimize downtime using data-driven predictive models and exploratory analysis.

## Dataset
- **Source:** [AI4I 2020 Predictive Maintenance Data (Kaggle)](https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020)
- **Features:**
  - Product and sensor data: air/process temperature, rotational speed, torque, tool wear
  - Failure indicators: Machine failure target, and five causes (TWF, HDF, PWF, OSF, RNF)
- **Size:** 10,000 rows, 14 features

## Workflow Summary
- Data ingestion using KaggleHub
- Data exploration: class balance, distribution plots, null value check, summary statistics
- Feature engineering: failure type classification based on failure columns (TWF, HDF, PWF, OSF, RNF)
- Visualization: Distribution of machine and failure types, target imbalance review
- Model build and evaluation section (extend as needed)

## Example Analysis Code (from notebook)
```python
# Import libraries
df = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "stephanmatzka/predictive-maintenance-dataset-ai4i-2020",
    "ai4i2020.csv",
)

# Quick EDA
df.isnull().sum()   # Check missing values
df.describe()       # Statistics and feature ranges

# Failure type engineering
failure_cols = ['TWF', 'HDF', 'PWF', 'OSF', 'RNF']
def classify_failure_type(row):
    for col in failure_cols:
        if row[col] == 1:
            return col
    return "No failure"
df["Failure_Type"] = df.apply(classify_failure_type, axis=1)

# Plot class distributions
sns.countplot(x="Failure_Type", data=df)
sns.countplot(x="Type", data=df)
```

## Visual Insights
- Dataset is heavily imbalanced: only 339 out of 10,000 samples indicate machine failure
- Multiple failure subtypes: TWF, HDF, PWF, OSF, RNF
- Product and operational types are well represented in features

## Technologies Used
- Python 3.x, pandas, NumPy
- Seaborn, matplotlib for visualization
- KaggleHub for data loading
- Jupyter Notebook

## Usage
Clone the repo and run the notebook:
```
git clone https://github.com/Mehdi007bond/Predictive_maintenance_ML.git
cd Predictive_maintenance_ML
jupyter notebook ML_Predictive_maintenance.ipynb
```

## Next Steps
- Implement and compare ML classifiers
- Report accuracy, recall, confusion matrix
- Extend EDA and feature engineering

## Author
Developed by [GHOSTBOND007](https://github.com/Mehdi007bond)

## License
MIT License
