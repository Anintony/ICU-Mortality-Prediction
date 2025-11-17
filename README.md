# Predicting In-Hospital Mortality using MIMIC-III Data

This is a machine learning project that builds a model to predict in-hospital mortality for patients in the Intensive Care Unit (ICU), based on the MIMIC-III dataset.

The final **XGBoost model** achieved a **93% accuracy** and **0.88 AUC** on the test set, demonstrating a strong balance between precision and recall for the imbalanced dataset.

- **Authors:** Jingyi(Jenny) Chen, Yien(Martina) Chen, Nuonan(Juana) Zhang
- **Full Report:** [`/report/predict_mortality.pdf`](./report/predict_mortality.pdf)

---

## View the Reports (HTML)

For easy viewing, the rendered HTML reports for each step are available in the `/html/` folders.

* **[Phase 1: Data Cleaning (HTML)](https:/github.com/github.com/Anintony/ICU-Mortality-Prediction/blob/main/html_reports/02_data_cleaning.html))**
* **[Phase 2: Exploratory Data Analysis (HTML)]((https://github.com/Anintony/ICU-Mortality-Prediction/blob/main/html_reports/03_EDA.html))**
* **[Phase 3: Feature Selection and Engineering (HTML)](https://github.com/Anintony/ICU-Mortality-Prediction/blob/main/html_reports/04_Feature_Selection_and_Engineering.html)**
* **[Phase 4: Modeling and Experiments (HTML)](https://github.com/Anintony/ICU-Mortality-Prediction/blob/main/html_reports/05_Modeling_and_Experiments.html)**

---

## 1. Project Objective

The goal was to develop a robust classification model to identify high-risk patients. This is crucial for clinical decision support and resource allocation in critical care. The primary challenge was handling the **highly imbalanced dataset** (more survivors than non-survivors).

## 2. Tech Stack

- **Data Analysis:** Python, Pandas, NumPy
- **Modeling:** Scikit-learn, XGBoost
- **Visualization:** Matplotlib, Seaborn

## 3. Methodology

1.  **Data Preprocessing:** Merged and cleaned data from 7 different MIMIC-III tables. Handled extreme outliers (e.g., age > 100), missing values, and skewed distributions.
2.  **Feature Engineering:** Simplified high-cardinality categorical features (like `language`, `religion`) and applied One-Hot Encoding. Standardized continuous features.
3.  **Model Comparison:** Evaluated three models, focusing on **Recall** and **F1-Score** for the minority class (class 1: non-survivors).

## 4. Key Results (Model Comparison)

| Model | AUC | Minority (1) Precision | Minority (1) Recall | Minority (1) F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| Logistic Regression | 0.85 | 0.26 | **0.80** | 0.39 |
| Random Forest | **0.89** | **0.69** | 0.45 | 0.54 |
| **XGBoost (Selected)** | 0.88 | 0.67 | 0.49 | **0.57** |

**Conclusion:** XGBoost provided the best balance, significantly reducing the "false alarms" of Logistic Regression and improving on the Random Forest's ability to identify high-risk patients.

## 5. How to Replicate

1.  **Code:** The full analysis is available in the Jupyter Notebooks in the `/code/` folder.
2.  **Data:** The project uses the [MIMIC-III dataset](https://physionet.org/content/mimiciii/1.4/), which requires access permission from PhysioNet. The code assumes the raw data tables are available.

## 6. Repository Structure

```
.
├── /code/
│   ├── 01_1_VASOPRESSOR_USE_flag.ipynb
│   ├── 01_2_ventilation__flag.ipynb
│   ├── 01_3_data aggregation.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_EDA.ipynb
│   └── 04_Feature_Selection_and_Engineering.ipynb
│   └── 05_Modeling_and_Experiments.ipynb            
├── /html_reports/
│   ├── 01_1_VASOPRESSOR_USE_flag.html
│   ├── 01_2_ventilation__flag.html
│   ├── 02_data_cleaning.html
│   ├── 03_EDA.html
│   └── 04_Feature_Selection_and_Engineering.html
│   └── 05_Modeling_and_Experiments.html   
├── /report/
│   └── predict_mortality.pdf
└── README.md               
```
