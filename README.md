# 🏠 Residential Property Price Prediction Using Linear Models with Advanced Feature Engineering

This project develops a **highly interpretable yet competitive housing price prediction model** using a **linear regression framework enhanced with advanced feature engineering, spatial signal extraction, and regularization techniques**.

The study demonstrates that **carefully engineered features can significantly close the performance gap between linear and nonlinear models**, achieving results close to XGBoost while maintaining interpretability and stability.

---

# 1. Problem Statement

Accurately predicting residential property prices is a critical task in real estate analytics. However, housing data is highly:

- Nonlinear in structure  
- Spatially dependent  
- Sensitive to interaction effects  

This project investigates whether **linear models, when properly engineered, can achieve performance comparable to nonlinear models** such as XGBoost while maintaining interpretability.

---

# 2. Dataset Description
```
house_dataset.csv
```

The dataset contains structured housing market data, including:

### Structural Features
- bedrooms, bathrooms, floors  
- sqft_living, sqft_above, sqft_basement  
- condition, view, waterfront  

### Location Features
- city  
- zipcode  
- neighborhood-derived signals  

### Temporal Features
- house_age  
- years_since_renovation  

### Engineered Features
- spatial encodings  
- interaction terms  
- nonlinear transformations  

---

# 3. Methodology

## 3.1 Data Preprocessing
Key cleaning steps included:

- Removal of duplicates  
- Handling invalid values (e.g., price = 0, inconsistent sqft structure)  
- Fixing inconsistent renovation records  
- Filtering resale duplicates  

Final dataset size: **4,537 observations**

---

## 3.2 Feature Engineering Strategy

Feature engineering is the core contribution of this project and is categorized as follows:

### (A) Structural Features
Direct housing attributes representing physical property characteristics.

### (B) Nonlinear Transformations
- log(sqft), sqrt(sqft), squared terms  
- Stabilize skewed distributions and variance  

### (C) Spatial Signals
- zipcode_price_signal (target encoding)  
- city_price_signal  
- neighbor_price_proxy (KNN-based)  

### (D) Interaction Features
- sqft × condition  
- sqft × view  
- age × condition  

### (E) Domain-Based Features
- lot_utilization  
- effective_living  
- avg_room_size  

### (F) Clustering Features
- KMeans-based spatial segmentation  

---

## 3.3 Modeling Approach

The project evaluates progressively more complex linear models:

### Baseline Model
- Ordinary Least Squares (OLS)

### Regularized Models
- Ridge Regression (L2)  
- Lasso Regression (L1)  
- ElasticNet (L1 + L2)  
- Bayesian Ridge  
- Huber Regression  

### Advanced Linear Models
- Polynomial Ridge Regression (degree 2)  
- Feature selection (RFECV)  
- PCA + Ridge  
- Spline-based regression  

### Benchmark Model
- XGBoost (tuned via RandomizedSearchCV)

---

## 3.4 Validation Strategy

- Train-test split: 80/20  
- 5-fold cross-validation  
- Robust scaling for regularized models  
- Target encoding using K-fold strategy (to prevent leakage)  

---

# 4. Key Results

## 4.1 Model Performance Comparison

| Model | Test MAPE | R² |
|------|-----------|----|
| Baseline OLS | 30.59% | 0.48 |
| Feature-Engineered Linear Models | ~18.2% | ~0.69 | (approximately)
| **PolyRidge (Best Linear Model)** | **17.91%** | **0.70** |
| XGBoost (Benchmark) | **17.22%** | **0.71** |

---

## 4.2 Key Performance Insight

- Feature engineering reduces error by **~13% from baseline**
- PolyRidge is only **~0.7% MAPE worse than XGBoost**
- Linear models become **highly competitive with nonlinear models**

---

# 5. Final Model: PolyRidge Regression

## 5.1 Why PolyRidge was selected

PolyRidge (Ridge + Polynomial Features) is selected as the final model due to:

- Best trade-off between bias and variance  
- Strong generalization performance  
- Low train-test performance gap  
- Robustness to multicollinearity  
- High interpretability  

---

## 5.2 Key Predictors

| Feature | Importance | Interpretation |
|--------|------------|----------------|
| zipcode_price_signal | Very High | Strongest location-based driver |
| neighbor_price_proxy | Very High | Local market structure effect |
| city_price_signal | High | City-level pricing influence |
| sqft_living_log | High | Core structural size effect |
| sqft_above_log | High | Above-ground area contribution |
| waterfront | High | Premium property indicator |
| view | Moderate | Aesthetic value contribution |
| condition × sqft | Moderate | Interaction effect |

---

# 6. Model Diagnostics

## 6.1 Residual Analysis
- Residuals are centered around zero  
- No strong systematic bias detected  
- Slight underprediction in luxury segment  

## 6.2 Learning Curve Analysis
- Performance stabilizes at ~17–18% MAPE  
- Indicates diminishing returns beyond current feature set  

## 6.3 Multicollinearity
- High VIF observed in spatial features  
- Controlled using Ridge regularization  

## 6.4 Heteroscedasticity
- Significantly reduced after log transformation  

---

# 7. Benchmark Analysis: Linear vs XGBoost

| Model | MAPE | R² | Interpretation |
|------|------|----|---------------|
| PolyRidge | 17.91% | 0.70 | Best linear model |
| XGBoost | 17.22% | 0.71 | Nonlinear benchmark |

### Key Insight:
> The performance gap (~0.7% MAPE) shows that **feature engineering can significantly reduce the need for complex nonlinear models**.

---

# 8. Key Insights

### 1. Location is the dominant pricing factor
Spatial signals outperform structural variables in predictive power.

### 2. Feature engineering is the main performance driver
Spatial encoding alone contributes the largest improvement.

### 3. Linear models remain highly competitive
With sufficient feature engineering, linear models approach nonlinear performance.

### 4. Luxury segment is inherently difficult
High-value properties show greater prediction variance and underestimation.

---

# 9. Limitations

- Limited granularity in spatial data (no latitude/longitude)  
- Luxury segment underrepresentation  
- No external macroeconomic features  
- Linear assumption still limits extreme nonlinear patterns  

---

# 10. Future Work

- Incorporate geospatial coordinates and distance-based features  
- Add macroeconomic indicators (interest rates, inflation)  
- Explore graph-based spatial modeling  
- Improve ensemble learning strategies  
- Apply SHAP for interpretability  

---

# 11. Conclusion

This study demonstrates that **linear regression models, when enhanced with strong feature engineering and regularization, can achieve near state-of-the-art performance in housing price prediction**.

While XGBoost slightly outperforms PolyRidge in accuracy, PolyRidge is preferred for deployment due to:

- Strong interpretability  
- Stability and robustness  
- Minimal overfitting  
- Transparent decision-making  

### Final Conclusion:
> PolyRidge provides the best balance between **accuracy, interpretability, and generalization**, making it the most suitable model for real-world real estate price prediction.

---

# 12. Authors

**DSS5104 Group 9**  
- Vivian Witjaksono – A0326440M  
- Chaisathid Patanan – A0327119E  
- Raissa Shafira – A0329591U  

**National University of Singapore**
