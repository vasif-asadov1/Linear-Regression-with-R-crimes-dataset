# Linear Regression Analysis of Violent Crime Rates

**Author:** Vasif Asadov

This project presents a complete statistical and machine learning pipeline implemented in R to model and predict **ViolentCrimesPerPop** using socio-economic and demographic indicators. The workflow combines classical statistical modeling techniques with modern machine learning infrastructure, emphasizing interpretability, multicollinearity control, and robust evaluation.

The project is designed to demonstrate how careful preprocessing, variance inflation control, and statistical feature selection can significantly improve linear model stability and generalization.

## Project Overview

The dataset used in this project is a structured tabular dataset containing multiple numeric predictors related to population, income, education, and social conditions. The target variable, **ViolentCrimesPerPop**, represents the rate of violent crimes per population unit. All predictors are numeric, which allows direct application of linear modeling techniques without categorical encoding.

The primary objective is to construct a reliable and interpretable regression model that explains variation in violent crime rates while avoiding multicollinearity and overfitting.

## Data Exploration and Preprocessing

The workflow begins by loading the dataset and inspecting column names, data types, and overall structure. Missing value analysis confirms that the dataset contains no missing observations. As a result, no imputation procedures are required.

All predictors are numeric, enabling a streamlined preprocessing pipeline. Prior to modeling, feature scaling is applied to normalize the predictors and ensure coefficient comparability within the linear regression framework.

## Multicollinearity Analysis

Multicollinearity is addressed using a two-stage process. First, a generalized linear model is constructed using all predictors to detect perfect linear dependencies through the `alias()` function. Any perfectly collinear predictors are removed.

Second, Variance Inflation Factor (VIF) analysis is performed iteratively. Predictors with VIF values exceeding a predefined threshold are removed one at a time, and the model is refit after each removal. This iterative process continues until all remaining predictors exhibit acceptable VIF values. This step ensures numerical stability and meaningful coefficient interpretation.

## Model Training

After preprocessing and feature selection, the dataset is converted into H2O’s optimized data structure. The data is split into training and testing subsets using an 80/20 ratio to evaluate generalization performance.

A linear regression model is trained using H2O’s `glm` implementation with 10-fold cross-validation. Statistical inference is enabled to compute p-values for each predictor. Predictors with p-values greater than 0.05 are iteratively removed, and the model is retrained until all remaining features are statistically significant.

## Model Evaluation

Model performance is evaluated using Root Mean Squared Error (RMSE), R², and Adjusted R². These metrics are computed on the test set to assess predictive accuracy and explanatory power.

Residual analysis is conducted by comparing observed and predicted values. Interactive visualizations are generated to examine model fit and error structure. These plots provide insight into linearity, variance consistency, and overall prediction quality.

## Overfitting Assessment

To assess overfitting, the same evaluation metrics are computed on the training set and compared with test set results. The similarity between training and testing RMSE and Adjusted R² values indicates that the model generalizes well and does not suffer from significant overfitting or underfitting.

Visual comparison of predicted versus observed values for both training and test sets further supports this conclusion.

## Conclusion

This project demonstrates that linear regression remains a powerful and interpretable modeling technique when combined with rigorous preprocessing, multicollinearity control, and statistical feature selection. By systematically addressing variance inflation and predictor significance, the final model achieves stable performance and strong generalization.

The workflow presented here is suitable for academic coursework, applied data science projects, and portfolio demonstrations focused on explainable modeling and statistical rigor.

## Notes

The rendered HTML report is fully self-contained and includes interactive visualizations. All supporting files generated during rendering are required for correct display when deployed on GitHub Pages. This project emphasizes interpretability and methodological correctness rather than black-box optimization.
