# Proyek Klasifikasi Gambar: Intel Image Classification

Proyek ini bertujuan untuk membangun model klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengklasifikasikan gambar pemandangan alam dan perkotaan dari dataset Intel Image Classification.

## Detail Dataset

Dataset yang digunakan adalah "Intel Image Classification" yang tersedia di Kaggle.
- Sumber: [https://www.kaggle.com/datasets/puneet6060/intel-image-classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
- Dataset ini berisi sekitar 25.000 gambar yang terbagi dalam 6 kelas:
    1.  `buildings`
    2.  `forest`
    3.  `glacier`
    4.  `mountain`
    5.  `sea`
    6.  `street`
- Gambar memiliki resolusi 150x150 piksel.
- Dataset dibagi menjadi data training (`seg_train`), data validasi (`seg_test`), dan ada juga folder `seg_pred` untuk prediksi (tidak digunakan untuk training berlabel).

## Arsitektur Model

Model CNN yang dibangun menggunakan arsitektur Sequential dengan beberapa layer Convolutional (Conv2D), MaxPooling2D, BatchNormalization, Dropout, dan Dense layer. Fungsi aktivasi ReLU digunakan pada hidden layer dan Softmax pada output layer untuk klasifikasi multi-kelas.

## Tahapan Proyek

1.  **Persiapan Data:**
    * Mengunduh dan mengekstrak dataset.
    * Memuat data training dan validasi menggunakan `image_dataset_from_directory`.
    * Melakukan augmentasi data pada data training untuk meningkatkan variasi dan robustisitas model.
    * Normalisasi data gambar.
2.  **Pembuatan Model:**
    * Mendefinisikan arsitektur model CNN.
    * Menggunakan `Adam` optimizer dan `SparseCategoricalCrossentropy` sebagai loss function.
3.  **Pelatihan Model:**
    * Melatih model dengan data training dan validasi.
    * Menggunakan callbacks: `EarlyStopping` untuk mencegah overfitting dan `ModelCheckpoint` untuk menyimpan model terbaik.
4.  **Evaluasi Model:**
    * Memvisualisasikan metrik akurasi dan loss selama training.
    * Mengevaluasi performa model pada data test.
5.  **Konversi Model:**
    * Menyimpan model dalam format `SavedModel`.
    * Mengonversi model ke format `TensorFlow Lite (TFLite)`.
    * Mengonversi model ke format `TensorFlow.js (TFJS)`.
6.  **Inferensi Model:**
    * Melakukan contoh inferensi menggunakan model TFLite pada gambar baru.

## Hasil

- Akurasi Training: [Isi dengan akurasi training Anda, target >= 95%]
- Akurasi Validasi/Test: [Isi dengan akurasi validasi/test Anda, target >= 95%]

Model berhasil disimpan dalam format `SavedModel`, `TFLite`, dan `TFJS`. Bukti inferensi juga disertakan dalam notebook.

## Cara Menjalankan Notebook

1.  Pastikan semua library dalam `requirements.txt` sudah terpasang.
    ```bash
    pip install -r requirements.txt
    ```
2.  Unduh dataset Intel Image Classification dari Kaggle dan letakkan dalam struktur direktori yang sesuai, atau sesuaikan path dataset dalam notebook.
    Contoh path yang diharapkan:
    ```
    <base_path>/intel-image-classification/seg_train/
    <base_path>/intel-image-classification/seg_test/
    ```
3.  Jalankan semua sel dalam file `notebook.ipynb`.
