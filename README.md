# 🌊 Contrast-Enhanced Satellite Optical Imagery for Marine Ecosystem Monitoring  

![12](https://github.com/user-attachments/assets/0f6724a0-745f-4ad7-86e5-53328abef3c0)


## A Clustering-Based Approach to Phytoplankton Segmentation

This repository accompanies the research journal titled:  
**"Contrast-Enhanced Satellite Optical Imagery for Marine Ecosystem Monitoring: A Clustering-Based Approach to Phytoplankton Segmentation"**

---

## 🌍 Project Scope

This project applies unsupervised clustering on Sentinel-2 satellite imagery to analyze **phytoplankton density variations** from **2016 to 2025** across three key marine ecosystems:

- 🇪🇸 **Gulf of Cádiz** – Spain  
- 🇮🇳 **Arabian Sea** – India  
- 🇧🇩 **Bay of Bengal** – Bangladesh  

The segmentation aims to uncover ecological shifts in **marine biodiversity**, particularly as phytoplankton—being a foundational food source—impacts the migration patterns of marine species.

---

## 📦 Data Acquisition

- **Source**: ESA’s Copernicus Climate Data Store (CDS)  
- **Satellites Used**: Sentinel-2 and Sentinel-1  
- **Resolution**: ≥10,000×10,000 pixels  
- **Temporal Coverage**: 2016–2025  
- **Sky Conditions**: ≤6% cloud cover to minimize atmospheric distortion  

---

## 🧪 Methodology

### ✅ Selection Criteria
- High-resolution, georeferenced, low-noise optical images  
- Selected images had clear visibility with minimum distortion  
- RGB true-color and enhanced variants were both utilized  

### ✅ Preprocessing Pipeline
1. **Image Resizing** to reduce computational cost  
2. **Contrast Stretching** using OpenCV for enhancing chlorophyll presence visibility  
3. **Min-Max Normalization** for intensity consistency  
4. **Gaussian Blurring** for noise reduction  
5. **Resolution Enhancement** via bicubic interpolation
   
![11](https://github.com/user-attachments/assets/8eb55fcc-ea77-4ff7-91c9-d0c22dd4c3dc)


### ✅ Land-Ocean Segmentation
- HSV-based thresholding applied to extract ocean from land  
- Hue range 65–80 classified land; rest isolated as ocean  
- Adaptive thresholding generated a binary mask  

![13](https://github.com/user-attachments/assets/70472687-5a15-48c2-8bf6-9b1e166e72c9)


### ✅ Ocean Segmentation & Clustering
- Clustering categorized pixels into:
  - Deep water
  - Low, medium, and high-density phytoplankton zones
- **K-Means Clustering** isolated phytoplankton densities
- **SLIC Superpixels** validated the segmented boundaries  

![14](https://github.com/user-attachments/assets/0dc2fd61-9797-406f-818c-7d5abae03dd9)


### ✅ Temporal Analysis (2016–2025)
- Images sampled seasonally (quarterly)
- **Phytoplankton Density Index (PDI)** calculated  
- **Trend detection** using linear regression + Fourier decomposition  
- Geolocation of hotspots extracted from coordinate grids  

---

## 🧠 Ecological Motivation

Phytoplankton changes can signal large-scale marine disturbances. These organisms drive the marine food web, and their densities influence:
- Deep-sea species migration  
- Non-predator fish stock fluctuations  
- Risk levels of **harmful algal blooms (HABs)**  

---

## 📈 Key Results & Discussion

### 📊 Phytoplankton Density Trends

| Region         | Density Change | Diatoms | Dinoflagellates | Cyanobacteria |
|----------------|----------------|---------|------------------|----------------|
| **Bay of Bengal** | +30%           | -16%    | +11%             | +5%            |
| **Arabian Sea**   | +45%           | -18%    | +14%             | +4%            |
| **Gulf of Cádiz** | -22%           | -17%    | +14%             | +3%            |

### 📍 Geolocation Observations
- Northward shift of **1.5°–2°** in bloom zones  
- **High-density areas** aligned with **nutrient-rich upwelling zones**  
- **Low-density** zones in stratified, warmer regions  

### 🐠 Ecosystem Impacts
- Temporary increase in small pelagic fish in bloom regions  
- Reduction in diatoms and increase in dinoflagellates → risk of HABs  
- Migration of deep-sea life following phytoplankton redistribution  

---

## ⚙️ Computational Efficiency

- Parallel processing of 256×256 tiles using Python multiprocessing  
- ~63% speed-up with tiling strategy  
- Segmentation accelerated using optimized OpenCV + SLIC  
- Peak RAM: ~2.1GB  
- GPU-friendly (runs on NVIDIA Xavier, RTX 1060, Colab A100)  

---

## 💡 Notable Contributions

- Temporal phytoplankton mapping for marine monitoring  
- Geospatial density tracking of ocean micro-organisms  
- Computationally optimized remote sensing pipeline  

---

## 📁 What's in this Repo?

- `machli.ipynb` — Full pipeline (preprocessing, clustering, analysis)  
- Visual comparisons: 2016 vs 2025 bloom zones  
- Heatmaps & geolocation tracking from segmented outputs  

---

## 🚀 Future Directions

- Use chlorophyll bands or multispectral indices  
- Train deep learning models for supervised phytoplankton classification  
- Build a dashboard for real-time bloom monitoring  
- Integrate with fish stock data for conservation alerts  

---

## 🤝 Contributing

Pull requests and suggestions for:
- Model performance  
- Dataset expansion  
- Biological validation  
are welcome and appreciated!

---

## 📜 License

This project is licensed under the MIT License.

---

## 📚 References

See `Methodology.docx` for full academic references.
