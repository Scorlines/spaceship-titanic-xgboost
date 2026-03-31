# 🚀 Spaceship Titanic - Prediksi Survival dengan XGBoost

Proyek machine learning yang memprediksi apakah penumpang akan "ditransport" ke dimensi lain dalam versi futuristik dari dataset Titanic klasik.

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Kaggle Competition](https://img.shields.io/badge/kaggle-spaceship--titanic-blue)](https://www.kaggle.com/competitions/spaceship-titanic)

## 📋 Daftar Isi

- [Tentang Proyek](#tentang-proyek)
- [Dataset](#dataset)
- [Metodologi](#metodologi)
- [Hasil](#hasil)
- [Instalasi](#instalasi)
- [Cara Pakai](#cara-pakai)
- [Struktur Proyek](#struktur-proyek)
- [Kontribusi](#kontribusi)
- [Lisensi](#lisensi)

## 📌 Tentang Proyek

Proyek ini mengikuti kompetisi Kaggle [Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic). Menggunakan machine learning dan feature engineering, kami membangun model prediktif untuk menentukan penumpang mana yang ditransport ke dimensi lain.

### Pernyataan Masalah
Diberikan data penumpang dari bencana Spaceship Titanic, prediksi apakah setiap penumpang ditransport (masalah klasifikasi biner).

### Fitur Utama yang Dianalisis
- **Informasi Pribadi**: Usia, status VIP, planet asal
- **Lokasi Kabin**: Deck, nomor kabin, sisi kapal
- **Pola Pengeluaran**: Biaya room service, food court, mall, spa, VR deck
- **Status Perjalanan**: Bepergian sendiri atau dengan grup

## 📊 Dataset

| Metrik | Nilai |
|--------|-------|
| Sampel Pelatihan | ~8.700 penumpang |
| Sampel Test | ~4.300 penumpang |
| Fitur Input | 13 fitur yang sudah diproses |
| Variabel Target | Ditransport (Biner: Ya/Tidak) |

**File Data:**
- `train.csv` - Data pelatihan dengan label
- `test.csv` - Data test untuk prediksi
- `sample_submission.csv` - Format submission contoh

## 🔧 Metodologi

### 1. Feature Engineering
- **Dekomposisi Kabin**: Pisahkan string kabin (contoh: "B/0/P") menjadi fitur terpisah:
  - Deck (huruf)
  - Nomor Kabin (numerik)
  - Sisi (port/starboard)
- **Total Pengeluaran**: Gabungkan semua kolom pengeluaran untuk analisis daya belanja
- **Flag Perjalanan Solo**: Indikator biner untuk penumpang yang bepergian sendiri
- **Ukuran Grup**: Ekstrak dari pola kabin

### 2. Pemrosesan Data
- **Nilai yang Hilang**: Diisi dengan median (numerik) atau modus (kategorikal)
- **Encoding Kategorikal**: Label encoding untuk variabel kategorikal
- **Pembagian Data**: 80% pelatihan / 20% validasi (stratified split)
- **Scaling**: Standard scaling untuk fitur numerik

### 3. Arsitektur Model
**XGBoost Classifier** dengan hyperparameter yang dioptimalkan:
```python
XGBClassifier(
    n_estimators=500,
    max_depth=6,
    learning_rate=0.05,
    early_stopping_rounds=10,
    random_state=42
)
```

### 4. Metrik Evaluasi
- Akurasi
- Precision, Recall, F1-Score
- ROC-AUC Score
- Analisis Pentingnya Fitur

## 📈 Hasil

Model mencapai performa kompetitif melalui:
- Feature engineering yang komprehensif
- Penanganan nilai yang hilang dengan tepat
- Kemampuan gradient boosting XGBoost
- Tuning hyperparameter strategis

## 🚀 Instalasi

### Prasyarat
- Python 3.8 atau lebih tinggi
- pip atau conda

### Langkah Setup

1. **Clone repository**
```bash
git clone https://github.com/Scorlines/spaceship-titanic-xgboost.git
cd spaceship-titanic-xgboost
```

2. **Buat virtual environment** (direkomendasikan)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python -m venv venv
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

## 🎯 Cara Pakai

### Mulai Cepat

Jalankan notebook untuk melatih model dan menghasilkan prediksi:

```bash
jupyter notebook spaceship-titanic-xgboost.ipynb
```

### Alur Notebook

1. **Load Data** - Baca file CSV pelatihan dan test
2. **Exploratory Data Analysis** - Pahami distribusi dan korelasi data
3. **Feature Engineering** - Buat dan tingkatkan fitur
4. **Pemrosesan Data** - Tangani nilai yang hilang dan encoding
5. **Pelatihan Model** - Latih XGBoost dengan early stopping
6. **Evaluasi Model** - Nilai performa pada set validasi
7. **Prediksi** - Hasilkan file submission dengan prediksi test
8. **Visualisasi** - Plot pentingnya fitur dan metrik performa

## 📁 Struktur Proyek

```
spaceship-titanic-xgboost/
├── README.md                              # Dokumentasi proyek
├── spaceship-titanic-xgboost.ipynb        # Notebook utama dengan model XGBoost
├── requirements.txt                       # Python dependencies
├── .gitignore                            # File git ignore
├── LICENSE                               # Lisensi MIT
│
└── spaceship-titanic/                    # Folder dataset
    ├── train.csv                         # Data pelatihan (8.693 baris)
    ├── test.csv                          # Data test (4.277 baris)
    └── sample_submission.csv             # Format submission contoh
```

## 📦 Dependencies

Library utama yang digunakan:
- **pandas** - Manipulasi dan analisis data
- **numpy** - Komputasi numerik
- **scikit-learn** - Preprocessing ML dan metrik
- **xgboost** - Gradient boosting classifier
- **matplotlib** - Visualisasi data
- **seaborn** - Visualisasi data statistik

Untuk daftar lengkap, lihat [requirements.txt](requirements.txt)

## 🔍 Insight Kunci

- Pola pengeluaran adalah prediktor kuat dari status transportasi
- Lokasi kabin/deck sangat relevan
- Penumpang solo memiliki tingkat transportasi berbeda
- Status VIP berkorelasi dengan hasil survival

## 🤝 Kontribusi

Kontribusi sangat diterima! Untuk berkontribusi:

1. Fork repository
2. Buat branch fitur Anda (`git checkout -b feature/FiturBagus`)
3. Commit perubahan Anda (`git commit -m 'Tambah FiturBagus'`)
4. Push ke branch (`git push origin feature/FiturBagus`)
5. Buka Pull Request

## 📝 Lisensi

Proyek ini dilisensikan di bawah MIT License - lihat file [LICENSE](LICENSE) untuk detail.

## 🙌 Ucapan Terima Kasih

- [Kompetisi Kaggle Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic)
- Dokumentasi dan komunitas XGBoost
- Komunitas data science Python

---

**Catatan:** Proyek ini untuk tujuan pendidikan dan kompetisi. Prediksi didasarkan pada model machine learning dan harus digunakan sesuai dengan itu.
6. Evaluasi di validation set
7. Generate `submission.csv` untuk Kaggle

## Hasil

Setelah training selesai, kita dapat:
- **Akurasi validation:** Berapa akurat model di data yang belum pernah dilihat
- **Feature importance:** Grafik menunjukkan fitur mana yang paling berpengaruh
- **Classification report:** Detail metrik seperti precision, recall, F1-score
- **Submission file:** Siap upload ke Kaggle

## Insight Menarik

- Lokasi kabin (deck & side) sangat prediktif untuk penentuan transport
- Penumpang yang bepergian sendiri punya pola berbeda
- Spending patterns jelas membedakan antar kelompok penumpang
- Total pengeluaran adalah indikator kuat

## Library yang Dipakai

- pandas: untuk manipulasi data
- numpy: komputasi numerik
- scikit-learn: preprocessing & metrics
- xgboost: model machine learning
- matplotlib & seaborn: visualisasi
- jupyter: notebook interaktif

## Buat Hasil Lebih Baik

Ini masih bisa diimprove:
- Tuning hyperparameter lebih detail
- Coba ensemble dengan model lain
- Cross-validation untuk hasil lebih robust
- Handle class imbalance jika ada
- Model deep learning sebagai alternative

## Note

Pastikan path ke dataset sudah sesuai dengan struktur folder lokal Anda sebelum run notebook!
