# Kerala Rainfall Prediction (JJAS & OND)

Seasonal rainfall prediction for Kerala using machine learning (KNN, ELM, ANN). The project works on preprocessed grid-wise seasonal totals (JJAS and OND) and includes spatial visualizations masked to Kerala's boundary.

---

## Project Structure

```text
Rainfall/
│
├── data/
│   ├── data_preprocessing.ipynb
│   ├── kerala_jjas.csv
│   └── kerala_ond.csv
│
├── JJAS.ipynb
├── OND.ipynb
├── JJAS_with_OND.ipynb
├── OND_with_JJAS.ipynb
├── JJAS ensemble.ipynb
├── seasonal_detrending.ipynb
├── ne_10m_admin_1_states_provinces/  (shapefile)
└── README.md
```

---

##  Quick Start

The preprocessing step is already completed. You can directly run:

* `JJAS.ipynb` → JJAS season model
* `OND.ipynb` → OND season model

✔ Uses preprocessed CSV files
✔ No need to process NetCDF again

---

##  Data Preprocessing (Optional)

If you want to regenerate the dataset:

###  Requirements

* NetCDF rainfall data (`.nc`)
* Shapefile for Kerala boundary

---

###  NetCDF Data Source

Download rainfall datasets from:

 https://cds.climate.copernicus.eu/
 https://data.gov.in/

(Search for: *India gridded rainfall NetCDF*)

---

###  Run preprocessing

Open:

```text
data/data_preprocessing.ipynb
```

This will:

1. Load `.nc` files
2. Extract seasonal rainfall:

   * JJAS (June–September)
   * OND (October–December)
3. Filter using Kerala shapefile
4. Generate CSV files

---

##  Shapefile Information

This project uses a shapefile to accurately extract **Kerala’s geographical boundary**.

###  Download Link

 [Download Natural Earth Admin-1 Shapefile](https://naciscdn.org/naturalearth/10m/cultural/ne_10m_admin_1_states_provinces.zip?utm_source=chatgpt.com)

---

###  Notes

* Extract the ZIP file
* Place all extracted files inside:

```text
ne_10m_admin_1_states_provinces/
```

* Required components:

  ```
  .shp, .shx, .dbf, .prj, .cpg
  ```

---

## Notebooks

- `JJAS.ipynb` — JJAS-only experiments and visualization
- `OND.ipynb` — OND-only experiments and visualization
- `JJAS_with_OND.ipynb` — JJAS prediction using previous OND features
- `OND_with_JJAS.ipynb` — OND prediction using same-year JJAS features
- `JJAS ensemble.ipynb` — ensemble/combined analyses
- `seasonal_detrending.ipynb` — detrending and signal processing
- `data/data_preprocessing.ipynb` — regenerate CSVs from NetCDF

---

## Data

- Preprocessed CSVs: `data/kerala_jjas.csv`, `data/kerala_ond.csv`
- Shapefile folder: `ne_10m_admin_1_states_provinces/` (place the extracted Natural Earth admin-1 files here)

Dataset format (per-row):

```text
LATITUDE | LONGITUDE | YEAR | SEASON_SUM
```

* `kerala_jjas.csv` → `JJAS_SUM`
* `kerala_ond.csv` → `OND_SUM`

---

## Models & Hyperparameters (used in notebooks)

- **KNN**: `n_neighbors=5`, `metric='euclidean'`, `weights='uniform'`
- **ELM (Extreme Learning Machine)**: `n_hidden=15`, `activation='sigmoid'`, `alpha=1e-3`, `random_state=42`
- **ANN (Radial-Basis + LM trainer)**: `hidden_size=20`, radial-basis activation, `LM damping=1.0`, `max_iters=20–50` (varies by notebook), `torch.manual_seed(42)`

If you want these exposed or changed, open the model definition cells in the notebooks and edit the parameters at the top of the training sections.

---

## Recent Fixes (May 2026)

- Placed colorbars in a dedicated right-side axis (`cax`) and reserved figure space in `JJAS_with_OND.ipynb` and `OND_with_JJAS.ipynb` to avoid Matplotlib `tight_layout` warnings.
- Fixed a `NameError: Tuple` in `OND_with_JJAS.ipynb` by adding `from typing import Tuple` to the imports.

---

## How to run

- Start Jupyter: `jupyter lab` or `jupyter notebook` and open the desired notebook.
- Run preprocessing only if you need to recreate `data/*.csv` from NetCDF.
- Visualizations require the shapefile folder to be present to mask maps to Kerala.

---

##  Notes

* Preprocessing is one-time
* CSV files are optimized for fast ML training
* Shapefile ensures **accurate region-based filtering**

---

##  License

Academic and research use.

---

##  Acknowledgment

* Climate data: Public/government datasets
* Shapefile: Natural Earth

---

##  Recommendation

* Use provided CSV files for faster execution
* Ensure shapefile folder is present for visualization
