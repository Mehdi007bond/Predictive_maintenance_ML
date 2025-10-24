# ML Predictive Maintenance Project

This project focuses on **predictive maintenance** using the "AI4I 2020 Predictive Maintenance Dataset" from Kaggle. It demonstrates a complete machine learning workflow, including data exploration, feature engineering, and visualization to predict machine failures.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Key Findings from EDA](#key-findings-from-eda)
- [Feature Engineering](#feature-engineering)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)
- [Future Work](#future-work)
- [License](#license)

## Project Overview
Predictive maintenance is a proactive approach to prevent equipment failure by analyzing data to identify patterns and predict issues before they happen. This project implements a machine learning model to predict machine failure based on sensor data and operational parameters. The primary goal is to create a system that can help reduce downtime and optimize maintenance schedules.

## Dataset
The project uses the **AI4I 2020 Predictive Maintenance Dataset**, which contains 10,000 data points with 14 features. The data includes:
- **UID**: A unique identifier for each data point.
- **Product ID**: A unique identifier for each product.
- **Type**: The quality variant of the product (L, M, or H).
- **Air temperature [K]**: The ambient air temperature in Kelvin.
- **Process temperature [K]**: The temperature of the process in Kelvin.
- **Rotational speed [rpm]**: The rotational speed of the machine.
- **Torque [Nm]**: The torque of the machine.
- **Tool wear [min]**: The wear of the tool in minutes.
- **Machine failure**: A binary flag indicating whether the machine failed.
- **Failure Types**: Binary flags for specific failure modes:
  - `TWF`: Tool Wear Failure
  - `HDF`: Heat Dissipation Failure
  - `PWF`: Power Failure
  - `OSF`: Overstrain Failure
  - `RNF`: Random Failure

## Key Findings from EDA
Exploratory Data Analysis (EDA) revealed several important insights:
- **No Missing Data**: The dataset is complete with no null values.
- **Imbalanced Target**: The `Machine failure` target variable is highly imbalanced, with failures accounting for only about 3.4% of the data.
- **Outliers**: The `Torque [Nm]` and `Rotational speed [rpm]` features contain outliers that could affect model performance.
- **Failure Distribution**: Heat Dissipation Failure (`HDF`) is the most common type of failure, while Random Failure (`RNF`) is the least common.

## Feature Engineering
To better understand the causes of failure, a new feature, `Failure_Type`, was created by classifying each failure based on the binary failure flags (`TWF`, `HDF`, `PWF`, `OSF`, `RNF`). This helps in analyzing the specific conditions that lead to different types of failures.

## Technologies Used
- **Python**: The primary programming language.
- **Pandas**: For data manipulation and analysis.
- **Seaborn & Matplotlib**: For data visualization.
- **Jupyter Notebook**: For interactive development and analysis.

## How to Run
To run this project, follow these steps:
1. **Clone the repository**:
   ```bash
   git clone https://github.com/Mehdi007bond/Predictive_maintenance_ML.git
   ```
2. **Navigate to the project directory**:
   ```bash
   cd Predictive_maintenance_ML
   ```
3. **Install the required libraries**:
   ```bash
   pip install pandas seaborn matplotlib jupyter
   ```
4. **Run the Jupyter Notebook**:
   ```bash
   jupyter notebook ML_Predictive_maintenance.ipynb
   ```

## Future Work
This project provides a strong foundation for further development. Some potential next steps include:
- **Handling Outliers**: Implement strategies to manage the outliers in `Torque` and `Rotational speed`, such as removing or transforming them.
- **Addressing Class Imbalance**: Use techniques like SMOTE (Synthetic Minority Over-sampling Technique) or ADASYN (Adaptive Synthetic Sampling) to address the imbalance in the target variable.
- **Model Building**: Train and evaluate various classification models (e.g., Logistic Regression, Random Forest, Gradient Boosting) to predict machine failures.
- **Hyperparameter Tuning**: Optimize the models using techniques like GridSearchCV or RandomizedSearchCV to improve performance.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
