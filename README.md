# Electricity Demand Sensitivity to Heat Index in the Baltimore Region (2020–2025)

## Project Overview
This project examines how electricity demand in the Baltimore Gas and Electric (BGE) service territory responds to atmospheric heat stress, as measured by the heat index observed at Baltimore–Washington International Airport (BWI). Using hourly electricity demand and meteorological data from 1 November 2020 through 31 October 2025, the study quantifies the relationship between electricity demand and heat index across multiple years and evaluates whether this relationship has changed over time in a manner consistent with climate-driven warming.

The analysis integrates exploratory data analysis, regression-based sensitivity estimation, threshold-based regime separation, and a physically grounded degree-day modeling framework. Particular emphasis is placed on cooling-driven demand during extreme heat events, while heating-driven demand behavior during colder conditions is also characterized.

---

## Repository Structure
The repository is organized into three main folders:

├── data/
├── scripts/
└── results/


Each folder corresponds to a distinct stage of the project workflow, from raw data ingestion to final analytical outputs.

---

## Data (`data/`)

The `data` folder contains all raw observational datasets used in the analysis.

### Meteorological Data
- **`BWI dataset 2020-2025.csv`**  
  Hourly meteorological observations from Baltimore–Washington International Airport (BWI), reported in UTC.  
  Variables include air temperature (°F), relative humidity (%), and NOAA heat index (“feel”, °F).  
  These data provide the atmospheric input for all demand–weather analyses.

### Electricity Demand Data
Hourly electricity demand (MW) for the BGE service territory, provided as annual CSV files:
- **`BGE dataset 2020-2021.csv`**
- **`BGE dataset 2021-2022.csv`**
- **`BGE dataset 2022-2023.csv`**
- **`BGE dataset 2023-2024.csv`**
- **`BGE dataset 2024-2025.csv`**

All files use UTC timestamps and are concatenated during preprocessing.

---

## Analysis Scripts (`scripts/`)

The `scripts` folder contains Jupyter notebooks implementing the full analytical workflow.

- **`Analysis-1.ipynb`**  
  Data ingestion, preprocessing, and cleaning.  
  Merges BGE and BWI datasets, aligns timestamps to hourly resolution, removes invalid or missing values, and produces the final cleaned dataset.

- **`Analysis-2.ipynb`**  
  Exploratory analysis of hourly and daily electricity demand versus meteorological variables.  
  Includes time-series plots, scatter plots, and preliminary regression diagnostics used to evaluate demand–weather relationships.

- **`Analysis-3.ipynb`**  
  Daily aggregation and threshold-based sensitivity analysis.  
  Constructs daily mean and daily peak demand metrics, applies a high-heat filter (feel ≥ 70°F), and implements a regime split at 65°F to distinguish heating- and cooling-dominated conditions.

- **`Analysis-4.ipynb`**  
  Degree-day modeling and synthesis.  
  Computes Heating Degree Days (HDD) and Cooling Degree Days (CDD) relative to a 65°F baseline and estimates yearly demand sensitivities using multiple linear regression.

All figures and tables referenced in the final report are generated within these notebooks.

---

## Results (`results/`)

The `results` folder contains processed datasets and compiled analytical outputs.

- **`Final.csv`**  
  Fully cleaned and merged hourly dataset combining BGE electricity demand with BWI meteorological variables.  
  This file is the primary dataset used for all regression and sensitivity analyses.

- **`Final Summary.csv`**  
  Yearly summary of sensitivity estimates, correlations, and regression diagnostics derived from threshold-based and degree-day analyses.

- **`Tables and Figures.pdf`**  
  Compiled set of all tables and figures produced during the analysis, including:
  - Daily mean and peak demand time series
  - Hourly demand vs. meteorological variable scatter plots
  - Daily aggregated regression panels
  - High-heat (feel ≥ 70°F) cooling sensitivity plots
  - Heating and cooling regime comparisons
  - Degree-day regression summaries

These outputs directly support the interpretations presented in the final report.

---

## Methodological Summary
The analytical framework proceeds as follows:
1. Exploratory analysis to establish seasonal structure and baseline demand–weather relationships.
2. Daily aggregation to reduce high-frequency noise and clarify structured behavior.
3. Threshold-based sensitivity analysis using:
   - A high-heat subset (feel ≥ 70°F) to isolate extreme cooling-driven demand.
   - A regime split at 65°F to separate heating- and cooling-dominated conditions.
4. Degree-day modeling using Heating Degree Days (HDD) and Cooling Degree Days (CDD) to obtain physically interpretable demand sensitivities and enable year-to-year comparison.

The year 2020 is treated with care, as the dataset begins in November 2020 and does not include the 2020 summer season; heating behavior from late 2020 is valid, while cooling sensitivity for that year is not interpreted climatically.

---

## Conclusions
The analysis shows that electricity demand in the BGE service territory exhibits a strong and persistent sensitivity to elevated heat index conditions across all complete years (2021–2025). Cooling-driven demand sensitivity remains consistently high, while heating-driven sensitivity is comparatively stable over time. Although the five-year record is insufficient for definitive attribution, the sustained exposure to high heat-index conditions is consistent with broader regional warming trends and highlights the growing importance of extreme heat for grid stress and power system planning.

---

## References
All scientific context, methodology, and interpretation are documented in the accompanying AMS-style report and supported by peer-reviewed literature cited therein.
