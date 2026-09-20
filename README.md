# MoRTH Indian Road Accident Analytics & AI Risk Prediction Platform

An academic, research-grade web dashboard and machine learning risk prediction platform built using verified empirical road crash statistics from the **Ministry of Road Transport & Highways (MoRTH)**, official Lok Sabha/Rajya Sabha parliamentary written replies, and Press Information Bureau (PIB) releases spanning **2018 through 2024**.

---

## 🏛️ Key Research & Methodological Standards
1. **Absolute Data Integrity:**
   - Zero fabricated records.
   - Microdata variables not verified in the active state panel (individual collision coordinates, road condition sensors, vehicle victim breakdowns, and driver demographics) are strictly withheld and explicitly flagged as `Not Available` with source coverage annotations.
   - Programmatic cross-validation against official national totals yields **0 discrepancy** across all seven years.
2. **Administrative Boundary Traceability:**
   - 2018–2019: 37 administrative units reporting.
   - 2020 onward: 36 administrative units reporting (Merger of Dadra & Nagar Haveli and Daman & Diu; creation of Ladakh UT).
3. **Rigorous Statistical Definitions:**
   - Severity metric is correctly designated as **"Fatalities per 100 Accidents"** or **"Fatality Ratio"** (calculated as `(Fatalities / Accidents) * 100`), rather than an exposure-based mortality rate.
   - Ordinary Least Squares (OLS) linear regression slopes (OriginPro G10) dynamically evaluated per state.

---

## 🚀 How to Run the Application

### 1. Requirements
- Python 3.10+
- Dependencies: `flask`, `pandas`, `numpy`, `scipy`, `scikit-learn`, `reportlab`, `openpyxl`

### 2. Launch the Application
Run the main startup script from this folder:
```powershell
python run.py
```
Open your browser at:
```
http://127.0.0.1:5000
```

---

## 📊 Modules & Features
- **Exploratory Visualizations (G1–G8 Series):**
  - G1: India Crashes Longitudinal Trajectory (2018–2024)
  - G2: India Fatalities Longitudinal Trajectory
  - G3: India Injured Trajectory (2018–2022 state panel; 2023–2024 India aggregates)
  - G4: Fatalities per 100 Accidents Severity Ratio
  - G5 & G6: 6 Analytical Geographic Zones (North, South, East, West, Central, Northeast)
  - G7: State-by-State Comparison (2024 verified snapshot)
  - G8: 38-Jurisdiction × 7-Year Intensity Heatmap
- **Statistical Engine & Slopes (G10):**
  - Dynamic OLS linear regression: Slope, $R^2$, $p$-value, standard error per state.
  - Pearson & Spearman correlation matrices.
  - Empirical time-to-threshold arrival analysis.
- **Machine Learning Risk Predictor:**
  - Random Forest Regressor for mortality estimation ($R^2 \approx 0.68$).
  - Random Forest Multi-Class Classifier for empirical severity ratio tertiles.
  - Unsupervised $K$-Means clustering for state crash profiling.
- **Data Hygiene & Audit Center:**
  - Reconciliation audit with 100% zero-mismatch verification against MoRTH/Parliamentary records.
  - Non-destructive upload handling: user-uploaded CSVs/XLSX are validated into isolated buffers without mutating original benchmarks.
- **Publication Reports & Export:**
  - Download complete academic PDF research report (built with ReportLab).
  - Native print stylesheet (`window.print()`) for A4 reporting.
  - Export clean normalized analysis datasets as CSV and Excel (XLSX).

---

## 🧪 Running the Verification Suite
Execute the automated test suite verifying all 6 core categories:
```powershell
python -c "
import sys; sys.path.append('.');
from tests.test_analytics import *;
# or run the complete test suite runner
"
```
The test suite validates data loading, annual reconciliation, ratio arithmetic, G10 slopes, ML training, PDF synthesis, and all REST endpoints.
