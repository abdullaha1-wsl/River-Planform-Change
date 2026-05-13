# Flood-Driven River Planform Change Detection — Chenab River, Indus Basin

[![GEE](https://img.shields.io/badge/Google%20Earth%20Engine-4285F4?logo=googleearth&logoColor=white)](https://earthengine.google.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**A complete pipeline to detect and quantify river planform changes (erosion/deposition) using Sentinel‑2 imagery, Google Earth Engine, and Random Forest with SHAP explanation.**

---

## 📌 Overview

This repository contains a Jupyter Notebook that implements a fully automated workflow for:

- **Water mask extraction** from Sentinel‑2 SR imagery using MNDWI + dual cloud masking (QA60 + SCL)
- **Dynamic Otsu thresholding** with clamping to avoid all‑zero exports
- **Planform change mapping** → erosion / deposition areas (km²) between pre‑flood and post‑flood windows
- **Hydrograph analysis** from GRDC `.day` discharge files (peak, duration, cumulative, rise/fall rates)
- **Random Forest regression** to predict lateral erosion from hydro‑meteorological features
- **SHAP explainability** (beeswarm + bar charts) to interpret model predictions

**Case study:** Chenab River (Indus Basin), Pakistan — 2014, 2022 (megaflood), and 2023 events.

---

## 📂 Repository Structure
River-Planform-Change/
├── river_planform_change.ipynb # Main Jupyter notebook (full pipeline)
├── data/
│ └── discharge_data/ # Synthetic GRDC .day files
│ ├── discharge_2014.day
│ ├── discharge_2022.day
│ └── discharge_2023.day
└── README.md # You are here

text

After running the notebook, additional folders will be created:

- `data/masks/` – GeoTIFF water masks exported from GEE
- `outputs/` – PNG figures (change maps, hydrographs, SHAP plots) + Excel workbooks

---

## 🚀 Getting Started

### 1. Prerequisites

- **Python** 3.8 or higher
- **Google Earth Engine** account ([sign up here](https://signup.earthengine.google.com/))
- Google Cloud project with Earth Engine API enabled

### 2. Clone the repository

```bash
git clone https://github.com/abdullaha1-wsl/River-Planform-Change.git
cd River-Planform-Change
3. Install dependencies
bash
pip install earthengine-api numpy pandas matplotlib rasterio scikit-learn shap openpyxl matplotlib-scalebar
4. Authenticate with Google Earth Engine
python
import ee
ee.Authenticate()   # follow the browser link
ee.Initialize(project='your-project-id')
Replace your-project-id with your actual GEE project ID (the notebook already contains one – change it to yours).

5. Run the notebook
Open Jupyter Notebook or JupyterLab:

bash
jupyter notebook river_planform_change.ipynb
Then run all cells sequentially.

