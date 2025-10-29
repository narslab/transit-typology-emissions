# Transit System Typology and Emissions Prediction

This repository contains the data and code used in the study *Typology of U.S. transit systems reveals energy data gap and potential for diesel-based emissions reductions* .  
The work develops a novel national typology of 2,205 U.S. transit agencies and uses predictive modeling to estimate energy consumption and emissions where reporting is missing.

---

## Overview

The project integrates kernel principal component analysis (kPCA), Gaussian mixture modeling (GMM), and XGBoost prediction to:

- Classify U.S. transit systems into five operationally distinct types.  
- Address the **76% reporting gap** in diesel consumption across transit agencies.  
- Estimate **system-level and national transit emissions** on a well-to-wheel (WTW) basis.  
- Simulate **fleet electrification** and **grid decarbonization** scenarios to assess maximum potential reductions.

  <img width="4777" height="1387" alt="framework_diagram-v02" src="https://github.com/user-attachments/assets/b4bfc2e1-7a05-4054-96ec-0220cb60436d" />


---

## Repository Contents

| Directory / File | Description |
|------------------|-------------|
| `bin/python/`    | Scripts for dimensionality reduction (kPCA), clustering (GMM), and prediction (XGBoost). |
| `bin/jupyter/`   | Jupyter notebooks for exploratory analysis, visualization, and model validation. |
| `data/`          | Integrated NTD 2022 datasets (167 indicators, global + mode-specific). |
| `figures/`       | Plots of typology clusters, SHAP importance values, predicted vs. observed diesel use, and scenario results. |
| `results/`       | Clustering outputs, prediction metrics, and emissions scenario summaries. |

---


## Data Dictionary 
The dataset integrates information from the **2022 National Transit Database (NTD)** across operations, performance, financial, and service datasets for 2,205 U.S. transit systems.  
In the initial preprocessing phase, we began with **190 variables** aggregated from multiple NTD tables.  
After removing columns with more than **5% missing data**, **167 variables** remained for modeling and typology analysis.

Variables are organized into two categories:
- **Global variables** — apply to the entire transit agency.  
- **Mode-specific variables** — reported separately for each mode (e.g., MB = Motor Bus, DR = Demand Response, CR = Commuter Rail).


### File provided
- data/variable_dictionary.csv — complete list of all 167 variables with descriptions and metadata.

### Columns in variable_dictionary.csv
| Column          | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `variable_name` | Exact variable name used in the dataset or model.                           |
| `description`   | Short definition of what the variable measures.                             |
| `category`      | Either `global` or `mode_specific`.                                         |
| `mode`          | Transit mode abbreviation(s) if applicable (e.g., MB, DR, CR).              |
| `units`         | Measurement units (e.g., miles, hours, USD).                                |
| `source_table`  | Original NTD table or dataset.                                             |
| `transform`     | Scaling or preprocessing applied (e.g., log, min–max).                      |
| `missing_rate`  | Proportion of systems with missing data (0–1).                              |
| `notes`         | Additional clarifications or remarks.                                       |


### Mode Suffix Legend
| Code | Mode                        | Code | Mode                          |
|------|-----------------------------|------|-------------------------------|
| AR   | Aerial Tramway              | MB   | Motor Bus                     |
| CB   | Commuter Bus                | MG   | Monorail/Automated Guideway   |
| CC   | Cable Car                   | OR   | Other                         |
| CR   | Commuter Rail               | OT   | Other Transit                 |
| DR   | Demand Response             | PB   | Public Bike                   |
| DT   | Demand Response Taxi        | RB   | Rapid Bus                     |
| FB   | Ferryboat                   | SR   | Streetcar Rail                |
| HR   | Heavy Rail                  | TB   | Trolleybus                    |
| IP   | Inclined Plane              | TR   | Tram                          |
| JT   | Jitney                      | VP   | Vanpool                       |
| LR   | Light Rail                  | YR   | Hybrid Rail                   |


## Key Findings

- **Five transit types** identified: Metro Bus–Rail, Mid-Sized Urban, Hybrid Multimodal, Urban Specialized, and Diverse Operations.  
- **Data gap:** 76% of agencies do not report diesel use, primarily Mid-Sized Urban systems.  
- **Prediction model:** XGBoost yields R² = 0.92 and MAPE = 24% for diesel consumption .  
- **National baseline (2022):** 666M gallons of diesel → 8.17 MMTCO₂e annual WTW emissions.  
- **Decarbonization scenarios:**  
  - Fleet Electrification → 79% reduction (1.71 MMTCO₂e remaining).  
  - Fleet Electrification + Grid Decarbonization → 100% reduction (net zero WTW).  

---

## Contact

For questions or collaborations, contact **Mahsa Arabi** at [marabi@umass.edu](mailto:marabi@umass.edu).
