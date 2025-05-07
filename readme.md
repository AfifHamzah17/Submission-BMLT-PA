# 📊 Laporan Proyek Machine Learning: Prediksi Cuaca

## 1. **Domain Proyek** 🌍

### **Latar Belakang**
Prediksi cuaca memiliki peran yang sangat krusial dalam berbagai aspek kehidupan, termasuk perencanaan aktivitas harian ☀️, mitigasi risiko bencana alam 🌪️, hingga pengambilan keputusan dalam sektor pertanian, transportasi, dan logistik 🚚. Kemajuan teknologi dan ketersediaan data meteorologis historis yang kaya memungkinkan pengembangan model prediktif berbasis machine learning untuk menghasilkan prakiraan cuaca yang lebih akurat dan responsif 📈.

### **Rumusan Masalah**
Proyek ini bertujuan untuk membangun model klasifikasi yang mampu memprediksi probabilitas hujan pada hari berikutnya berdasarkan data cuaca historis dari berbagai kota 🌦️.

### **Tujuan Proyek**
- 🤖 Mengembangkan model klasifikasi berbasis *Neural Network* untuk memprediksi apakah akan terjadi hujan pada hari esok.
- 📊 Mengidentifikasi variabel cuaca yang paling berpengaruh terhadap kemungkinan terjadinya hujan.

---

## 2. **Business Understanding** 💼

### **Goals**
- 🚨 Menghasilkan model prediktif yang dapat memberikan sinyal peringatan dini terhadap potensi hujan.
- 🧠 Menyediakan analisis prediktif yang dapat digunakan dalam pengambilan keputusan di sektor publik dan industri.

---

## 3. **Data Understanding** 📘

### **Deskripsi Dataset**
Dataset yang digunakan berasal dari berkas `kumpulan_data_prediksi_cuaca.csv`, yang mencakup data meteorologis harian dari berbagai kota. Dataset ini terdiri dari **165 kolom fitur** dan merepresentasikan atribut seperti suhu 🌡️, kelembaban 💧, tekanan udara, dan kecepatan angin 💨.

### 📂 **Link Sumber Data**
Dataset dapat diunduh melalui platform Kaggle pada tautan berikut:  
🔗 [Weather Prediction Dataset on Kaggle](https://www.kaggle.com/datasets/thedevastator/weather-prediction?select=weather_prediction_dataset.csv)

### **Contoh Fitur:**
- `BASEL_cloud_cover`: Tingkat tutupan awan di Basel ☁️
- `BASEL_temp_mean`: Suhu rata-rata harian di Basel 🌡️
- `STOCKHOLM_humidity`: Tingkat kelembaban di Stockholm 💧
- `TOURS_wind_speed`: Kecepatan angin di Tours 💨
- `rain_tomorrow`: Label target biner (1 = hujan, 0 = tidak hujan) 🌧️

---

## 4. **Data Preparation** 🛠️

### **A. Pemeriksaan Nilai Hilang**
Hasil eksplorasi awal menunjukkan bahwa dataset relatif bersih, namun dilakukan validasi ulang untuk memastikan tidak ada *missing values*.  
Kolom dengan nilai hilang diimputasi sebagai berikut:
- Kolom numerik: imputasi menggunakan nilai **mean**
- Kolom kategorikal (jika ada): imputasi menggunakan **modus**

### **B. Pemeriksaan Duplikasi**
Tidak ditemukan data duplikat, yang mengindikasikan kualitas data yang baik dan meminimalkan risiko *overfitting*.

### **C. Pemisahan Fitur dan Label**
- Fitur (`X`): Seluruh kolom kecuali `DATE` dan `rain_tomorrow`
- Label (`y`): Kolom target `rain_tomorrow`

### **D. Normalisasi**
Fitur numerik distandarisasi menggunakan *StandardScaler* untuk mempercepat proses konvergensi selama pelatihan model Neural Network.

---

## 5. **Modeling** 🧠

### **A. Arsitektur Model**
Model dibangun menggunakan pustaka **Keras (TensorFlow backend)** dengan konfigurasi sebagai berikut:

- **Input Layer**: Jumlah neuron setara dengan jumlah fitur
- **Hidden Layer 1**: 64 neuron, aktivasi ReLU
- **Hidden Layer 2**: 32 neuron, aktivasi ReLU
- **Output Layer**: 1 neuron, aktivasi sigmoid (untuk klasifikasi biner)

### **B. Kompilasi dan Pelatihan**
- **Optimizer**: Adam ⚙️
- **Loss Function**: Binary Crossentropy
- **Epochs**: 30
- **Batch Size**: 32
- **Validation Split**: 20% dari data pelatihan digunakan untuk validasi

---

## 6. **Evaluation** 🧪

### **A. Metrik Evaluasi**
Model dievaluasi berdasarkan:
- ✅ **Accuracy**: Persentase prediksi benar
- 📉 **Loss**: Binary cross-entropy loss
- 🔲 **Confusion Matrix**: Untuk melihat distribusi prediksi kelas
- 📋 **Classification Report**: Menyediakan precision, recall, dan F1-score

### **B. Hasil Evaluasi**
- Akurasi model stabil di kisaran **80%** pada data pelatihan dan validasi
- Kurva *loss* dan *accuracy* menunjukkan bahwa model belajar secara konsisten tanpa indikasi *overfitting*
- Confusion matrix mengindikasikan keseimbangan yang relatif baik antara kelas positif dan negatif

---

## 7. **Struktur Laporan** 📑

Laporan ini disusun mengikuti pipeline standar dalam proyek machine learning, yakni:
1. *Import library dan data*
2. *Eksplorasi dan pembersihan data*
3. *Pra-pemrosesan data*
4. *Pembangunan dan pelatihan model*
5. *Evaluasi dan interpretasi hasil*

Seluruh tahapan dilengkapi dengan cuplikan kode Python yang relevan untuk replikasi.

---

## 8. **Insight dan Rekomendasi** 💡

### **Pengolahan Data**
- ✅ Standardisasi numerik terbukti meningkatkan stabilitas pelatihan Neural Network
- 🔄 Imputasi nilai hilang dengan *mean/mode* cukup efektif dalam menjaga performa model

### **Modeling**
- 🔧 Arsitektur dengan dua hidden layer sudah memberikan performa yang memadai
- 🔍 Eksperimen lanjutan dengan *tuning* jumlah neuron, penambahan dropout, atau penggunaan arsitektur yang lebih kompleks (seperti LSTM untuk data sekuensial) dapat dieksplorasi

### **Evaluasi**
- 📈 Evaluasi menggunakan metrik klasifikasi biner menunjukkan performa yang cukup baik
- 📊 Disarankan untuk mengimplementasikan *cross-validation* untuk evaluasi yang lebih robust

---

> 📌 *Kesimpulan:*  
Model Neural Network yang dibangun menunjukkan performa yang menjanjikan dalam memprediksi kemungkinan hujan esok hari. Dengan penyempurnaan lanjutan pada preprocessing dan hyperparameter tuning, akurasi prediksi masih dapat ditingkatkan untuk aplikasi dunia nyata 🌧️📈.
