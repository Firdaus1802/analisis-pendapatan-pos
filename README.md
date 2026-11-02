# Tugas Mata Kuliah Data Science

Repositori ini berisi tugas mata kuliah **Data Science** oleh **Firdaus** (NIM: **10124497**). Seluruh analisis dan pemrosesan data diimplementasikan menggunakan Python dan pustaka Pandas dengan standar arsitektur direktori data modern.

## Identitas Mahasiswa

- **Nama:** Firdaus
- **NIM:** 10124497
- **Mata Kuliah:** Data Science

---

## Daftar Tugas

### 1. Analisis Pendapatan Transaksi POS (2024–2025)

File: [`pos_analysis_Firdaus_10124497.ipynb`](pos_analysis_Firdaus_10124497.ipynb)

Analisis komparasi performa pendapatan kotor dan bersih antara tahun 2024 dan 2025 pada data transaksi *Point of Sale* (POS).

| Periode | Volume Transaksi | Total Pendapatan Bersih | Rata-rata per Transaksi | Status Perubahan |
| :---: | :---: | :---: | :---: | :---: |
| **2024** | 2.364 transaksi | **Rp 385.920.077,40** | Rp 163.248,76 | Baseline |
| **2025** | 2.385 transaksi | **Rp 244.899.662,90** | Rp 102.683,30 | -36,54% |

**Temuan Utama:**

- Volume transaksi relatif stabil dengan kenaikan tipis +0,89% (bertambah 21 transaksi).
- Penurunan pendapatan sebesar Rp 141.020.414,50 (-36,54%) pada tahun 2025 disebabkan oleh penurunan nilai rata-rata belanja per transaksi (*Average Order Value*).

---

### 2. Manipulasi Data Menggunakan Pandas

File: [`pandas_manipulation_Firdaus_10124497.ipynb`](pandas_manipulation_Firdaus_10124497.ipynb)

Implementasi operasi manipulasi data tabular Pandas yang mencakup 5 topik utama:

1. **Task 1 — Indexing & Selection (Pembersihan Anomali & Imputasi):**
   - Pembersihan string koma menjadi titik desimal pada atribut `harga_satuan` serta konversi ke tipe float.
   - Penanganan kuantitas negatif (`jumlah < 0`) akibat retur/koreksi menggunakan Boolean Indexing, `.loc[]`, dan `.abs()`.
   - Imputasi nilai kosong (NaN) pada atribut `kode_kasir` dengan label default `'K_UNKNOWN'` menggunakan `.loc[]`.
   - Seleksi atribut `id_transaksi`, `tanggal`, `kode_gerai`, dan `jumlah` untuk 5 baris pertama menggunakan `.iloc[]`.
2. **Task 2 — Operasi Aritmatika (Feature Engineering):**
   - Pembuatan kolom `Total_Kotor` dari hasil perkalian vektor `harga_satuan * jumlah`.
   - Pembuatan kolom `Nominal_Diskon` berdasarkan kalkulasi persentase diskon desimal (`diskon_persen / 100`).
   - Pembuatan kolom `Total_Bersih` dari nilai omzet setelah diskon ditambah pengenaan PPN 11%:
     $$\text{Total\_Bersih} = (\text{Total\_Kotor} - \text{Nominal\_Diskon}) \times 1.11$$
3. **Task 3 — Filtering (Penyaringan Data):**
   - Filter multi-kondisi: status `SELESAI`, gerai `G05` atau `G09`, dan `Total_Bersih` > Rp 100.000 (menghasilkan 139 baris data).
   - Filter query menggunakan `.query("kode_gerai == 'G10' and jumlah >= 5")` (menghasilkan 39 baris data).
4. **Task 4 — Sorting (Pengurutan Data):**
   - Pengurutan multi-kolom berdasarkan `kode_gerai` (A–Z) dan `Total_Bersih` secara menurun (*descending*).
   - Ekstraksi 5 transaksi dengan nilai `Total_Bersih` tertinggi menggunakan `.nlargest(5, 'Total_Bersih')`.
5. **Task 5 — Grouping & Agregasi (Pelaporan Kinerja Gerai):**
   - Pembuatan tabel `laporan_gerai` dari transaksi `SELESAI` menggunakan `.groupby('kode_gerai').agg()` untuk metrik `Jumlah_Transaksi`, `Total_Unit_Terjual`, `Total_Omzet_Bersih`, dan `Rata_Rata_Transaksi`, diurutkan menurun dan dibulatkan 2 digit desimal.
   - Transformasi kelompok (*Window Function*) menggunakan `.groupby().transform()` untuk menghitung persentase kontribusi omzet tiap transaksi terhadap total omzet gerainya (`Kontribusi_Gerai_Persen`).

---

## Struktur Direktori Repositori

```text
├── data/
│   └── paket_a_transaksi_pos_2024_2025.csv       # Dataset mentah transaksi POS (2024–2025)
├── output/
│   ├── dataset_cleaned.csv                       # Output Tugas 1: Dataset bersih
│   ├── ringkasan_pendapatan_2024_2025.csv        # Output Tugas 1: Rekapitulasi tahunan
│   └── laporan_gerai.csv                         # Output Tugas 2: Ringkasan kinerja gerai
├── pos_analysis_Firdaus_10124497.ipynb           # Notebook Tugas 1 (Analisis Pendapatan POS)
├── pandas_manipulation_Firdaus_10124497.ipynb    # Notebook Tugas 2 (Manipulasi Data Pandas)
└── README.md                                     # Dokumentasi resmi repositori
```

---

## Panduan Menjalankan Proyek

1. Clone repositori ini:

   ```bash
   git clone https://github.com/Firdaus1802/analisis-pendapatan-pos.git
   cd analisis-pendapatan-pos
   ```

2. Jalankan notebook pilihan menggunakan Jupyter:

   ```bash
   jupyter notebook pos_analysis_Firdaus_10124497.ipynb
   # atau
   jupyter notebook pandas_manipulation_Firdaus_10124497.ipynb
   ```
