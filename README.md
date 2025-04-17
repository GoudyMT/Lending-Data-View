# Loan Default Prediction Project

## Overview
This project is part of the **Data and Programming Foundations for AI/ML** final project, focusing on predicting loan defaults using the Lending Club dataset. The goal is to apply data analytics techniques to explore, clean, and prepare the dataset for potential machine learning modeling. The project currently covers data loading, verification, exploratory data analysis (EDA), and data cleaning, laying a strong foundation for future modeling.

## Dataset
- **Source**: Lending Club loan data, available from [Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club).
- **Files**:
  - `lending_club_loan_data.csv`: Main dataset with loan-level data (e.g., `loan_amnt`, `int_rate`, `loan_status`).
  - `lending_club_info.csv`: Metadata describing column meanings.
- **Key Variables**:
  - **Target**: `loan_status` (e.g., "Fully Paid", "Charged Off").
  - **Features**: Numerical (e.g., `loan_amnt`, `int_rate`, `dti`), categorical (e.g., `grade`, `home_ownership`, `purpose`), and date (e.g., `earliest_cr_line`).
- **Size**: Approximately 396,030 rows after cleaning, 44 columns (including one-hot encoded features).

## Project Objectives
1. **Verify Dataset**: Ensure the dataset has the correct unit of observation (individual loans), granularity (loan-level), and required variables.
2. **Exploratory Data Analysis (EDA)**: Analyze feature distributions and relationships with `loan_status` to identify predictive patterns.
3. **Data Cleaning**: Handle missing values, filter `loan_status` for binary classification, encode categorical variables, and prepare the dataset for modeling.
4. **Prepare for Modeling**: Save a cleaned dataset (`lending_club_cleaned.csv`) for future machine learning tasks.

## Steps Completed
The project is implemented in a Jupyter notebook (`analysis.ipynb`). The following steps have been completed:

### 1. Data Loading and Verification
- Loaded `lending_club_loan_data.csv` and `lending_club_info.csv` using Pandas.
- Verified:
  - **Unit of Observation**: Individual loan applicants (confirmed via unique rows).
  - **Granularity**: Loan-level data with features like `loan_amnt`, `int_rate`, `loan_status`.
  - **Variables**: All expected columns present (e.g., `loan_amnt`, `int_rate`, `loan_status`, `home_ownership`).
  - **Data Sufficiency**: ~396,030 rows, sufficient for analysis, with minimal missing values in key columns.

### 2. Exploratory Data Analysis (EDA)
- **Initial EDA**:
  - Visualized distributions of `loan_amnt` (right-skewed), `int_rate` (clustered 5–20%), and `grade` (more A–C grades).
  - Explored `int_rate` vs. `loan_status` (higher rates for "Charged Off" loans).
- **Findings**:
  - `loan_amnt` and `int_rate` show potential predictive power.
  - Class imbalance in `loan_status` (~80% Fully Paid, ~20% Charged Off) noted for future modeling.

### 3. Data Cleaning
- **Missing Values**:
  - Numerical columns (e.g., `revol_util`, `mort_acc`): Imputed with median.
  - Categorical columns (e.g., `emp_length`): Imputed with mode.
  - Non-key columns (e.g., `emp_title`, `title`): Retained with missing values (~22,927 and ~1,756 missing, respectively).
  - No columns dropped (none >50% missing).
- **Loan Status**:
  - Filtered to "Fully Paid" and "Charged Off".
  - Mapped to binary: 0 (Fully Paid), 1 (Charged Off).
- **Categorical Encoding**:
  - One-hot encoded: `home_ownership`, `verification_status`, `purpose` (e.g., `home_ownership_RENT`, `purpose_debt_consolidation`).
  - Label encoded: `grade`, `sub_grade` (converted to numerical).
  - `emp_length`: Converted to numerical (0–10 years).
- **Dates**: `earliest_cr_line` converted to `years_since_cr_line` (years since credit line opened).
- **Output**: Saved cleaned dataset as `lending_club_cleaned.csv` (396,030 rows, 44 columns).

## Project Structure
- **Files**:
  - `analysis.ipynb`: Jupyter notebook with all code for data loading, verification, EDA, and cleaning.
  - `lending_club_loan_data.csv`: Original dataset.
  - `lending_club_info.csv`: Column descriptions.
  - `lending_club_cleaned.csv`: Cleaned dataset for future use.
- **Dependencies**:
  - Python 3.12.1
  - Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

## Setup Instructions
1. **Clone Repository** (if applicable):
   ```bash
   git clone <repository-url>
   cd loan-default-prediction
   ```
2. **Install Dependencies**:
   Ensure Python 3.12.1 is installed, then install required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. **Prepare Dataset**:
   - Place `lending_club_loan_data.csv` and `lending_club_info.csv` in the project directory.
   - Alternatively, download from [Kaggle](https://www.kaggle.com/datasets/wordsforthewise/lending-club).
4. **Run Notebook**:
   - Launch Jupyter Notebook:
     ```bash
     jupyter notebook
     ```
   - Open `analysis.ipynb` and execute all cells sequentially.
5. **Outputs**:
   - Visualizations (e.g., histograms, count plots, boxplots) saved in the notebook.
   - Cleaned dataset saved as `lending_club_cleaned.csv`.

## Results
- **Dataset Ready for Modeling**:
  - Cleaned dataset with 396,030 rows and 44 columns.
  - No missing values in key columns; minor missingness in `emp_title` (~5.8%) and `title` (~0.4%).
  - `loan_status` is binary, with ~80% Fully Paid and ~20% Charged Off.
- **EDA Insights**:
  - Higher `int_rate` associated with "Charged Off" loans.
  - `loan_amnt` and `grade` are potential predictors.
  - Class imbalance noted, suggesting future use of techniques like SMOTE.

## Future Work
- **Modeling**: Train baseline models (e.g., logistic regression, decision tree) to predict `loan_status`.
- **Class Imbalance**: Apply SMOTE or class weights to address the ~80/20 split in `loan_status`.
- **Feature Engineering**: Create new features (e.g., debt-to-income ratios).
- **Advanced Models**: Explore random forests or gradient boosting for improved performance.

## Acknowledgments
- **Dataset**: Lending Club via Kaggle.
- **Guidance**: xAI’s Grok 3 for step-by-step assistance in data verification, EDA, and cleaning.
- **Course**: Data and Programming Foundations for AI/ML, providing the framework for this project.

## Contact
For questions or feedback, contact GoudyMT at goudymt@gmail.com

---
*Last Updated: April 16, 2025*