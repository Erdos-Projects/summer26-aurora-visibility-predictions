# Aurora Visibility Prediction

## Overview

This project builds a classification model to predict whether auroras will be visually observable from a specific geographic latitude given geophysical and local-sky conditions. Given the following key features for a particular time and location, predict a binary label: visually observable (yes/no).

- Kp index: global geomagnetic activity (0–9)
- Solar wind speed: km/s
- Bz IMF: Bz component of the interplanetary magnetic field (nT)
- Cloud percentage cover: local cloudiness (%)

The goal is to provide a short-term forecast for observers, helping photographers, astronomers, and aurora enthusiasts plan observations.

## Data
Tabular list of data sources, access methods, licensing, and limitations: `data_inventory.csv`

1. Space-weather data: file fetched from: https://omniweb.gsfc.nasa.gov/form/dx1.html. Contains hourly measurements of Kp, solar wind speed, and Bz from Jan 1st, 2021 to Jan 1st, 2026.
`data/raw/omni2_Qj2SZdRRin.lst.txt`

2. Local weather data: file fetched from: https://open-meteo.com/en/docs/historical-forecast-api?hourly=cloud_cover. Contains hourly historical weather data of two cities Regina `data/raw/open-meteo-50.45N104.63W578m.csv`and Yellowknife `data/raw/open-meteo-62.46N114.32W192m.csv`.

## Data acquisition scripts
Preprocess raw data from space and earth weather, to produce a cleaned and merged dataset ready for feature engineering.

Running this script:
```
src/data/data_acquisition.ipynb
```
produces the processed dataset: `data/processed/data_aurora.csv`

<!-- ## Next Steps

- Exploratory data analysis and feature selection.
- Baseline classifiers: logistic regression, decision tree.
- Stronger models: random forest, gradient boosting (XGBoost/LightGBM).
- Model validation with ROC/AUC, precision/recall. -->

