
# Vendor Credit Risk Assessment

## Project Overview

This project aims to build a credit risk assessment model to evaluate potential vendors. By analyzing various factors, the model provides a risk percentage and a recommendation ('Go' or 'No-Go') to help in the decision-making process for engaging with a vendor.

## Data

The project utilizes the **German Credit Data** dataset, sourced from the UCI Machine Learning Repository. This dataset contains information about credit applications from German individuals.

*   **Source:** UCI Machine Learning Repository
*   **Number of Instances:** 1000
*   **Number of Features:** 20 predictive features and 1 target variable ('credit_risk')

The features include a mix of numerical and categorical attributes related to the applicant's financial situation, personal status, and credit history.

## Methodology

The following steps were performed to build and evaluate the credit risk assessment model:

1.  **Data Loading:** The dataset was loaded into a pandas DataFrame.
2.  **Preprocessing:**
    *   Categorical features were identified and one-hot encoded to convert them into a numerical format suitable for modeling.
    *   Numerical features were scaled using `StandardScaler` to ensure they have a similar range, preventing features with larger values from dominating the model.
    *   The target variable ('credit_risk') was transformed from its original values (1 and 2) to binary labels (0 for 'Good Risk' and 1 for 'Bad Risk').
3.  **Model Training:** Two classification models were trained on the preprocessed data:
    *   Logistic Regression
    *   LightGBM Classifier
    The data was split into training and testing sets (80/20 split) using `train_test_split` with stratification to maintain the proportion of the target variable in both sets.
4.  **Model Evaluation:** The performance of each model was evaluated on the test set using the following metrics:
    *   Accuracy Score
    *   Confusion Matrix
    *   Classification Report (including precision, recall, and f1-score)
    The model with the highest accuracy was selected as the best model.
5.  **Vendor Recommendation Function:** A Python function `get_vendor_recommendation` was created to take new vendor data, preprocess it using the same steps as the training data (one-hot encoding and scaling), and then use the trained model to predict the credit risk and provide a 'Go' or 'No-Go' recommendation along with the risk percentage.

## Results

The trained models were evaluated based on their performance on the test set.

*   **Logistic Regression:** Achieved an accuracy of 0.785.
*   **LightGBM:** Achieved an accuracy of 0.765.

Based on the accuracy score, **Logistic Regression** was selected as the best model for vendor credit risk assessment.

Visualizations were created to understand the distribution of the calculated risk percentages and recommendations:

*   The histogram of **Risk Percentage** shows the frequency of different risk score ranges across the dataset.
*   The count plot of **Recommendation** shows the number of vendors classified as 'Go' and 'No-Go'.
*   A box plot comparing **Risk Percentage by Original Credit Risk** demonstrates the model's ability to assign higher risk percentages to vendors originally classified as 'Bad Risk' and lower percentages to those classified as 'Good Risk'.
*   A stacked bar chart comparing **Recommendation and Original Credit Risk** visually shows the alignment between the model's recommendations and the original credit risk labels, highlighting the number of correct and incorrect classifications for both 'Good Risk' and 'Bad Risk' categories.

Overall, the project successfully developed a model that can assess vendor credit risk, providing valuable insights and recommendations.
