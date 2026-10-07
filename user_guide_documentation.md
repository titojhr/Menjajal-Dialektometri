# Panduan Penggunaan & Referensi Teknis: Alat Dialektometri Colab

Dokumen ini melengkapi `README.md` dengan memberikan panduan terperinci mengenai format struktur data Excel yang dibutuhkan, penjelasan metode perhitungan, serta cara membaca interpretasi hasil klasifikasi dialektometri.

---

## 📂 1. Format Standar Berkas Excel Masukan (`.xlsx`)

Agar skrip dapat membaca data dengan benar, berkas Excel yang diunggah harus memenuhi struktur kolom dan baris berikut:

* **Baris Mulai (`START_ROW`)**: Data dibaca mulai dari **baris ke-8**.
* **Baris Selesai (`END_ROW`)**: Batas akhir pembacaan pada **baris ke-1089** (sesuaikan jika daftar konsep Anda lebih sedikit atau lebih banyak).
* **Kolom Kode Konsep (`COL_KODE` / Kolom ke-2)**: Berisi kode nomor konsep (contoh: `1001` untuk Swadesh, atau kode kategori seperti `2A`, `2B`, dll.).
* **Kolom Kosakata/Berian (`COL_BERIAN` / Kolom ke-4)**: Berisi transkripsi fonetis atau data leksikon dari titik pengamatan (TP). Jika ada variasi/polimorfi dalam satu titik, pisahkan dengan tanda baca seperti titik koma (`;`), koma (`,`), atau garis miring (`/`) (misal: `mata; paning`).

---

## 🧮 2. Penjelasan Metode & Rumus

### A. Jarak Levenshtein (*Levenshtein Distance*)
Jarak Levenshtein digunakan untuk mengukur jarak minimum perubahan suntingan (*edit distance*) yang diperlukan untuk mengubah satu kata menjadi kata lain (penambahan, penghapusan, atau penggantian karakter).

Rumus rasio beda kata dalam persen:
$$\text{Rasio Beda Kata (\%)} = \left( \frac{\text{Jarak Levenshtein}}{\max(\text{panjang kata}_1, \text{panjang kata}_2)} \right) \times 100$$

### B. Klasifikasi Dialektometri Guiter (1973)
Berdasarkan persentase perbedaan leksikal ($p$), skala Guiter mengklasifikasikan hubungan antar-titik pengamatan sebagai berikut:
* $p \le 20\%$: **Tidak ada perbedaan**
* $20\% < p \le 30\%$: **Beda wicara**
* $30\% < p \le 50\%$: **Beda subdialek**
* $50\% < p \le 80\%$: **Beda dialek**
* $p > 80\%$: **Beda bahasa**

### C. Klasifikasi Dialektometri Lauder
Menggunakan ambang batas persentase perbedaan ($p$) yang sedikit berbeda:
* $p \le 30\%$: **Tidak ada perbedaan**
* $30\% < p \le 40\%$: **Beda wicara**
* $40\% < p \le 50\%$: **Beda subdialek**
* $50\% < p \le 69\%$: **Beda dialek**
* $p > 69\%$: **Beda bahasa**

---

## 🛠️ 3. Pemecahan Masalah (Troubleshooting)

1. **Error: "Gagal membaca file"**
   * *Penyebab*: Berkas Excel rusak, dilindungi kata sandi, atau nama sheet utama tidak aktif di posisi teratas.
   * *Solusi*: Simpan ulang berkas Excel ke format `.xlsx` standar menggunakan Microsoft Excel atau LibreOffice.

2. **Hasil Perbandingan Kosong / Tidak Ada Data**
   * *Penyebab*: Kode konsep pada kolom ke-2 tidak cocok atau rentang baris (`START_ROW` dan `END_ROW`) tidak mencakup data Anda.
   * *Solusi*: Periksa kembali letak baris data di file Excel Anda dan sesuaikan variabel baris di dalam kode skrip Colab jika perlu.

3. **Browser Macet Saat Menampilkan Pratinjau**
   * *Penyebab*: Terlalu banyak baris detail yang dirender di antarmuka web Colab.
   * *Solusi*: Pratinjau di layar memang dibatasi maksimal 50 baris untuk mencegah *lag*, namun data **seluruhnya** tetap tersimpan dengan lengkap di dalam berkas hasil unduhan Excel (`Hasil_Menjajal_Dialektometri.xlsx`).