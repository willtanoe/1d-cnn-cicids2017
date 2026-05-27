# Klasifikasi Serangan Jaringan Multi-Kelas Menggunakan 1D-CNN pada Dataset CIC-IDS2017

| Nama | NIM |
| --- | --- |
| Muhamad Wildan Rizky | 201012520001 |
| Haamid Ahmad Saragih | 201012520025 |

Tugas kuliah mata kuliah Pembelajaran Mendalam Untuk Teknik Elektro.

## Struktur Proyek
- `pipeline.ipynb` - end-to-end notebook
- `confusion_matrix.png` - confusion matrix output

## Dataset
CIC-IDS2017 dalam format MachineLearningCSV dengan 11 kelas.

**Credits:** Dataset diunduh dari [Kaggle - Network Intrusion Dataset](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset)

Dataset asli: [UNB CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) oleh Canadian Institute for Cybersecurity.

## Preprocessing
- Membersihkan whitespace di nama kolom
- Normalisasi label (non-ASCII cleanup)
- Menggabungkan variasi Web Attack jadi satu kelas
- Menghapus kelas Heartbleed dan Infiltration
- Menghapus baris NaN/Inf dan kolom zero-variance
- Label encoding + StandardScaler per fold

## Model
1D-CNN: Conv1d + BatchNorm + ReLU + Dropout + MaxPool (3 blok) → FC head (11 kelas)

## Training
- 80/20 stratified split
- 5-fold StratifiedKFold CV
- CrossEntropyLoss dengan class weights
- Early stopping (patience=5)

## Hasil (Test Set)
| Metrik | Nilai |
| --- | --- |
| Macro F1-score | 0.6320 |
| Accuracy | 0.9146 |

## Cara Menjalankan
1. Download dataset dari [Kaggle](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset)
2. Ekstrak ke folder `cic-ids2017/`
3. Buka `pipeline.ipynb`
4. Jalankan semua cell

## Kebutuhan
- Python 3.10+
- PyTorch (CUDA)
- scikit-learn, pandas, numpy, matplotlib
