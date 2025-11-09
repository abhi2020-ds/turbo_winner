# The Cities of Tomorrow – Urban Growth & Sustainability 🏙️

Author: [Abhineet Singh](https://www.linkedin.com/in/abhineetsing/)  
Last Modified: 11/6/2025  
Dataset: https://www.kaggle.com/datasets/programmer3/sustainable-urban-planning-and-landscape-dataset

Additional sources:
- UN Open Spaces & Green Areas: https://data.unhabitat.org/pages/open-spaces-and-green-areas
- UN Population & Demographic Trends: https://data.unhabitat.org/pages/urban-population-and-demographic-trends
- State & Local Energy (NREL viewer): https://maps.nrel.gov/slope/data-viewer

---

## Project Objective
Explore drivers of urban sustainability and livability using the Sustainable Urban Planning & Landscape Dataset. Goals:
- Identify features that influence urban sustainability scores and population movement.
- Rank cities with high sustainability potential and investigate drivers.
- Relate city-level indicators with state-level clean energy mixes.

---

## Key Features
- green_cover_percentage
- renewable_energy_usage
- public_transport_access
- disaster_risk_index
- crime_rate
- carbon_footprint
- building_density, road_connectivity, population_density, avg_income
- land_use_type_* (Residential, Commercial, Green Space, Industrial)
- urban_sustainability_score

---

## Data Preparation
- Data loaded from built-in CSVs into pandas DataFrames.
- Basic checks: df.info(), df.isnull().sum() — dataset treated as complete (no nulls in provided copy).
- Typical steps applied/available: type conversions for categorical variables, scaling/normalization, feature selection.

---

## Exploratory Data Analysis (EDA) — summary
- Distribution, correlation matrix and scatter matrices were used to inspect relationships.
- Top positively correlated features with urban_sustainability_score: green_cover_percentage, renewable_energy_usage, public_transport_access.
- Top negative correlations: disaster_risk_index, crime_rate, carbon_footprint.
- Visual analyses: histograms, heatmaps, pair plots, scatter plots for selected feature pairs and time-series plots for green area trends.

Key takeaways:
- Green cover and renewable energy are the strongest positive levers.
- Public transport correlates with lower carbon footprint and higher livability.
- High disaster risk and carbon emissions are associated with lower sustainability.

---

## Predictive Modeling
- Model: RandomForestRegressor (n_estimators=100, random_state=42)
- Pipeline:
    - X = all features except urban_sustainability_score
    - y = urban_sustainability_score
    - Train/test split: 80/20
- Evaluation metrics reported: RMSE and R^2
- Feature importance extracted to highlight actionable levers (green cover, renewable usage, public transport, etc.).

---

## Bonus: US Cities — Population Drift & Green Space
- Merged green-area and urban population change datasets to identify cities where population movement aligns with green-area availability.
- Visualizations: mapbox scatter, time-series of green area share and per-capita green area, population change periods.
- Ranked top cities by green area per capita and recent population growth; found greener cities tend to attract population growth.
- Linked city-level green metrics with state-level energy mix (renewable vs fossil) using state energy CSV (stdscen23_low_ccs_cost_state.csv) for 2020.

---

## Recommendations & Policy Actions
- Prioritize expanding and protecting urban green spaces to improve livability and attract residents.
- Scale renewable energy adoption and integrate it into urban sustainability planning.
- Invest in public transport to reduce emissions and enhance access.
- Mitigate disaster risk and reduce carbon footprint to protect sustainability gains.
- Balance land use; avoid overconcentration of residential/commercial development at the expense of green areas.

---

## How to run (local / notebook)
1. Create a Python environment (recommended: conda or venv).
2. Install dependencies:
     - pandas, numpy, matplotlib, seaborn, scikit-learn, plotly
     - Example: pip install pandas numpy matplotlib seaborn scikit-learn plotly
3. Place dataset CSVs in the notebook resources path or update file paths in the notebook.
4. Open and run the notebook (Fabric notebook or Jupyter) in sequence:
     - 1) Data cleaning & inspection
     - 2) EDA visualizations
     - 3) Model training & evaluation
     - 4) Bonus US cities analyses and state energy aggregation

---

## Reproducibility notes
- Random seed used for model training: 42.
- Ensure numeric columns are coerced correctly (remove commas, strip whitespace) before plotting or modeling.
- Some plots depend on specific column names present in source CSVs (year column naming varies — check and adapt).

---

## Next steps / Extensions
- Integrate external benchmarks (World Bank, UN-Habitat) for cross-country comparisons.
- Explore causal inference or scenario modeling to support policy decisions.
- Build an interactive dashboard (Plotly Dash / Streamlit) for planners to explore scenarios.

---

## License & Contributions
- This README summarizes analyses performed on public datasets. Reuse and extensions welcome — open an issue or PR in the repo for changes.

Created: 11/5/2025