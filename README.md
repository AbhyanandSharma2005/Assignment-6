# Assignment 6 - Weather Condition Classification using SVM and Open-Meteo API

## Project Overview
This project classifies weather conditions as **Cool** or **Warm** based on meteorological observations from the Open-Meteo API using Support Vector Machine (SVM) classification with RBF kernel.

## Tasks Completed

### Task 1: Data Collection and Understanding (2 Marks)
- Fetched weather data from Open-Meteo API for New Delhi (latitude=28.6139, longitude=77.2090)
- Retrieved 7 days of hourly data (168 records) including:
  - Temperature at 2m (°C)
  - Relative humidity at 2m (%)
  - Surface pressure (hPa)
  - Wind speed at 10m (km/h)
- Created target variable: Weather_Class (Warm ≥ 25°C, Cool < 25°C)

### Task 2: Data Preprocessing (2 Marks)
- Checked for missing values (none found)
- Removed 'time' column (non-predictive)
- Encoded target variable: Cool → 0, Warm → 1
- Split data: 80% training (134 samples), 20% testing (34 samples)
- Standardized features using StandardScaler (zero mean, unit variance)

### Task 3: Model Development (3 Marks)
- Built SVM Classifier with RBF kernel (C=1.0, random_state=42)
- Trained on scaled training data
- Made predictions on test set

### Task 4: Model Evaluation (2 Marks)
- **Accuracy**: 1.0000 (100%)
- **Precision**: 1.0000 (100%)
- **Recall**: 1.0000 (100%)
- **F1-Score**: 1.0000 (100%)

**Confusion Matrix:**
| | Predicted Cool | Predicted Warm |
|---|---|---|
| Actual Cool | 17 | 0 |
| Actual Warm | 0 | 17 |

**Observations:**
1. Perfect classification achieved (100% across all metrics)
2. Zero false positives and false negatives
3. Clear temperature threshold (25°C) creates well-separated classes that RBF kernel easily learns

### Task 5: Conclusion (1 Mark)
The SVM classifier with RBF kernel achieved 100% accuracy in classifying weather conditions. Feature scaling was crucial as SVM's RBF kernel relies on distance calculations. One advantage of SVM is effectiveness in high-dimensional spaces with non-linear kernels; one limitation is sensitivity to feature scaling and computational cost with large datasets.

## Requirements
```
pandas
numpy
scikit-learn
requests
seaborn
matplotlib
```

## How to Run
1. Install dependencies: `pip install pandas numpy scikit-learn requests seaborn matplotlib`
2. Open `Assignment-6.ipynb` in Jupyter Notebook or VS Code
3. Run all cells sequentially

## API Reference
- **Open-Meteo API**: https://open-meteo.com/
- Endpoint: `https://api.open-meteo.com/v1/forecast`
- Parameters: latitude, longitude, hourly variables, forecast_days

## Author
**Abhyanand Sharma**  
Assignment 6 - Weather Analytics Classification

## License
This project is for educational purposes.