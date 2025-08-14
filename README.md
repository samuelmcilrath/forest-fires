# Forest Fire Prediction

## Problem
Forest fires have severe impacts on ecosystems and human communities.  
Predicting their spread is challenging due to the many contributing factors such as weather, topography, and ground cover.  
This project aimed to determine whether meteorological and environmental data could accurately predict the **spread of a forest fire**.

Initially, the problem was approached as a **regression task** to predict burned area (in hectares) based on features such as temperature, humidity, wind speed, rainfall, and fuel moisture indexes.  
After further inspection, we noticed the dataset was heavily skewed towards 0 -> the problem was reframed as a **binary classification task**:  
- **Class 0:** No fire or very small burned area  
- **Class 1:** Significant burned area  

---

## Tech Used
- **Languages & Tools:** Python, Jupyter Notebook, Pandas, NumPy, Matplotlib
- **Machine Learning:**  
  - `scikit-learn` (Linear Regression, Ridge, Lasso, KNN, Logistic Regression, SVM, MLPClassifier, PCA)  
  - `tensorflow` / Keras (1D CNN)
- **Data Preprocessing:**  
  - StandardScaler, MinMaxScaler, PolynomialFeatures, PCA  
  - Log transformation of target variable  
  - Threshold-based binary labeling

---

## Approach
1. **Data Exploration & Visualization**
   - Plotted spatial fire data
   - Examined distributions of target variable
   - Identified heavy skew toward zero area burned
   - Investigated feature correlations with fire area
<img width="694" height="395" alt="image" src="https://github.com/user-attachments/assets/3f268a91-9d81-4ef7-a019-a6d7849d6e8c" />

2. **Regression Attempts**
   - Linear, Ridge, Lasso Regression
   - MLPRegressor (Neural Network)
   - Polynomial Regression  
   → All models performed poorly (R² near zero or negative)

3. **Feature Grouping Experiments**
   - Separated ground, weather, and location features
   - Assessed predictive power individually (low R² scores)

4. **Switch to Binary Classification**
   - Converted target to binary fire/no-fire
   - Tested models: KNN, Logistic Regression, SVM, MLP, PCA + KNN, 1D CNN
   - Explored different thresholds for defining “fire”  
     → Higher thresholds grouping small fires with no-fire improved accuracy

5. **Results**
   - Regression: Poor performance due to weak correlations and high class imbalance
   - Classification: With adjusted thresholds, models like KNN, Logistic Regression, and SVM achieved **~80% test accuracy**

---
