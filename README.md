project_name = "Klasifikasi Gambar: Shoe vs Sandal vs Boot"

# {Shoe vs Sandal vs Boot}

- **Nama:** {Hasbi Abdullah}
- **Email:** {hasbiabdullah75571@gmail.coml}
- **ID Dicoding:** {m198d5y0743}

## 1. Pendahuluan
Proyek ini adalah implementasi sistem klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengidentifikasi jenis alas kaki (Sepatu, Sandal, atau Boot). Dataset yang digunakan adalah 'Shoe vs Sandal vs Boot'.

## 2. Setup Lingkungan
Untuk menjalankan notebook ini, pastikan Anda telah menginstal semua dependensi yang tercantum dalam `requirements.txt`. Anda dapat menginstalnya menggunakan pip:

```bash
pip install -r requirements.txt
```

## 3. Persiapan Data
Dataset 'Shoe vs Sandal vs Boot' diekstrak dan kemudian dibagi menjadi data pelatihan, validasi, dan pengujian dengan rasio 70:15:15. Augmentasi data (rotasi, pergeseran lebar/tinggi, shear, zoom, horizontal flip) diterapkan pada data pelatihan untuk meningkatkan ketahanan model.

### Statistik Data:
- Jumlah gambar pelatihan: {train_generator.samples}
- Jumlah gambar validasi: {validation_from_validation_dir_generator.samples}
- Jumlah gambar pengujian: {test_generator.samples}
- Ukuran gambar: 150x150 piksel
- Kelas: {', '.join(labels)}

## 4. Arsitektur Model
Model yang digunakan adalah arsitektur CNN sequential sederhana dengan beberapa lapisan konvolusi dan pooling, diikuti oleh lapisan Flatten dan Dense. Arsitekturnya adalah sebagai berikut:

- `Conv2D(32, (3, 3), activation='relu', input_shape=(150, 150, 3))`
- `MaxPooling2D(2, 2)`
- `Conv2D(64, (3, 3), activation='relu')`
- `MaxPooling2D(2, 2)`
- `Conv2D(128, (3, 3), activation='relu')`
- `MaxPooling2D(2, 2)`
- `Flatten()`
- `Dense(512, activation='relu')`
- `Dense({train_generator.num_classes}, activation='softmax')`

Model dikompilasi dengan optimizer Adam (learning rate 0.001) dan fungsi kerugian 'categorical_crossentropy'.

## 5. Pelatihan Model
Model dilatih selama maksimal 50 epoch dengan callback `EarlyStopping` (patience=5) untuk mencegah overfitting dan `ModelCheckpoint` untuk menyimpan model terbaik berdasarkan `val_loss`. Callback kustom juga diimplementasikan untuk menghentikan pelatihan jika akurasi dan validasi akurasi mencapai >= 95%.

### Hasil Pelatihan Terakhir:
- Akurasi Pelatihan: {train_acc:.2f}
- Akurasi Validasi: {val_acc:.2f}

## 6. Evaluasi Model
Model dievaluasi pada set data pengujian yang terpisah.

### Hasil Evaluasi pada Data Uji:
- Loss Uji: {test_loss:.4f}
- Akurasi Uji: {test_accuracy:.4f}

## 7. Konversi Model
Model telah dikonversi ke format `TensorFlow Lite` (`vegs.tflite`) dan `TensorFlow.js` (`model_tfjs/`) untuk penyebaran ke perangkat mobile atau web.

## 8. Contoh Inferensi
Bagian inferensi opsional menunjukkan bagaimana model dapat digunakan untuk memprediksi kelas gambar baru yang diunggah, menampilkan prediksi dan tingkat kepercayaan.

"""

with open('README.md', 'w') as f:
    f.write(readme_content)

print("File README.md berhasil dibuat.")
