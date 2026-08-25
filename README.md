# Sales Prediction Using Python

A practical machine-learning project that predicts product sales from advertising spend across **TV**, **Radio**, and **Newspaper** channels. The project uses exploratory data analysis, preprocessing, visualization, and regression-model comparison in a Jupyter Notebook.

## Project Overview

Marketing teams can use this type of analysis to understand how advertising investment relates to sales and to estimate expected sales for future campaign budgets.

The notebook:

- explores the structure and quality of the advertising dataset;
- checks for missing values and duplicate records;
- visualizes relationships between advertising channels and sales;
- removes an identified high-value Newspaper advertising outlier;
- standardizes the input features;
- trains and evaluates Linear Regression, Decision Tree, and Random Forest models;
- compares model performance using regression metrics and R² visualizations.

## Results

The notebook reports the following conclusions:

| Model | Reported test result |
| --- | --- |
| Linear Regression | Test R²: **0.9099** |
| Decision Tree | Performs well, with signs of overfitting |
| Random Forest | Test R²: **0.9792**, RMSE: **0.7489**, MAE: **0.6069** |

Based on the reported results, **Random Forest is the recommended model** for this dataset. TV and Radio advertising show the strongest relationship with Sales.

> The metrics above are the results recorded in the notebook. Re-run the notebook in your own environment to reproduce and verify them.

## Repository Contents

```text
.
├── main.ipynb    # Exploratory analysis, model training, evaluation, and visualizations
└── README.md     # Project documentation
```

## Dataset

The analysis expects an advertising dataset with these columns:

- `TV`
- `Radio`
- `Newspaper`
- `Sales`

The original notebook loads the CSV from a local Windows path:

```python
df = pd.read_csv("C:\\Users\\Aalhad Ramteke\\Downloads\\Advertising data.csv")
```

Because that path is machine-specific, place the CSV in your preferred project directory and update the `pd.read_csv(...)` line before running the notebook. The source CSV is included in this repository.

## Getting Started

### Prerequisites

- Python 3.9 or later
- Jupyter Notebook or VS Code with the Jupyter extension

### Installation

Create and activate a virtual environment, then install the required packages:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install numpy pandas seaborn matplotlib scikit-learn xgboost graphviz jupyter
```

> The notebook imports Graphviz for optional tree visualization. Depending on your operating system, the Graphviz system application may also need to be installed and added to `PATH`.

### Run the Notebook

1. Open `main.ipynb` in Jupyter Notebook or VS Code.
2. Update the dataset path in the data-loading cell.
3. Select the configured Python environment as the notebook kernel.
4. Run the cells from top to bottom.

## Methodology

### Exploratory Data Analysis

The notebook inspects the first and last records, dimensions, data types, missing values, duplicates, correlations, pairwise relationships, and advertising-channel scatter plots.

### Preprocessing

- Drops the `Unnamed: 0` index column.
- Treats `Sales` as the dependent variable.
- Uses `TV`, `Radio`, and `Newspaper` as predictors.
- Removes records where `Newspaper > 90` based on the identified outlier.
- Applies `StandardScaler` to the predictor variables.
- Splits the data into 80% training and 20% testing sets with `random_state=0`.

### Models

The following regression models are compared:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor

Evaluation includes:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- Training R²
- Testing R²
- Adjusted R²

## Limitations and Next Steps

- The dataset is small, so results may not generalize to larger campaigns.
- The notebook uses a single train-test split; cross-validation would provide a more robust estimate of generalization performance.
- Hyperparameter tuning, feature engineering, and model persistence could be added for production use.
- A future version could expose the selected model through a small web API or interactive dashboard.
