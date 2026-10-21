# UTS Machine Learning – Linear & Logistic Regression

- **Nama  :** Indra Gunawan
- **NIM   :** 241011400601
- **Kelas :** Reg B
- **random_state :** 1 (2 digit terakhir NIM = 01)

Semua model dan metrik diimplementasikan sendiri dengan NumPy (tanpa scikit-learn, kecuali soal bonus).

## Isi Repositori
| File | Keterangan |
|---|---|
| `tugas_UTS.ipynb` | Notebook jawaban lengkap dengan output dan grafik |
| `Ads_Data.csv` | Data biaya iklan vs penjualan (40 data) |
| `Email_Data.csv` | Data jumlah link, kata promo, dan label spam (60 data) |

## Ringkasan Hasil

### Bagian A – Linear Regression (`Ads_Data.csv`)
Persamaan: `y_hat = 29.8900 + 8.9707 * BiayaIklan` (setiap tambahan biaya iklan 1 juta Rp menaikkan penjualan sekitar 8,97 juta Rp).

| Data | MAE | RMSE | R² |
|---|---|---|---|
| Training | 4.1355 | 5.7582 | 0.9447 |
| Testing | 6.1503 | 7.2733 | 0.9315 |

Gradient descent (5000 iterasi): lr = 0.001 terlalu lambat (belum konvergen), lr = 0.02 konvergen dan sama dengan normal equation, lr = 0.1 divergen (overflow pada iterasi ke-204).

### Bagian B – Logistic Regression (`Email_Data.csv`)
`P(Spam) = sigmoid(-8.6728 + 0.7786 * JumlahLink + 0.7087 * KataPromo)`

Pada data testing (threshold 0,5): accuracy = 0.9333, precision = 0.8750, recall = 1.0, F1 = 0.9333.

| Threshold | FP | FN | Precision | Recall |
|---|---|---|---|---|
| 0.3 | 1 | 0 | 0.8750 | 1.0000 |
| 0.5 | 1 | 0 | 0.8750 | 1.0000 |
| 0.7 | 0 | 2 | 1.0000 | 0.7143 |

Threshold pilihan: 0,5 (paling seimbang; threshold 0,7 menghilangkan 1 FP tetapi meloloskan 2 spam).

### Bonus
Linear Regression scikit-learn identik dengan implementasi sendiri. Pada Logistic Regression koefisien berbeda karena scikit-learn memakai regularisasi L2 (`C=1.0`) secara default, namun metrik testing sama.
