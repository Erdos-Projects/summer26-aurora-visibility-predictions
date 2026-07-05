# Aurora Visibility Prediction

## Overview

This project builds a classification model to predict whether auroras will be visually observable from a specific geographic latitude given geomagnetic and local-sky conditions. Given the following key features for a particular time and location, predict a binary label: visually observable (yes/no).

- Kp index: global geomagnetic activity (0–9)
- Solar wind speed: km/s
- Bz IMF: Bz component of the interplanetary magnetic field (nT)
- Solar elevation angle
- Moon darkness index
- Cloud percentage cover: local cloudiness (%)

The goal is to provide a short-term forecast for observers, helping photographers, astronomers, and aurora enthusiasts plan observations.


## Data
Tabular list of data sources, access methods, licensing, and limitations: [`aurora_data_pipeline.ipynb`](https://github.com/Erdos-Projects/summer26-aurora-visibility-predictions/blob/main/aurora_data_pipeline.ipynb) 
1. Actual aurora observations reported by citizens from 2014-2025, submitted to the Aurorasaurus citizen science project: available at https://zenodo.org/records/16783265
2. Space-weather data: file fetched from: https://omniweb.gsfc.nasa.gov/form/dx1.html. Contains hourly measurements of Kp, solar wind speed, and Bz from Jan 1st, 2021 to Jan 1st, 2026.
`data/raw/omni2_Qj2SZdRRin.lst.txt`
3. Local weather data: file fetched from: https://open-meteo.com/en/docs/historical-forecast-api?hourly=cloud_cover, cached for ease of access.

## Data acquisition scripts
Preprocess raw data from space and earth weather, to produce a cleaned and merged dataset ready for feature engineering.

Running this script:
```
aurora_data_pipeline.ipynb
```
produces the processed dataset: `aurora_dataset_clean.csv`

## Observations from exploratory data analysis
- Out of 22,280 observations 73.5% report positive sighting and 26.5% report no aurora seen.
- Of the positive sightings 62.5% also report images taken (image not included in the dataset).
- Aurora sightings went up in 2024 conciding with the solar cycle peaking. That also reflects on a larger number of negative sightings, consistent with higher overall reportings of any such events.
- 31.1% of the positive sightings had local cloud cover > 80% according to open-meteo weather source at the location latitude, longitude, date and time.
- 32.3% of the positive sightings had sun above the horizon (sun elevation angle $> 0^{\degree}$) computed analytically at the observer's exact lat/lon and UTC datetime using the [astral](https://astral.readthedocs.io/en/latest/package.html) library.

  
 ## Next Steps
- Exploratory data analysis and feature selection.
- Baseline classifiers: logistic regression, decision tree.
- Stronger models: random forest, gradient boosting (XGBoost/LightGBM).
- Model validation with ROC/AUC, precision/recall. -->

## Outcome
The end outcome of the model is more alligned with the prediction of whether a motivated observer sees aurora and not ``is aurora objectively present".
