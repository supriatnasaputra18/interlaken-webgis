# 🛰️ Deteksi Perubahan Tutupan Lahan Interlaken, Swiss (2020 & 2025)

Proyek analisis perubahan tutupan lahan di Kota Interlaken, Swiss, menggunakan citra satelit **Sentinel-2** dan algoritma klasifikasi **Random Forest**, divisualisasikan dalam WebGIS interaktif.

---

## 👥 Anggota Kelompok

| Nama | NIM |
|---|---|
| Davina Maulidya Maghfira | 1242002052 |
| Muhammad Khoiruddin | 1242002026 |
| Muhammad Afzaal Ghofran | 1232002004 |
| Nuraini | 1232002077 |
| Salvina Rosalie | 1232002074 |
| Supriatna Saputra | 1232002067 |

**Mata Kuliah:** Kapita Selekta & Mahadata — Universitas Bakrie

---

## 🌍 Informasi Studi

| | |
|---|---|
| **Kota/Wilayah** | Interlaken, Kanton Bern, Swiss |
| **Objek Klasifikasi** | Vegetasi vs Bangunan (2 kelas) |
| **Periode** | 2020 & 2025 (composite Juli–Agustus) |
| **Sumber Citra** | Sentinel-2 Surface Reflectance Harmonized (resolusi 10m) |
| **Metode** | Random Forest (150 trees), cloud masking berbasis band SCL |
| **Akurasi Model** | 94,64% (Kappa 0,893) |

---
## 📁 Struktur Folder
 
```
├── README.md              # Dokumen ini
├── index.html              # WebGIS interaktif (single-file: peta, data proses, evaluasi, insight)
├── interlaken-hero.jpg     # Gambar hero/header WebGIS
├── GEE/                     # Script Google Earth Engine
│   └── Script.js                # Preprocessing, cloud masking, composite, training & klasifikasi RF
├── Data Source/              # Data mentah/sumber
│   ├── Batas_Wilayah_Interlaken.geojson   # Batas administrasi (sumber: GADM)
│   ├── Interlaken_Classified_2020.tif     # Raster hasil klasifikasi 2020
│   ├── Interlaken_Classified_2025.tif     # Raster hasil klasifikasi 2025
│   ├── GroundTruth_NDVI_2020.zip          # Titik ground truth vegetasi (NDVI) 2020
│   ├── GroundTruth_NDVI_2025.zip          # Titik ground truth vegetasi (NDVI) 2025
│   ├── GroundTruth_NDBI_2020.zip          # Titik ground truth bangunan (NDBI) 2020
│   ├── GroundTruth_NDBI_2025.zip          # Titik ground truth bangunan (NDBI) 2025
│   ├── TrainingSet_Gabungan_2020_2025.csv # Data training ground truth (432 titik)
│   ├── TestingSet_Gabungan_2020_2025.csv  # Data testing ground truth (168 titik)
│   ├── Target_2020_GeoJSON.geojson        # Vektor area bangunan 2020
│   ├── Target_2025_GeoJSON.geojson        # Vektor area bangunan 2025
│   ├── Gain_GeoJSON.geojson               # Area bangunan baru (2020→2025)
│   └── Loss_GeoJSON.geojson               # Area bangunan hilang (2020→2025)
├── Result/                  # Hasil olahan/output analisis
│   ├── Interlaken_Classified_2020.tif        # Raster hasil klasifikasi 2020
│   ├── Interlaken_Classified_2025.tif        # Raster hasil klasifikasi 2025
│   ├── Sentinel_RGB_2020.tif                 # Komposit RGB Sentinel-2 2020
│   ├── Sentinel_RGB_2025.tif                 # Komposit RGB Sentinel-2 2025
│   ├── Target_2020_GeoJSON.geojson           # Vektor area bangunan 2020
│   ├── Target_2025_GeoJSON.geojson           # Vektor area bangunan 2025
│   ├── Gain_GeoJSON.geojson                  # Area bangunan baru (2020→2025)
│   ├── Loss_GeoJSON.geojson                  # Area bangunan hilang (2020→2025)
│   ├── TrainingSet_Gabungan_2020_2025.csv    # Data training ground truth
│   ├── TestingSet_Gabungan_2020_2025.csv     # Data testing ground truth
│   ├── Feature_Importance_Random_Forest.png  # Chart kontribusi band/indeks ke model
│   ├── Gain_vs_Loss_Building_2020_ke_2025.png # Chart perbandingan luas gain vs loss
│   ├── Net_Change_2020_ke_2025.png           # Chart net change per kelas
│   └── Perbandingan_Luas_Tutupan_Lahan.png   # Chart luas tutupan lahan 2020 vs 2025
└── Report/                  # Laporan tugas akhir
    └── Laporan_Akhir_Lahan_Interlaken.pdf

```
## 🔗 Tautan

- **WebGIS (Live):** https://interlaken-webgis.vercel.app/
- **Script GEE:** https://code.earthengine.google.com/a973923d548488ed179181facb59533a
- **Laporan Lengkap (PDF):** https://drive.google.com/drive/folders/1PLVG6aTRll79fBG3PK3kllD9PNMY2cQa?usp=sharing

---

## 🚀 Cara Membuka WebGIS

**Opsi 1 — Online (paling mudah)**
Klik langsung tautan WebGIS di atas.

**Opsi 2 — Offline / dari repository ini**
1. Unduh atau clone repository ini
2. Buka folder `webgis/`
3. Buka file `index.html` dua kali klik — akan langsung terbuka di browser (Chrome/Firefox/Edge), tanpa perlu instalasi apapun

---

## 🗺️ Fitur WebGIS

WebGIS terdiri dari 5 tab + 1 fitur pendukung:

1. **Home** — ringkasan proyek & statistik utama
2. **Peta Hasil** — peta interaktif (basemap, batas kota, klasifikasi 2020/2025, target bangunan/vegetasi, gain/loss, popup info, layer control)
3. **Data & Proses** — transparansi metodologi (sumber data, preprocessing, ground truth, parameter model)
4. **Evaluasi Model** — confusion matrix, accuracy, precision, recall, F1-score, keterbatasan model
5. **Insight Hasil** — ringkasan perubahan, lokasi & pola perubahan terbesar, rekomendasi
6. **Chatbot Statis** — mempermudah menjawab/menjelaskan hasil analisis & insight hasil

---

## 🧰 Teknologi

Sentinel-2 · Google Earth Engine · Random Forest · Leaflet.js · Chart.js · GeoJSON/GeoTIFF · Python (rasterio, numpy) · JavaScript
