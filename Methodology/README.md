# BAB III – METODOLOGI PENELITIAN

---

## **3.1 Pendekatan Penelitian**

Penelitian ini menggunakan pendekatan **kuantitatif eksperimental**. Tujuannya adalah untuk merancang, mengimplementasikan, dan mengevaluasi kinerja model *deep learning* **hybrid Convolutional Neural Network (CNN) - Long Short-Term Memory (LSTM)** dalam mengklasifikasikan transaksi keuangan sebagai normal atau mencurigakan. Pendekatan ini dipilih karena fokus penelitian adalah pada pengukuran performa model secara objektif menggunakan metrik standar dan analisis statistik terhadap hasil eksperimen pada dataset yang ditentukan.

Metode pengembangan yang diadopsi mengikuti alur kerja standar dalam proyek *machine learning* dan *data science*, yang meliputi tahapan pemahaman data, persiapan data, pemodelan, evaluasi, dan analisis hasil. Pendekatan ini bersifat iteratif, di mana hasil evaluasi dapat digunakan untuk menyempurnakan model atau langkah *preprocessing* pada iterasi berikutnya jika diperlukan.

---

## **3.2 Tahapan Penelitian**

Pengembangan model klasifikasi transaksi mencurigakan ini meliputi beberapa tahapan utama:

1.  **Studi Literatur dan Perumusan Masalah**
2.  **Pengumpulan dan Pemahaman Data**
3.  **Persiapan Data (*Data Preprocessing*)**
4.  **Perancangan dan Implementasi Model**
5.  **Pelatihan dan Pengujian Model**
6.  **Evaluasi Kinerja Model**
7.  **Analisis Hasil dan Penarikan Kesimpulan**

---

### **3.2.1 Studi Literatur dan Perumusan Masalah**

Tahap awal ini melibatkan pengkajian mendalam terhadap penelitian-penelitian sebelumnya yang relevan dengan deteksi anomali finansial, *deep learning*, arsitektur CNN dan LSTM, serta penanganan data tidak seimbang. Hasil kajian digunakan untuk mengidentifikasi *research gap* dan merumuskan masalah penelitian yang spesifik, seperti yang telah diuraikan pada Bab 1.

---

### **3.2.2 Pengumpulan dan Pemahaman Data**

Data yang digunakan dalam penelitian ini adalah dataset sekunder publik.

* **Sumber Data:** Dataset **"Financial Anomaly Data"** yang diperoleh dari platform Kaggle ([https://www.kaggle.com/datasets/devondev/financial-anomaly-data](https://www.kaggle.com/datasets/devondev/financial-anomaly-data)).
* **Deskripsi Data:** Dataset ini berisi data transaksi keuangan sintetis yang mencakup fitur-fitur seperti `Transaction_ID`, `User_ID`, `Timestamp`, `Amount`, `Merchant_Name`, `Location`, `Transaction_Type`, dan label target `Is_Anomaly` (1 untuk mencurigakan, 0 untuk normal).
* **Pemahaman Data (EDA - *Exploratory Data Analysis*):** Melakukan analisis awal untuk memahami karakteristik dataset, termasuk:
    * Distribusi fitur numerik (misalnya, `Amount`).
    * Distribusi fitur kategorikal (misalnya, `Transaction_Type`).
    * Identifikasi dan visualisasi ketidakseimbangan kelas target (`Is_Anomaly`).
    * Pemeriksaan nilai yang hilang (*missing values*) dan pencilan (*outliers*).

---

### **3.2.3 Persiapan Data (*Data Preprocessing*)**

Tahap ini krusial untuk menyiapkan data agar sesuai dan optimal untuk pelatihan model *deep learning*. Langkah-langkah yang dilakukan meliputi:

1.  **Pembersihan Data:** Menangani *missing values* (jika ada) menggunakan metode imputasi yang sesuai (misalnya, mengisi dengan modus atau nilai konstan).
2.  ***Feature Engineering*:** Membuat fitur-fitur baru yang relevan dari data yang ada. Contoh:
    * Ekstraksi komponen waktu (jam, hari, menit) dari fitur `Timestamp`.
3.  ***Encoding* Fitur Kategorikal:** Mengubah fitur non-numerik (misalnya, `Merchant_Name`, `Location`) menjadi representasi numerik menggunakan teknik seperti *One-Hot Encoding* atau *Label Encoding*.
4.  **Normalisasi/Standardisasi Fitur Numerik:** Melakukan penskalaan pada fitur numerik (seperti `Amount` dan fitur waktu yang diekstrak) menggunakan *StandardScaler* atau *MinMaxScaler* agar memiliki rentang nilai [0, 1] atau rerata 0 dan standar deviasi 1.
5.  **Pembagian Data:** Membagi dataset secara acak menjadi **Data Latih (80%)** dan **Data Uji (20%)**. Pembagian ini dilakukan sebelum menerapkan SMOTE untuk mencegah kebocoran data (*data leakage*) dari data uji ke data latih.
6.  **Penanganan Data Tidak Seimbang (SMOTE):** Menerapkan **SMOTE (*Synthetic Minority Over-sampling Technique*)** *hanya pada data latih* untuk menyeimbangkan distribusi antara kelas transaksi mencurigakan dan normal.

---

### **3.2.4 Perancangan dan Implementasi Model**

Tahap ini fokus pada perancangan arsitektur model *deep learning* dan implementasinya.

#### **a. Arsitektur Model Utama: Hybrid CNN-LSTM**

Model hybrid dirancang untuk memanfaatkan keunggulan CNN dan LSTM:
1.  **Lapisan Input:** Menerima data fitur yang telah diproses. Dimensi input disesuaikan dengan jumlah fitur hasil *preprocessing*.
2.  **Lapisan 1D-CNN (*Convolutional 1D*):** Satu atau lebih lapisan Conv1D untuk mengekstraksi pola lokal atau fitur spasial dari sekuens fitur. Menggunakan fungsi aktivasi **ReLU**.
3.  **Lapisan Pooling (*Max Pooling 1D*):** Mengurangi dimensi output dari lapisan CNN, mempertahankan fitur paling penting.
4.  **Lapisan LSTM:** Menerima output dari lapisan pooling/CNN dan memprosesnya untuk menangkap dependensi temporal atau pola sekuensial.
5.  **Lapisan Dense (Fully Connected):** Satu atau lebih lapisan Dense untuk pemrosesan lebih lanjut.
6.  **Lapisan Output:** Satu neuron Dense dengan fungsi aktivasi **Sigmoid** untuk menghasilkan probabilitas klasifikasi biner (0 atau 1).

Implementasi model dilakukan menggunakan *library* **TensorFlow** dan **Keras** dalam bahasa pemrograman **Python**.

#### **b. Model Pembanding (*Baseline*)**

Untuk mengevaluasi keunggulan model hybrid CNN-LSTM, akan diimplementasikan juga model *machine learning* konvensional yang kuat sebagai *baseline*. Model yang dipilih adalah **XGBoost** atau **Random Forest**, yang diimplementasikan menggunakan *library* **Scikit-learn**.

---

### **3.2.5 Pelatihan dan Pengujian Model**

1.  **Pelatihan Model:**
    * Model hybrid CNN-LSTM dan model *baseline* dilatih menggunakan **data latih yang sudah di-SMOTE**.
    * **Parameter Pelatihan CNN-LSTM:**
        * *Optimizer*: Adam.
        * *Loss Function*: Binary Crossentropy.
        * *Metrics*: Accuracy, Precision, Recall.
        * *Epochs*: Jumlah iterasi pelatihan yang ditentukan dengan *early stopping* untuk mencegah *overfitting*.
        * *Batch Size*: Jumlah sampel yang diproses dalam satu iterasi.
    * **Parameter Pelatihan Baseline:** Menggunakan parameter default atau hasil *tuning* sederhana.
2.  **Pengujian Model:**
    * Model yang telah dilatih digunakan untuk melakukan prediksi pada **data uji** (yang *tidak* di-SMOTE dan belum pernah dilihat model sebelumnya).
    * Hasil prediksi dibandingkan dengan label sebenarnya dari data uji.

---

### **3.2.6 Evaluasi Kinerja Model**

Kinerja kedua model (CNN-LSTM dan *baseline*) dievaluasi secara kuantitatif menggunakan metrik standar untuk masalah klasifikasi biner, terutama pada data tidak seimbang:

1.  ***Confusion Matrix:*** Menyajikan jumlah *True Positive* (TP), *True Negative* (TN), *False Positive* (FP), dan *False Negative* (FN).
2.  ***Accuracy:*** `(TP + TN) / Total` - Proporsi prediksi benar secara keseluruhan.
3.  ***Precision:*** `TP / (TP + FP)` - Dari semua yang diprediksi mencurigakan, berapa yang benar-benar mencurigakan.
4.  ***Recall (Sensitivity):*** `TP / (TP + FN)` - Dari semua transaksi mencurigakan yang sebenarnya, berapa yang berhasil terdeteksi. **Metrik ini menjadi fokus utama.**
5.  ***F1-Score:*** `2 * (Precision * Recall) / (Precision + Recall)` - Rata-rata harmonik antara Precision dan Recall.
6.  ***ROC Curve & AUC:*** Visualisasi *trade-off* antara *True Positive Rate* (Recall) dan *False Positive Rate*, serta nilai Area Under Curve (AUC) untuk mengukur kemampuan diskriminatif model.

Perhitungan metrik dilakukan menggunakan *library* **Scikit-learn**.

---

### **3.2.7 Analisis Hasil dan Penarikan Kesimpulan**

Tahap akhir metodologi ini adalah menganalisis hasil evaluasi:

* Membandingkan kinerja model hybrid CNN-LSTM dengan model *baseline* berdasarkan metrik yang dihitung.
* Menganalisis secara spesifik dampak penerapan SMOTE terhadap peningkatan metrik *Recall* dan *F1-Score*.
* Menarik kesimpulan berdasarkan temuan untuk menjawab rumusan masalah penelitian.

---


## **3.3 Sumber Daya Penelitian**

* **Perangkat Lunak:**
    * Sistem Operasi: Windows
    * Bahasa Pemrograman: Python
    * Lingkungan Pengembangan: Jupyter Notebook, VS Code (atau IDE lain).
    * *Library* Utama: TensorFlow, Keras, Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn.
    * Platform Cloud (Opsional): Google Colaboratory 
* **Dataset:** "Financial Anomaly Data" dari Kaggle.

---

## **3.4 Indikator Keberhasilan Model**

Model hybrid CNN-LSTM dinilai berhasil apabila:

1.  Menunjukkan kinerja yang **lebih unggul** dibandingkan model *baseline* (XGBoost/Random Forest), terutama pada metrik **Recall** dan **F1-Score**.
2.  Mampu mencapai nilai **Recall** yang tinggi (misalnya, > 85% atau 90%), menunjukkan kemampuan yang baik dalam mendeteksi sebagian besar transaksi mencurigakan.
3.  Menunjukkan nilai **F1-Score** yang baik, mengindikasikan keseimbangan antara Precision dan Recall.
4.  Proses pelatihan model dapat berjalan hingga konvergen tanpa *overfitting* yang signifikan.