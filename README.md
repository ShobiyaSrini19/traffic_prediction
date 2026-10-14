# LSTM Traffic Prediction

A time-series traffic-volume prediction project using an LSTM neural network.

## Project Overview

This project uses the Metro Interstate Traffic Volume dataset to predict the **next-hour traffic volume** from historical traffic, weather, and time-based features.

The model uses a **24-hour sequence** of input data and predicts traffic volume for the following hour.

## Model

- Algorithm: LSTM (Long Short-Term Memory)
- Sequence length: 24 hours
- Input features: 20
- Output: Next-hour traffic volume
- Loss function: Mean Squared Error
- Optimizer: Adam
- Epochs: 20
- Batch size: 64

## Input Features

The model uses:

- temp
- rain_1h
- snow_1h
- clouds_all
- hour
- day_of_week
- month
- year
- is_weekend
- weather_Clear
- weather_Clouds
- weather_Drizzle
- weather_Fog
- weather_Haze
- weather_Mist
- weather_Rain
- weather_Smoke
- weather_Snow
- weather_Squall
- weather_Thunderstorm

## Project Files

```text
traffic-prediction-lstm/
├── lstm_networks_for_traffic_prediction.py
├── requirements.txt
├── sample_request.json
├── API_TEST.md
├── .gitignore
└── README.md
```

## Dataset

The code expects the Metro Interstate Traffic Volume dataset.

Place the dataset file in the project directory before running the training code:

```text
Metro_Interstate_Traffic_Volume.csv.gz
```

The dataset is not included in this repository.

## Preprocessing

The code performs:

1. Date-time conversion
2. Duplicate timestamp removal
3. Missing-value inspection
4. Time-based feature extraction
5. Weather one-hot encoding
6. Chronological 80/20 train-test split
7. Min-Max scaling
8. Creation of continuous 24-hour LSTM sequences

## Evaluation

The project calculates:

- MAE
- RMSE
- R²

It also includes actual-vs-predicted plots, training/validation loss visualization, prediction-error analysis, and analysis of the largest prediction errors.

## Model Artifacts

The training workflow saves:

```text
traffic_lstm_model.keras
feature_scaler.joblib
target_scaler.joblib
```

These generated model files should only be committed to GitHub if they are small enough and you intentionally want them versioned. For larger models, use Git LFS or an external model-storage service.

## Running the Project

Install dependencies:

```bash
pip install -r requirements.txt
```

Then run:

```bash
python lstm_networks_for_traffic_prediction.py
```

Note: The uploaded training script contains Google Colab/Google Drive paths because it was developed in Colab. Those paths may need to be changed when running locally.

## API

The code also contains a Flask backend design with:

```text
GET  /health
POST /predict
```

The prediction interface expects a 24 × 20 input sequence and returns the predicted traffic volume in vehicles/hour.

## Important

This repository contains the project code and documentation. Dataset files and large trained-model artifacts are intentionally excluded from Git unless added separately.
