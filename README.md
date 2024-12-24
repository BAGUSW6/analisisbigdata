# 🏨 Strategi Optimalisasi Reservasi Hotel: Analisis Pola Pemesanan dan Faktor Utama Pembatalan

## 🔖 Bab 1: Pendahuluan

### 🔎 Latar Belakang
Pembatalan pemesanan hotel adalah masalah signifikan yang berdampak pada pendapatan dan efisiensi operasional. Masalah ini memerlukan perhatian serius untuk membantu hotel memahami faktor-faktor utama yang memengaruhi pembatalan dan mengembangkan strategi pencegahan yang efektif.

Penelitian ini menggunakan data pemesanan hotel dari tahun 2015 hingga 2017 dan menggabungkan metodologi Exploratory Data Analysis (EDA) serta Model-Based Feature Selection dengan algoritma Random Forest Classifier. Melalui pendekatan ini, analisis dilakukan untuk menampilkan pola demografis tamu, pola pemesanan, serta mengidentifikasi fitur atau variabel yang paling berpengaruh terhadap pembatalan pemesanan.

Dengan hasil analisis ini, diharapkan dapat memberikan wawasan strategis bagi manajemen hotel terkait penyebab utama pembatalan. Temuan dari penelitian ini memberikan wawasan strategis untuk mengurangi pembatalan dan menyempurnakan layanan hotel.

---

## 🔧 Bab 2: Package yang Diperlukan

Untuk menjalankan analisis ini, pastikan Anda telah menginstal package berikut:

 `requests`  `pandas`  `numpy`  `matplotlib`  `seaborn`  `plotly` 
 `scikit-learn`

### 📃 Perintah Instalasi:
```bash
!pip install pandas numpy matplotlib seaborn plotly scikit-learn
```

---

## 📊 Bab 3: Dataset

### 🔍 Sumber Data
Dataset ini diambil dari [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010) yang mencakup data pemesanan hotel dari tahun 2015 hingga 2017. Dataset ini berisi informasi tentang 32 variabel yang terkait dengan detail pemesanan, termasuk data tamu, karakteristik hotel, dan faktor-faktor yang dapat memengaruhi status reservasi. 

Dataset "Hotel Bookings" yang digunakan dalam proyek TidyTuesday pada 11 Februari 2020 berasal dari penelitian Antonio, Almeida, dan Nunes (2019). Data mencakup 32 variabel dan bertujuan untuk menganalisis faktor-faktor yang memengaruhi pembatalan pemesanan hotel.

### 🔄 Pembersihan Data
Dataset memiliki nilai NULL pada beberapa kolom:

- **`company`**: 112.593
- **`agent`**: 16.340

Pembersihan dilakukan dengan:
- Menghapus kolom **`country`** dengan 488 nilai NULL.
- Menghapus kolom **`children`** dengan 4 nilai NULL.

| 🔬 Variabel            | Nilai Null (Before) | Nilai Null (After) |
|-------------------|---------------------|--------------------|
| `children`        | 4                   | 0                  |
| `country`         | 488                 | 0                  |
| **Total Data**    | 119.390             | 118.898            |

Penanganan nilai NULL pada variabel utama:

| 🔹 **Variabel** | **Penanganan Nilai Null**              | **Wawasan Utama**       |
|--------------|----------------------------------------|-------------------------|
| `agent`      | Null diganti dengan 1000 (Tanpa Agen)  | Sebagian besar pemesanan tanpa agen adalah pemesanan langsung. |
| `company`    | Null diganti dengan 1000 (Tanpa Perusahaan) | Sebagian besar pemesanan tanpa perusahaan adalah individu atau grup kecil. |

---

## 📊 Bab 4: Exploratory Data Analysis (EDA)

### 🔍 Distribusi Status Pemesanan

| Status Pemesanan       | Jumlah   |
|------------------------|----------|
| `Not Canceled (0)`     | 74.745   |
| `Canceled (1)`         | 44.153   |

Jumlah pemesanan yang tidak dibatalkan jauh lebih tinggi dibandingkan pembatalan.

### 🌍 Asal Negara Tamu

Mayoritas tamu berasal dari Portugal (PRT) dengan lebih dari 20.000 kunjungan tanpa pembatalan, diikuti oleh Inggris (GBR) dan Prancis (FRA). Mayoritas tamu berasal dari kategori dewasa:

| 🔹 Kategori | Jumlah Tamu |
|----------|-------------|
| Adults   | 136.965     |
| Children | 7.680       |
| Babies   | 776         |

### 🔎 Jumlah Pelanggan Berdasarkan Tipe Pelanggan

| 🔹 Tipe Pelanggan  | Jumlah Pelanggan |
|-----------------|------------------|
| Transient       | 52.714           |
| Transient-Party | 18.705           |
| Contract        | 2.814            |
| Group           | 512              |

Pelanggan tipe Transient dominan, mencerminkan fleksibilitas individu atau kelompok kecil.

### 🗌 Durasi Rata-Rata Menginap

Pelanggan tipe Contract memiliki rata-rata durasi menginap tertinggi, terutama di Resort Hotel.

### 🏨 Proporsi Pelanggan Berdasarkan Tipe Hotel

- **City Hotel** memiliki tingkat pembatalan lebih tinggi dibandingkan **Resort Hotel**.
- **Resort Hotel** lebih efektif mempertahankan reservasi.

---

## 🔧 Bab 5: Analisis Lanjutan

### 🔍 Faktor Utama Pembatalan

#### 🌐 Tabel Feature Importance

| Rank | Feature                       | Importance |
|------|-------------------------------|------------|
| 1    | ADR (Average Daily Rate)      | 29.5%      |
| 2    | Lead Time                     | 28.9%      |
| 3    | Deposit Type (Non Refund)     | 14.5%      |
| 4    | Total Special Requests        | 6.2%       |
| 5    | Previous Cancellations        | 5.1%       |

#### 🔖 Analisis Deposit Type dan Total Special Requests

- Mayoritas pelanggan memilih pemesanan tanpa deposit (**No Deposit**), yang memiliki tingkat pembatalan tinggi.
- Pelanggan dengan **0 permintaan khusus** memiliki tingkat pembatalan tertinggi.

**Strategi:**
- Menawarkan insentif untuk deposit **Non Refund**.
- Memfasilitasi permintaan khusus untuk meningkatkan keterlibatan pelanggan.

---

## 🎡 Bab 6: Kesimpulan

Pembatalan reservasi hotel berdampak signifikan pada pendapatan dan efisiensi operasional. Analisis ini menggunakan dataset tahun 2015-2017 dan Random Forest Classifier untuk mengidentifikasi faktor utama seperti ADR, lead_time, deposit_type, dan total_special_requests. Temuan menunjukkan:

- Tingginya pembatalan pada **No Deposit** dapat diatasi dengan insentif.
- Keterlibatan pelanggan melalui permintaan khusus dapat mengurangi pembatalan.
- City Hotel membutuhkan strategi tambahan untuk mempertahankan reservasi.

---

## 📜 Acknowledgment

Visualisasi dan analisis ini dibuat berdasarkan data dari [![ScienceDirect](https://img.shields.io/badge/Dataset-ScienceDirect-blue)](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010)
Semua kode tersedia di [![Open Colab](https://img.shields.io/badge/Notebook-Colab-green)](https://colab.research.google.com/drive/13tV-R2nSngDVyNmIW7pcxmyaxqE6a35J?usp=sharing).

