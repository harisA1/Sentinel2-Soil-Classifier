# Sentinel2-Soil-Classifier

This repository provides a complete pipeline for classifying bare soil and vegetation pixels using Sentinel-2 multispectral imagery, multiple spectral indices, and statistically derived thresholds based on the HISET method. Ground truth reference is derived from ESA WorldCover land use data.

---

## 🛰️ Data Sources

- **Sentinel-2**: Multiband imagery used to compute spectral indices.
- **ESA WorldCover (10m)**: Used as reference land cover for Cropland vs Grassland classes.

---

## 🧮 Methodology

1. **Index Computation**: Computes a variety of indices including:
    - NDVI
    - NBR2
    - PV+IR2 (custom)
    - BSI, NDTI, SAVI, RI, etc.
2. **Alignment**: ESA WorldCover is reprojected to match Sentinel-2 spatial grid.
3. **Thresholding with HISET**: For each index, thresholds are selected based on minimizing histogram overlap between cropland and grassland classes.
4. **Classification**:
    - Pixels are classified as **Bare Soil**, **Vegetation**, or **Other**.
    - A final soil/veg mask is exported as a GeoTIFF file.

---

## 📦 Output

- **bare_soil_mask_026.tif**: Raster with classified pixels:
    - `0` – Other  
    - `1` – Bare Soil  
    - `2` – Vegetation

---

