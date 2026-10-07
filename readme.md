# Menjajal Dialektometri (Google Colab Python Script)

Alat berbasis Python untuk melakukan perhitungan **dialektometri** (analisis perbandingan leksiko-statistik dan jarak fonetis antar-titik pengamatan bahasa/dialek) yang dirancang untuk dijalankan di lingkungan **Google Colab**.

---

## 📌 Fitur Utama

1. **Pengumpulan Berkas Fleksibel**: Mengunggah beberapa berkas data leksikon dialektologi berformat Excel (`.xlsx`) secara bertahap dari berbagai folder.
2. **Pra-pemrosesan Data Otomatis**: Membaca kolom kode konsep dan data berian/kosakata dari lembar kerja Excel berdasarkan rentang baris yang ditentukan.
3. **Pengkategorian Konsep Dinamis**: 
   - Deteksi khusus untuk kosakata *Swadesh (1001-1200)*.
   - Pengelompokan otomatis berdasarkan dua karakter pertama atau kategori leksikon standar.
4. **Analisis Jarak Levenshtein (*Levenshtein Distance*)**: Menghitung jarak minimum dan rasio perbedaan fonetis antar-leksem (`$dist / max\_len \times 100$`).
5. **Klasifikasi Dialektometri**: Mengukur tingkat perbedaan menggunakan dua skala rujukan utama:
   - **Skala Guiter (1973)**
   - **Skala Lauder**
6. **Antarmuka Interaktif (`ipywidgets`)**: Pemilihan kategori konsep secara multi-pilih (*multi-select*) langsung di antarmuka notebook Colab.
7. **Ekspor Hasil Komprehensif**: Mengemas hasil akhir ke dalam satu berkas Excel tersruktur (`Hasil_Menjajal_Dialektometri.xlsx`) yang mencakup:
   - *Keterangan TP* (Mapping Titik Pengamatan)
   - *Ringkasan Klasifikasi Keseluruhan*
   - *Detail Perbandingan*

---

## 🛠️ Prasyarat & Kebutuhan Sistem

- **Python 3.x**
- Pustaka pendukung standar Google Colab & ekosistem data:
  - `pandas`
  - `openpyxl`
  - `ipywidgets`
  - `IPython`

---

## 🚀 Cara Penggunaan

1. Buka Google Colab dan buat notebook baru.
2. Salin dan tempel kode program yang tersedia ke dalam sel Colab.
3. Jalankan sel utama (`Cell`).
4. Ikuti instruksi dialog untuk mengunggah minimal **2 (dua) file Excel data dialektologi** (`.xlsx`).
5. Pilih kategori konsep yang ingin dianalisis pada widget interaktif yang muncul (gunakan `Ctrl+Click` atau `Cmd+Click` untuk memilih lebih dari satu kategori).
6. Klik tombol **"Hitung Dialektometri"**.
7. Unduh hasil rekapitulasi lengkap melalui tombol unduh berkas Excel yang disediakan.

---

## 📊 Struktur Keluaran (Output Excel)

Berkas keluaran `Hasil_Menjajal_Dialektometri.xlsx` memuat 3 lembar kerja (*sheet*):
- **Keterangan TP**: Daftar alias Titik Pengamatan (TP 1, TP 2, dst.) dipetakan dengan nama asli daerah.
- **Ringkasan Klasifikasi Keseluruhan**: Tabel perbandingan pasangan daerah, total kosakata dibandingkan, jumlah perbedaan, persentase leksikal, serta status klasifikasi Guiter dan Lauder.
- **Detail Perbandingan**: Rincian perbandingan per konsep, pasangan kata terbaik, jarak fonetis, persentase beda kata, dan status variasi (Identik, Variasi Fonetis, Beda Leksikal).
