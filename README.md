# Interannual BRDF and Reflectance Fitting Datasets

This repository contains the core datasets and related processing scripts for analyzing the interannual stability and phenological variations of surface reflectance.

## 📊 Overview

To comprehensively evaluate the year-to-year variations and deviations from the multi-year mean curve, we derived and compiled two main sets of parameters across seven spectral bands covering a 11-year period (2014–2024):
1. **BRDF Model Parameters**: Parameters required for the Bidirectional Reflectance Distribution Function modeling.
2. **Reflectance Fitting Parameters**: Continuous modeling statistics of Nadir BRDF-Adjusted Reflectance (NBAR).

## 🗂️ Data Structure

The datasets are provided in both standard `CSV` and high-performance `HDF5` formats for broad accessibility.

* `multi_year_fitting_stats.h5` / `.csv`: The quantified multi-year phenological fitting statistics. Contains the following key metrics for each band and year:
  * **A (Amplitude)**: The seasonal magnitude of reflectance.
  * **tp (Phase)**: The day of year (DOY) corresponding to the peak reflectance.
  * **C (Offset)**: The annual baseline reflectance.
  * **R-squared ($R^2$) & Mean Bias**: Statistical indicators of model fitting accuracy.
  * **N**: Number of valid observations.
* `brdf_parameters_data...` *(根据你的实际文件名修改)*: The processed BRDF weighting parameters.

## 🚀 Quick Start (Python)

You can easily load the reflectance fitting statistics using the `pandas` library. Note that reading `.h5` files requires the `tables` (PyTables) dependency.

```python
import pandas as pd

# Load the multi-year fitting parameters
file_path = "multi_year_fitting_stats.h5"
df_stats = pd.read_hdf(file_path, key="stats")

# Display the data for the year 2021
data_2021 = df_stats[df_stats['Year'] == 2021]
print(data_2021)
