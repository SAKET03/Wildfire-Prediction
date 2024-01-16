# Wildfire-Prediction

## Overview
Wildfires represent increasingly destructive natural disasters, annually consuming millions of acres of forests and vegetation globally. This project aims to address the challenges in accurately predicting and monitoring wildfires by integrating satellite remote sensing and numerical weather prediction model data.

### Key Features
Data Integration: Utilizing comprehensive geospatial datasets from the IBM PAIRS platform, incorporating data from NASA, Copernicus, and NOAA sources.

Machine Learning Techniques: Implementing machine learning techniques through the `AutoGluon` automated ML toolkit to optimize an ensemble model for burned area prediction.

Interactive Interface: Featuring an intuitive interface developed in `Gradio`, allowing users to customize wildfire projections by incorporating key input parameters, such as vegetation indices and weather variables.

Visualizations: Interactive Plotly visualizations categorize predicted fire severity levels across regions.

This study demonstrates the value of synergizing Earth observations from spaceborne instruments and forecast data from numerical models to strengthen real-time wildfire monitoring and post-fire impact assessment capabilities for improved disaster management. The project optimizes an ensemble model by comparing various algorithms to minimize the root mean squared error between predicted and actual burned areas, achieving improved predictive performance over any individual model.




## Methodology
The methodology involves a comprehensive process, including data loading and inspection, data cleaning, handling missing values, univariate analysis, outlier treatment, region-wise distribution analysis, principal component analysis (PCA), and data preparation for training.

[Methodology](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Methodology.png)

### Data Loading and Inspection:
- Loading Data: Incorporating weather-related time series data from 2005 to 2021 from `dataset1.csv` into a Pandas DataFrame.
- Initial Observation: Using methods like `head()` for a snapshot of initial rows and shape for insights into the dataset's size.

### Data Cleaning:
- Column Renaming: Ensuring consistency and readability by renaming columns associated with vegetation indices.
- Duplicate Elimination: Addressing redundancies using the `drop_duplicates()` method.
Column Pruning: Removing non-contributory columns.

### Handling Missing Values:
- Identification: Recognizing columns with incomplete data.
- Numeric Columns Imputation: Filling missing values for numeric columns based on semantic derivations.
- Categorical Columns Imputation: Imputing missing values for non-numeric columns using the mode.
Row Exclusion: Removing rows with pervasive missingness.

### Univariate Analysis:
- Boxplots: Visualizing central tendency, spread, and skewness of various attributes.

[Indices_Distribution](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Distribution%20of%20Indices.png)

### Outlier Treatment:
- IQR Method: Utilizing the Interquartile Range (IQR) to discern potential outliers.
- Visualization: Generating boxplots after outlier treatment for optimized data distributions.

[Before_Removal](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Boxplot%20(Before%20Outlier%20Removal).png)
**After Outlier Removal:**
[After_Removal](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Boxplot%20(After%20Outlier%20Removal).png)

### Region-wise Distribution:
- Histograms: Visualizing how different attributes behaved across various regions.

[Region_Distribution](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Region%20Distribution.png)

### Principal Component Analysis (PCA):
- Pattern Recognition: Synthesizing data's information into fewer dimensions to facilitate recognition of inherent patterns.
- Variance Analysis: Plotting explained variance to determine the significance of each principal component.

[PCA_Components](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/PCA%20Bar%20Chart.png)
[PCA_Distribution](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/PCA%20Biplots.png)

### Data Preparation for Training:
- Feature Engineering: Crafting new features or transforming existing ones to enhance the model's ability to capture patterns.

### Model Training:
- Employing AutoGluon Framework: Utilizing AutoGluon for automated machine learning with a focus on regression tasks.
- Defining Target Variable and Problem Type: Framing the problem as a regression task with the target variable as `"Estimated_fire_area`
- Assessing Model Performance: Evaluating model performance using the `root mean squared error (RMSE)`.
- Setting Time Limit for Training: Imposing a time limit for efficient resource management.

### Model Evaluation:
- Evaluating Model Performance: Assessing the model's performance on a separate test dataset.
- `Diverse Evaluation Metrics`: Computing various metrics, including RMSE, MSE, MAE, R-squared, Pearson correlation coefficient, and Median absolute error.

### Model Interface:
- Gradio-Enabled Model Interface: Developing a model interface using Gradio for users to estimate wildfire areas quickly.
- Interactive Severity Visualization through Plotly: Hosting an interactive and dynamic plot powered by Plotly for categorizing wildfire severity.

[Interface](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Interface.png)



## Results
We employed AutoGluon for an automated machine learning approach to predict wildfire-burned areas using weather and satellite data. Seventeen algorithms, including neural networks and forests, were trained and optimized to minimize RMSE on a validation dataset.

[Accuracy](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Model%20Table.png)
[Model](https://github.com/SAKET03/Wildfire-Prediction/blob/main/Images/Model.png)

The `WeightedEnsemble_L2 model` excelled, blending top performers for improved accuracy. `CatBoostRegressor` stood out among standalone models with the lowest validation error. Tree-based methods and neural networks generally outperformed k-nearest neighbor regressors.

Assessing generalization on an unseen test set, the `WeightedEnsemble model achieved an RMSE of 1.564 km^2`, indicating a deviation of around 1.2 km^2 in predictions. Additional metrics highlighted areas for improvement in capturing fire progression drivers.

These initial results showcase the potential of data fusion, leveraging Earth observations and numerical forecasts for wildfire preparedness. Estimated burn zones aid in evacuation sizing, air quality prediction, and recovery planning. Future iterations aim to enhance accuracy and establish operational benchmarks tailored to end-user risk management needs.