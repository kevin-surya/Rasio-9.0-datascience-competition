# Rasio-9.0-datascience-competition
kevin-surya: buatkan readme dari file ini tentang penjelasan apa yang dilakukan pada syntax ini secara runtut dalam bahasa indonesia

GitHub Copilot: Read [](file:///d%3A/Perlombaan%20Duniawi/rasio/notebook1.ipynb)

Berikut adalah README yang menjelaskan secara runtut apa yang dilakukan pada notebook ini dalam bahasa Indonesia:

---

# README - Penjelasan Alur Notebook Prediksi Emisi CO₂

Notebook ini berisi tahapan lengkap untuk melakukan prediksi emisi CO₂ harian menggunakan data time series, dengan pendekatan hybrid Prophet dan CatBoost. Berikut penjelasan setiap langkahnya:

## 1. Persiapan Data
- Import library utama: numpy, pandas, matplotlib.
- Membaca data pelatihan (`train`) dan data pengujian (`tes`) dari file CSV.

## 2. Eksplorasi Data
- Menampilkan data untuk melihat struktur dan isi.
- Melakukan visualisasi time series untuk variabel numerik dan target (`daily_ktCO2`) berdasarkan tanggal.

## 3. Identifikasi dan Penanganan Missing Values
- Menghitung jumlah nilai yang hilang pada setiap kolom.
- Menghitung persentase missing values dan menampilkan kolom dengan missing values tertinggi.
- Menghapus kolom yang memiliki proporsi missing values tinggi dari kedua dataset.

## 4. Imputasi Data Numerik
- Menambahkan kolom bantu `month` dan `day` dari tanggal.
- Melakukan imputasi nilai hilang pada data numerik berdasarkan rata-rata per bulan dan hari.
- Imputasi pada data tes menggunakan lookup dari data train.
- Menghapus kolom bantu setelah proses selesai.

## 5. Imputasi Data Kategorik
- Menambahkan kolom `month` dari tanggal.
- Melakukan imputasi nilai hilang pada data kategorik menggunakan modus (nilai terbanyak) per bulan.
- Imputasi pada data tes menggunakan lookup modus dari data train.
- Menghapus kolom bantu setelah proses selesai.

## 6. Pembersihan Data dan One-Hot Encoding
- Membersihkan data kategorik dengan mengubah ke huruf kecil dan mengatasi string "nan".
- Melakukan One-Hot Encoding pada kolom kategorik utama (`rain`, `conditions`, `seasons`, `holiday`) agar siap digunakan untuk model.

## 7. Visualisasi Time Series Setelah Pembersihan
- Memvisualisasikan emisi CO₂ harian setelah tanggal 18 Juli 2022.

## 8. Hybrid Time Series Forecasting (Prophet + CatBoost)
- Menyiapkan data untuk model Prophet dan CatBoost.
- Membuat fitur hari libur khusus (Desember dan awal Januari).
- Melakukan split data menjadi train dan validasi.
- Melatih model Prophet untuk baseline prediksi.
- Menghitung residual (selisih prediksi Prophet dengan aktual).
- Melatih CatBoost untuk memprediksi residual.
- Menggabungkan hasil Prophet dan CatBoost untuk prediksi hybrid.
- Menghitung dan membandingkan RMSE dari kedua pendekatan.
- Visualisasi hasil prediksi hybrid.

## 9. Prediksi pada Data Test
- Menyiapkan data test dan melakukan prediksi hybrid pada data test.
- Visualisasi hasil prediksi pada data test.

## 10. Analisis Feature Importance
- Menampilkan komponen musiman dari Prophet.
- Menampilkan dan memvisualisasikan feature importance dari model CatBoost.

## 11. Membuat File Submission
- Membuat DataFrame hasil prediksi hybrid untuk submission.
- Mengubah format tanggal sesuai kebutuhan.
- Mengganti nama kolom agar sesuai format submission.
- Menyimpan hasil prediksi ke file CSV.

---

Notebook ini dapat digunakan sebagai referensi untuk pipeline data science time series forecasting, khususnya prediksi emisi CO₂ dengan pendekatan hybrid dan penanganan data yang komprehensif.
