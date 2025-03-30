# Menyelesaikan Permasalahan Institusi Pendidikan

## Business Understanding

Jaya Jaya Institut merupakan institusi pendidikan perguruan tinggi yang telah berdiri sejak tahun 2000 dan memiliki reputasi yang baik dalam mencetak lulusan berkualitas. Namun, institusi ini menghadapi tantangan serius dengan meningkatnya jumlah siswa yang tidak menyelesaikan pendidikannya atau **dropout**.

Tingginya tingkat dropout menjadi perhatian utama karena dapat memengaruhi reputasi institusi, kepercayaan masyarakat, serta efektivitas operasional. Dengan angka dropout yang signifikan, Jaya Jaya Institut ingin mengidentifikasi faktor-faktor utama penyebab dropout dan mencari solusi untuk mencegahnya.

Sebagai langkah awal, pihak institusi ingin memanfaatkan data yang telah dikumpulkan untuk membuat model prediktif yang mampu mendeteksi siswa dengan risiko dropout tinggi. Selain itu, mereka membutuhkan **dashboard interaktif** untuk memantau performa siswa dan membantu tim manajemen dalam mengambil keputusan berbasis data. Melalui langkah ini, diharapkan institusi dapat meningkatkan retensi siswa dan memberikan pengalaman pendidikan yang lebih baik.

### Permasalahan Bisnis

1. **Mengidentifikasi Faktor-Faktor Penyebab Tingginya Dropout Rate**  
   Apa saja faktor utama yang berkontribusi terhadap siswa memutuskan untuk tidak melanjutkan pendidikan di Jaya Jaya Institut?

2. **Membuat Visualisasi Data yang Informatif**  
   Bagaimana menyajikan data dengan visualisasi yang mudah dipahami untuk membantu pihak institusi memantau performa siswa dan mengidentifikasi siswa yang berpotensi dropout?

3. **Memprediksi Risiko Dropout Siswa**  
   Bagaimana memprediksi risiko seorang siswa akan dropout sehingga pihak institusi dapat memberikan bimbingan atau intervensi yang tepat waktu?

4. **Mempermudah Akses Prediksi dengan Deployment**  
   Bagaimana memastikan bahwa model prediksi yang dikembangkan mudah digunakan oleh pihak institusi dengan cara di-deploy ke cloud?

### Cakupan Proyek

1. **Analisis Data Siswa**  
   - Melakukan eksplorasi data (EDA) untuk menemukan pola dan wawasan yang relevan terkait performa siswa dan dropout.  
   - Mengidentifikasi fitur-fitur utama yang berpengaruh terhadap risiko dropout, seperti nilai akademik, finasial, etc.

2. **Pembuatan Dashboard Interaktif**  
   - Mengembangkan dashboard yang memvisualisasikan faktor-faktor utama yang memengaruhi performa siswa dan dropout.  
   - Dashboard ini akan digunakan oleh pihak institusi untuk memantau kinerja siswa secara real-time.

3. **Pengembangan Model Prediksi**  
   - Membangun model machine learning untuk memprediksi risiko dropout siswa.  
   - Model ini akan memberikan prioritas pada siswa yang memiliki risiko tinggi sehingga dapat diberikan intervensi yang tepat waktu.  
   - Model prediksi ini akan di-deploy di **Streamlit Cloud** untuk mempermudah akses dan penggunaan oleh pihak institusi.

4. **Rekomendasi Strategi**  
   - Memberikan rekomendasi berbasis data kepada Jaya Jaya Institut untuk mengurangi angka dropout di masa depan.  
   - Rekomendasi ini meliputi tindakan preventif seperti bimbingan khusus, program remedial, atau pelibatan orang tua siswa.  

### Persiapan

Dataset yang disediakan oleh institusi ini berisi informasi tentang siswa. Dataset ini dapat digunakan untuk mengidentifikasi pola dan hubungan dengan tingkat dropout.

Tautan Dataset: https://github.com/dicodingacademy/dicoding_dataset/blob/main/students_performance/data.csv

### Setup environment

1. Prasyarat
   - **Anaconda** atau **Miniconda**: [Anaconda](https://www.anaconda.com/).
   - **Docker** (untuk Metabase): [Docker](https://www.docker.com/).

2. Clone Repository

    Clone repository proyek ini menggunakan `git`:
    ```bash
    git clone https://github.com/mellisadmyn/dropout-predictions.git
    cd dropout-predictions
    ```

3. Setup Conda Environment
   
   ```bash
   conda create -n dp_project python=3.9 -y
   conda activate dp_project
   ```

4. Instal semua dependency dari file `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

5. Setup Metabase
   - Pastikan **Docker** sudah diinstal dan berjalan.
   - Jalankan perintah berikut untuk menjalankan Metabase dengan Docker:
      ```bash
      docker run -d -p 3000:3000 --name metabase metabase/metabase
      ```
    - Buka browser dan akses:
      ```
      http://localhost:3000
      ```
    - Ikuti langkah-langkah onboarding Metabase, seperti:
      - Membuat akun admin.
      - Menyambungkan database (contoh: PostgreSQL dari Supabase).

6. Setup Database (Supabase)
    - Buat akun dan login di [Supabase Dashboard](https://supabase.com/dashboard/sign-in).
    - Buat **new project** di Supabase.
    - Buka **database settings** di dashboard Supabase, lalu copy URI database.
    - Kirim dataset ke database menggunakan **SQLAlchemy** dengan kode berikut:
        ```python
        from sqlalchemy import create_engine

        # Ganti "DATABASE_URL" dengan URI database Anda
        URL = "DATABASE_URL"
        
        engine = create_engine(URL)
        
        # Kirim dataset (contoh: DataFrame bernama 'df')
        df.to_sql('orders', engine, if_exists='replace', index=False)
        ```
   - Dataset telah tersedia di database Supabase dan dapat digunakan untuk analisis atau dashboard.

7. Jalankan Proyek

   Setelah semua setup selesai, Anda dapat menjalankan skrip utama atau melakukan prediksi:

   - Untuk menjalankan analisis utama terdapat pada `notebook.ipynb`
   - Untuk mencoba prediksi menggunakan model machine learning, jalankan perintah berikut di terminal atau command prompt `streamlit run app.py`


## **Business Dashboard**

Business dashboard yang telah dibuat dirancang untuk membantu Jaya Jaya Institut memonitor berbagai faktor yang memengaruhi tingkat dropout siswa. Dashboard ini memberikan wawasan mendalam tentang pola data, hubungan antar variabel, dan faktor risiko utama yang menyebabkan siswa tidak menyelesaikan pendidikan mereka.

Dashboard ini mencakup:

1. **Overview Section**:
   - **Total Students**: Menampilkan jumlah total siswa yang tercatat di Jaya Jaya Institut, yaitu **4,424 siswa**.
   - **Total Dropout**: Menggambarkan jumlah siswa yang dropout, yaitu **1,421 siswa**.
   - **Percentage of Dropout**: Menyediakan persentase siswa yang dropout terhadap total siswa, yaitu **32.12%**. Angka ini memberikan gambaran seberapa besar tantangan dropout di institusi ini.

2. **Correlates of Dropout**:
   - **Grade Distribution and Dropout**:
     - Pada semester kedua, mayoritas siswa dengan **rentang nilai 0-5** memiliki tingkat dropout tertinggi (**727 siswa**), dibandingkan dengan siswa di rentang nilai yang lebih tinggi.
     - Tren serupa terlihat pada semester pertama, dengan **570 siswa** dropout dari kelompok dengan rentang nilai terendah (0-5).
   - **Approved Curricular Units and Dropout**:
     - Sebagian besar siswa yang dropout memiliki jumlah **curricular units yang disetujui di rentang 0-5** baik pada semester pertama (**1,217 siswa**) maupun semester kedua (**1,287 siswa**), menunjukkan hubungan yang signifikan antara rendahnya pencapaian akademik dengan dropout.

3. **Factors Related to Dropout**:
   - **Tuition Fees Payment Status**:
     - Sebanyak **964 siswa yang dropout** tidak membayar biaya pendidikan tepat waktu, menunjukkan bahwa masalah keuangan memainkan peran besar dalam dropout.
   - **Scholarship Holders**:
     - Hanya **134 siswa yang dropout** adalah penerima beasiswa, dibandingkan dengan **1,287 siswa tanpa beasiswa**, menyoroti pentingnya dukungan finansial dalam menurunkan risiko dropout.
   - **Debtor Status**:
     - Sebanyak **1,109 siswa yang dropout** memiliki status sebagai debitur, menunjukkan hubungan yang signifikan antara status hutang dan risiko dropout.

4. **Demographics and Dropout**:
   - **Gender Distribution**:
     - Sebanyak **720 siswa perempuan** dan **701 siswa laki-laki** mengalami dropout. Meskipun angka ini hampir seimbang, penting untuk mempertimbangkan pengaruh gender dalam strategi mitigasi dropout.
   - **Age at Enrollment**:
     - Kelompok usia **17-20 tahun** memiliki jumlah dropout tertinggi (**409 siswa**), diikuti oleh kelompok usia **20-30 tahun** (**331 siswa**), menunjukkan bahwa usia saat pendaftaran dapat menjadi faktor risiko.

Dashboard ini memberikan wawasan strategis yang dapat membantu Jaya Jaya Institut untuk:
- Mengidentifikasi siswa berisiko tinggi berdasarkan performa akademik dan status finansial.
- Merancang program intervensi seperti beasiswa tambahan atau bimbingan belajar.
- Memantau kinerja siswa secara berkala dan memperkuat strategi pencegahan dropout untuk menciptakan lingkungan pendidikan yang lebih inklusif dan mendukung.

Link: http://localhost:3000/public/dashboard/8bda01a3-27bd-4618-9c44-189f8452b918

## Menjalankan Sistem Machine Learning
Untuk menjalankan prototipe sistem machine learning yang telah dibuat, terdapat dua metode yang dapat digunakan: secara lokal dan melalui Streamlit Cloud.

1. **Menjalankan Secara Lokal**  
   - Pastikan semua dependensi yang diperlukan sudah terinstal
   - Jalankan perintah berikut di terminal atau command prompt:  
     ```bash
     streamlit run app.py
     ```
   - File Python yang berisi aplikasi diberi nama **`app.py`**.

2. **Menjalankan di Streamlit Cloud**  
   - Prototipe sistem machine learning dapat diakses melalui tautan berikut:  
     **[dropout-predictions.streamlit.app](https://dropout-predictions.streamlit.app/)**


## Conclusion

Proyek ini berhasil memberikan pemahaman mendalam terkait faktor-faktor yang memengaruhi dropout siswa di Jaya Jaya Institut. Berdasarkan analisis data, ditemukan bahwa faktor akademik (nilai rendah dan pencapaian curricular units), masalah keuangan (tunggakan biaya pendidikan dan status hutang), serta dukungan finansial (beasiswa) memiliki dampak signifikan terhadap risiko siswa mengalami dropout. Dashboard yang dibuat mempermudah institusi untuk memonitor data secara real-time dan mengambil keputusan berbasis data untuk mencegah dropout di masa depan.

Dengan implementasi model prediksi dan dashboard, Jaya Jaya Institut kini memiliki alat yang andal untuk mengidentifikasi siswa berisiko tinggi secara dini sehingga intervensi dapat dilakukan lebih efektif.

## Rekomendasi Action Items (Optional)

1. **Meningkatkan Dukungan Akademik**
   - Menyediakan program bimbingan belajar atau mentoring untuk siswa dengan nilai rendah (rentang 0-5) di kedua semester.
   - Mengadakan sesi konsultasi dengan dosen atau pembimbing akademik untuk membantu siswa memahami materi yang sulit.

2. **Meningkatkan Dukungan Finansial**
   - Memperluas program beasiswa untuk siswa yang berisiko finansial tinggi, terutama yang memiliki status sebagai debitur atau terlambat membayar biaya pendidikan.
   - Menyediakan opsi pembayaran biaya pendidikan yang lebih fleksibel atau cicilan untuk meringankan beban siswa.

3. **Memperkuat Sistem Pemantauan**
   - Menggunakan dashboard secara aktif untuk memonitor performa siswa setiap semester, termasuk nilai, pencapaian curricular units, dan status pembayaran.
   - Membuat sistem peringatan dini berbasis data untuk mengidentifikasi siswa berisiko tinggi sehingga tim manajemen dapat memberikan perhatian khusus.

4. **Melibatkan Orang Tua/Wali**
   - Melibatkan orang tua/wali siswa dalam diskusi terkait perkembangan akademik dan status finansial siswa. Komunikasi yang baik dengan pihak keluarga dapat membantu mencegah dropout.

Dengan mengambil langkah-langkah ini, Jaya Jaya Institut diharapkan dapat mengurangi tingkat dropout secara signifikan dan menciptakan lingkungan pendidikan yang mendukung kesuksesan siswa.


