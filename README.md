# Sentinel2-Soil-Classifier

This repository provides a complete pipeline for classifying bare soil and vegetation pixels using a **minimum composite** of three Sentinel-2 multispectral images. It computes multiple spectral indices and uses statistically derived thresholds via the HISET method, aligned to ESA WorldCover reference land cover data.

---

## 🛰️ Data Sources

- **Sentinel-2**: Three images from different dates (`S2_enmap_AOI.tif`, `_09.tif`, `_11.tif`) used to compute spectral indices and build a **minimum-value composite** to reduce vegetation and highlight persistent bare soil.
- **ESA WorldCover (10m)**: Used as reference land cover to identify Cropland and Grassland pixels.

---

## 🧮 Methodology

1. **Index Computation**: For each Sentinel-2 image, several spectral indices are computed:
    - NDVI
    - NBR2
    - PV+IR2 (custom)
    - BSI, NDTI, SAVI, RI, and others

2. **Minimum Composite**: A pixel-wise **minimum composite** is created across the three acquisition dates to suppress transient vegetation effects and emphasize stable surface reflectance (bare soil pixels).

3. **Reprojection & Alignment**: ESA WorldCover land cover map is reprojected to align with Sentinel-2 spatial resolution and CRS.

4. **HISET Thresholding**:
    - For each index, histograms of Cropland and Grassland pixel values are compared.
    - HISET is used to find the most statistically distinct threshold between the two classes.

5. **Classification**:
    - Pixels are classified as:
        - **0** – Other
        - **1** – Bare Soil
        - **2** – Vegetation
    - Output is saved as a GeoTIFF raster.

---

## 📦 Output

- **bare_soil_mask.tif**: 2D raster of classified pixels.

---


