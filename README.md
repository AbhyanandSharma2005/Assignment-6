# Assignment 6 - Weather Condition Classification using SVM and Open-Meteo API

## Objective
Classify weather conditions as **Cool** or **Warm** based on meteorological observations from the Open-Meteo API using Support Vector Machine (SVM) classification with RBF kernel.

## API Documentation Link
- **Open-Meteo API**: https://open-meteo.com/
- **Historical Weather API**: https://archive-api.open-meteo.com/v1/archive
- **Forecast API**: https://api.open-meteo.com/v1/forecast

## Libraries Used
```
pandas
numpy
scikit-learn
requests
seaborn
matplotlib
```

## Methodology

### Task 1: Data Collection and Understanding (2 Marks)
- Fetched weather data from **Open-Meteo Historical API** for London (latitude=51.5074, longitude=-0.1278)
- Retrieved full year 2024 hourly data (8,784 records) including:
  - Temperature at 2m (°C)
  - Relative humidity at 2m (%)
  - Surface pressure (hPa)
  - Wind speed at 10m (km/h)
- Created target variable: `Weather_Class` (Warm ≥ 25°C, Cool < 25°C)
- **Input Features**: temperature_2m, relative_humidity_2m, surface_pressure, wind_speed_10m
- **Target Variable**: Weather_Class (Cool/Warm)
- Class distribution: Cool (8,683), Warm (101)

### Task 2: Data Preprocessing (2 Marks)
- Checked for missing values (none found)
- Removed 'time' column (non-predictive)
- Encoded target variable: Cool → 0, Warm → 1 (LabelEncoder)
- Split dataset: 80% training (7,027 samples), 20% testing (1,757 samples) with stratification
- Standardized features using StandardScaler (zero mean, unit variance)

### Task 3: Model Development (3 Marks)
- Built SVM Classifier with **RBF kernel** (random_state=42)
- Trained on scaled training data
- Predicted weather class for test dataset

### Task 4: Model Evaluation (2 Marks)
- **Accuracy**: 0.9994 (99.94%)
- **Precision**: 1.0000 (100%)
- **Recall**: 0.9500 (95%)
- **F1-Score**: 0.9744 (97.44%)

**Confusion Matrix:**
| | Predicted Cool | Predicted Warm |
|---|---|---|
| Actual Cool | 1,737 | 0 |
| Actual Warm | 1 | 19 |

**Observations:**
1. The model achieves excellent accuracy (99.94%) on the test set, demonstrating effective classification of weather conditions using meteorological features from the Open-Meteo API.
2. The confusion matrix shows the model correctly identifies 1,737 Cool samples and 19 Warm samples, with only 1 false negative. Given the class imbalance (Cool significantly outnumbers Warm), the model performs well on both classes.
3. Feature scaling (StandardScaler) was critical for SVM performance. Without scaling, features like surface pressure (~1000 hPa) would dominate the RBF kernel's distance calculations compared to temperature (~10-20°C) and wind speed (~10-20 km/h), leading to biased decision boundaries.

### Task 5: Conclusion (1 Mark)
This assignment successfully developed an SVM classifier to categorize weather as Cool or Warm using meteorological data from the Open-Meteo Historical API for London (2024). The model achieved strong performance with high accuracy (99.94%), precision (100%), recall (95%), and F1-score (97.44%), demonstrating effective classification using temperature, humidity, pressure, and wind speed features.

Key findings indicate temperature is the dominant feature for this classification, as the target variable was directly derived from a temperature threshold (≥25°C = Warm, <25°C = Cool). The RBF kernel effectively captured the non-linear decision boundary between weather classes.

Feature scaling proved crucial for SVM performance. StandardScaler normalized all features to zero mean and unit variance, preventing features with larger magnitudes (like surface pressure ~1000 hPa) from dominating the distance calculations in the RBF kernel. Without scaling, the model would be biased toward high-magnitude features.

One advantage of SVM is its effectiveness in high-dimensional spaces and ability to handle non-linear boundaries through kernel functions. One limitation is its sensitivity to feature scaling and high computational cost with large datasets, making it less suitable for real-time applications with massive data volumes.

## Results Summary

| Metric | Value |
|--------|-------|
| Accuracy | 0.9994 |
| Precision | 1.0000 |
| Recall | 0.9500 |
| F1-Score | 0.9744 |

## How to Run
1. Install dependencies: `pip install pandas numpy scikit-learn requests seaborn matplotlib`
2. Open `Assignment-6.ipynb` in Jupyter Notebook or VS Code
3. Run all cells sequentially

## Author
**Abhyanand Sharma**  
Assignment 6 - Weather Analytics Classification