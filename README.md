# POS Sales Revenue Analysis (2024 - 2025)

Repository ini berisi pemrosesan dan analisis data transaksi Point of Sale (POS) untuk periode tahun 2024 dan 2025. Analisis dilakukan menggunakan Python di Jupyter Notebook untuk menghitung total pendapatan kotor (gross revenue) per tahun serta menangani permasalahan *missing values*.

## 📌 Highlight Hasil Analisis

| Tahun | Jumlah Transaksi | Total Pendapatan |
| :---: | :---: | :---: |
| **2024** | 2.364 baris | **Rp 385.928.077,48** |
| **2025** | 2.385 baris | **Rp 244.899.662,50** |

---

## 🛠️ Langkah Pemrosesan Data

1. **Handling Missing Value:**
   - Kolom kategorikal seperti `kode_kasir` yang bernilai *null* diimputasi dengan nilai `'Unknown'`.
   - Kolom numerik yang bernilai *null* diisi dengan `0`.

2. **Filtering Transaksi Valid:**
   - Menyaring data transaksi yang berstatus sukses/selesai (`SELESAI`, `Completed`, `Success`, `Paid`) untuk memastikan kalkulasi pendapatan akurat.

3. **Perhitungan Pendapatan (Gross Revenue):**
   - Menghitung subtotal dari `harga_satuan * jumlah`.
   - Memotong persentase diskon (`diskon_persen`) untuk mendapatkan nilai pendapatan bersih per transaksi.

4. **Pemisahan & Ekspor Data:**
   - Memisahkan data transaksi berdasarkan tahun `2024` dan `2025`.
   - Meng-export dataset hasil pembersihan ke `dataset_cleaned.csv` dan ringkasan pendapatan ke `ringkasan_pendapatan_2024_2025.csv`.

---

📁 Struktur File

- pos_analysis_Firdaus_10124497.ipynb : Main Jupyter Notebook berisi kode pemrosesan data.
- paket_a_transaksi_pos_2024_2025.csv : Raw dataset transaksi POS.
- dataset_cleaned.xls : Dataset transaksi yang telah dibersihkan dan diproses.
- ringkasan pendapatan 2024 2025.xls : Hasil kalkulasi pendapatan per tahun.

---

## 🚀 Cara Menjalankan Project

1. Clone repository ini:
   ```bash
   git clone [https://github.com/USERNAME_KAMU/pos-sales-analysis-2024-2025.git](https://github.com/USERNAME_KAMU/pos-sales-analysis-2024-2025.git)
