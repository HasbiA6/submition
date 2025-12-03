# Proyek Klasifikasi Gambar: Bunga

- **Nama:** [Hasbi Abdullah]
- **Email:** [hasbiabdullah75571@gmail.com]
- **ID Dicoding:** [M198D5Y0743]

# Proyek Klasifikasi Gambar: [Flowers Dataset]

## Deskripsi Proyek
Proyek ini bertujuan untuk mengembangkan model klasifikasi gambar menggunakan *Convolutional Neural Network* (CNN) untuk mengidentifikasi berbagai jenis bunga dari dataset `Flowers`. Model ini dilatih menggunakan TensorFlow dan Keras, serta dioptimalkan untuk performa dan akurasi dalam mengenali sepuluh kelas bunga yang berbeda.

## Fitur
-   **Klasifikasi Gambar:** Menggunakan model CNN untuk mengklasifikasikan gambar bunga ke dalam 10 kategori berbeda.
-   **Augmentasi Data:** Mengimplementasikan augmentasi data untuk meningkatkan robustnya model dan mencegah *overfitting*.
-   **Optimasi Model:** Menggunakan *optimizer* Adam dan *callback* seperti `EarlyStopping` dan `ModelCheckpoint` untuk melatih model secara efisien.
-   **Konversi Model:** Model dikonversi ke format TensorFlow Lite (TFLite) dan TensorFlow.js (TFJS) untuk *deployment* di berbagai platform.

## Struktur Dataset
Dataset bunga dibagi menjadi tiga direktori utama:
-   `train`: Berisi gambar untuk pelatihan model.
-   `validation`: Berisi gambar untuk validasi selama pelatihan.
-   `test`: Berisi gambar untuk evaluasi akhir model.

Setiap direktori memiliki sub-direktori yang sesuai dengan nama kelas bunga (misalnya, 'Bunga Dandelions', 'Bunga Daisy', dll.).

## Teknologi yang Digunakan
-   Python
-   TensorFlow 2.x
-   Keras
-   Numpy
-   Pandas
-   Matplotlib
-   Scikit-learn
-   `split-folders` (untuk membagi dataset)
-   `tensorflowjs` (untuk konversi model ke TFJS)

## Instalasi
1.  **Clone repositori:**
    ```bash
    git clone [LINK_REPO_ANDA]
    cd [NAMA_FOLDER_PROYEK]
    ```
2.  **Buat virtual environment (opsional tapi direkomendasikan):**
    ```bash
    python -m venv venv
    source venv/bin/activate # On Windows, use `venv\Scripts\activate`
    ```
3.  **Instal dependensi:**
    ```bash
    pip install -r requirements.txt
    ```

## Penggunaan
1.  **Persiapan Data:** Pastikan dataset bunga Anda tersusun rapi dalam direktori `FLOWERS` dengan sub-direktori `train`, `validation`, dan `test`, serta sub-direktori kelas bunga di dalamnya.
2.  **Pelatihan Model:** Jalankan notebook Jupyter (`[NAMA_NOTEBOOK_ANDA].ipynb`) untuk melatih model. Pastikan semua *cell* dijalankan secara berurutan.
3.  **Evaluasi Model:** Setelah pelatihan selesai, model akan dievaluasi menggunakan data test dan *confusion matrix* akan ditampilkan.
4.  **Inference:** Anda dapat menggunakan bagian Inferensi di notebook untuk menguji model dengan gambar baru.

## Hasil
Model mencapai akurasi sebesar [ISI_AKURASI_TEST_DISINI]% pada dataset pengujian.
