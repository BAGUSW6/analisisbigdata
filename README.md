# Strategi Optimalisasi Reservasi Hotel: Analisis Pola Pemesanan dan Faktor Utama Pembatalan

![Ilustrasi Proyek](https://2.bp.blogspot.com/-NZPpkWswwSM/VtW5wbsNCmI/AAAAAAAAA7Q/t8ZQg9J7PDs/s1600/jasa%2Breservasi%2Bhotel.jpg)

## Bab 1: About

Pembatalan pemesanan hotel adalah masalah signifikan yang berdampak pada pendapatan dan efisiensi operasional. Masalah ini memerlukan perhatian serius untuk membantu hotel memahami faktor-faktor utama yang memengaruhi pembatalan dan mengembangkan strategi pencegahan yang efektif.

Penelitian ini menggunakan data pemesanan hotel dari tahun 2015 hingga 2017 dan menggabungkan metodologi Exploratory Data Analysis (EDA) serta Model-Based Feature Selection dengan algoritma Random Forest Classifier. Melalui pendekatan ini, analisis dilakukan untuk menampilkan pola demografis tamu, pola pemesanan, serta mengidentifikasi fitur atau variabel yang paling berpengaruh terhadap pembatalan pemesanan.

Dengan hasil analisis ini, diharapkan dapat memberikan wawasan strategis bagi manajemen hotel terkait penyebab utama pembatalan. Temuan dari penelitian ini memberikan wawasan strategis untuk mengurangi pembatalan dan menyempurnakan layanan hotel.

---

## Bab 2: Package yang Diperlukan

Untuk menjalankan analisis ini, pastikan Anda telah menginstal package berikut:

```
requests pandas numpy matplotlib seaborn plotly scikit-learn
```

Atau jalankan perintah berikut:

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn
```

---

## Bab 3: Dataset

Dataset ini diambil dari [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010) yang mencakup data pemesanan hotel dari tahun 2015 hingga 2017. Dataset ini berisi informasi tentang 32 variabel terkait detail pemesanan, termasuk data tamu, karakteristik hotel, dan faktor-faktor yang memengaruhi status reservasi.

### Ringkasan Data

- **Sumber**: Penelitian oleh Antonio, Almeida, dan Nunes (2019).
- **Periode**: Tahun 2015 hingga 2017.
- **Variabel**: 32 variabel terkait pemesanan hotel.
- **Pembersihan Data**:
  - Kolom `country` dengan 488 nilai NULL dihapus.
  - Kolom `children` dengan 4 nilai NULL dihapus.
  - Kolom `agent` dan `company` diganti dengan nilai default (1000) jika NULL.

| Variabel               | Nilai Null Sebelum | Nilai Null Setelah |
|------------------------|--------------------|--------------------|
| `children`             | 4                  | 0                  |
| `country`              | 488                | 0                  |
| **Total Data**         | 119.390            | 118.898            |

### Ringkasan Variabel Utama

| **Variabel** | **Penanganan Nilai Null**              | **Wawasan Utama**                                  |
|--------------|----------------------------------------|--------------------------------------------------|
| `agent`      | Null diganti dengan 1000 (Tanpa Agen)  | Sebagian besar pemesanan tanpa agen adalah langsung. |
| `company`    | Null diganti dengan 1000 (Tanpa Perusahaan) | Sebagian besar pemesanan tanpa perusahaan adalah individu. |

---

## Bab 4: Exploratory Data Analysis (EDA)

### Analisis Dasar

| Status Pemesanan       | Jumlah |
|------------------------|--------|
| Not Canceled (0)       | 74.745 |
| Canceled (1)           | 44.153 |

Tabel di atas menunjukkan distribusi status pemesanan, di mana jumlah pemesanan yang tidak dibatalkan jauh lebih tinggi dibandingkan pembatalan.

### 10 Negara Teratas Asal Tamu (2015-2017)

![Top 10 Negara](path/to/top10_country_chart.png)

| **Kategori** | **Jumlah Tamu** |
|--------------|-----------------|
| Adults       | 136.965         |
| Children     | 7.680           |
| Babies       | 776             |

Mayoritas tamu berasal dari Portugal (PRT), diikuti oleh Inggris (GBR) dan Prancis (FRA), dengan kategori dewasa mendominasi.

### Pembatalan Berdasarkan Kategori Tamu

![Kategori Tamu](path/to/guest_category_chart.png)

Kategori tamu Personal mendominasi pasar dengan tingkat pembatalan yang lebih tinggi dibandingkan tamu dari perusahaan (Company).

### Jumlah Pelanggan Berdasarkan Tipe Pelanggan

| **Tipe Pelanggan** | **Jumlah** |
|--------------------|------------|
| Transient          | 52.714     |
| Transient-Party    | 18.705     |
| Contract           | 2.814      |
| Group              | 512        |

Pelanggan tipe Transient dan Transient-Party mendominasi pemesanan fleksibel, sementara tipe Contract cenderung lebih terencana.

---

## Bab 5: Analisis Lanjutan

### Grafik Pemesanan per Bulan

![Jumlah Pemesanan Tiap Bulan](path/to/monthly_booking_chart.png)

Puncak pemesanan terjadi pada bulan Agustus, mencerminkan musim liburan sebagai periode favorit pelanggan.

### Rata-rata Durasi Menginap

![Durasi Menginap](path/to/average_stay_chart.png)

Pelanggan tipe Contract memiliki rata-rata durasi menginap tertinggi, terutama di Resort Hotel.

### Proporsi Pelanggan Berdasarkan Tipe Hotel

![Proporsi Tipe Hotel](path/to/hotel_type_chart.png)

City Hotel memiliki tingkat pembatalan lebih tinggi dibandingkan Resort Hotel.

### Feature Importance

#### Tabel Feature Importance

| Rank | Feature                   | Importance |
|------|---------------------------|------------|
| 1    | ADR (Average Daily Rate)  | 29.5%      |
| 2    | Lead Time                 | 28.9%      |
| 3    | Deposit Type (Non Refund) | 14.5%      |
| 4    | Total Special Requests    | 6.2%       |
| 5    | Previous Cancellations    | 5.1%       |

![Feature Importance](path/to/feature_importance_chart.png)

#### Analisis Feature Utama

- **Deposit Type**: Non Refund mengurangi pembatalan secara signifikan.
- **Total Special Requests**: Semakin banyak permintaan khusus, semakin rendah tingkat pembatalan.

---

## Bab 6: Kesimpulan

Pembatalan reservasi hotel merupakan masalah signifikan yang berdampak pada pendapatan dan efisiensi operasional. Penelitian ini mengidentifikasi bahwa **No Deposit** memiliki tingkat pembatalan tertinggi, sementara **Non Refund** lebih efektif dalam mengurangi pembatalan. Pelanggan dengan **0 permintaan khusus** memiliki tingkat pembatalan tertinggi, menunjukkan perlunya keterlibatan lebih besar melalui permintaan khusus. Analisis ini mendorong adopsi kebijakan fleksibel seperti **Non Refund dengan insentif** dan peningkatan layanan di City Hotel.

Namun, analisis ini terbatas pada data historis 2015-2017 dan tidak mencakup faktor eksternal seperti kondisi ekonomi. Pengembangan lebih lanjut dapat mencakup data real-time, ulasan pelanggan, dan faktor eksternal untuk wawasan yang lebih strategis.

---

## Acknowledgment

Visualisasi dan analisis ini dibuat berdasarkan data dari [![ScienceDirect](https://img.shields.io/badge/Dataset-ScienceDirect-blue)](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010)

Semua kode tersedia di [![Open Colab](https://img.shields.io/badge/Notebook-Colab-green)](https://colab.research.google.com/drive/13tV-R2nSngDVyNmIW7pcxmyaxqE6a35J?usp=sharing).

