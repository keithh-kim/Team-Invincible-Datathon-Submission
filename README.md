# Team-Invincible-Datathon-Submission
# Predicting Household Economic Resilience in Kenya 🇰🇪
### Strathmore Data Community × iLabAfrica | DataSprint 2026

---

## 📋 1. Project Overview & Objective
This project leverages advanced machine learning techniques to analyze, predict, and understand household financial wellbeing trajectories using national survey data. In an economic landscape where **52.6% of respondents report a deteriorating financial situation** compared to the previous year, this pipeline serves as a data-driven framework to help stakeholders identify socio-economic vulnerabilities early.

### Core Objective:
* Build an optimized classification engine to accurately predict whether an individual's financial status will **Improve**, **Stay the same**, or **Worsen**.
* Extract and rank key predictive feature weights to support evidence-based financial and policy interventions across Kenya.

---

## 🛠️ 2. Tools & Technologies Used
* **Data Manipulation & Analysis:** `Python`, `Pandas`, `NumPy`
* **Data Visualization:** `Matplotlib`, `Seaborn`
* **Machine Learning Frameworks:** `Scikit-Learn`, `XGBoost`, `CatBoost`
* **Imbalance Engineering:** `Imbalanced-Learn (SMOTE)`

---

## 🧼 3. Data Preprocessing & Cleaning Pipeline
To ensure complete reproducibility and model integrity, the raw survey data went through a rigorous, step-by-step engineering sequence:

1. **Target Imputation:** Diagnosed a 27.5% missing value gap in the `barriers_bank` column. Following institutional data guidelines, missing entries were structurally imputed with `'No barrier'`, as these entries represented individuals who already hold formal bank accounts.
2. **Text Standardization:** Applied global whitespace stripping and case normalization across all categorical text features to eliminate duplicated entry states (e.g., matching regional variations across counties) while explicitly preserving target label casing.
3. **Feature Expansion (One-Hot Encoding):** Utilized a binary matrix expansion (`pd.get_dummies`) with dummy dropping to cleanly transform processed categorical strings into a 109-column mathematical matrix ready for Scikit-Learn classifiers.

---

## 🤖 4. Modeling Methodology & Strategy
The cleaned dataset, consisting of **20,871 records across all 47 Kenyan counties**, was split into an 80/20 stratified train-test distribution to perfectly lock in and preserve target class ratios.

### Handling Class Imbalance:
Because the target variable is heavily skewed toward financial decline (52.6% Worsened), simple accuracy metrics are a dangerous illusion. A model could blindly guess "Worsened" for every row and score highly while failing completely. To solve this:
* The training stream was evaluated strictly using the **Weighted F1-Score**.
* A **SMOTE (Synthetic Minority Over-sampling Technique)** pipeline was integrated alongside cost-sensitive tree weight balancing to protect minority prediction classes (the individuals who actually improved).

### The Model Tournament:
We pitted five distinct algorithmic architectures against each other:
1. **Logistic Regression** (Baseline normalized linear model)
2. **Decision Tree Classifier** (Interpretable depth splitting)
3. **Random Forest Ensemble** (Bagging robustness)
4. **CatBoost Classifier** (Optimized categorical gradient boosting)
5. **XGBoost Classifier** (Extreme Gradient Boosting)

---

## 🏆 5. Key Findings & Model Performance

### The Champion Model:
Following an exhaustive hyperparameter grid search and optimization sequence, **XGBoost emerged as our absolute top-performing engine**, delivering the highest verified **Weighted F1-Score** on unseen test data.

### Top 4 Predictive Feature Drivers:
The feature importance matrix extracted from our champion model proved that financial deterioration follows clear systemic patterns:
1. **Monthly Income Structures:** The foundational economic baseline determining household resource allocation.
2. **Financial Shocks (`experienced_shock`):** The heaviest categorical trigger. Sudden climate, health, or market shocks act as immediate catalysts forcing families into economic distress.
3. **Loan Default History (`defaulted`):** Highly concentrated among struggling cohorts, signaling a rigid, high-risk digital debt trap cycle.
4. **Household Size:** High dependency ratios directly dilute monthly income buffers, leaving zero margin to withstand economic disruptions.

---

## 🏛️ 6. Actionable Strategic Recommendations

### 1. For Policymakers (Shift from Credit to Shock Buffers)
Move away from relying heavily on short-term micro-credit injections as a cure-all. Instead, prioritize building national index-based weather and crop insurance infrastructure to cushion rural farming communities against climate shocks, alongside expanded social protection cash transfers for large households.

### 2. For Commercial Banks & FinTechs (Shock-Adaptive Product Design)
Abandon rigid, high-frequency repayment frequencies for low-income segments. Leverage predictive machine learning models to design flexible lending lines that automatically pause, reduce interest, or restructure repayments during regional or environmental shock windows to prevent loan default traps.

### 3. For NGOs & Development Partners (Predictive Resource Triaging)
Utilize this optimized XGBoost framework to run predictive vulnerability mapping. By ingesting local dependency ratios and economic indicators, partners can route direct emergency relief and asset-building programs to at-risk rural households *before* regional crises fully manifest.

---
*Developed as part of DataSprint 2026 submission requirements.*
