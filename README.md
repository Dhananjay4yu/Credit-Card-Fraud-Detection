# 💳 Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-orange?logo=scikit-learn)
---

## 📌 Project Overview  
Credit card fraud is one of the biggest challenges in the financial sector.  
This project demonstrates an **end-to-end pipeline** for fraud detection using:  

✅ Exploratory Data Analysis (EDA)  
✅ Data preprocessing & feature scaling  
✅ Handling imbalanced data (SMOTE, Oversampling, Undersampling, ADASYN)  
✅ Building & tuning multiple ML models  
✅ Evaluating performance with **ROC-AUC, Precision, Recall, F1-score**  
✅ Business-oriented cost-benefit analysis  

---

## 📊 Exploratory Data Analysis (EDA)  
- Dataset is **PCA-transformed**, so no additional outlier treatment needed.  
- Only `Amount` column required **feature scaling**.  
- Skewness mitigated with **PowerTransformer** → variables became normally distributed.  
- Severe class imbalance observed (only **0.17% fraudulent transactions**).  

---

## ⚙️ Data Preprocessing  
- **Scaling:** Applied only on `Amount`.  
- **No leakage:** Fit scaler only on **train**, transform **test**.  
- **Balancing techniques used:**  
  - Undersampling  
  - Oversampling  
  - SMOTE  
  - ADASYN  

---

## 📈 Model Building & Evaluation  

### 🔎 Algorithms Explored
- **Baseline:** Logistic Regression, Decision Tree  
- **Ensemble:** Random Forest, XGBoost  

❌ **Not Used:**  
- **SVM** → Too computationally expensive on large datasets.  
- **KNN** → Memory-inefficient and slow for large datasets.  

### 🔧 Hyperparameter Tuning  
- **Grid Search + K-Fold CV**
- **OPTUNA based tuning- uses Baysean search**
- Tuned key params like **C (Logistic Regression)**, tree depth, learning rates, etc.  

### 📊 Metrics Used
- ROC-AUC (primary)  
- F1-Score  
- Precision & Recall  
- Confusion Matrix  

---

## 🏆 Model Performance  

**Example (SMOTE + XGBOOST):**  
- **Accuracy:** `0.9993`  
- **Sensitivity (Recall):** `0.6591`  
- **Specificity:** `0.9999`  
- **F1-Score:** `0.7688`  
- **ROC-AUC:** ~`0.97` (test set)  

---

## 🏅 Best Model Selection  
- **Undersampling** → Good, but lost valuable info.  
- **SMOTE & ADASYN** → Produced strong, balanced results.  

✅ **Best Choice:** **Logistic Regression + SMOTE**  
- Train ROC-AUC: `0.99` | Test ROC-AUC: `0.97`  
- High Recall → catches fraudulent transactions effectively  
- Simple, interpretable, low-resource model  

---

## 💡 Business Insights  

### Small Transaction Banks 🏦  
- Need **high precision** → fewer false fraud alerts → reduces manual verification cost  

### Large Transaction Banks 💰  
- Need **high recall** → avoid missing high-value fraud cases  

### Cost-Benefit Tradeoff  
- Complex models (Random Forest, XGBoost) = high infra cost 🚨  
- Logistic Regression = efficient, interpretable, cost-effective ✅  

---
## ✨ Future Work  
- Try **Deep Learning (Autoencoders, LSTMs)** for anomaly detection  
- Deploy as **real-time API** for banks  
- Explore **cost-sensitive learning**  

