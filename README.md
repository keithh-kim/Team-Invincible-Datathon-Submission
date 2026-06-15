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

### The
