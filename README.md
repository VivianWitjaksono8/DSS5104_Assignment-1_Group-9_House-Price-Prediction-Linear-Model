# Residential Property Price Prediction

This project/assignment develops a **highly accurate and interpretable housing price prediction model** using a **linear regression framework enhanced by advanced feature engineering and regularization techniques**.

Rather than relying solely on complex black-box algorithms, this project demonstrates how **careful feature engineering and regularized linear models** can achieve **near good performance**.

---

# Project Overview

The goal of this project is to build a **robust predictive model for residential property prices** using structured housing data.

Instead of jumping directly to complex machine learning models, the project focuses on:

- progressive **feature engineering**
- **spatial signal extraction**
- **regularized regression**
- thorough **model diagnostics and validation**

Through **several feature engineering stages**, the dataset was transformed into a **robust predictive modeling pipeline**, significantly improving the performance over the baseline model.

---

# Project Assets

### Dataset
```
house_dataset.csv
```

Contains residential housing attributes such as:

- living area size
- property characteristics
- neighborhood signals
- location indicators
- structural attributes

---

### Model Development Notebook
```
Assignment1_DSS5104_Group9.ipynb
```

The notebook contains the **complete modeling workflow**, including:

- data preprocessing  
- feature engineering  
- model development  
- model validation  
- diagnostic analysis  
- benchmark comparison
- key insight of each model

---

# Key Achievements

### Performance Improvement

Baseline model:

```
MAPE = 30.59%
R²   = 0.48
```

Final model:

```
MAPE = 18.43%
R²   = 0.70
```

This represents approximately **40% reduction in prediction error** through systematic feature engineering and model optimization.

---

### Advanced Linear Modeling Techniques

The project evaluates several **regularized linear regression models** to improve generalization and reduce overfitting:

- **Ridge Regression (L2 regularization)**
- **Lasso Regression (L1 regularization)**
- **ElasticNet Regression (combined L1 + L2)**
- **Huber Regression (robust to outliers)**

Additional modeling enhancements include:

- **KNN-based neighborhood price proxies**
- **K-Means clustering for spatial segmentation**
- **polynomial transformations**
- **feature interaction terms**

The final model selected is **ElasticNet**, as it provides the best balance between:

- interpretability  
- coefficient stability  
- predictive performance  

---

# Final Model Performance

| Model | Test MAPE | R² | Notes |
|------|-----------|----|------|
| **ElasticNet** | **18.43%** | **0.70** | Final chosen interpretable model |
| **XGBoost** | 17.24% | 0.71 | Nonlinear benchmark |

Despite being a **linear model**, ElasticNet performs within:

```
1.19% MAPE difference
```

of the **XGBoost benchmark**, highlighting the strength of the engineered feature space.

---

# Key Predictors (ElasticNet Model)

| Feature | Importance | Interpretation |
|-------|------|------|
| zipcode_price_signal | 0.28 | Local market price anchor |
| waterfront | 0.27 | Premium for waterfront properties |
| sqft_living | 0.22 | Interior living space |
| sqft_above | 0.15 | Above-ground area |
| is_historic | 0.13 | Historic home premium |
| neighbor_price_proxy | 0.10 | Neighborhood pricing influence |
| view | 0.09 | Scenic desirability |
| has_basement | 0.07 | Additional functional space |
| condition | 0.07 | Property condition impact |

### Nonlinear Effect

```
sqft_living_squared (-0.08)
```

indicates **diminishing marginal returns for extremely large homes**, reflecting realistic housing market behavior.

---

# Residual & Diagnostic Analysis

Extensive diagnostic testing confirms the statistical reliability of the model.

### Residual Distribution
Residuals follow a **near-normal distribution** with no major bias.

### Homoscedasticity
Variance remains relatively stable across prediction ranges.

### Learning Curve
Indicates **minimal overfitting** and good generalization.

### Prediction Density
Strong overlap between predicted and actual prices within the **core market range ($300K–$700K)**.

### Luxury Segment Behavior
For properties above **$1.5M**, the model shows a **slight conservative bias**, likely due to:

- higher transaction variance  
- fewer high-end observations  

---

# Modeling Workflow

### 1. Baseline Linear Model

```
R² = 0.48
MAPE = 30.59%
```

---

### 2. Feature Engineering

Introduced:

- polynomial features  
- ratio variables  
- interaction terms, etc

Performance improved to:

```
R² = 0.63
MAPE = 21.58%
```

---

### 3. Spatial Feature Engineering

Added neighborhood intelligence using:

- **KNN neighbor price signals**
- **location clustering**

Result:

```
R² = 0.69
MAPE = 18.52%
```

---

### 4. Regularized Regression

Models evaluated:

- Ridge  
- Lasso  
- ElasticNet  
- Huber  

ElasticNet provided the **best bias–variance tradeoff**.

---

### 5. Final Model Selection

**ElasticNet Regression**

```
R² = 0.70
MAPE = 18.43%
```

---

### 6. Nonlinear Benchmark

To evaluate potential upper-bound performance, **XGBoost** was trained as a comparison model.

```
MAPE = 17.24%
```

Only **1.19% improvement**, confirming that the linear model already captures most of the predictive structure.

---

# Executive Summary

Key insights from this project:

✔ Feature engineering dramatically improves predictive accuracy  
✔ Linear models can remain highly competitive with nonlinear models  
✔ ElasticNet provides strong **interpretability + performance**

Most influential drivers:

- zipcode_price_signal  
- waterfront  
- living space variables  
- neighborhood price signals  

This project demonstrates the value of **combining domain-driven feature engineering with regularized regression techniques** for structured tabular datasets.

---

# Getting Started

### Clone Repository

```
git clone <[repository-url](https://github.com/VivianWitjaksono8/DSS5104_Assignment-1_Group-9_House-Price-Prediction-Linear-Model)>
```

### Install Dependencies

```
pip install -r requirements.txt
```

### Run the Notebook

Open:

```
Assignment1_DSS5104_Group9.ipynb
```

---

# Project Structure

```
project
│
├── house_dataset.csv
├── Assignment1_DSS5104_Group9.ipynb
│
├── figures
│   ├── residual_plots
│   ├── density_plots
│   └── feature_importance, etc
│
├── requirements.txt
└── README.md
```

---

# Future Improvements

Potential directions to further enhance the model:

### Feature Engineering
- Explore alternative feature transformations
- Incorporate interaction terms
- Adapt based on model owner’s insights

### Spatial Modeling
- Use more granular location data (latitude & longitude)
- Geographically Weighted Regression (GWR)
- Spatial lag regression models

### Advanced Machine Learning
- Gradient Boosting (XGBoost)
- Stacked ensemble learning

### Temporal & Market Signals
- Include economic indicators
- Housing market cycles
- Interest rates

### Deep Learning for Spatial Representation
- Graph-based neighborhood modeling
- Neural spatial embeddings

# Final Verdict

- **ElasticNet vs XGBoost**: Predictive accuracy is very close (~1.19% difference)
- **Transparency**: ElasticNet is more interpretable and auditable
- **Practical Implementation**: Offers reliable, justifiable forecasts for real estate stakeholders
- **Overall**: ElasticNet balances performance and interpretability, making it a strong choice for deployment

---

# Authors

**DSS5104 Group 9**  
- Vivian Witjaksono – A0326440M  
- Chaisathid Patanan – A0327119E  
- Raissa Shafira – A0329591U  

**National University of Singapore**
