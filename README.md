# 🫀 Heart Disease Causal Analysis

Analisis hubungan kausalitas faktor-faktor klinis terhadap penyakit jantung menggunakan Structural Causal Modeling dan framework DoWhy.

## 📋 Deskripsi

Project ini menganalisis hubungan kausal antara faktor-faktor klinis (variabel eksogen) terhadap kejadian penyakit jantung menggunakan pendekatan **Structural Causal Modeling**. Berbeda dengan analisis korelasi tradisional, pendekatan kausal memungkinkan kita memahami hubungan sebab-akibat yang sebenarnya antar variabel.

### Mengapa Causal Inference?

> *"Correlation does not imply causation"*

Pendekatan tradisional dalam epidemiologi umumnya berfokus pada identifikasi korelasi atau asosiasi statistik. Namun, untuk merancang intervensi medis yang efektif, pemahaman kausalitas sangat penting.

## 📊 Dataset

**Heart Disease UCI Dataset** dari Kaggle/UCI Machine Learning Repository.

| Informasi | Nilai |
|-----------|-------|
| Total Records (setelah cleaning) | 302 |
| Jumlah Variabel | 14 |
| Missing Values | 0 |
| Duplikat Dihapus | 723 |

### Variabel Dataset

| Variabel | Deskripsi | Tipe |
|----------|-----------|------|
| `age` | Usia pasien dalam tahun | Numerik |
| `sex` | Jenis kelamin (1=pria, 0=wanita) | Kategorikal |
| `cp` | Tipe nyeri dada (0-3) | Kategorikal |
| `trestbps` | Tekanan darah istirahat (mm Hg) | Numerik |
| `chol` | Kolesterol serum (mg/dl) | Numerik |
| `fbs` | Gula darah puasa > 120 mg/dl | Kategorikal |
| `restecg` | Hasil ECG istirahat (0-2) | Kategorikal |
| `thalach` | Detak jantung maksimum | Numerik |
| `exang` | Angina akibat olahraga | Kategorikal |
| `oldpeak` | Depresi ST relatif terhadap istirahat | Numerik |
| `slope` | Slope segmen ST (0-2) | Kategorikal |
| `ca` | Jumlah pembuluh darah utama (0-4) | Kategorikal |
| `thal` | Thalassemia (0-3) | Kategorikal |
| `target` | Diagnosis penyakit jantung (0/1) | Target |

## 🔬 Metodologi

### 1. Dimension View
- Correlation Heatmap
- Distribusi variabel numerik dan kategorikal
- Boxplot comparison berdasarkan status penyakit
- Visualisasi 3D interaktif

### 2. Table View
- Statistik deskriptif
- Crosstab analysis
- Mean comparison by target group

### 3. Causal Graph View
- Theory-based Directed Acyclic Graph (DAG)
- 21 causal edges berdasarkan domain knowledge medis
- DoWhy causal inference model
- Refutation tests untuk validasi

## 📈 Hasil Utama

### Hubungan Kausal Teridentifikasi

Teridentifikasi **21 hubungan kausal** antar variabel. Penyakit jantung dipengaruhi langsung oleh 13 variabel klinis.

### Estimasi Efek Kausal (ATE)

| Treatment | Outcome | ATE | Interpretasi |
|-----------|---------|-----|--------------|
| Cholesterol | Heart Disease | -0.000868 | Setiap ↑1 mg/dl chol → ↓0.09% probabilitas |
| Blood Pressure | Heart Disease | -0.002851 | Setiap ↑1 mm Hg → ↓0.29% probabilitas |

### Validasi (Refutation Tests)

| Test | Original Effect | New Effect | Status |
|------|-----------------|------------|--------|
| Random Common Cause | -0.000868 | -0.000865 | ✅ ROBUST |
| Placebo Treatment | -0.000868 | -0.000060 | ✅ VALID |

### Variabel Paling Berpengaruh

1. **exang** (Exercise Induced Angina) - korelasi: -0.436
2. **cp** (Chest Pain Type) - korelasi: 0.432
3. **oldpeak** (ST Depression) - korelasi: -0.429
4. **thalach** (Max Heart Rate) - korelasi: 0.420
5. **ca** (Number of Major Vessels) - korelasi: -0.409

## 🚀 Instalasi & Penggunaan

### Prerequisites

- Python 3.8 atau lebih tinggi
- pip package manager

## 📁 Struktur Project

```
heart-disease-causal-analysis/
│
├── Heart_Disease_Causality_Explorer.ipynb  # Notebook utama
├── heart.csv                                # Dataset (upload terpisah)
├── requirements.txt                         # Dependencies
├── README.md                                # Dokumentasi
```

## 🛠️ Tech Stack

- **Python 3.8+** - Bahasa pemrograman
- **Pandas & NumPy** - Data manipulation
- **Matplotlib & Seaborn** - Visualisasi statis
- **Plotly** - Visualisasi interaktif
- **NetworkX** - Graph analysis
- **DoWhy** - Causal inference framework
- **Scikit-learn** - Machine learning utilities
- **Statsmodels** - Statistical modeling
- **SciPy** - Scientific computing

## 📚 Referensi

1. Janosi, A., Steinbrunn, W., Pfisterer, M., & Detrano, R. (1988). Heart Disease Data Set. UCI Machine Learning Repository.
2. Pearl, J. (2009). *Causality: Models, Reasoning, and Inference* (2nd ed.). Cambridge University Press.
3. Sharma, A., & Kiciman, E. (2020). DoWhy: An End-to-End Library for Causal Inference. [arXiv:2011.04216](https://arxiv.org/abs/2011.04216)
4. [DoWhy Documentation](https://www.pywhy.org/dowhy/)
5. [WHO Cardiovascular Diseases Fact Sheet](https://www.who.int/news-room/fact-sheets/detail/cardiovascular-diseases-(cvds))

## 👤 Author

**Gian Rofiqri Andra**  
NIM: 24917036  
Program Studi Informatika - Universitas Islam Indonesia

---

<p align="center">
  <i>Dibuat untuk memenuhi Tugas Besar mata kuliah Causal Modeling</i>
</p>
