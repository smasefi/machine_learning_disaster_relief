# Haiti Blue Tarp Detection - DS 6030 Group Project

## Overview
This project focuses on detecting blue tarps in aerial imagery of Haiti using supervised machine learning models. Blue tarps are commonly used as indicators of damaged infrastructure (e.g., post-disaster relief), making this a real-world classification problem with humanitarian relevance.

We use RGB pixel data to classify whether a given pixel corresponds to a Blue Tarp or Other.

## Dependencies
This project is built in R and uses the tidymodels ecosystem as well as parallelization

## Data Preprocessing
Training Data

The dataset is loaded and the target variable is transformed:

“Blue Tarp” → Blue_Tarp
“Other” → Other

The target variable is converted into a factor for classification.

Holdout Data

Multiple text files are combined into a single test dataset. These files contain both blue tarp and non-blue tarp observations and are used for final model evaluation.

Feature Engineering

Two key features are created to improve model performance:

BlueGreen ratio = Blue / Green
BlueRed ratio = Blue / Red

These ratios help highlight color differences that distinguish blue tarps from other surfaces.

## Models Used
- Linear Discriminant Analysis (LDA)
- Quadratic Discriminant Analysis (QDA)
- k-Nearest Neighbors (KNN)
- Penalized Logistic Regression (L1/L2 regularization)
- Random Forest
- Support Vector Machine (Polynomial kernel)

## Model Pipeline
Each model follows a consistent pipeline:

1. Preprocessing
   Normalize numeric predictors
   Dummy encode categorical variables
2. Cross-validation
   10-fold cross-validation
   Stratified by class
3. Hyperparameter tuning
   Latin hypercube grid search
   Evaluated using ROC AUC and F1 score

## Evaluation
Metrics Used - 
- ROC AUC
- F1 Score
- Accuracy
- Sensitivity
- J-index
Visualizations
- ROC curves (including zoomed views)
- Precision-recall curves
- Threshold performance plots
- Confusion matrices
- Heatmaps of model performance

Threshold Optimization
- Instead of using a default classification threshold of 0.5, thresholds between 0.001 and 0.5 were evaluated.

Optimal thresholds were selected based on:
- F1 Score
- Accuracy
- Sensitivity

Custom functions were created to:
- Evaluate performance across thresholds
- Visualize confusion matrices at optimal thresholds
- Compare models consistently

## Final Evaluation

Final models were trained on the full training dataset and evaluated on the holdout dataset.

Additional analysis included:
- Comparing training vs test performance
- Measuring overfitting using differences in F1 score

## Key Results
Random Forest and SVM models showed strong performance
Ratio-based features significantly improved classification
Threshold tuning led to meaningful improvements in F1 score
Some models showed mild overfitting, but overall generalization was strong

# #Authors
Claire Sullivan
Terrance Luangrath
Katie Dunning
Samantha Asef
