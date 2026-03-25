# Kerala Rainfall Prediction (JJAS & OND)

This project focuses on **seasonal rainfall prediction for Kerala** using machine learning models (KNN, ELM, ANN) trained on historical climate data.

The dataset is derived from NetCDF rainfall data and filtered using the **Kerala state boundary shapefile**.

---

##  Project Structure

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
│
├── ne_10m_admin_1_states_provinces/
│   ├── .shp, .shx, .dbf, .prj
│
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

##  Dataset Format

```text
LATITUDE | LONGITUDE | YEAR | SEASON_SUM
```

* `kerala_jjas.csv` → `JJAS_SUM`
* `kerala_ond.csv` → `OND_SUM`

---

##  Models Used

* KNN (K-Nearest Neighbors)
* ELM (Extreme Learning Machine)
* ANN (Artificial Neural Network)

---
##  Features

* Grid-wise rainfall modeling
* Time-series prediction (sliding window)
* Seasonal forecasting
* Spatial visualization using shapefile

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
