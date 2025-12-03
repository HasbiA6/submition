# Proyek Klasifikasi Gambar: Bunga

- **Nama:** [Input Nama Anda]
- **Email:** [Input Email Anda]
- **ID Dicoding:** [Input Username Dicoding Anda]

## Overview Proyek

Proyek ini bertujuan untuk mengembangkan model klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengidentifikasi berbagai jenis bunga. Model dilatih menggunakan dataset gambar bunga yang dibagi menjadi set pelatihan, validasi, dan pengujian. Tujuan utamanya adalah untuk mencapai akurasi klasifikasi minimal 85% pada set pengujian.

## Data Preparation

Dataset gambar bunga diakses dari Google Drive (`/content/drive/MyDrive/FLOWERS`). Dataset ini terdiri dari gambar-gambar bunga yang dikategorikan ke dalam beberapa kelas. Berikut adalah struktur direktori dataset:

```
/content/drive/MyDrive/FLOWERS
├── train
│   ├── Bunga Daisy
│   ├── Bunga Mawar
│   ├── ...
├── validation
│   ├── Bunga Tulip
│   ├── Bunga Matahari
│   ├── ...
└── test
    ├── Bunga Daisy
    ├── Bunga Tulip
    ├── ...
```

Jumlah kelas bunga yang terdeteksi adalah **10**.

**Data Augmentation:**
Untuk meningkatkan ketahanan model dan mencegah overfitting, augmentasi data diterapkan pada set pelatihan menggunakan `ImageDataGenerator` dengan parameter seperti rotasi, pergeseran lebar/tinggi, shear, zoom, dan flip horizontal. Data juga di-rescale ke rentang `0-1`.

## Model Architecture

Model yang digunakan adalah Sequential CNN dengan arsitektur sebagai berikut:

- `Conv2D(32, (3, 3), activation='relu', input_shape=(150, 150, 3))`
- `MaxPooling2D(2, 2)`
- `Conv2D(64, (3, 3), activation='relu')`
- `MaxPooling2D(2, 2)`
- `Conv2D(128, (3, 3), activation='relu')`
- `MaxPooling2D(2, 2)`
- `Flatten()`
- `Dense(512, activation='relu')`
- `Dense(jumlah_kelas, activation='softmax')`

Model dikompilasi dengan optimizer `Adam` (learning_rate=0.001), fungsi loss `categorical_crossentropy`, dan metrik `accuracy`.

## Training & Evaluation

Model dilatih dengan `ImageDataGenerator` yang dikonversi ke `tf.data.Dataset`. Digunakan custom callback untuk menghentikan pelatihan jika akurasi dan validasi akurasi mencapai >= 95%, serta `EarlyStopping` untuk memantau `val_loss` dengan kesabaran 5 epoch untuk mencegah overfitting. Model terbaik disimpan selama pelatihan.

- **Jumlah Epoch Pelatihan:** Model dilatih selama 50 epoch, namun dihentikan lebih awal pada epoch ke-16 karena Early Stopping.
- **Final Test Loss:** `0.3695`
- **Final Test Accuracy:** `0.8781`

Model berhasil mencapai akurasi pengujian sebesar **87.81%**, yang melebihi target 85%.

**Visualisasi Hasil Pelatihan:**
Grafik akurasi dan loss pelatihan serta validasi telah divisualisasikan untuk menunjukkan performa model sepanjang epoch.

## Model Conversion

Model yang telah dilatih diekspor dan dikonversi ke format `TensorFlow Lite (TFLite)` dan `TensorFlow.js (TFJS)` untuk memudahkan deployment pada perangkat mobile atau web.

- **SavedModel:** `saved_model/`
- **TFLite Model:** `vegs.tflite`
- **TFJS Model:** `model_tfjs/`

## Inference (Contoh)

Model dapat digunakan untuk melakukan prediksi pada gambar baru. Contoh prediksi pada gambar tunggal menunjukkan model dapat mengklasifikasikan jenis bunga dengan tingkat kepercayaan tertentu.

```python
# Contoh output inferensi
# Gambar: 9.jpg
# Prediksi: Bunga Mawar
# Confidence: 99.58%
```
