# Geely Auto Car Price Prediction (Multiple Linear & Polynomial Regression)

## 📌 Project Overview
This project focuses on predicting the price of cars for **Geely Auto**, a Chinese automobile manufacturer aiming to enter the US market. The primary objective is to analyze the factors influencing car prices and develop an optimal pricing model to help the company set competitive prices for its products.

The entire exploratory data analysis (EDA), feature selection, and predictive modeling were conducted using **JMP software**.

## 🛠️ Tools & Technologies
- **JMP Software:** Used for EDA, statistical testing, interaction analysis, Outlier Detection, and Regression Modeling.
- **Statistical Techniques:** Descriptive Statistics, Multiple Linear Regression, Polynomial Regression, Stepwise Regression, K-Fold Cross-Validation, Box-Cox Transformation, and Residual Analysis.

## 📂 Dataset Overview
The analysis is based on the `geely.csv` dataset, which contains 205 observations and 22 variables related to car specifications and pricing. The target variable (Response) is **Price**.

**Key Features (Predictors) Analyzed:**
- **Categorical Variables:** Fuel Type (gas/diesel), Aspiration (std/turbo), Door Number, Car Body (sedan, hatchback, etc.), Drive Wheel (fwd, rwd, 4wd), Engine Location, Engine Type, Cylinder Number, and Fuel System.
- **Numerical Variables:** Wheelbase, Car Length, Car Width, Car Height, Curb Weight, Engine Size, Bore Ratio, Stroke, Compression Ratio, Horsepower, Peak RPM, City MPG, and Highway MPG.

## 🚀 Analytical Approach & Methodology

### 1. Exploratory Data Analysis (EDA)
An initial descriptive analysis was performed to understand the relationship between each predictor and the car price:
- **Categorical Insights:** Rear-wheel drive cars, cars with rear-placed engines, and cars with 'ohcv' engine types showed significantly higher average prices.
- **Numerical Insights (Correlation):** Variables like Wheelbase, Car Length/Width/Height, Curb Weight, Engine Size, and Horsepower demonstrated a positive linear relationship with Price. Conversely, Peak RPM and Fuel Efficiency (City/Highway MPG) showed a negative relationship (higher efficiency/RPM correlates with lower prices).

### 2. Feature Selection & Interaction Analysis
- **Significant Variables:** Factors impacting the price were selected based on a significance level (p-value <= 0.10). Insignificant variables were removed.
- **Interaction Effects:** To capture complex relationships, interaction terms between variables were evaluated. Using **K-Fold Cross-Validation (k=10)** and **Stepwise Regression**, only the interactions that maximized the $R^2$ value were retained in the model.

### 3. Predictive Modeling
- **Initial Model:** A standard Multiple Linear Regression model yielded an $R^2$ of 0.9263 and an Adjusted $R^2$ of 0.9132.
- **Optimized Polynomial Model:** By incorporating significant interaction terms and utilizing K-Fold validation, a highly accurate polynomial regression model was developed. 
  - **Final Model Performance:** $R^2 = 0.9935$, Adjusted $R^2 = 0.9814$, RMSE = 1087.5.
  - The minimal difference between $R^2$ and Adjusted $R^2$ (less than 0.012%) indicates that the model is **not overfitted**.

### 4. Model Validation & Residual Analysis
To ensure the reliability of the model, regression assumptions were checked:
- **Normality of Residuals:** Initial tests showed non-normal distribution. A **Box-Cox transformation** ($\lambda = 0.625$) was applied to the target variable to normalize the residuals.
- **Heteroscedasticity:** Variance of errors was checked. The Box-Cox transformation also helped stabilize the variance across different price levels.
- **Outlier Detection:** Influential outliers were identified using **Cook's D Influence** metric. Observations with a Cook's D value significantly higher than 1 (specifically rows 144 and 135) were removed, which slightly adjusted the $R^2$ to 0.9920 but improved the RMSE to 1048.4, leading to a more robust model.

## 📁 Repository Structure
- `geely.csv`: The raw dataset containing car specifications and pricing.
- `Regression-NahidGholizadeh.pdf`: The detailed statistical report generated using JMP, documenting all charts, variable distributions, interaction selection steps, and final model validation.

```text
Geely-Auto-Car-Price-Prediction-Regression/
│
├── data/
│   └── geely.csv
│
├── Report/
│   └── Geely-Auto-Car-Price-Prediction.pdf
│
└── README.md
```

## 💻 How to Use
1. Clone this repository.
2. Review the `Geely-Auto-Car-Price-Prediction.pdf` report for a deep dive into the statistical distributions, scatter plots, and the step-by-step methodology used to refine the regression model.
3. The dataset (`geely.csv`) can be used to replicate the analysis in JMP, Python, or R.