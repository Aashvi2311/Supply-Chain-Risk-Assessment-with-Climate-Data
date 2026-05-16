# Supply Chain Risk Assessment with Climate Data

## Problem Statement
Existing supply chain datasets lack climate variables despite weather being a significant 
factor in logistics delays. This project bridges that gap by integrating real-world 
historical climate data with supply chain records to build a delay prediction model.

## Data Sources
- **Supply Chain Data**: Sourced from Kaggle
- **Climate Data**: Independently fetched via the 
[Open-Meteo Archive API](https://open-meteo.com/) across origin and destination cities

The merged dataset is publicly available on Kaggle:
[Supply Chain Risk Assessment with Climate Data](https://www.kaggle.com/datasets/aashvi2311/supply-chain-risk-assessment-with-climate-data)

## Methodology

### 1. Data Collection
- Identified unique origin city + order date and destination city + arrival date pairs
- Fetched historical max temperature and precipitation for each pair via Open-Meteo API
- Implemented file-based caching to avoid redundant API calls
- Merged climate variables into the supply chain dataset

### 2. Feature Engineering
- `origin_temp` — max temperature (°C) at origin on order date
- `origin_rain` — precipitation (mm) at origin on order date
- `dest_temp` — max temperature (°C) at destination on arrival date
- `dest_rain` — precipitation (mm) at destination on arrival date
- `diff_temp` — temperature differential between origin and destination
- `total_rain` — combined precipitation across both locations
- Date features extracted from Order Date and Arrival Date

### 3. Modelling
Trained and compared two regression models to predict supply chain delay in days:

| Model | MAE | R² |
|---|---|---|
| Random Forest | 0.27 | 0.922 |
| XGBoost | 0.27 | 0.922 |

Both models achieved consistent performance, validating the feature set.

## Tech Stack
- **Language**: Python
- **Libraries**: Pandas, NumPy, scikit-learn, XGBoost, Matplotlib, Seaborn
- **API**: Open-Meteo Archive API
- **Tools**: Jupyter Notebook

## Results
Both XGBoost and Random Forest regressors achieved **R² of 0.922** and 
**MAE of 0.27 days** on the test set, demonstrating that climate variables 
are meaningful predictors of supply chain delays.

## Dataset
Published on Kaggle: [Supply Chain Risk Assessment with Climate Data](https://www.kaggle.com/datasets/aashvi2311/supply-chain-risk-assessment-with-climate-data)
