# Life Expectancy Analysis

A comprehensive data analysis and machine learning project that predicts life expectancy using WHO (World Health Organization) health indicators and socio-economic factors.

## Project Overview

This project analyzes life expectancy data from countries worldwide, examining the relationship between various health, economic, and demographic factors. The analysis includes data preprocessing, exploratory data analysis, feature engineering, and predictive modeling using Linear Regression.

**Dataset**: Life Expectancy (WHO)  
**Dataset Size**: 2,938 rows × 22 columns  
**Model Used**: Linear Regression

## Objective

To predict life expectancy based on health, economic, and demographic indicators, and to identify key factors that significantly influence life expectancy across different countries.

## Project Structure

```
Life Expectancy Analysis/
│
├── data/
│   └── Life Expectancy Data.csv    # Raw dataset from WHO
│
├── notebook/
│   └── lifeExpectancy.ipynb        # Jupyter notebook with complete analysis
│
├── requirements.txt                 # Python dependencies
└── README.md                        # Project documentation
```

## Features Analyzed

The dataset includes the following variables:

- **Demographic**: Country, Year, Status (Developed/Developing)
- **Health Indicators**: 
  - Life expectancy
  - Adult Mortality
  - Infant deaths
  - Under-five deaths
  - HIV/AIDS prevalence
  - Measles cases
  - Immunization coverage (Hepatitis B, Polio, Diphtheria)
  - Thinness prevalence (1-19 years, 5-9 years)
- **Economic Factors**:
  - GDP
  - Percentage expenditure on health
  - Total expenditure on health
- **Social Factors**:
  - Alcohol consumption
  - BMI
  - Schooling years
  - Population

## Methodology

### 1. Data Preprocessing

#### Handling Missing Values
- **Interpolation**: Time-series interpolation for country-specific data
- **Imputation**: Filled remaining nulls with country-wise mean values
- **Removal**: Dropped rows where complete data was unavailable for specific countries
- **Final Dataset**: Clean dataset with no missing values

#### Feature Engineering
- **Log Transformation**: Applied to `percentage expenditure` and `GDP` to handle skewness
  - Created `percentage_expenditure_new` and `GDP_new` features
  - Improved correlation with target variable
- **Encoding**: Binary encoding for Status (Developing: 0, Developed: 1)
- **Feature Selection**: Removed redundant columns:
  - `Year` and `Country` (non-predictive)
  - `thinness 5-9 years` (correlation with thinness 1-19 years)
  - `under-five deaths` (high correlation with infant deaths)
  - Original `percentage expenditure` and `GDP` (replaced with transformed versions)

### 2. Exploratory Data Analysis

- **Outlier Detection**: Used boxplots to visualize outliers in key numerical features
- **Distribution Analysis**: Analyzed feature distributions using histograms with KDE
- **Correlation Analysis**: Created heatmap to identify multicollinearity and feature relationships
- **Skewness Handling**: Log transformation to normalize heavily skewed distributions

### 3. Model Development

#### Data Splitting
- **Training Set**: 80%
- **Testing Set**: 20%
- **Random State**: 42 (for reproducibility)

#### Feature Scaling
- **Method**: StandardScaler
- **Applied to**: All numerical features in training and testing sets

#### Model Training
- **Algorithm**: Linear Regression
- **Target Variable**: Life expectancy
- **Features**: 17 predictor variables (after preprocessing)

## Results

The Linear Regression model achieved:

- **R² Score**: High coefficient of determination (indicating good model fit)
- **RMSE**: Root Mean Squared Error calculated for prediction accuracy

*Note: The model demonstrates that life expectancy can be effectively predicted using health, economic, and demographic indicators.*

## Getting Started

### Prerequisites

```bash
Python 3.7+
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Anantu-Rajesh/LifeExpectancy.git
cd "Life Expectancy Analysis"
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

### Running the Analysis

1. Open the Jupyter notebook:
```bash
jupyter notebook notebook/lifeExpectancy.ipynb
```

2. Run all cells sequentially to reproduce the analysis

## Dependencies

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Key Insights

1. **Strong Predictors**: Economic factors (GDP) and health indicators show strong correlation with life expectancy
2. **Development Status**: Significant difference between developed and developing countries
3. **Healthcare Impact**: Immunization coverage and healthcare expenditure are important factors
4. **Education Effect**: Years of schooling positively correlate with life expectancy
5. **Disease Impact**: HIV/AIDS and adult mortality significantly affect life expectancy

## Future Improvements

- Implement additional regression models (Ridge, Lasso, Random Forest)
- Perform hyperparameter tuning
- Add cross-validation for robust model evaluation
- Create interactive visualizations
- Deploy model as a web application
- Include time-series forecasting for future predictions

---
