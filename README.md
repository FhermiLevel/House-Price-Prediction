# House-Price-Prediction
A document to show prediction of sales price for each house

---
### Model Evaluation and Selection

To identify the most effective model for prediction of priice if houses, I evaluated both the XGBoost Regressor and the Random Forest Regressor using multiple metrics before tuning, after tuning, and during cross-validation. The goal was to determine which model consistently produced a higher level of predictive accuracy, lower error, and stronger generalization performance.

---

**1. Before and After Hyperparameter Tuning**

Both models were first trained using default settings to establish a baseline and then optimized through systematic hyperparameter tuning.

XGBoost Performance

R² Before Tuning: ≈ 0.915

R² After Tuning: ≈ 0.921

RMSE Before Tuning: ≈ 25,530

RMSE After Tuning: ≈ 24,617

After tuning, XGBoost achieved a noticeable improvement in both R² and RMSE, indicating that the model became more precise and better aligned with the underlying structure of the data. The reduction in RMSE highlights XGBoost’s ability to minimize prediction error more aggressively when appropriately regularized and optimized.

Random Forest Performance

R² Before Tuning: ≈ 0.894

R² After Tuning: ≈ 0.896

RMSE Before Tuning: ≈ 28,440

RMSE After Tuning: ≈ 28,242

Random Forest also improved after tuning, but the magnitude of the improvement was much smaller. Its RMSE remained significantly higher than that of XGBoost, and its R² score did not surpass the performance of XGBoost either before or after tuning.

---

**2. Cross-Validation Results**

To further ensure that the model results were consistent and not the product of overfitting, I applied cross-validation using both RMSE and R² Score as evaluation metrics.

On RMSE

XGBoost RMSE: ≈ −27,787

Random Forest RMSE: ≈ −29,695

XGBoost consistently achieved a lower (less negative) RMSE value, meaning it produced smaller prediction errors across folds. Random Forest demonstrated higher variance and weaker consistency.

On R² Score

XGBoost R²: ≈ 0.875

Random Forest R²: ≈ 0.858

Once again, XGBoost achieved the highest coefficient of determination across all folds, confirming its superior ability to explain variance in the target variable.

---

**3. Final Model Selection**

Based on all evaluation stages—baseline comparison, hyperparameter tuning, and cross-validation—XGBoost demonstrated superior performance across all major accuracy and error metrics.

Specifically:

It achieved higher R², indicating stronger explanatory power.

It produced lower RMSE, confirming smaller prediction errors.

It performed more consistently during cross-validation with lower variance.

It responded significantly better to hyperparameter tuning, while Random Forest improvements were marginal.

Overall, XGBoost provided the best balance between predictive accuracy, model stability, and generalization performance.

---

**SHAP Summary Plot Interpretation**

To better understand the decision-making process of the model, I applied SHAP (SHapley Additive Explanations), which provides transparent, model-agnostic interpretability.

The SHAP summary plot highlights the most influential features driving house price predictions:

OverallQual, GrLivArea, YearBuilt, TotalBsmtSF, and 1stFlrSF are the strongest contributors to the model’s output.

Each point in the plot represents the impact of a feature for a single house in the dataset.

Red points indicate higher feature values, while blue points represent lower values.

Features with red points far to the right (e.g., OverallQual and GrLivArea) show that higher values of these features significantly increase predicted sale prices.

Conversely, blue points on the left indicate low values that reduce the predicted sale price.

The SHAP summary plot not only confirms the model’s learned patterns but also aligns with real-world expectations,for example, houses with higher quality ratings, newer construction, and larger living areas consistently sell at higher prices. This interpretability step ensures that the model is behaving reasonably and provides valuable insights for both stakeholders and end users.

---

**Final Decision:**

The XGBoost Regressor is selected as the final model for this project due to its superior accuracy, lower error rates, and stronger performance under cross-validation
