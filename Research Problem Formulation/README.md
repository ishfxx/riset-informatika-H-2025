# **BAB I – PERUMUSAN MASALAH PENELITIAN**

## **1.1 Latar Belakang**

Pesatnya kemajuan teknologi telah mendorong transformasi digital di berbagai sektor, termasuk sektor keuangan. Salah satu dampaknya adalah peningkatan signifikan pada volume transaksi keuangan yang dilakukan melalui media elektronik, seperti sistem pembayaran digital dan kartu kredit untuk berbagai keperluan. Namun, di balik kemudahan ini, muncul pula tantangan besar berupa peningkatan **risiko penipuan (fraud)** seperti pencurian identitas dan transaksi tidak sah.

Metode deteksi penipuan tradisional yang berbasis aturan (rule-based system) sering kali kesulitan mengimbangi pola dan perilaku fraud yang semakin kompleks dan dinamis. Sistem tersebut tidak mampu menangani data keuangan modern yang bersifat **berskala besar, berdimensi tinggi, dan memiliki karakteristik non-linear serta deret waktu (time series)**. Oleh karena itu, pendekatan berbasis **Machine Learning (ML)** dan **Deep Learning (DL)** menjadi semakin populer karena kemampuannya dalam mempelajari pola dari data transaksi secara otomatis dan adaptif.

Teknologi **Deep Learning** telah terbukti unggul dalam analisis data kompleks karena kemampuannya mengenali pola dan melakukan pembelajaran fitur (feature learning) tanpa intervensi manual. Dalam konteks **deteksi fraud**, dua arsitektur yang banyak digunakan adalah **Convolutional Neural Network (CNN)** dan **Long Short-Term Memory (LSTM)**. CNN unggul dalam mengenali pola spasial, sementara LSTM sangat efektif dalam memproses data sekuensial. Kombinasi keduanya dalam model **hybrid CNN-LSTM** memungkinkan sistem untuk menangkap pola spasial dan temporal sekaligus, menghasilkan performa yang lebih baik dibandingkan model tunggal.

Dengan demikian, penelitian ini akan berfokus pada **implementasi model hybrid CNN-LSTM untuk mengklasifikasikan transaksi mencurigakan**. Melalui pemanfaatan kemampuan model untuk mempelajari pola kompleks pada data keuangan, diharapkan sistem yang dikembangkan mampu memberikan deteksi yang lebih akurat dan adaptif terhadap ancaman penipuan di era digital perbankan modern.

---

## **1.2 Rumusan Masalah**

Berdasarkan latar belakang di atas, maka rumusan masalah dalam penelitian ini adalah sebagai berikut:

1. Bagaimana merancang dan mengimplementasikan arsitektur model hybrid **Convolutional Neural Network (CNN)** – **Long Short-Term Memory (LSTM)** yang efektif untuk mengklasifikasikan transaksi mencurigakan dengan mempertimbangkan karakteristik data keuangan yang sangat tidak seimbang?
2. Bagaimana kinerja model hybrid **CNN-LSTM** yang diusulkan dalam mendeteksi transaksi mencurigakan jika dievaluasi menggunakan metrik performa seperti **accuracy, precision, recall**, dan **F1-score**?
3. Sejauh mana pengaruh penerapan teknik penanganan data tidak seimbang seperti **SMOTE (Synthetic Minority Over-sampling Technique)** dalam meningkatkan kemampuan model mendeteksi kelas minoritas (transaksi mencurigakan), khususnya pada metrik **recall**?

---

## **1.3 Tujuan Penelitian**

Tujuan dari penelitian ini adalah:

1. Mengimplementasikan model hybrid **CNN-LSTM** untuk melakukan klasifikasi antara transaksi normal dan transaksi mencurigakan.
2. Mengevaluasi performa model dengan metrik evaluasi standar seperti **accuracy, precision, recall**, dan **F1-score**.
3. Menganalisis pengaruh penerapan teknik **SMOTE (Synthetic Minority Over-sampling Technique)** dalam meningkatkan kemampuan model mendeteksi kelas minoritas.

---

## **1.4 Manfaat Penelitian**

Adapun manfaat yang diharapkan dari penelitian ini adalah sebagai berikut:

### 1. **Manfaat Akademik**

Sebagai referensi bagi penelitian selanjutnya dalam bidang **data mining dan keamanan siber keuangan**, khususnya pada penerapan **Deep Learning hybrid (CNN-LSTM)** untuk deteksi anomali transaksi.

### 2. **Manfaat Praktis**

Sebagai acuan bagi lembaga keuangan atau penyedia layanan transaksi digital dalam **mengembangkan sistem deteksi penipuan otomatis** yang adaptif terhadap pola fraud yang terus berkembang.

### 3. **Manfaat Teknis**

Meningkatkan efektivitas dan efisiensi proses deteksi transaksi mencurigakan melalui **penerapan teknik pembelajaran mendalam dan penanganan data tidak seimbang (SMOTE)**, guna mengurangi potensi kerugian akibat fraud.

---

## **1.5 Ruang Lingkup Penelitian**

Penelitian ini dibatasi pada pengembangan dan pengujian model hybrid CNN-LSTM dengan ruang lingkup sebagai berikut:

* Dataset yang digunakan berupa data transaksi keuangan yang telah melalui proses preprocessing.
* Penerapan teknik **SMOTE** untuk menangani ketidakseimbangan data (imbalanced dataset).
* Model CNN digunakan untuk ekstraksi fitur spasial, sedangkan LSTM digunakan untuk menangkap pola temporal dari data transaksi.
* Evaluasi performa model menggunakan metrik **accuracy, precision, recall**, dan **F1-score**.
* Pengujian dilakukan pada data uji (testing set) untuk menilai generalisasi model terhadap transaksi baru.

---

## **1.6 Metodologi Penelitian (Gambaran Umum)**

Penelitian ini menggunakan pendekatan **eksperimen kuantitatif berbasis Machine Learning**, dengan tahapan sebagai berikut:

1. **Pengumpulan dan Preprocessing Data**  
   Melakukan pengumpulan dataset transaksi keuangan, dilanjutkan dengan proses pembersihan data, normalisasi, dan penerapan teknik **SMOTE** untuk menyeimbangkan distribusi kelas.

2. **Perancangan Arsitektur Model CNN-LSTM**  
   Mendesain model hybrid yang menggabungkan CNN untuk ekstraksi fitur dan LSTM untuk analisis sekuensial, disesuaikan dengan karakteristik data transaksi.

3. **Pelatihan Model (Training Phase)**  
   Melatih model menggunakan dataset yang telah diproses dengan algoritma optimasi seperti Adam dan fungsi loss yang sesuai dengan klasifikasi biner.

4. **Evaluasi Model (Testing & Validation)**  
   Mengukur kinerja model menggunakan metrik **accuracy, precision, recall**, dan **F1-score** guna menilai efektivitas dalam mendeteksi transaksi mencurigakan.

5. **Analisis Hasil dan Interpretasi**  
   Menganalisis hasil eksperimen, membandingkan performa model sebelum dan sesudah penerapan SMOTE, serta menarik kesimpulan terhadap efektivitas pendekatan yang digunakan.

Pendekatan ini diharapkan dapat menghasilkan model deteksi fraud yang **akurat, adaptif, dan efisien**, serta memberikan kontribusi nyata dalam penguatan sistem keamanan transaksi digital.
