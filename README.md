# Analytics of Educational Institution Problems

Proyek ini merupakan bagian dari submission akhir pada kelas **Belajar Penerapan Data Science** di Dicoding. Tujuan utama dari proyek ini adalah untuk mengidentifikasi, menganalisis, dan memvisualisasikan faktor-faktor utama yang menyebabkan tingginya tingkat **dropout** di institusi pendidikan.

Selain itu, proyek ini bertujuan untuk memanfaatkan data yang telah dikumpulkan guna membangun **model prediktif** yang dapat mendeteksi siswa dengan risiko dropout tinggi. Institusi juga membutuhkan **dashboard interaktif** untuk memantau performa siswa dan membantu tim manajemen dalam mengambil keputusan berbasis data. Dengan pendekatan ini, diharapkan institusi dapat meningkatkan **retensi siswa** serta memberikan pengalaman pendidikan yang lebih baik.

## 🎯 Objectives

1. **Mengidentifikasi Faktor-Faktor Penyebab Tingginya Dropout Rate**  
   Menganalisis faktor utama yang berkontribusi terhadap keputusan siswa untuk tidak melanjutkan pendidikan di Jaya Jaya Institut.

2. **Menyajikan Visualisasi Data yang Informatif**  
   Mengembangkan visualisasi data yang membantu institusi dalam memantau performa siswa serta mengidentifikasi siswa dengan potensi dropout.

3. **Memprediksi Risiko Dropout Siswa**  
   Membangun model prediktif yang dapat mengestimasi risiko dropout seorang siswa, sehingga institusi dapat memberikan intervensi dan bimbingan yang tepat waktu.

4. **Meningkatkan Aksesibilitas Prediksi melalui Deployment**  
   Memastikan model prediksi dapat diakses dengan mudah oleh pihak institusi melalui deployment ke cloud.

## 📑 Methodology

### 1️⃣ Data Collection
Dataset yang digunakan berasal dari [Dicoding Dataset](https://github.com/dicodingacademy/dicoding_dataset/blob/main/students_performance/data.csv) yang berisi informasi tentang siswa. Data ini dapat digunakan untuk mengidentifikasi pola dan hubungan dengan tingkat dropout. Data ini dikumpulkan dalam format CSV dan dimuat menggunakan library **pandas**.

### 2️⃣ Data Understanding
Analisis dilakukan terhadap dataset yang mencakup variabel **demografis, akademik, dan keuangan** untuk memahami faktor-faktor yang mempengaruhi dropout siswa.

**Temuan utama:**
- **Faktor risiko dropout**: Usia lebih tua saat pendaftaran, status debitur, keterlambatan pembayaran.
- **Faktor keberhasilan**: Nilai tinggi, jumlah mata kuliah disetujui, pembayaran tepat waktu.

### 3️⃣ Data Preparation
- Memilih **9 fitur utama** yang paling berpengaruh.
- Melakukan preprocessing data seperti encoding kategori dan normalisasi.
- Membagi dataset menjadi **80% training, 20% testing**.

### 4️⃣ Modelling
- Model yang digunakan: **Random Forest Classifier**.
- **Hyperparameter tuning** menggunakan `RandomizedSearchCV` untuk mendapatkan model terbaik.
- Model disimpan dalam format `.joblib` untuk digunakan dalam prediksi.

### 5️⃣ Model Evaluation
- **Akurasi model**: 83.95%
- **AUC-ROC**: 0.8884 (model cukup baik dalam membedakan mahasiswa dropout dan graduate).
- **Recall untuk dropout**: 68% (bisa ditingkatkan lebih lanjut).

### 6️⃣ Deployment
- Model dapat digunakan untuk memprediksi status mahasiswa baru.
- Langkah-langkah:
  1. Memuat model yang telah disimpan.
  2. Melakukan transformasi data input agar sesuai dengan model.
  3. Menghasilkan prediksi apakah mahasiswa kemungkinan **graduate atau dropout**, beserta probabilitasnya.

## 📊 Submission Review
<img width="917" alt="image" src="https://github.com/user-attachments/assets/4e4fe590-2c64-4748-b70d-d200e8728878" />

## 📌 Conclusion
Pada project ini dilakukan identifikasi faktor utama yang memengaruhi tingkat dropout mahasiswa, mengembangkan model prediksi risiko dropout, dan menyajikan dashboard interaktif untuk mendukung pengambilan keputusan oleh institusi pendidikan. Dengan pendekatan berbasis data, institusi dapat menerapkan strategi intervensi yang lebih efektif guna meningkatkan retensi siswa.

**Author:** Mellisa  
**Date:** 09-12-2024  
**Tools:** Python, Pandas, Scikit-Learn, Seaborn, Matplotlib, Streamlit, Metabase