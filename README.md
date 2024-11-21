

# Vegetation Moisture Prediction Using Time Series Analysis

## Overview

This project focuses on predicting vegetation moisture levels using time series analysis and advanced machine learning techniques. By leveraging remote sensing data and meteorological information, the model forecasts vegetation moisture, which is critical for applications such as wildfire prevention, drought monitoring, and crop management.

The framework integrates **Long Short-Term Memory (LSTM)** networks for predictive modeling, incorporates **Monte Carlo Dropout** for uncertainty estimation, and uses **SHAP values** to provide explainable predictions.

---

## Table of Contents

1. [Data Sources and Preprocessing](#data-sources-and-preprocessing)
2. [Modeling Approach](#modeling-approach)
3. [Framework Design](#framework-design)
4. [Getting Started](#getting-started)
5. [Requirements](#requirements)
6. [Usage](#usage)
7. [License](#license)

---

## Data Sources and Preprocessing

The dataset comprises remote sensing and meteorological data collected over two years. It includes:

- **Sentinel-1 Synthetic Aperture Radar (SAR) Data**:
  - Provides C-band backscatter coefficients, sensitive to surface moisture and vegetation structure.
  
- **Sentinel-2 Optical Imagery**:
  - Used to calculate key vegetation indices:
    - Normalized Difference Vegetation Index (NDVI)
    - Normalized Difference Water Index (NDWI)
    - Green Chlorophyll Index (GCI)
    - Moisture Stress Index (MSI)

- **Meteorological Data from ERA5 Reanalysis**:
  - Captures critical variables like:
    - Temperature
    - Precipitation
    - Relative Humidity

Together, these datasets form the foundation for time series analysis.

### Data Preprocessing:
- **Vegetation indices** are aggregated over spatial regions defined by polygons corresponding to specific vegetation types.
- **Temporal data** is aligned and processed to create **daily time series**, enabling the analysis of vegetation dynamics and seasonal trends.
- This preprocessing ensures **consistency** across all data sources while maintaining the **temporal resolution** necessary for accurate modeling.

---

## Modeling Approach

The predictive framework is built around the **LSTM** architecture, a recurrent neural network known for its ability to model long-term dependencies in sequential data. LSTMs are particularly well-suited for this project due to their capacity to capture complex temporal patterns in vegetation indices and environmental variables.

### Key Components:
- **LSTM Architecture**:
  - Captures long-term dependencies and complex temporal patterns in the data, especially in vegetation indices and environmental variables.
  
- **Monte Carlo Dropout**:
  - Integrated into the model to provide **uncertainty quantification**.
  - Enables more reliable predictions by estimating the range of possible outcomes.

- **SHAP Values for Interpretability**:
  - SHAP values are used to assess the contribution of each input feature to the model’s predictions.
  - This approach helps understand the relationship between:
    - Vegetation indices
    - SAR backscatter
    - Meteorological factors
    - Predicted moisture levels
  - Enhances model transparency and trust, helping identify key drivers of vegetation moisture.

---

## Framework Design

The project’s methodology consists of three main stages:

1. **Calculation of Vegetation Indices and Spatial Mappings**:
   - Data is aggregated over regions defined by vegetation types.
   - Captures the average vegetation health and moisture characteristics for specific areas.

2. **Compilation into Continuous Time Series**:
   - Aggregated data is structured into continuous time series.
   - Facilitates the analysis of temporal trends and enables robust forecasting.

3. **LSTM Model Processing**:
   - The LSTM model processes the time series data to generate moisture predictions.
   - Uncertainty estimation is integrated through **Monte Carlo Dropout** for reliable predictions.

A comprehensive diagram of the framework illustrates the integration of remote sensing data, meteorological information, and advanced modeling techniques to deliver accurate and explainable predictions.

![Framework Diagram](Diagram/framework_diagram.png)

---

## Getting Started

To run this project, you need to set up the environment and dependencies on your local machine. Follow the steps below to get started.

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/vegetation-moisture-prediction.git
cd vegetation-moisture-prediction
```

### 2. Install Required Dependencies
Create a virtual environment and install the necessary Python libraries.

```bash
pip install -r requirements.txt
```

---

## Requirements

- Python 3.x
- TensorFlow
- NumPy
- Matplotlib
- SHAP
- scikit-learn
- pandas
- geopandas
- other necessary libraries listed in the `requirements.txt` file.

---

## Usage

Once the environment is set up, you can run the Jupyter notebook to train and test the model for vegetation moisture prediction.

1. Open the Jupyter notebook:
   ```bash
   jupyter notebook vegetation_moisture_prediction.ipynb
   ```

2. Follow the notebook instructions to load data, train the LSTM model, and generate predictions.

3. The model includes Monte Carlo Dropout to estimate uncertainty and uses SHAP for interpretability.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Make sure to replace `"yourusername"` with your actual GitHub username, and update any necessary paths or filenames according to your actual project structure. This README gives a clear overview of the project, how to set it up, and how to use it.
