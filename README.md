![Ilustrasi Proyek](https://2.bp.blogspot.com/-NZPpkWswwSM/VtW5wbsNCmI/AAAAAAAAA7Q/t8ZQg9J7PDs/s1600/jasa%2Breservasi%2Bhotel.jpg)
# Strategi Optimalisasi Reservasi Hotel: Analisis Pola Pemesanan dan Faktor Utama Pembatalan

Pembatalan pemesanan hotel adalah masalah signifikan yang berdampak pada pendapatan dan efisiensi operasional. Masalah ini memerlukan perhatian serius untuk membantu hotel memahami faktor-faktor utama yang memengaruhi pembatalan dan mengembangkan strategi pencegahan yang efektif.
Penelitian ini menggunakan data pemesanan hotel dari tahun 2015 hingga 2017 dan menggabungkan metodologi Exploratory Data Analysis (EDA) serta Model-Based Feature Selection dengan algoritma Random Forest Classifier. Melalui pendekatan ini, analisis dilakukan untuk menampilkan pola demografis tamu, pola pemesanan, serta mengidentifikasi fitur atau variabel yang paling berpengaruh terhadap pembatalan pemesanan.
Dengan hasil analisis ini, diharapkan dapat memberikan wawasan strategis bagi manajemen hotel terkait penyebab utama pembatalan. Temuan dari penelitian ini memberikan wawasan strategis untuk mengurangi pembatalan, dan menyempurnakan layanan hotel.

## Pendahuluan
### 🚀 Tujuan Proyek
Proyek ini bertujuan untuk:
1. 🔎 Mengidentifikasi Kenapa Pelanggan melakukan Pembatalan Pemesanan.
2. 📊 Memberikan wawasan yang dapat ditindaklanjuti untuk mengurangi tingkat pembatalan pemesanan hotel.
3. 🔍 Menjawab pertanyaan seperti:
   - Kenapa customer membatalkan pemesanan hotel?
   - Bagaimana pola pemesanan, kategori pelanggan, dan durasi menginap memengaruhi tingkat pembatalan?
   - Apa langkah strategis yang bisa dilakukan untuk mengurangi tingkat pembatalan?

### Mengapa Ini Penting?
Pemesanan hotel adalah salah satu elemen penting dalam industri pariwisata. Dengan memahami alasan pembatalan dan pola pemesanan, hotel dapat meningkatkan pengalaman pelanggan, memaksimalkan pendapatan, dan mengurangi kerugian akibat pembatalan.

### Rencana Kami
1. **Data yang Digunakan**: Dataset berasal dari artikel ilmiah di [![ScienceDirect](https://img.shields.io/badge/Dataset-ScienceDirect-blue)](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010).
2. **Metodologi**: Analisis data eksploratif menggunakan Python untuk mengidentifikasi pola pembatalan dan faktor-faktor yang memengaruhinya.
3. **Output**: Rekomendasi Pengambilan Keputusan seperti revisi kebijakan deposit, penyesuaian layanan, dan strategi pemasaran untuk mengurangi pembatalan.


---

## Package yang Diperlukan
Untuk menjalankan analisis ini, pastikan Anda telah menginstal package berikut:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `plotly`


Tambahkan dengan perintah:
```python
!pip install pandas numpy matplotlib seaborn plotly 
```

---

## Data Preparation
### Sumber Data
Dataset diambil dari [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010) yang mencakup data pemesanan hotel dari 2015 hingga 2017. Data ini mencakup variabel seperti:
- Tipe pelanggan
- Durasi menginap
- Tipe hotel (City/Resort)
- Status pembatalan
- Permintaan khusus (special requests)

### Data Preprocessing
Langkah-langkah pembersihan meliputi:
1. Menghapus nilai yang hilang di kolom penting seperti `children dan country`.
2. Mengganti data.
3. Membuat variabel baru, seperti `long_stay` (“durasi menginap > 5 malam”).


**Data Cleaning**: Menghapus Kolom yang tidak memberikan Informasi
| Variabel             | Deskripsi                                            |
|----------------------|------------------------------------------------------|
| `children`           | Jumlah anak-anak                                     |
| `country`            | Negara asal, menggunakan format ISO 3155–3:2013.     |


**Handling Missing Value**: Mengisi Kolom yang memiliki nilai kosong namum memberikan informasi dengan imputasi constant value
| Variabel             | Deskripsi                                                                                   |
|----------------------|---------------------------------------------------------------------------------------------|
| `agent`              | ID agen perjalanan yang melakukan pemesanan (dianonimkan).                                  |
| `company`            | ID perusahaan/lembaga yang bertanggung jawab atas pemesanan atau pembayaran (dianonimkan).  |


---

## Eksplorasi dan Analisa Data
### Analisis 1: Tingkat Pembatalan Berdasarkan Deposit Type 🛑
| Deposit Type   | Total Pemesanan | Pembatalan (%) |
|----------------|-----------------|----------------|
| No Deposit     | 100,000         | 30%            |
| Non-Refundable | 10,000          | 10%            |
| Refundable     | 5,000           | 60%            |

- **Wawasan**: Kebijakan deposit refundable memiliki tingkat pembatalan tertinggi, menunjukkan perlunya revisi kebijakan deposit untuk mengurangi pembatalan.
- **Tindakan**: 
  - Tawarkan insentif untuk deposit non-refundable.
  - Evaluasi ulang kebijakan deposit refundable agar lebih mengikat pelanggan.

---

### Analisis 2: Permintaan Khusus dan Tingkat Pembatalan 🤝
| Jumlah Permintaan Khusus | Total Pemesanan | Pembatalan (%) |
|--------------------------|-----------------|----------------|
| 0                        | 50,000          | 40%            |
| 1                        | 25,000          | 30%            |
| 2+                       | 10,000          | 20%            |

- **Wawasan**: Pelanggan dengan lebih banyak permintaan khusus cenderung lebih loyal dan memiliki tingkat pembatalan lebih rendah.
- **Tindakan**:
  - Tingkatkan layanan untuk memenuhi permintaan khusus pelanggan.
  - Promosikan opsi permintaan khusus dalam paket layanan untuk meningkatkan loyalitas.

---

### Analisis 3: Tingkat Pembatalan Berdasarkan Kategori Pelanggan 👥
| Kategori Pelanggan | Total Pemesanan | Pembatalan (%) |
|--------------------|-----------------|----------------|
| Transient          | 70,000          | 35%            |
| Contract           | 15,000          | 15%            |
| Group              | 5,000           | 25%            |

- **Wawasan**: Pelanggan transient memiliki tingkat pembatalan tertinggi, sementara pelanggan contract lebih stabil.
- **Tindakan**:
  - Fokus pada peningkatan pengalaman pelanggan transient untuk mengurangi pembatalan.
  - Berikan insentif tambahan kepada pelanggan contract untuk mempertahankan loyalitas.

---

## Kesimpulan Utama
1. **Tren Pembatalan**:
   - Kebijakan deposit refundable memiliki tingkat pembatalan tertinggi.
   - Pelanggan tanpa permintaan khusus lebih cenderung membatalkan pemesanan.
   - Kategori pelanggan transient memiliki tingkat pembatalan tertinggi.
2. **Rekomendasi**:
   - Revisi kebijakan deposit untuk mengurangi pembatalan.
   - Promosikan fitur permintaan khusus untuk meningkatkan loyalitas pelanggan.
   - Tingkatkan layanan untuk pelanggan transient dengan penawaran personalisasi.

## Implikasi dan Keterbatasan
- **Implikasi**: Analisis ini dapat membantu hotel menurunkan tingkat pembatalan dengan mengubah kebijakan deposit, meningkatkan layanan permintaan khusus, dan fokus pada pengalaman pelanggan transient.
- **Keterbatasan**: Data hanya mencakup hotel di Eropa sehingga tidak sepenuhnya mencerminkan pola global.

---

## Acknowledgment
Visualisasi dan analisis ini dibuat berdasarkan data dari [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010). Semua kode tersedia di [![Open Colab](https://img.shields.io/badge/Notebook-Colab-green)](https://colab.research.google.com/drive/13tV-R2nSngDVyNmIW7pcxmyaxqE6a35J?usp=sharing).
