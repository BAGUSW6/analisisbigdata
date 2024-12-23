# Storyboard Proyek: Analisis Data Hotel 2015–2017

## Pendahuluan
### 🚀 Tujuan Proyek
Proyek ini bertujuan untuk:
1. 🔎 Mengidentifikasi pola penting dalam data pemesanan hotel dari 2015 hingga 2017.
2. 📊 Memberikan wawasan yang dapat ditindaklanjuti untuk meningkatkan kinerja operasional hotel.
3. 🔍 Menjawab pertanyaan seperti:
   - Siapa pelanggan utama hotel?
   - Apa faktor terbesar yang memengaruhi pembatalan?
   - Bagaimana tren pemesanan dari waktu ke waktu?
   - Apa tindakan strategis yang bisa dilakukan untuk meningkatkan layanan?

### Mengapa Ini Penting?
Pemesanan hotel adalah salah satu elemen penting dalam industri pariwisata. Dengan memahami pola pemesanan, pembatalan, dan preferensi pelanggan, hotel dapat meningkatkan pengalaman pelanggan dan memaksimalkan pendapatan.

### Rencana Kami
1. **Data yang Digunakan**: Dataset berasal dari artikel ilmiah di [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010).
2. **Metodologi**: Analisis data eksploratif menggunakan Python untuk mengidentifikasi pola, tren musiman, dan faktor pembatalan.
3. **Output**: Wawasan yang actionable seperti rekomendasi pemasaran dan kebijakan pengelolaan pembatalan.

![Ilustrasi Proyek](https://2.bp.blogspot.com/-NZPpkWswwSM/VtW5wbsNCmI/AAAAAAAAA7Q/t8ZQg9J7PDs/s1600/jasa%2Breservasi%2Bhotel.jpg)

---

## Package yang Diperlukan
Untuk menjalankan analisis ini, pastikan Anda telah menginstal package berikut:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `plotly`
- `geopandas`

Tambahkan dengan perintah:
```python
!pip install pandas numpy matplotlib seaborn plotly geopandas
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

### Pembersihan Data
Langkah-langkah pembersihan meliputi:
1. Menghapus nilai yang hilang di kolom penting seperti `duration_stay`.
2. Mengonversi tipe data untuk konsistensi (contoh: tanggal ke format datetime).
3. Membuat variabel baru, seperti `long_stay` (“durasi menginap > 5 malam”).

**Hasil Data yang Telah Dibersihkan**:
| Variabel             | Tipe Data   | Deskripsi                                 |
|----------------------|-------------|-------------------------------------------|
| `hotel`              | Kategorikal | Tipe hotel (City atau Resort)             |
| `is_canceled`        | Biner       | Status pembatalan (0 = Tidak, 1 = Ya)     |
| `lead_time`          | Numerik     | Waktu dari pemesanan hingga check-in      |
| `arrival_date_month` | Kategorikal | Bulan kedatangan                          |
| `stays_in_week_nights` | Numerik    | Durasi menginap selama hari kerja         |

---

## Eksplorasi dan Analisa Data
### Analisis 1: Pola Pemesanan Bulanan 🌐
- **Visualisasi**: Jumlah pemesanan per bulan menunjukkan puncak di bulan **Agustus**.
- **Tindakan**: Tingkatkan promosi selama bulan sepi (Januari, Desember).

### Analisis 2: Tingkat Pembatalan 🛑
- **Visualisasi**: Pembatalan lebih banyak terjadi pada pemesanan dengan deposit refundable.
- **Tindakan**: Revisi kebijakan deposit untuk mengurangi tingkat pembatalan.

### Analisis 3: Durasi Menginap 🏨
- **Visualisasi**: Rata-rata durasi menginap adalah 3,4 malam.
- **Tindakan**: Promosikan paket khusus untuk tamu long stay di Resort Hotel.

Kode Python untuk analisis dapat ditemukan di [Colab Notebook](https://colab.research.google.com/drive/13tV-R2nSngDVyNmIW7pcxmyaxqE6a35J?usp=sharing).

---

## Kesimpulan Utama
1. **Tren Musiman**: Agustus menjadi bulan puncak pemesanan.
2. **Faktor Pembatalan**: Kebijakan deposit memengaruhi tingkat pembatalan.
3. **Tipe Pelanggan**: Mayoritas pelanggan adalah transient.
4. **Durasi Menginap**: Sebagian besar tamu menginap untuk waktu singkat.

## Implikasi dan Keterbatasan
- **Implikasi**: Data ini dapat digunakan untuk menyusun strategi pemasaran dan kebijakan pembatalan yang lebih baik.
- **Keterbatasan**: Data hanya mencakup hotel di Eropa sehingga tidak sepenuhnya mencerminkan pola global.

---

## Acknowledgment
Visualisasi dan analisis ini dibuat berdasarkan data dari [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340918315191#f0010). Semua kode tersedia di [Colab Notebook](https://colab.research.google.com/drive/13tV-R2nSngDVyNmIW7pcxmyaxqE6a35J?usp=sharing).
