# Bangladesh GDP Growth Forecasting

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Statsmodels](https://img.shields.io/badge/Forecasting-ARIMA%20%7C%20SARIMAX-green.svg)](https://www.statsmodels.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

**Bangladesh GDP Growth Forecasting** is a time-series analysis and forecasting project focused on Bangladesh's **annual GDP growth rate**. The project explores historical GDP-growth data, evaluates stationarity and time-series behavior, fits ARIMA/SARIMAX forecasting models, measures forecast error, and generates future GDP-growth projections.

The repository also includes a simple front-end interface for presenting Bangladesh GDP-related information.

## Project Overview

The forecasting notebook uses annual GDP-growth observations from **1960 to 2021** and applies a complete time-series workflow:

- Historical GDP-growth exploration
- Time-series visualization
- Stationarity analysis
- Differencing
- ACF and PACF analysis
- Automatic ARIMA order selection
- ARIMA forecasting
- Seasonal ARIMA / SARIMAX forecasting
- Forecast evaluation
- Future GDP-growth projection

The saved dataset contains **62 annual observations** with the following fields:

```text
Year
GDP growth (annual %)
```

## Forecasting Workflow

```text
Historical GDP Growth Data
           │
           ▼
    Data Preparation
           │
           ▼
 Time-Series Visualization
           │
           ▼
 Stationarity Analysis
           │
           ▼
 Differencing / ACF / PACF
           │
           ▼
   ARIMA Order Selection
        (auto_arima)
           │
           ▼
     ARIMA(0,1,1)
           │
           ▼
 SARIMAX / Seasonal Model
           │
           ▼
  Forecast Evaluation
   RMSE • MAE • MAPE
           │
           ▼
Future GDP-Growth Forecast
```

## Dataset

The dataset is located at:

```text
Machine Learning Model & DataSet/
└── datasetGDPforTimeseries.csv
```

It contains annual Bangladesh GDP-growth observations from **1960 through 2021**.

Example:

```text
Year, GDP growth (annual %)
01/01/1960, 2.632
01/01/1961, 6.058
01/01/1962, 5.453
...
01/01/2020, 5.200
01/01/2021, 6.800
```

## Time-Series Modeling

### Automatic ARIMA Selection

The notebook uses `pmdarima.auto_arima()` to search for an appropriate ARIMA configuration.

The saved notebook output selects:

```text
ARIMA(0, 1, 1)
```

as the best non-seasonal ARIMA model according to the automated AIC-based search.

### ARIMA Model

The initial forecasting model is fitted as:

```python
ARIMA(
    train_data["GDP growth (annual %)"],
    order=(0, 1, 1)
)
```

The dataset is split into:

```text
Training observations: 42
Test observations:     20
```

### SARIMAX Model

The notebook also applies a seasonal state-space model:

```python
sm.tsa.statespace.SARIMAX(
    data_s["GDP growth (annual %)"],
    order=(0, 1, 1),
    seasonal_order=(0, 1, 1, 6)
)
```

This model is used for the final forecasting workflow in the saved notebook.

## Evaluation

The notebook evaluates forecast performance using:

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R² score
- Mean Absolute Percentage Error (MAPE)-based percentage score

The saved notebook reports:

| Metric | Saved Notebook Result |
|---|---:|
| RMSE | 1.5724 |
| MAE | 1.2543 |
| MAPE-derived score | 81.01% |

> **Note:** The 81.01% value in the notebook is calculated as `100 - mean(MAPE)` and should not be interpreted as a classification accuracy.

## Future Forecasting

The notebook allows the user to enter a future forecasting horizon:

```python
step = int(input("Enter how many year(Maximum 30 year) you need to know: "))
```

The saved output demonstrates GDP-growth forecasting through **2030**.

Example forecasts stored in the notebook output include:

| Year | Forecast GDP Growth (%) |
|---|---:|
| 2022 | 7.704 |
| 2023 | 6.960 |
| 2024 | 7.916 |
| 2025 | 7.085 |
| 2026 | 6.350 |
| 2027 | 7.007 |
| 2028 | 8.182 |
| 2029 | 7.437 |
| 2030 | 8.393 |

> These values are outputs of the historical model trained on data available through 2021. They are included to document the original experiment and should not be treated as current official economic forecasts.

## Repository Structure

```text
Bangladesh-GDP-Growth-Forecasting/
│
├── Machine Learning Model & DataSet/
│   ├── GDP project.ipynb
│   └── datasetGDPforTimeseries.csv
│
├── Front-End BD GDP Indicator/
│   ├── assets/
│   ├── index.html
│   └── technology.html
│
├── Documents/
│   └── GDP.pptx
│
├── LICENSE
└── README.md
```

## Technologies Used

### Data Analysis & Forecasting

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Plotly
- Statsmodels
- pmdarima
- scikit-learn

### Front End

- HTML
- CSS
- JavaScript

## Installation

Clone the repository:

```bash
git clone https://github.com/kowshir-bitto/Bangladesh-GDP-Growth-Forecasting.git
cd Bangladesh-GDP-Growth-Forecasting
```

Install the main Python dependencies:

```bash
pip install numpy pandas matplotlib plotly statsmodels pmdarima scikit-learn jupyter
```

## Running the Forecasting Notebook

Move into the model directory:

```bash
cd "Machine Learning Model & DataSet"
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
GDP project.ipynb
```

Make sure `datasetGDPforTimeseries.csv` remains in the same folder as the notebook.

## Running the Front End

Open:

```text
Front-End BD GDP Indicator/index.html
```

in a web browser.

For a local development server, you can also run:

```bash
python -m http.server 8000
```

and open the displayed local address in your browser.

## Important Notes

- The dataset used by the original notebook ends in **2021**.
- Forecasts shown in the notebook are model-generated historical experiment outputs, not current official projections.
- ARIMA and SARIMAX are statistical time-series forecasting methods; the project is therefore better described as a **time-series forecasting and analytics project** than a general machine-learning system.
- Economic forecasts are inherently uncertain and should be interpreted with appropriate caution.

## License

This project is distributed under the **Apache License 2.0**.

See the [LICENSE](LICENSE) file for details.

## Author

**Abu Kowshir Bitto**

- GitHub: [@kowshir-bitto](https://github.com/kowshir-bitto)
- Website: [kowshirbitto.me](http://kowshirbitto.me/)
- Google Scholar: [Abu Kowshir Bitto](https://scholar.google.com/citations?hl=en&user=AO0dWsgAAAAJ&view_op=list_works&gmla=AJ1KiT30Ms5pY2DUl6pfWl4cwjlBOwygW_3wawpWiD_769YBbLX8_0rqv4MiIf05GjDe6xY81ApN7Gy1DfwYJCZu)
