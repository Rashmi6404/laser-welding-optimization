# Laser Welding Process Optimization using Machine Learning

An end-to-end machine learning workflow for predicting laser-welding outcomes and identifying promising process parameters through constrained optimization.

## Project Goal

The notebook models laser-welding process behavior from experimental data and uses the trained models to support process optimization.

### Predictions

**Regression targets**
- Weld width — steel (µm)
- Weld width — copper (µm)
- Weld depth — copper (µm)
- Gap (µm)

**Classification target**
- Cracking in the weld metal: Yes / No

## Machine Learning Approach

1. Load and inspect the experimental welding dataset
2. Clean irrelevant columns and encode the crack target
3. Engineer process features such as heat input and interaction terms
4. Train Random Forest regression models for weld-quality measurements
5. Train a Random Forest classifier for crack prediction
6. Use SMOTE to handle class imbalance in the classification task
7. Evaluate models using R², MAE, ROC-AUC, classification reports, confusion matrices, and feature importance
8. Use Optuna to search for process parameters that maximize predicted copper weld depth subject to engineering constraints

## Feature Engineering

The notebook derives features including:

- `heat_input`
- `heat_input_sq`
- `speed_sq`
- `focal_abs`
- `heat_x_angular`
- `gas_x_heat`
- `heat_x_material`
- `power_x_material`

## Recorded Optimization Result

The notebook's recorded optimization run used:

- Maximum crack probability: **20%**
- Steel weld-width range: **1800–2500 µm**
- Objective: **maximize weld depth copper**

The recorded best solution produced:

| Metric | Predicted value |
|---|---:|
| Weld width steel | 2260.8 µm |
| Weld width copper | 88.6 µm |
| Weld depth copper | 299.7 µm |
| Gap | 103.9 µm |
| Crack probability | 14.1% |

The optimization searched 500 trials.

> These values are model predictions, not experimental guarantees. Recommended settings should be validated experimentally before production use.

## Dataset

The original Colab notebook loaded:

`sample_data_1/sample_data_1.xlsx`

For the GitHub version, put the Excel file here:

```text
data/sample_data_1.xlsx
```

The dataset is **not included in this repository package** because it was not provided with the uploaded notebook. If the dataset is proprietary or restricted, do not publish it publicly.

## Repository Structure

```text
laser-welding-optimization/
├── laser_welding_optimization.ipynb
├── original_colab_notebook.ipynb
├── requirements.txt
├── .gitignore
└── data/
    └── sample_data_1.xlsx   # add locally; do not commit if confidential
```

## Installation

```bash
pip install -r requirements.txt
```

## Running the Project

Open `laser_welding_optimization.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.

If using Colab, upload the Excel dataset to:

```text
data/sample_data_1.xlsx
```

Then run the notebook from top to bottom.

## Tools & Libraries

Python, NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn, Imbalanced-learn, Joblib, and Optuna.

## Author

**Rashmi Patil**
