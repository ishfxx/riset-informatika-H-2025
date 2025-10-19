# Implementasi Model Hybrid CNN-LSTM untuk Klasifikasi Transaksi Mencurigakan

---

## 🎯 Latar Belakang Masalah & Celah Penelitian (Problem & Research Gap)

Pengembangan model klasifikasi yang akurat untuk transaksi keuangan mencurigakan merupakan tantangan krusial dalam memerangi kejahatan finansial di era digital. Untuk memetakan kontribusi penelitian ini, dilakukan analisis mendalam terhadap berbagai literatur ilmiah terkini, baik dari jurnal internasional bereputasi (Scopus) maupun konferensi terkemuka (IEEE).

### Tinjauan Penelitian Terdahulu (State-of-the-Art Review)

Tabel berikut merangkum penelitian-penelitian utama yang menjadi landasan dan pembanding dalam riset ini.

| No | Peneliti & Tahun | Judul Penelitian | Metode / Teknologi | Hasil Utama | Keterbatasan / Gap | Link Sumber |
|:---|:---|:---|:---|:---|:---|:---|
| 1 | G. Anish Mary & S. Sudha (2025) | A Comprehensive Deep Learning Model for Banking Transaction Fraud Detection | Hybrid CNN-LSTM, SMOTE | [cite_start]Model hybrid **unggul signifikan** (Akurasi 98.1%) dibandingkan model tunggal (CNN atau LSTM saja)[cite: 1191]. | Terbatas pada satu jenis dataset perbankan; belum diuji pada variasi anomali lain. | [IEEE Xplore](https://doi.org/10.1109/ICCRTEE64519.2025.11053118) |
| 2 | Yuan Li, dkk. (2025) | Research on Anomaly Detection Algorithm System for Financial Transaction Data Processing Based on Deep Learning | Hybrid MLP-LSTM | [cite_start]Model *deep learning* **jauh melampaui** metode ML tradisional (SVM, Random Forest) dengan *recall* 95.2%[cite: 1050]. | Fokus pada deteksi anomali secara umum, belum spesifik pada arsitektur CNN-LSTM. | [IEEE Xplore](https://doi.org/10.1109/ICIPCA65645.2025.11138739) |
| 3 | Yaddarabullah, dkk. (2025) | Fraud and Anomaly Detection Model in Digital Transactions Based One-Class Support Vector Machine | One-Class SVM (OC-SVM) | [cite_start]Mencapai **Recall sempurna (1.00)**, membuktikan efektivitas deteksi anomali dalam menangkap semua kasus fraud[cite: 23]. | [cite_start]Akurasi keseluruhan lebih rendah (72%)[cite: 21]; belum ada perbandingan langsung dengan model *supervised deep learning*. | [IEEE Xplore](https://doi.org/10.1109/ICoCSET163724.2025.11019985) |
| 4 | H. Al-Dweik, et al. (2024) | A novel hybrid model based on an attention-based CNN-LSTM for credit card fraud detection | CNN-LSTM + **Attention Mechanism** | Penambahan *attention* meningkatkan kemampuan model untuk fokus pada fitur yang paling relevan. | Kompleksitas arsitektur lebih tinggi; belum banyak diimplementasikan pada dataset non-kartu kredit. | [Expert Systems with Applications (Elsevier)](https://doi.org/10.1016/j.eswa.2024.123519) |
| 5 | R. K. Rout, et al. (2023) | An efficient hybrid deep learning model for credit card fraud detection | Hybrid GRU-LSTM, **Feature Selection** (Boruta) | Menunjukkan bahwa seleksi fitur sebelum pelatihan *deep learning* dapat meningkatkan efisiensi dan akurasi. | Fokus pada model GRU-LSTM, belum pada sinergi CNN-LSTM. | [The Journal of Supercomputing (Springer)](https://doi.org/10.1007/s11227-023-05243-7) |
| 6 | Muhammad Rasikh, dkk. (2023) | Penerapan Algoritma Machine Learning Untuk Memprediksi Term Deposit Nasabah | Random Forest, XGBoost | [cite_start]Membuktikan efektivitas model **Random Forest & XGBoost** (Akurasi 91.7%) [cite: 552] sebagai *baseline* yang kuat. | Konteksnya bukan deteksi fraud, namun metodologinya relevan sebagai pembanding. | Local Research Archive |

### Analisis Kesenjangan (Gap Analysis)
Berdasarkan tinjauan di atas, ditemukan beberapa kesenjangan signifikan yang mendorong penelitian ini:

* **Kesenjangan Dataset & Generalisasi**: Sebagian besar penelitian (seperti [4], [5]) berfokus pada dataset fraud kartu kredit yang sudah umum. Terdapat kekurangan validasi model canggih seperti CNN-LSTM pada dataset publik yang lebih baru dengan **variasi anomali yang lebih beragam** (misalnya, anomali geografis, kategori merchant), untuk menguji kemampuan generalisasi model.
* **Kurangnya Perbandingan Metodologi**: Terdapat dua pendekatan utama: klasifikasi *supervised* yang akurat (seperti [1], [2]) dan deteksi anomali yang sangat sensitif (seperti [3]). Namun, sangat sedikit penelitian yang **membandingkan secara langsung** kelebihan dan kekurangan kedua pendekatan ini pada dataset yang sama untuk melihat mana yang lebih optimal.
* [cite_start]**Potensi Peningkatan Arsitektur**: Meskipun model CNN-LSTM terbukti efektif[cite: 1191], penelitian yang lebih baru [4] menunjukkan bahwa ada potensi peningkatan dengan menambahkan **mekanisme atensi (*attention mechanism*)**. Ini merupakan celah untuk eksplorasi di masa depan.
* [cite_start]**Eksplorasi *Feature Engineering***: Banyak penelitian [cite: 1189, 926] yang lebih fokus pada arsitektur model. Terdapat celah dalam **eksplorasi *feature engineering* yang mendalam** untuk menciptakan fitur-fitur baru yang lebih informatif dari data mentah sebelum dimasukkan ke dalam model *deep learning*.

---

## 💡 Solusi & Posisi Penelitian (Our Solution & Positioning)

Penelitian ini secara strategis mengisi celah tersebut dengan menawarkan solusi yang:

* ✅ **Menguji Generalisasi Model**: Mengimplementasikan dan memvalidasi model hybrid CNN-LSTM pada dataset publik **"Financial Anomaly Data"** dari Kaggle, yang memiliki karakteristik anomali yang lebih bervariasi.
* ✅ **Berbasis Klasifikasi Akurat**: Menggunakan pendekatan klasifikasi *supervised* untuk membangun model yang tidak hanya sensitif tetapi juga akurat, dengan **Random Forest/XGBoost sebagai *baseline*** untuk membuktikan keunggulannya.
* [cite_start]✅ **Fokus pada Metrik Kritis**: Secara khusus menekankan evaluasi pada metrik **Recall** dan **F1-Score**, sejalan dengan temuan [cite: 23] yang menyoroti pentingnya meminimalkan transaksi mencurigakan yang terlewat.
* ✅ **Implementasi Praktis & Terdokumentasi**: Menyediakan implementasi konkret dari arsitektur *deep learning* canggih pada studi kasus data keuangan publik, yang dapat direplikasi dan dikembangkan lebih lanjut.

---

## 🏆 Kontribusi Utama Penelitian (Key Contributions)

1.  **Validasi Empiris Model Hybrid**: Memberikan bukti kinerja model hybrid CNN-LSTM pada dataset keuangan modern yang belum banyak dieksplorasi, menguji kemampuan generalisasinya.
2.  **Analisis Kinerja Komprehensif**: Menyediakan analisis perbandingan yang terukur antara model *deep learning* canggih (CNN-LSTM) dengan model *machine learning* tradisional yang kuat (Random Forest/XGBoost) dalam konteks data tidak seimbang.
3.  **Model Acuan (*Benchmark*)**: Menghasilkan model klasifikasi yang terdokumentasi dengan baik yang dapat menjadi acuan atau *benchmark* untuk penelitian selanjutnya pada dataset serupa.

---

## 🛠️ Teknologi yang Digunakan (Tech Stack)

* **Bahasa Pemrograman**: Python
* **Framework Deep Learning**: TensorFlow / Keras
* **Library Machine Learning & Data**: Scikit-learn, Pandas, NumPy
* **Visualisasi**: Matplotlib, Seaborn