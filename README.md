EM Project: Energy Demand Sensitivity Analysis (2020–2025)

Overview

This repository documents an in-depth analysis of the relationship between hourly electricity load (BGE) and corresponding weather conditions (BWI Heat Index) across five years (2020–2025).
EM Project: Energy Demand Sensitivity Analysis (2020–2025)

Overview

This repository documents an in-depth analysis of the relationship between hourly electricity load (BGE) and corresponding weather conditions (BWI Heat Index) across five years (2020–2025).

The primary objective was to move beyond simple correlation to quantify the annual change in the grid's sensitivity to extreme heating and cooling events, proving that load growth is disproportionately driven by climate factors.

The project confirms the necessity of separating cooling load and heating load, providing definitive quantitative proof of growing vulnerability to summer heat.

Repository Structure

Directory

Content Description

data/raw/

Original, unmerged datasets: five BGE load files and one BWI weather file.

data/processed/

Final.csv: The merged, cleaned, and analysis-ready master dataset.

src/scripts/

Core data cleaning and merging script (Final_Data_Merge_and_Clean.py).

src/notebooks/

All analytical Jupyter notebooks used for modeling and visualization.

results/

Final figures, tables (e.g., yearly sensitivity), and model outputs.

docs/

Project documentation and final report materials.

Methodology and Solution Progression

The analysis was executed in three progressive stages, validating findings at each step and building towards the final, most robust model.

Phase 1: Data Preparation & Foundation

Data Acquisition & Cleaning: The process starts by running the merging script to align BGE load (mw) with the BWI weather data (feel) by UTC timestamp. Critical cleaning steps ensure that all entries are valid (e.g., non-negative load and temperature).

Notebook: Final_Data_Merge_and_Clean.ipynb (or .py version)

Output: Final.csv (The authoritative dataset).

Initial Exploration (EDA): Simple summary statistics confirm the high-level trends in demand and weather across the five years.

Phase 2: Model Validation & Threshold Discovery

These steps proved that simple models were inadequate and established the foundation for the final Degree Day solution.

Notebook

Model Type

Core Finding

Em Project-1.ipynb

Simple Linear Regression (SLR)

Baseline Correlation. Proves a strong linear relationship exists (high R-squared), but fails to capture the distinct dynamics of heating and cooling.

EM Project-2.ipynb

Piecewise Linear Regression (PLR)

Cooling Threshold Discovery. Identifies the precise temperature (the "elbow") where cooling load begins to spike, validating the need to split the data.

Phase 3: The Final Solution (Degree Day Regression)

This is the definitive stage, directly addressing the project's objective to quantify change by separating weather effects.

Two-Regime Analysis:

Notebook: Complete_Heating_Cooling_Analysis.ipynb

Process: Implements a manual split of the data at $65^\circ \text{F}$ (the industry standard base temperature) to calculate separate heating and cooling slopes for each year. This confirmed that the cooling slope was getting steeper year-over-year.

Degree Day Regression Model:

Notebook: Final_Degree_Day_Model.ipynb

Process: The most robust approach. It uses Multiple Linear Regression with two engineered features: Heating Degree Days (HDD) and Cooling Degree Days (CDD). This models the entire year's load in a single, high-fidelity equation, yielding two primary coefficients (slopes) per year.

Definitive Project Conclusion

Based on the Final Degree Day Model analysis, the following conclusions are drawn:

Model Accuracy: The model consistently achieved high predictive accuracy (R-squared typically above $0.90$), validating the HDD/CDD approach as the definitive methodology.

Growing Cooling Vulnerability (The Key Finding): The most significant result is the increase in the Cooling Sensitivity (MW/CDD) over the period. The coefficient representing the load added per degree of heat above $65^\circ \text{F}$ has [Insert specific percentage change from your final run] from the start year (2020-2021) to the end year (2024-2025). This proves that the system is reacting more drastically to equivalent heat now than it did five years ago.

Heating Stability: The Heating Sensitivity (MW/HDD) remained relatively stable, confirming that the primary driver of rapid growth in peak demand is cooling-related (AC saturation and thermal stress).

This quantifiable increase in cooling sensitivity is the Final Solution to the problem, providing specific metrics for capacity planning and climate risk assessment.The primary objective was to move beyond simple correlation to quantify the annual change in the grid's sensitivity to extreme heating and cooling events, proving that load growth is disproportionately driven by climate factors.

The project confirms the necessity of separating cooling load and heating load, providing definitive quantitative proof of growing vulnerability to summer heat.

Repository Structure

Directory

Content Description

data/raw/

Original, unmerged datasets: five BGE load files and one BWI weather file.

data/processed/

Final.csv: The merged, cleaned, and analysis-ready master dataset.

src/scripts/

Core data cleaning and merging script (Final_Data_Merge_and_Clean.py).

src/notebooks/

All analytical Jupyter notebooks used for modeling and visualization.

results/

Final figures, tables (e.g., yearly sensitivity), and model outputs.

docs/

Project documentation and final report materials.

Methodology and Solution Progression

The analysis was executed in three progressive stages, validating findings at each step and building towards the final, most robust model.

Phase 1: Data Preparation & Foundation

Data Acquisition & Cleaning: The process starts by running the merging script to align BGE load (mw) with the BWI weather data (feel) by UTC timestamp. Critical cleaning steps ensure that all entries are valid (e.g., non-negative load and temperature).

Notebook: Final_Data_Merge_and_Clean.ipynb (or .py version)

Output: Final.csv (The authoritative dataset).

Initial Exploration (EDA): Simple summary statistics confirm the high-level trends in demand and weather across the five years.

Phase 2: Model Validation & Threshold Discovery

These steps proved that simple models were inadequate and established the foundation for the final Degree Day solution.

Notebook

Model Type

Core Finding

Em Project-1.ipynb

Simple Linear Regression (SLR)

Baseline Correlation. Proves a strong linear relationship exists (high R-squared), but fails to capture the distinct dynamics of heating and cooling.

EM Project-2.ipynb

Piecewise Linear Regression (PLR)

Cooling Threshold Discovery. Identifies the precise temperature (the "elbow") where cooling load begins to spike, validating the need to split the data.

Phase 3: The Final Solution (Degree Day Regression)

This is the definitive stage, directly addressing the project's objective to quantify change by separating weather effects.

Two-Regime Analysis:

Notebook: Complete_Heating_Cooling_Analysis.ipynb

Process: Implements a manual split of the data at $65^\circ \text{F}$ (the industry standard base temperature) to calculate separate heating and cooling slopes for each year. This confirmed that the cooling slope was getting steeper year-over-year.

Degree Day Regression Model:

Notebook: Final_Degree_Day_Model.ipynb

Process: The most robust approach. It uses Multiple Linear Regression with two engineered features: Heating Degree Days (HDD) and Cooling Degree Days (CDD). This models the entire year's load in a single, high-fidelity equation, yielding two primary coefficients (slopes) per year.

Definitive Project Conclusion

Based on the Final Degree Day Model analysis, the following conclusions are drawn:

Model Accuracy: The model consistently achieved high predictive accuracy (R-squared typically above $0.90$), validating the HDD/CDD approach as the definitive methodology.

Growing Cooling Vulnerability (The Key Finding): The most significant result is the increase in the Cooling Sensitivity (MW/CDD) over the period. The coefficient representing the load added per degree of heat above $65^\circ \text{F}$ has [Insert specific percentage change from your final run] from the start year (2020-2021) to the end year (2024-2025). This proves that the system is reacting more drastically to equivalent heat now than it did five years ago.

Heating Stability: The Heating Sensitivity (MW/HDD) remained relatively stable, confirming that the primary driver of rapid growth in peak demand is cooling-related (AC saturation and thermal stress).

This quantifiable increase in cooling sensitivity is the Final Solution to the problem, providing specific metrics for capacity planning and climate risk assessment.
