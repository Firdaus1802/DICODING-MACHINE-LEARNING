# Proyek Akhir: Membangun Proyek Machine Learning

Repositori ini berisi proyek akhir untuk kelas **Belajar Machine Learning untuk Pemula** dari Dicoding Indonesia. Proyek mencakup analisis data transaksi perbankan, segmentasi nasabah (*Clustering*), dan pembangunan model prediksi cluster (*Classification*).

---

## Ringkasan Proyek

Pipeline pengerjaan dibagi menjadi dua tahap utama:

### 1. Clustering (Segmentasi Nasabah)
- **EDA & Pembersihan Data**: Penanganan missing value, penghapusan duplikasi, dan filtering kolom identifier (`ID`, `IP Address`, `Date`).
- **Preprocessing**: Feature encoding dengan `LabelEncoder`, deteksi dan penanganan outlier menggunakan metode IQR, serta standarisasi fitur numerik dengan `StandardScaler`.
- **Modeling**: Penentuan jumlah cluster optimal menggunakan **Elbow Method (KElbowVisualizer)** dan pemodelan dengan **K-Means Clustering** ($K=2$).
- **Evaluasi & Visualisasi**: Evaluasi menggunakan *Silhouette Score* serta reduksi dimensi 2D menggunakan PCA untuk visualisasi sebaran cluster dan centroid.
- **Interpretasi**: Analisis karakteristik tiap cluster sebelum dan sesudah inverse scaling, dilanjutkan dengan ekspor dataset berlabel kolom `Target`.

### 2. Klasifikasi (Prediksi Target Cluster)
- **Data Splitting**: Pembagian dataset latih dan uji (80:20) dengan `stratify=y` untuk menjaga proporsi kelas.
- **Model Baseline**: **Decision Tree Classifier** (`random_state=42`).
- **Model Pembanding**: **Random Forest Classifier**.
- **Hyperparameter Tuning**: Optimasi model Random Forest menggunakan **GridSearchCV** (5-Fold Cross Validation).
- **Evaluasi**: Pengukuran performa model menggunakan *Precision*, *Recall*, *F1-Score*, dan *Accuracy*.

---

## Hasil dan Evaluasi Singkat

### Karakteristik Cluster
| Cluster | Usia Rata-rata | Nominal Transaksi (Mean) | Saldo Akun (Mean) | Profil Dominan |
| :---: | :---: | :---: | :---: | :--- |
| **0** | ~45 tahun | $255.55 | $5,142.17 | Nasabah usia matang, mayoritas profesi Dokter, transaksi via Cabang |
| **1** | ~44 tahun | $258.15 | $5,058.81 | Nasabah dinamis, mayoritas Mahasiswa (Student), durasi transaksi lebih cepat |

### Metrik Klasifikasi
- **Decision Tree**: Akurasi 100% pada data uji.
- **Random Forest**: Akurasi 100% pada data uji.
- **Tuned Random Forest**: Akurasi 100% setelah tuning parameter (`n_estimators`, `max_depth`, `min_samples_split`).

---

## Struktur Berkas

```text
├── [Clustering]_Submission_Akhir_BMLP_Firdaus Dhuha Prabowo.ipynb   # Notebook tahap Clustering
├── [Klasifikasi]_Submission_Akhir_BMLP_Firdaus Dhuha Prabowo.ipynb  # Notebook tahap Klasifikasi
├── data_clustering.csv                                             # Dataset hasil clustering (scaled)
├── data_clustering_inverse.csv                                     # Dataset hasil clustering (inversed)
├── model_clustering.h5                                             # Model K-Means (Disimpan via joblib)
├── PCA_model_clustering.h5                                         # Model K-Means berbasis PCA
├── decision_tree_model.h5                                          # Model Decision Tree
├── explore_RandomForest_classification.h5                          # Model Random Forest
├── tuning_classification.h5                                        # Model Random Forest hasil tuning
├── Submission_BMLP_Firdaus_Dhuha_Prabowo.zip                       # Arsip berkas submission Dicoding
├── .gitignore
└── README.md
```

---

## Cara Menjalankan

1. Clone repositori ini:
   ```bash
   git clone https://github.com/Firdaus1802/DICODING-MACHINE-LEARNING.git
   cd DICODING-MACHINE-LEARNING
   ```

2. Instal dependensi yang diperlukan:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn yellowbrick joblib
   ```

3. Jalankan Jupyter Notebook secara berurutan:
   - Buka dan jalankan `[Clustering]_Submission_Akhir_BMLP_Firdaus Dhuha Prabowo.ipynb` untuk menghasilkan dataset `data_clustering_inverse.csv` dan model clustering.
   - Buka dan jalankan `[Klasifikasi]_Submission_Akhir_BMLP_Firdaus Dhuha Prabowo.ipynb` untuk melatih dan mengevaluasi model klasifikasi.

---
**Author**: Firdaus Dhuha Prabowo
