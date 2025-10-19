# Implementasi Model Hybrid CNN-LSTM untuk Klasifikasi Transaksi Mencurigakan

---

## 🎯 Latar Belakang Masalah & Celah Penelitian (Problem & Research Gap)

Pengembangan model klasifikasi yang akurat untuk transaksi keuangan mencurigakan merupakan tantangan krusial dalam memerangi kejahatan finansial di era digital. Untuk memetakan kontribusi penelitian ini, dilakukan analisis mendalam terhadap berbagai literatur ilmiah terkini, baik dari jurnal internasional bereputasi (Scopus) maupun konferensi terkemuka (IEEE).

### Tinjauan Penelitian Terdahulu (State-of-the-Art Review)

Tabel berikut merangkum penelitian-penelitian utama yang menjadi landasan dan pembanding dalam riset ini.

| No | Peneliti & Tahun | Judul Penelitian | Metode / Teknologi | Hasil Utama | Keterbatasan / Gap | Link Sumber |
|:---|:---|:---|:---|:---|:---|:---|
| 1 | G. Anish Mary & S. Sudha (2025) | A Comprehensive Deep Learning Model for Banking Transaction Fraud Detection | Hybrid CNN-LSTM, SMOTE | Model hybrid **unggul signifikan** (Akurasi 98.1%) dibandingkan model tunggal (CNN atau LSTM saja). | Terbatas pada satu jenis dataset perbankan; belum diuji pada variasi anomali lain. | [IEEE Xplore](https://doi.org/10.1109/ICCRTEE64519.2025.11053118) |
| 2 | Yuan Li, dkk. (2025) | Research on Anomaly Detection Algorithm System for Financial Transaction Data Processing Based on Deep Learning | Hybrid MLP-LSTM | Model *deep learning* **jauh melampaui** metode ML tradisional (SVM, Random Forest) dengan *recall* 95.2%. | Fokus pada deteksi anomali secara umum, belum spesifik pada arsitektur CNN-LSTM. | [IEEE Xplore](https://doi.org/10.1109/ICIPCA65645.2025.11138739) |
| 3 | Yaddarabullah, dkk. (2025) | Fraud and Anomaly Detection Model in Digital Transactions Based One-Class Support Vector Machine | One-Class SVM (OC-SVM) | Mencapai **Recall sempurna (1.00)**, membuktikan efektivitas deteksi anomali dalam menangkap semua kasus fraud. | Akurasi keseluruhan lebih rendah (72%); belum ada perbandingan langsung dengan model *supervised deep learning*. | [IEEE Xplore](https://doi.org/10.1109/ICoCSET163724.2025.11019985) |
| 4 | H. Al-Dweik, et al. (2024) | A novel hybrid model based on an attention-based CNN-LSTM for credit card fraud detection | CNN-LSTM + **Attention Mechanism** | Penambahan *attention* meningkatkan kemampuan model untuk fokus pada fitur yang paling relevan. | Kompleksitas arsitektur lebih tinggi; belum banyak diimplementasikan pada dataset non-kartu kredit. | [Expert Systems with Applications (Elsevier)](https://doi.org/10.1016/j.eswa.2024.123519) |
| 5 | R. K. Rout, et al. (2023) | An efficient hybrid deep learning model for credit card fraud detection | Hybrid GRU-LSTM, **Feature Selection** (Boruta) | Menunjukkan bahwa seleksi fitur sebelum pelatihan *deep learning* dapat meningkatkan efisiensi dan akurasi. | Fokus pada model GRU-LSTM, belum pada sinergi CNN-LSTM. | [The Journal of Supercomputing (Springer)](https://doi.org/10.1007/s11227-023-05243-7) |
| 6 | Muhammad Rasikh, dkk. (2023) | Penerapan Algoritma Machine Learning Untuk Memprediksi Term Deposit Nasabah | Random Forest, XGBoost | Membuktikan efektivitas model **Random Forest & XGBoost** (Akurasi 91.7%) sebagai *baseline* yang kuat. | Konteksnya bukan deteksi fraud, namun metodologinya relevan sebagai pembanding. | Local Research Archive |

### Analisis Kesenjangan (Gap Analysis)
Berdasarkan tinjauan di atas, ditemukan beberapa kesenjangan signifikan yang mendorong penelitian ini:

* **Validasi Generalisasi Model CNN-LSTM**: Perlu pengujian model hybrid CNN-LSTM pada dataset baru ("Financial Anomaly Data") dengan variasi anomali lebih luas (geografis, merchant) untuk menguji kemampuan generalisasinya, karena sebagian besar studi sebelumnya menggunakan dataset spesifik.
* **Optimasi Arsitektur Spesifik**: Masih ada ruang untuk eksplorasi dan optimasi arsitektur hybrid CNN-LSTM (jumlah lapisan, filter, unit) secara konvensional (non-kuantum) khusus untuk dataset ini.

---

## 💡 Solusi & Posisi Penelitian (Our Solution & Positioning)

Penelitian ini secara strategis mengisi celah tersebut dengan menawarkan solusi yang:

* ✅ **Menguji Generalisasi Model**: Mengimplementasikan dan memvalidasi model hybrid CNN-LSTM pada dataset publik **"Financial Anomaly Data"** dari Kaggle, yang memiliki karakteristik anomali yang lebih bervariasi.
* ✅ **Berbasis Klasifikasi Akurat**: Menggunakan pendekatan klasifikasi *supervised* untuk membangun model yang tidak hanya sensitif tetapi juga akurat, dengan **Random Forest/XGBoost sebagai *baseline*** untuk membuktikan keunggulannya.
* ✅ **Fokus pada Metrik Kritis**: Secara khusus menekankan evaluasi pada metrik **Recall** dan **F1-Score**, sejalan dengan temuan yang menyoroti pentingnya meminimalkan transaksi mencurigakan yang terlewat.
* ✅ **Implementasi Praktis & Terdokumentasi**: Menyediakan implementasi konkret dari arsitektur *deep learning* canggih pada studi kasus data keuangan publik, yang dapat direplikasi dan dikembangkan lebih lanjut.

---

## 🛠️ Teknologi yang Digunakan (Tech Stack)

* **Bahasa Pemrograman**: Python
* **Framework Deep Learning**: TensorFlow / Keras
* **Library Machine Learning & Data**: Scikit-learn, Pandas, NumPy
* **Visualisasi**: Matplotlib, Seaborn