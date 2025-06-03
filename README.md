# Proyek Klasifikasi Gambar: Subset (5 Kelas) dari Animals-10

Proyek ini bertujuan untuk membangun model klasifikasi gambar menggunakan Convolutional Neural Network (CNN) untuk mengklasifikasikan 5 jenis hewan dari dataset Animals-10. Penggunaan subset ini bertujuan untuk memenuhi kriteria jumlah gambar spesifik (10.000-15.000) sambil tetap mempertahankan karakteristik penting dataset seperti resolusi gambar yang tidak seragam.

- **Nama:** Muhammad Hasan Fadhlillah
- **Email:** mc006d5y2342@student.devacademy.id
- **ID Dicoding:** MC006D5Y2342

## Detail Dataset

Dataset asli yang digunakan adalah "Animals-10" yang tersedia di Kaggle. Untuk proyek ini, digunakan subset yang terdiri dari 5 kelas hewan.

- Sumber Dataset Asli: [https://www.kaggle.com/datasets/alessiocorrado99/animals10](https://www.kaggle.com/datasets/alessiocorrado99/animals10)
- **Kelas yang Digunakan (Contoh):**
  1.  `dog` (cane)
  2.  `cat` (gatto)
  3.  `horse` (cavallo)
  4.  `sheep` (pecora)
  5.  `elephant` (elefante)
      _(Nama folder dalam dataset asli mungkin dalam bahasa Italia atau Inggris, sesuaikan dalam kode jika perlu)_
- **Jumlah Gambar (Subset):** Sekitar 13.000 gambar (tergantung jumlah pasti per kelas yang dipilih).
- **Resolusi Gambar:** Gambar-gambar dalam dataset ini memiliki resolusi yang beragam dan tidak seragam, yang memenuhi salah satu saran penting.
- **Pembagian Dataset:** Data akan dimuat dan dibagi menjadi data training dan validasi. Selanjutnya, data validasi akan digunakan juga sebagai test set untuk evaluasi akhir.

## Arsitektur Model

Model CNN yang dibangun menggunakan arsitektur Sequential dengan beberapa layer Convolutional (Conv2D), MaxPooling2D, BatchNormalization, Dropout, dan Dense layer. Fungsi aktivasi ReLU digunakan pada hidden layer dan Softmax pada output layer untuk klasifikasi multi-kelas.

## Tahapan Proyek

1.  **Persiapan Data:**
    - Mengunduh dataset Animals-10 (atau menggunakan yang sudah diunduh).
    - Membuat struktur direktori baru untuk subset 5 kelas yang dipilih.
    - Menyalin gambar dari kelas-kelas yang dipilih ke direktori subset.
    - Memuat data training dan validasi dari direktori subset menggunakan `image_dataset_from_directory`.
    - Melakukan augmentasi data pada data training.
    - Normalisasi data gambar (menggunakan layer `Rescaling`).
2.  **Pembuatan Model:**
    - Mendefinisikan arsitektur model CNN.
    - Menggunakan `Adam` optimizer dan `CategoricalCrossentropy` (atau `SparseCategoricalCrossentropy` tergantung `label_mode`) sebagai loss function.
3.  **Pelatihan Model:**
    - Melatih model dengan data training dan validasi.
    - Menggunakan callbacks: `EarlyStopping` dan `ModelCheckpoint`.
4.  **Evaluasi Model:**
    - Memvisualisasikan metrik akurasi dan loss selama training.
    - Mengevaluasi performa model pada data test/validasi.
5.  **Konversi Model:**
    - Menyimpan model dalam format `SavedModel`.
    - Mengonversi model ke format `TensorFlow Lite (TFLite)`.
    - Mengonversi model ke format `TensorFlow.js (TFJS)`.
6.  **Inferensi Model:**
    - Melakukan contoh inferensi menggunakan model TFLite pada gambar baru.

## Hasil

- Akurasi Training:
- Akurasi Validasi/Test:

Model berhasil disimpan dalam format `SavedModel`, `TFLite`, dan `TFJS`. Bukti inferensi juga disertakan dalam notebook.

## Cara Menjalankan Notebook

1.  Pastikan semua library dalam `requirements.txt` sudah terpasang.
    ```bash
    pip install -r requirements.txt
    ```
2.  **Persiapan Dataset:**
    - Unduh dataset "Animals-10" dari Kaggle.
    - Jalankan sel-sel awal di notebook yang berfungsi untuk membuat direktori subset dan menyalin file gambar dari 5 kelas yang dipilih. Pastikan path ke dataset Animals-10 yang asli sudah benar.
    - Contoh struktur path dataset asli yang diharapkan: `<base_animals10_path>/raw-img/<class_name>/...`
    - Contoh struktur path dataset subset yang akan dibuat oleh notebook: `animals_subset/train/<class_name>/...` dan `animals_subset/val/<class_name>/...`
3.  Jalankan semua sel dalam file `notebook.ipynb` secara berurutan.
