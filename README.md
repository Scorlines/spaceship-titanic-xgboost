# 🚀 Spaceship Titanic - Survival Prediction with XGBoost

A machine learning project that predicts whether passengers will be transported to an alternate dimension in this sci-fi twist on the classic Titanic dataset.

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Kaggle Competition](https://img.shields.io/badge/kaggle-spaceship--titanic-blue)](https://www.kaggle.com/competitions/spaceship-titanic)

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results](#results)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## 📌 About the Project

This project participates in the Kaggle [Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic) competition. Using machine learning and feature engineering, we build a predictive model to determine which passengers were transported to an alternate dimension.

### Problem Statement
Given passenger data from a Spaceship Titanic disaster, predict whether each passenger was transported (binary classification problem).

### Key Features Analyzed
- **Personal Information**: Age, VIP status, planet of origin
- **Cabin Location**: Deck, cabin number, side of the ship
- **Spending Patterns**: Room service, food court, shopping mall, spa, VR deck expenses
- **Travel Status**: Traveling solo or with group

## 📊 Dataset

| Metric | Value |
|--------|-------|
| Training Samples | ~8,700 passengers |
| Test Samples | ~4,300 passengers |
| Input Features | 13 processed features |
| Target Variable | Transported (Binary: Yes/No) |

**Data Files:**
- `train.csv` - Training data with labels
- `test.csv` - Test data for predictions
- `sample_submission.csv` - Sample submission format

## 🔧 Methodology

### 1. Feature Engineering
- **Cabin Decomposition**: Split cabin strings (e.g., "B/0/P") into separate features:
  - Deck (letter)
  - Cabin Number (numeric)
  - Side (port/starboard)
- **Total Spending**: Aggregate all expense columns for spending power analysis
- **Solo Travel Flag**: Binary indicator for passengers traveling alone
- **Group Size**: Extract from cabin patterns

### 2. Data Processing
- **Missing Values**: Imputed with median (numeric) or mode (categorical)
- **Categorical Encoding**: Label encoding for categorical variables
- **Data Split**: 80% training / 20% validation (stratified split)
- **Scaling**: Standard scaling for numeric features

### 3. Model Architecture
**XGBoost Classifier** with optimized hyperparameters:
```python
XGBClassifier(
    n_estimators=500,
    max_depth=6,
    learning_rate=0.05,
    early_stopping_rounds=10,
    random_state=42
)
```

### 4. Evaluation Metrics
- Accuracy
- Precision, Recall, F1-Score
- ROC-AUC Score
- Feature Importance Analysis

## 📈 Results

The model achieves competitive performance through:
- Comprehensive feature engineering
- Proper handling of missing values
- XGBoost's gradient boosting capabilities
- Strategic hyperparameter tuning

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip or conda

### Setup Steps

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/spaceship-titanic-xgboost.git
cd spaceship-titanic-xgboost
```

2. **Create a virtual environment** (recommended)
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

## 🎯 Usage

### Quick Start

Run the notebook to train the model and generate predictions:

```bash
jupyter notebook spaceship-titanic-xgboost.ipynb
```

### Notebook Workflow

1. **Data Loading** - Read training and test CSV files
2. **Exploratory Data Analysis** - Understand data distributions and correlations
3. **Feature Engineering** - Create and enhance features
4. **Data Preprocessing** - Handle missing values and encoding
5. **Model Training** - Train XGBoost classifier with early stopping
6. **Model Evaluation** - Assess performance on validation set
7. **Predictions** - Generate submission file with test predictions
8. **Visualization** - Feature importance plots and performance metrics

### Command Line Usage

```python
# To run just the training:
python train.py
```

## 📁 Project Structure

```
spaceship-titanic-xgboost/
├── README.md                              # Project documentation
├── spaceship-titanic-xgboost.ipynb        # Main notebook with XGBoost model
├── requirements.txt                       # Python dependencies
├── .gitignore                            # Git ignore file
├── LICENSE                               # MIT License
│
└── spaceship-titanic/                    # Dataset directory
    ├── train.csv                         # Training data (8,693 rows)
    ├── test.csv                          # Test data (4,277 rows)
    └── sample_submission.csv             # Expected submission format
```

## 📦 Dependencies

Key libraries used:
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computations
- **scikit-learn** - ML preprocessing and metrics
- **xgboost** - Gradient boosting classifier
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization

For complete list, see [requirements.txt](requirements.txt)

## 🔍 Key Insights

- Spending patterns are strong predictors of transportation status
- Cabin location/deck is highly relevant
- Solo travelers have different transportation rates
- VIP status correlates with survival outcomes

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙌 Acknowledgments

- [Kaggle Spaceship Titanic Competition](https://www.kaggle.com/competitions/spaceship-titanic)
- XGBoost documentation and community
- Python data science community

---

**Note:** This project is for educational and competition purposes. Predictions are based on machine learning models and should be used accordingly.
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
