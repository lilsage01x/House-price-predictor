# House Price Prediction Using Machine Learning

## 1. Project Objective

The objective of this project is to build and evaluate machine learning models that predict house prices using property characteristics. The project compares Linear Regression and Random Forest Regression to determine which model performs better on the test dataset.

## 2. Dataset Description

The dataset contains property information, including:

- `Location` — the property's location.
- `Property_Type` — the type of property.
- `Size_SqFt` — the size of the property in square feet.
- `Bedrooms` — number of bedrooms.
- `Bathrooms` — number of bathrooms.
- `Garage_Spaces` — number of garage spaces.
- `Property_Age_Years` — age of the property in years.
- `Distance_City_Centre_Km` — distance from the city centre in kilometres.
- `Has_Garden` — whether the property has a garden.
- `House_Price` — the target variable to be predicted.
- `Property_ID` — a property identifier, excluded from the model features.

The dataset was provided as a CSV file named `New_housing_data(1).csv`.

## 3. Data Preprocessing

The following preprocessing steps were performed:

- **Missing values:** Missing values in `Location` were filled using the mode. Missing values in `Property_Type` were handled using a machine learning approach. Other missing values were handled using imputation.
- **Categorical encoding:** Categorical features, including location and property type, were converted into numerical representations so the models could use them.
- **Garden encoding:** `Has_Garden` was converted into numerical values.
- **Duplicate investigation:** Duplicate `Property_ID` values were investigated rather than automatically removing the corresponding rows.
- **Feature selection:** `Property_ID` was excluded from the predictors because it is an identifier rather than a meaningful property characteristic.
- **Train-test split:** The data was split into 80% training data and 20% testing data, using `random_state=42`.

*Note: The preprocessing steps should be checked against the final notebook to ensure this description accurately reflects the implementation.*

## 4. Machine Learning Models

Two regression models were trained:

### Linear Regression

Linear Regression estimates house prices by learning a linear relationship between the property features and house prices.

### Random Forest Regression

Random Forest Regression combines predictions from multiple decision trees to model relationships that may be more complex than a straight-line relationship.

Both models were trained on the same training set and evaluated on the same test set.

## 5. Model Evaluation Results

The models were evaluated using Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and the coefficient of determination (R²).

| Model | MSE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 55,404,322,826,803.63 | 7,443,408.01 | 0.9414 |
| Random Forest | 82,574,058,451,046.05 | 9,087,026.93 | 0.9126 |

### Understanding the Metrics

- **MSE:** Measures the average squared difference between actual and predicted prices. Lower values indicate better predictions, but the squared units make the result less intuitive.
- **RMSE:** Measures prediction error in the same units as the target variable. The Linear Regression model had an RMSE of approximately 7.44 million, compared with approximately 9.09 million for Random Forest.
- **R²:** Measures how much of the variation in house prices is explained by the model relative to predicting the mean price. The Linear Regression model achieved an R² of 0.9414, while Random Forest achieved 0.9126.

### Best-Performing Model

Linear Regression performed better on this test split because it had a lower MSE and RMSE and a higher R² score.

Its R² score indicates that it explained approximately 94.14% of the variation in house prices in the test set. This does not mean that 94.14% of its predictions were exactly correct.

## 6. Major Findings

- Linear Regression outperformed Random Forest on all three evaluation metrics.
- The model captured much of the relationship between the property features and house prices.
- The actual-versus-predicted plot showed that many predictions were relatively close to the ideal prediction line, although some differences remained.
- The residual plot showed prediction errors on both sides of zero, with some larger errors. This indicates that the model was not equally accurate for every property.
- The trained Linear Regression model was also used to generate price estimates for three hypothetical properties, demonstrating how the model could be applied to new inputs.

## 7. Visualizations

The project includes the following evaluation charts:

- `actual_vs_predicted.png` — compares actual house prices with model predictions.
- `residual_error_plot.png` — displays prediction errors to help identify patterns and large errors.
- `model_evaluation_summary.png` — provides a visual comparison of model evaluation results.

These visualizations help assess model performance beyond the numerical metrics alone.


## 8. How to Review or Run the Project

### Option A: Review on GitHub

1. Open the repository on GitHub.
2. Read this README to understand the project's objective, methods, and findings.
3. Open `house_price_prediction.ipynb` to inspect the code, explanations, evaluation metrics, and visualizations.
4. Review the charts in the `house_price_charts` folder.

### Option B: Run in Google Colab

1. Download or clone the project repository.
2. Open [Google Colab](https://colab.research.google.com/).
3. Upload `house_price_prediction.ipynb` or open it from GitHub.
4. Upload the dataset when prompted, or update the notebook's file path to match the dataset's location.
5. Run the notebook cells in order, from data loading and preprocessing through model training, evaluation, visualization, and prediction.
6. Confirm that the generated evaluation metrics are consistent with the reported results.

### Requirements

The notebook uses Python and common data science libraries, including:

- pandas
- NumPy
- scikit-learn
- Matplotlib

If running locally, install the required libraries with:

```bash
pip install pandas numpy scikit-learn matplotlib jupyter
```

## 9. Limitations and Future Improvements

### Limitations

- Missing-value imputation can introduce uncertainty into the dataset.
- The available features may not capture every factor affecting house prices, such as property condition, security, amenities, and current market demand.
- The evaluation used a single train-test split, so results may vary with different splits.
- The predictions are estimates and should not be treated as guaranteed market values.
- Preprocessing before the train-test split, if performed, could introduce data leakage and make the evaluation overly optimistic.

### Future Improvements

- Use a preprocessing pipeline fitted only on the training data to reduce data leakage.
- Apply cross-validation to evaluate model performance more reliably.
- Investigate properties with large residual errors.
- Add relevant features that may improve prediction quality.
- Tune Random Forest hyperparameters and experiment with other models, such as Gradient Boosting.
- Test the final model on additional, representative property data.

## 10. Conclusion

This project demonstrates how data preprocessing, regression models, evaluation metrics, and visualizations can be used to build a house-price prediction system.

Between the two models tested, Linear Regression produced the better results on the selected test set. Further testing, improved preprocessing, and additional property features could help establish how well the model generalizes to unseen properties.
