# EM Project (Energy Data Analysis, 2020–2025)

## Overview
This repository contains the datasets, code, and results for the EM Project analyzing energy and weather data from BGE and BWI sites between 2020–2025.  
The raw yearly datasets were combined and corrected into a single master dataset (`Final.csv`), which serves as the basis for analysis in the Jupyter notebooks.

---

## Repository Structure
- `data/raw/` → Original datasets (`20-21.csv` … `24-25.csv`, `BWI data 20-25 UTC.csv`)
- `data/processed/Final.csv` → Combined and corrected dataset used for analysis
- `src/notebooks/` → Jupyter notebooks (`EM Project-1.ipynb`, `EM Project-2.ipynb`) containing code and experiments
- `results/` → Figures, tables, and outputs generated from the notebooks
- `docs/` → Documentation and reports

---

## Installation
Clone the repository and install dependencies:

```bash
git clone https://github.com/aravindbharath03-pixel/EM-Project.git
cd EM-Project
pip install -r requirements.txt
