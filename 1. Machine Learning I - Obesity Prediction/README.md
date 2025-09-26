# Obesity Prediction

## 📌 Overview
- **Course:** Machine Learning I — NOVA IMS (2024/25)  
- **Type:** Group Project  
- **Goal:** Predict obesity levels based on lifestyle habits, demographics, and health indicators.  
- **Dataset:** 1,611 survey responses (train) and 501 unseen cases (test).  
- **Deliverables:** Report, notebook, Kaggle submission.  

Obesity is one of the most urgent public health challenges worldwide. The aim of this project was to
develop a machine learning model capable of predicting an individual's obesity level and to extract
insights that can guide public health strategies.

---

## 📊 Dataset
- **Source:** Survey data (ages 16–56, LatAm region)  
- **Features:** Lifestyle (eating habits, alcohol, smoking, exercise, water, veggies), demographics (age, gender, marital status, siblings, region), and physical indicators (weight, height).  
- **Target:** `obese_level` (7 categories: Insufficient Weight, Normal Weight, Overweight I, Overweight II, Obesity I, Obesity II, Obesity III).  

---

## ⚙️ Methodology
### Data Preprocessing
- Dropped irrelevant columns (`marital_status`, `region`)  
- Outlier removal (`age <16 or >56`, `weight >167kg`, `height <141cm`)  
- Encoding categorical variables with custom mapping  
- Handling missing values via **KNN Imputer**, **Iterative Imputer**, and constants  
- Feature engineering:  
  - **BMI Class** (age-adjusted, WHO & CDC standards)  
  - **Life Index** (composite lifestyle score)  
- Normalization with `StandardScaler`  

### Feature Selection
- **Recursive Feature Elimination (RFE)**  
- **Random Forest Feature Importance**  
- **Chi-Square Tests** for categorical variables  
- Dropped weak predictors (`monitor_calories`, `siblings`, `smoke`)  

### Modeling
- Models tested: Random Forest, Gradient Boosting, Decision Tree, AdaBoost, Bagging, MLP  
- Validation: Stratified 10-Fold Cross-Validation  
- Metric: **Macro F1-score** (suited for class imbalance)  
- Hyperparameter tuning: `RandomizedSearchCV` + `HalvingGridSearchCV`  

---

## 🏆 Results
- **Best Model:** Gradient Boosting Classifier (Halving Random Search optimized)  
- **Performance:**  
  - Validation Macro F1 ≈ **0.95**  
  - Kaggle Test Score ≈ **0.96**  
- **Key Features:** BMI class, weight, age, gender, lifestyle habits  
- **Limitations:** Model struggles to differentiate **Normal Weight vs Overweight I** due to BMI’s limited ability to capture body composition.  

---

## 📈 Insights
- Strong correlation between **parental overweight** and obesity.  
- **Physical activity** has protective effect (negative correlation with obesity).  
- Lifestyle factors like **water intake**, **vegetables**, and **snacking frequency** play a measurable role.  
- Obesity Type III most prevalent among **ages 26–31**, with rising trend in younger cohorts.  

---

## 🧠 Key Learnings
- Importance of advanced preprocessing and feature engineering  
- Need for balanced evaluation metrics in imbalanced multi-class problems  
- Trade-off between model accuracy and interpretability  
- Practical public health insights derived from feature importances 
