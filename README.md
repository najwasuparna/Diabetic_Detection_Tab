# 🩺 Diabetic Prediction App

Proyek Machine Learning ini bertujuan untuk memprediksi risiko diabetes pada pasien berdasarkan indikator kesehatan individual seperti usia, riwayat hipertensi, tingkat glukosa darah, indeks massa tubuh (BMI), dan variabel klinis lainnya.

Aplikasi ini dilengkapi dengan antarmuka web interaktif berbasis **Gradio** untuk pengujian prediksi secara langsung.

---

## 📊 Ringkasan Dataset

Dataset awal berisi **100.000 data pasien** dengan **9 atribut/kolom**:
- **Gender**: Jenis kelamin pasien.
- **Age**: Usia pasien.
- **Hypertension**: Riwayat hipertensi (`0` = Tidak, `1` = Ya).
- **Heart Disease**: Riwayat penyakit jantung (`0` = Tidak, `1` = Ya).
- **Smoking History**: Riwayat merokok (`never`, `No Info`, `current`, dll.).
- **BMI**: *Body Mass Index* (Indeks Massa Tubuh).
- **HbA1c Level**: Rata-rata kadar gula darah selama ±3 bulan terakhir.
- **Blood Glucose Level**: Kadar gula darah acak/saat ini.
- **Diabetes (Target)**: Variabel target (`0` = Tidak Diabetes, `1` = Diabetes).

> *Catatan: Untuk efisiensi pelatihan model pada notebook ini, data disampling sebanyak 2.000 sampel secara acak.*

---

## ⚙️ Metodologi & Alur Kerja

1. **Preprocessing Data**:
   - Pengodean fitur kategorikal (`gender` dan `smoking_history`) menggunakan `LabelEncoder`.
   - Pemisahan Fitur (`X`) dan Target (`y`).
2. **Eksperimen Model Klasifikasi**:
   - **K-Nearest Neighbors (KNN)**
   - **Decision Tree Classifier**
   - **Logistic Regression**
3. **Evaluasi & Pengujian Split Data**:
   Masing-masing model diuji menggunakan 3 skema pembagian data (*Train:Test*):
   - **80 : 20**
   - **70 : 30**
   - **90 : 10**
4. **Metrik Evaluasi**:
   - *Accuracy Score*, *Precision*, *Recall*, *F1-score*, dan *Confusion Matrix*.

---

## 📈 Hasil Evaluasi Perbandingan Akurasi

| Model | Split 70:30 | Split 80:20 | Split 90:10 |
| :--- | :---: | :---: | :---: |
| **Decision Tree** | 95.50% | 95.50% | **97.00%** |
| **KNN** | 94.50% | 95.00% | 93.50% |
| **Logistic Regression** | 95.67% | **96.50%** | 96.00% |

- **Decision Tree** mencapai akurasi tertinggi pada split **90:10** (**97.00%**).
- **Logistic Regression** menunjukkan performa yang paling stabil dan konsisten di seluruh rasio *split* (mencapai **96.50%** pada split **80:20**), sehingga dipilih sebagai model utama untuk aplikasi prediksi.

---

## 🖥️ Antarmuka Web (Gradio App)

Proyek ini terintegrasi dengan **Gradio** untuk memberikan tampilan antarmuka berbasis web. Pengguna dapat memasukkan variabel kesehatan pasien dan menerima hasil prediksi secara instan (`🟩 Tidak Diabetes` / `🟥 Diabetes`).

### Cara Menjalankan Aplikasi:
1. Pastikan library terinstall:
   ```bash
   pip install pandas scikit-learn gradio
