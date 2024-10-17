# PJME Energy Forecasting

This project focuses on forecasting PJME energy consumption using time series data. The goal is to predict future energy usage in megawatts (MW) based on historical data.

## Table of Contents

- [Overview](#overview)
- [Data](#data)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Model Saving](#model-saving)

## Overview

This project utilizes the XGBoost regression model to predict future PJME energy consumption based on hourly historical data. The analysis employs time series features and lagged values to capture seasonal patterns and trends in the dataset.

## Data

The dataset used in this project is derived from PJM Interconnection's hourly energy consumption data. It includes the following key variable:

- **PJME_MW**: PJM Eastern Hub's energy consumption in megawatts.

### Input File

- `PJME_hourly.csv`: Contains historical energy consumption data.

## Features

The following features are created from the timestamp data to improve model performance:

- **Hour**: Hour of the day (0-23)
- **Day of Week**: Day of the week (0=Monday, 6=Sunday)
- **Quarter**: Quarter of the year (1-4)
- **Month**: Month of the year (1-12)
- **Year**: Year extracted from the date
- **Day of Year**: Day of the year (1-365)
- **Day of Month**: Day of the month (1-31)
- **Week of Year**: Week of the year according to ISO calendar
- **Lagged Features**: Previous values of PJME_MW from 1, 2, and 3 years ago.

## Installation

To run this project, you will need to install the following dependencies:

```bash
pip install pandas numpy matplotlib seaborn xgboost scikit-learn
```

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/PJME-Energy-Forecasting.git
   cd PJME-Energy-Forecasting
   ```

2. Place the `PJME_hourly.csv` file in the `dataset` directory.

3. Run the Jupyter Notebook or Python script to execute the code:
   ```bash
   python your_script.py
   ```

## Results

The model's performance is evaluated using Root Mean Squared Error (RMSE) across different folds of the time series data. The average RMSE and individual fold scores are displayed after running the model training.

```plaintext
Score across folds: [average RMSE]
Fold scores: [list of RMSE scores]
```

## Model Saving

After training the model, it can be saved for later use in predictions. The model is saved in JSON format:

```python
reg.save_model('model.json')
```
