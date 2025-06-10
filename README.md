# Proyek Klasifikasi Gambar: Animals-10

## Deskripsi
Proyek ini adalah submission untuk kelas Belajar Machine Learning untuk Pemula dari Dicoding. Tujuan proyek ini adalah untuk membangun model klasifikasi gambar yang mampu mengenali 10 jenis hewan berbeda dari dataset "Animals-10" yang diambil dari Kaggle.

Dataset terdiri dari sekitar 28.000 gambar hewan yang terbagi dalam 10 kategori: cane, cavallo, elefante, farfalla, gallina, gatto, mucca, pecora, ragno, scoiattolo.

## Detail Implementasi
- **Nama:** Muhammad Hasan Fadhlillah
- **Email:** mc006d5y2342@student.devacademy.id
- **ID Dicoding:** MC006D5Y2342
- **Dataset**: Animals-10 dari Kaggle (oleh alessiocorrado99)
- **Path Dataset di Kaggle**: /kaggle/input/animals10/raw-img
- **Ukuran Gambar Input**: 224x224
- **Batch Size**: 16
- **Arsitektur Model**: Transfer Learning dengan EfficientNetB0 + Custom layers (11 lapisan total)
- **Optimizer**: Adam dengan learning rate adaptif
- **Loss Function**: Categorical Crossentropy
- **Callbacks**: ModelCheckpoint, EarlyStopping, ReduceLROnPlateau
- **Target Akurasi Dicoding**: >85% (Wajib), >95% (Saran untuk Bintang 5)
- **Akurasi Test Aktual**: 95.18%

## Teknik yang Digunakan untuk Mencapai Akurasi >95%
1. **Transfer Learning**: Menggunakan EfficientNetB0 pre-trained pada ImageNet
2. **Two-Phase Training**: 
   - Phase 1: Frozen base model (20 epochs)
   - Phase 2: Fine-tuning dengan learning rate sangat kecil (30 epochs)
3. **Advanced Data Augmentation**: Rotasi, shift, zoom, brightness, dll.
4. **Batch Normalization**: Untuk stabilitas training
5. **Dropout Layers**: Untuk mencegah overfitting
6. **Learning Rate Scheduling**: ReduceLROnPlateau callback
7. **Early Stopping**: Dengan patience untuk mencegah overfitting

## Struktur Direktori Submission
```
submission/
├── tfjs_model/
│   ├── group1-shard1of1.bin
│   └── model.json
├── tflite_model/
│   ├── model.tflite
│   └── labels.txt
├── saved_model/
│   ├── saved_model.pb
│   └── variables/
├── proyek-klasifikasi-gambar-animals10-classification.ipynb
├── README.md
└── requirements.txt
```

## Cara Menjalankan di Kaggle
1. Buat notebook baru di Kaggle
2. Tambahkan dataset "Animals-10" (oleh alessiocorrado99) ke notebook
3. Pastikan GPU/TPU aktif di pengaturan notebook
4. Copy-paste semua code dari notebook ini
5. Jalankan semua sel secara berurutan
6. Save & Run All (Commit) setelah selesai
7. Download file submission.zip dari tab Output

## Format Model yang Dihasilkan
- **SavedModel**: Format standar TensorFlow untuk deployment
- **TF-Lite**: Format optimized untuk mobile/edge devices
- **TensorFlow.js**: Format untuk deployment di web browser

## Catatan Penting
- Model menggunakan Transfer Learning untuk mencapai akurasi tinggi
- Dataset dapat dikurangi menjadi 13.000 gambar untuk mempercepat training
- Two-phase training approach untuk hasil optimal
- Model telah dioptimasi untuk berbagai platform deployment
