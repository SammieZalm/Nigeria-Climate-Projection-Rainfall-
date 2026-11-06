# Modelling of Rainfall Projection in Nigeria using Climate Models (CMIP6)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Framework: Xarray & Cartopy](https://img.shields.io/badge/Framework-Xarray%20%7C%20Cartopy-green.svg)](https://docs.xarray.dev/)

## 📌 Project Overview
This repository contains the verified computational workflows, climate index extraction algorithms, multi-model ensemble scripts, and quantitative assessment tools for projected rainfall change and climate extremes (SDII and CWD) across Nigeria ($2^\circ\text{E}$–$15^\circ\text{E}$, $4^\circ\text{N}$–$14^\circ\text{N}$) under **CMIP6** Shared Socioeconomic Pathways (**SSP1-2.6**, **SSP2-4.5**, and **SSP5-8.5**).

The methodology integrates high-resolution climate datasets (**ACCESS-CM2** and **MPI-ESM1-2-HR**) across:
* **Historical Baseline Period:** 1985–2014
* **Future Projection Period:** 2019–2050

---

## 🔬 Scientific & Methodological Framework

### 1. Evaluated Climate Indices (ETCCDI Standards)
* **Precipitation Climatology ($P$):** Mean daily precipitation rate ($\text{mm day}^{-1}$).
* **Simple Daily Intensity Index (SDII):** Total precipitation divided by the number of wet days ($P \ge 1.0\text{ mm day}^{-1}$).
  $$\text{SDII} = \frac{\sum_{i=1}^{W} P_i}{W}$$
  where $W$ is the total count of days where $P_i \ge 1.0\text{ mm day}^{-1}$.
* **Consecutive Wet Days (CWD):** Maximum annual duration of consecutive days with $P_i \ge 1.0\text{ mm day}^{-1}$.

### 2. Relative Change Percentage ($\Delta\%$)
To isolate climate change signals from background bias, relative changes are calculated against the historical baseline (1985–2014):
$$\Delta P (\%) = \left( \frac{P_{\text{future (2019–2050)}} - P_{\text{historical (1985–2014)}}}{P_{\text{historical (1985–2014)}}} \right) \times 100$$

### 3. Multi-Model Ensemble Mean (MME)
Structural model uncertainties are constrained by averaging model outputs across scenarios:
$$\text{MME}_{k} = \frac{P_{\text{ACCESS}, k} + P_{\text{MPI}, k}}{2}$$

---

## 📂 Repository Structure & Approved Scripts

```text
├── figures/                                    # Generated publication-quality PNG maps and tables
├── data/                                       # Directory containing extracted NetCDF datasets
├── 01_ACCESS_Historical_Validation.ipynb       # Approved Code 1: Baseline validation & maps
├── 02_MultiModel_Scenario_Projections.ipynb    # Approved Code 2: Full 12-Panel Matrix & TS analysis
├── 03_Summary_Tables_Generator.ipynb           # Approved Code 3: Quantitative summary table exporter
├── 04_Model_Agreement_Analysis.ipynb          # Approved Code 4: Inter-model variance & disagreement
└── README.md                                   # Repository documentation
```

---

## 🛠️ Summary of the 4 Approved Workflows

### 📜 Approved Code 1: ACCESS Historical Baseline & Validation
* **Notebook Name:** `01_ACCESS_Historical_Validation.ipynb`
* **Objective:** Computes historical climatological baseline (1985–2014) for ACCESS precipitation, SDII, and CWD. Plots spatial baseline maps and time-series trends over Nigeria.

### 📜 Approved Code 2: Multi-Model Scenario Projections & Ensemble Analysis
* **Notebook Name:** `02_MultiModel_Scenario_Projections.ipynb`
* **Objective:** Executes end-to-end evaluation for both ACCESS and MPI models across Historical, SSP126, SSP245, and SSP585. Constructs Multi-Model Ensemble Means (MME), generates **12-Panel Spatial Matrix Maps**, and plots **Multi-Model Time Series Projections**.

### 📜 Approved Code 3: Summary Tables Exporter
* **Notebook Name:** `03_Summary_Tables_Generator.ipynb`
* **Objective:** Generates publication-grade, styled image tables (`Table1_Precipitation_Summary.png`, `Table2_SDII_Summary.png`, `Table3_CWD_Summary.png`) summarizing country-wide mean values and relative changes ($\Delta\%$).

### 📜 Approved Code 4: Model Agreement & Disagreement Evaluation
* **Notebook Name:** `04_Model_Agreement_Analysis.ipynb`
* **Objective:** Quantifies absolute inter-model divergence ($|\text{ACCESS} - \text{MPI}|$) under SSP5-8.5 to identify regional convergence vs. spatial uncertainty, exporting styled agreement summary tables.

---

## 💻 Prerequisites & Installation

### Environment Setup
Create and activate a Python environment with required geospatial packages:

```bash
# Create conda environment
conda create -n climate_env python=3.10 -y
conda activate climate_env

# Install dependencies
conda install -c conda-forge xarray netcdf4 numpy pandas matplotlib cartopy jupyterlab -y
```

---

## 📊 Summary of Baseline & Projected Multi-Model Results

| Index / Metric | Historical (1985–2014) | SSP1-2.6 (2019–2050) | SSP2-4.5 (2019–2050) | SSP5-8.5 (2019–2050) |
| :--- | :---: | :---: | :---: | :---: |
| **Precipitation ($\text{mm day}^{-1}$)** | 3.3471 | 3.5657 (+6.53%) | 3.6994 (+10.53%) | 3.8557 (+15.20%) |
| **SDII Intensity ($\text{mm day}^{-1}$)** | 9.1618 | 9.5587 (+4.33%) | 9.8308 (+7.30%) | 10.0344 (+9.52%) |
| **CWD Spell Length (Days)** | 20.9498 | 22.7148 (+8.43%) | 22.6076 (+7.91%) | 27.9665 (+33.49%) |

---

## 🤝 Citation & Acknowledgments
* Data processed following **WASCAL** postprocessing procedures and **CMIP6** protocols.
* Boundary shapefiles and extraction parameters calibrated for Nigeria domain.

```text
Author: Samuel (SammieZalm)
Repository: https://github.com/SammieZalm/Nigeria-Climate-Projection-Rainfall-
```