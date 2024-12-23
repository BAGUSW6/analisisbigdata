# Analisis Pemesanan dan Pembatalan Hotel (2015-2017)

## **Pendahuluan**
Tingginya tingkat pembatalan pemesanan hotel berdampak negatif pada pendapatan dan efisiensi operasional. Analisis ini bertujuan untuk:
- Mengidentifikasi pola pembatalan dan pemesanan.
- Menemukan faktor dominan yang memengaruhi pembatalan.
- Memberikan solusi strategis untuk meningkatkan retensi pelanggan dan efisiensi hotel.

**Solusi yang Diusulkan:**
1. Penghapusan fitur "No Deposit" untuk meningkatkan komitmen pelanggan.
2. Penambahan fitur "Special Request" untuk meningkatkan kepuasan pelanggan.

---

## **Teknik Analisis**

### **Library yang Digunakan:**
- `pandas` : Manipulasi data.
- `matplotlib` dan `seaborn`: Visualisasi data.
- `scikit-learn`: Analisis prediktif.

### **Deskripsi Data Sumber:**
- **Asal Data**: Dataset Pemesanan Hotel (2015-2017).
- **Variabel Utama**: 
  - Tipe pelanggan: `Contract`, `Transient`, `Transient-Party`, `Group`.
  - Tipe hotel: `City Hotel`, `Resort Hotel`.
  - Status pembatalan, deposit, permintaan khusus, dll.

### **Pembersihan Data:**
1. Nilai hilang pada `Company` dan `Agent` dibiarkan karena mencerminkan karakteristik pemesanan langsung.
2. Variabel waktu ditransformasikan untuk analisis tren.
3. Outlier di variabel `adr` (average daily rate) diidentifikasi tetapi tidak dihapus untuk menjaga integritas data.

---

## **Statistik Deskriptif**
### **Rangkuman Variabel Penting:**
| Variabel            | Deskripsi                              | Statistik Utama |
|---------------------|------------------------------------------|-----------------|
| `lead_time`        | Waktu antara pemesanan dan check-in     | Rata-rata: xx hari |
| `adr`              | Rata-rata tarif harian                 | Median: xx      |
| `total_of_special_requests` | Permintaan khusus oleh pelanggan | Mayoritas: 0    |

### **Temuan Utama:**
1. Mayoritas tamu berasal dari **Portugal**, diikuti oleh **Inggris** dan **Prancis**.
2. **City Hotel** mendominasi pemesanan, tetapi tingkat pembatalannya lebih tinggi dibandingkan **Resort Hotel**.
3. Tamu **Contract** memiliki durasi menginap rata-rata tertinggi (**6.18 malam**).

---

## **Visualisasi Penting**

### **1. Tingkat Pembatalan Berdasarkan Tipe Deposit**
_Tambahkan plot pembatalan deposit di sini._

### **2. Distribusi Pemesanan Berdasarkan Negara**
_Tambahkan peta dunia distribusi tamu di sini._

### **3. Rata-rata Durasi Menginap Berdasarkan Tipe Pelanggan**
_Tambahkan plot durasi menginap di sini._

### **4. Tren Pemesanan Bulanan**
_Tambahkan grafik tren pemesanan di sini._

---

## **Solusi yang Diusulkan**
1. **Penghapusan Fitur "No Deposit":**
   - Meningkatkan komitmen pelanggan terhadap pemesanan.
   - Mengurangi tingkat pembatalan.
2. **Penambahan Fitur "Special Request":**
   - Meningkatkan kepuasan pelanggan.
   - Menekan tingkat pembatalan oleh tamu dengan kebutuhan khusus.

---

## **Kesimpulan**
1. **Wawasan Utama:**
   - Tingkat pembatalan tinggi di **City Hotel** dan tamu tipe **Transient**.
   - Deposit non-refundable efektif menekan pembatalan.
   - Musim liburan (Agustus) menunjukkan puncak pemesanan.
2. **Langkah Berikutnya:**
   - Implementasi strategi deposit fleksibel dan fitur permintaan khusus.
   - Analisis tambahan dengan data baru.

---

## **Poin Tambahan**
1. **Statistik Deskriptif yang Sederhana Berdampak Besar:**
   - Menunjukkan perbedaan signifikan antar subkelompok pelanggan (misalnya, tipe `Transient` vs `Contract`).
   - Visualisasi seperti diagram batang atau pie chart mempermudah pemahaman.

2. **Subkelompok Penting dalam Data:**
   - Tipe pelanggan `Contract` dan `Transient` memiliki pola berbeda yang relevan dengan strategi hotel.
   - Data negara asal tamu membantu menentukan fokus pemasaran (misalnya, Portugal sebagai pasar utama).

3. **Tren Temporal Penting:**
   - Tingkat pemesanan tertinggi di musim liburan (Agustus) memberikan panduan untuk pengelolaan sumber daya.
   - Peningkatan pembatalan dari 2015 ke 2017 menunjukkan perlunya evaluasi strategi bisnis.

---

**Catatan Replikasi:**
- Pastikan seluruh library Python terinstal.
- Langkah pembersihan dan analisis data dapat ditemukan di notebook Jupyter terkait.

---
