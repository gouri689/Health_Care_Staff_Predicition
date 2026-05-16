# 🏥 Healthcare Staff Availability Prediction

A data science project that analyzes global healthcare leadership data to explore patient admission patterns, hospital resource utilization, and predict **staff availability** using a Random Forest Regressor.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Workflow](#workflow)
- [Key Insights](#key-insights)
- [Model Performance](#model-performance)
- [Getting Started](#getting-started)
- [Results](#results)

---

## Overview

This project performs end-to-end data analysis and machine learning on a healthcare dataset. It covers:

- Exploratory Data Analysis (EDA)
- Data cleaning and preprocessing
- Outlier detection and handling
- Feature engineering and selection
- Predictive modeling using Random Forest

The primary goal is to **predict the number of staff available** in a hospital department based on key hospital resource features.

---

## Dataset

| Property | Details |
|---|---|
| **File** | `GlobalLeadershipProject_v1.csv` |
| **Source** | HuggingFace – Healthcare domain |
| **Key Columns** | `Department`, `Severity of Illness`, `Type of Admission`, `gender`, `health_conditions`, `Stay (in days)`, `Available Extra Rooms in Hospital`, `Ward_Facility_Code`, `Age`, `staff_available` |

---

## Project Structure

```
Healthcare_Project/
│
├── Healthcare_Project.ipynb   # Main Jupyter Notebook
├── README.md                  # Project documentation
└── data/
    └── GlobalLeadershipProject_v1.csv  # Dataset (not included in repo)
```

---

## Tech Stack

| Library | Purpose |
|---|---|
| `pandas` | Data loading, manipulation, and analysis |
| `numpy` | Numerical operations and array handling |
| `matplotlib` | Static visualizations |
| `seaborn` | Statistical data visualizations |
| `scikit-learn` | Model training, preprocessing, and evaluation |

---

## Workflow

### 1. 📥 Data Loading & Inspection
- Loaded dataset using `pandas`
- Checked shape, data types (`info()`), first/random rows
- Computed descriptive statistics (`describe()`)

### 2. 🧹 Data Cleaning
- Identified null values and calculated missing percentage per column
- Imputed missing `health_conditions` values with `'Other'`

### 3. 📊 Exploratory Data Analysis (EDA)
- **Pie chart** – Staff availability distribution by Department
- **Count plot** – Type of Admission vs. Severity of Illness
- **Count plot** – Severity of Illness by Gender
- **Pie chart** – Total patient stay by health condition
- **Bar plot** – Stay (in days) broken down by Severity of Illness and Health Condition

### 4. 🔍 Outlier Detection & Handling
- **Numerical columns** – Visualized using box plots; handled `Available Extra Rooms in Hospital` using the **IQR capping method**
- **Categorical columns** – Rare categories identified by frequency threshold and replaced with `'Other'` for `Department` and `health_conditions`

### 5. ⚙️ Feature Selection
Selected the best 3 features after analysis:

```
Available Extra Rooms in Hospital | Department | staff_available
```

### 6. 🤖 Model Training
- **Algorithm**: `RandomForestRegressor`
- **Hyperparameters**: `n_estimators=125`, `max_depth=10`, `max_features='sqrt'`, `random_state=42`
- **Train/Test Split**: 80% / 20%
- **Encoding**: `OneHotEncoder` (drop='first') for categorical features

### 7. 📈 Model Evaluation
Evaluated using regression metrics:
- **R² Score** (coefficient of determination)
- **MAE** (Mean Absolute Error)
- **RMSE** (Root Mean Squared Error)

---

## Key Insights

- 🏥 **Trauma** departments have the majority of moderate-level admissions; the same trend holds for urgent and emergency types.
- 👩 **Female patients** dominate across all severity categories compared to male and other genders.
- 🌡️ **Extreme severity** patients with **Asthma** have the longest hospital stays.
- 💊 **Moderate severity** stays are most associated with **High Blood Pressure (B.P.)**.
- 🛏️ **Minor severity** stays are largely from the **"Other" health conditions** group.

---

## Model Performance

| Metric | Train Set | Test Set |
|---|---|---|
| **R² Score** | ~(logged) | ~(logged) |
| **MAE** | — | ~(logged) |
| **RMSE** | — | ~(logged) |

> ℹ️ Actual metric values are printed at runtime inside the notebook. Update the table above with your output values.

---

## Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Run the Notebook

```bash
git clone https://github.com/<your-username>/Healthcare_Project.git
cd Healthcare_Project
jupyter notebook Healthcare_Project.ipynb
```

> ⚠️ **Note:** Update the dataset path in the notebook from the local path (`E:\Datasets\...`) to the relative path `./data/GlobalLeadershipProject_v1.csv` before running.

---

## Results

The Random Forest Regressor successfully learned patterns from the cleaned healthcare dataset. With careful feature selection and outlier handling, the model generalizes well on the test set, making it useful for **hospital resource planning and staffing decisions**.

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
