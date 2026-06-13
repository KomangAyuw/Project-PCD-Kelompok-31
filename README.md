# 🥭 Klasifikasi Penyakit pada Citra Buah Mangga Menggunakan Ekstraksi Fitur Tekstur GLCM dengan Metode KNN, SVM, dan Random Forest

## 👥 Anggota Kelompok 31

| Nama | NIM |
|------|-----|
| Sobihatun Nufus | F1D02410024 |
| Ni Komang Ayu Sumeitri | F1D02410084 |
| Sri Zul'Aini Ulya | F1D02410096 |

---

## 📖 Latar Belakang

Buah mangga merupakan salah satu komoditas pertanian unggulan yang memiliki nilai ekonomi tinggi. Namun, penyakit pada buah mangga menjadi salah satu faktor utama yang menurunkan kualitas dan nilai jual. Deteksi penyakit secara manual membutuhkan keahlian khusus dan waktu yang lama.

Pengolahan Citra Digital (PCD) menawarkan solusi otomatis untuk mendeteksi dan mengklasifikasikan penyakit pada buah mangga melalui analisis tekstur citra. Proyek ini mengimplementasikan teknik preprocessing dan ekstraksi fitur tekstur menggunakan **Gray Level Co-occurrence Matrix (GLCM)** yang dikombinasikan dengan model machine learning untuk mengklasifikasikan jenis penyakit pada buah mangga.

---

## 📋 Deskripsi Program

Program ini mengklasifikasikan penyakit buah mangga menggunakan pendekatan berikut:

1. **Preprocessing** — Menerapkan teknik pengolahan citra dari Modul 1-5 untuk meningkatkan kualitas citra sebelum ekstraksi fitur
2. **Ekstraksi Fitur** — Menggunakan GLCM untuk mengekstraksi fitur tekstur (contrast, dissimilarity, homogeneity, ASM, energy, correlation, entropy) pada 4 sudut arah (0°, 45°, 90°, 135°)
3. **Klasifikasi** — Membandingkan performa 3 model: **Random Forest**, **SVM**, dan **KNN**
4. **Analisis** — Membandingkan pengaruh berbagai kombinasi preprocessing terhadap akurasi klasifikasi

---

## 🍋 Dataset

Dataset terdiri dari **400 citra** buah mangga yang dibagi menjadi 4 kelas:

| Kelas | Jumlah Citra | Keterangan |
|-------|-------------|------------|
| **Alternaria** | 100 | Penyakit bercak titik hitam kecil |
| **Anthracnose** | 100 | Penyakit bercak hitam tersebar |
| **Healthy** | 100 | Buah mangga sehat |
| **Stem and Rot** | 100 | Penyakit busuk batang |

**Total: 400 citra | 4 kelas | Seimbang (100 citra/kelas)**

---

## 🔬 Tahap Preprocessing

### Baseline — Tanpa Preprocessing
Citra langsung dikonversi ke grayscale tanpa preprocessing tambahan dan langsung diproses GLCM sebagai acuan perbandingan.

### Percobaan 1
Pipeline preprocessing:
1. **Histogram Equalization** — Meratakan distribusi intensitas citra untuk memperjelas kontras
2. **Median Filter** — Mengurangi noise salt-and-pepper sambil mempertahankan tepi bercak penyakit

### Percobaan 2
Pipeline preprocessing:
1. **Median Filter** — Mengurangi noise salt-and-pepper sambil mempertahankan tepi bercak penyakit
2. **Otsu Thresholding** — Segmentasi otomatis area bercak penyakit
3. **Morphology Opening** — Membersihkan noise kecil pada hasil segmentasi Otsu
4. **Masking** — Mengisolasi area bercak penyakit dan meng-overlay warna kuning sebagai visualisasi


---

## 📊 Analisis & Hasil

### Ringkasan Akurasi (Testing)

| Model | Baseline | Percobaan 1 | Percobaan 2 |
|-------|:--------:|:-----------:|:-----------:|
| Random Forest | 83.75% | - | 73.75% |
| SVM | 83.75% | - | 78.75% |
| KNN | **85.00%** | - | 78.75% |

*(Percobaan 1 dan 3 akan diupdate setelah selesai)*

---

## 🏁 Kesimpulan

Proyek ini bertujuan membuktikan bahwa pemilihan teknik preprocessing yang tepat dapat mempengaruhi akurasi klasifikasi penyakit buah mangga. Hasil dari tiga percobaan dengan kombinasi preprocessing yang berbeda dibandingkan untuk menentukan pipeline preprocessing optimal bagi dataset ini.

---

## 📁 Struktur Repository

```
Project-PCD-Kelompok-31/
│
├── dataset/
│   ├── Alternaria/
│   ├── Anthracnose/
│   ├── Healthy/
│   └── Stem and Rot/
│
├── tanpa_preprocessing.ipynb       # Baseline
├── percobaan1.ipynb                # Percobaan 1: Histogram Equalization + Median
├── percobaan2.ipynb                # Percobaan 2: Median + Otsu + Opening + Masking
│
├── hasil_ekstraksi_baseline.csv
└── hasil_ekstraksi_percobaan2.csv
```
