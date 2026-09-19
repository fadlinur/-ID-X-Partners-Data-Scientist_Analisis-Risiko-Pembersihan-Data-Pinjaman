# 💳 Credit Risk Classification - ID/X Partners Data Science Project

Repositori ini berisi proyek *end-to-end* **Credit Risk Classification** menggunakan dataset **Lending Club (2007–2014)**. Proyek ini bertujuan untuk membangun sistem prediktif berbasis *Machine Learning* guna mendeteksi risiko kredit macet (*loan default*) secara objektif, akurat, dan otomatis.

---

## 📊 Project Overview
Lembaga keuangan menghadapi risiko kerugian finansial yang signifikan akibat gagal bayar pinjaman. Proyek ini mengimplementasikan model klasifikasi untuk membedakan antara **Good Loan** dan **Bad Loan** guna mengoptimalkan proses penyaringan risiko kredit.

* **Sumber Data:** Dataset Lending Club (`loan_data_2007_2014.csv`)
* **Target Variabel (`target`):** Diklasifikasikan berdasarkan status pinjaman (`loan_status`), di mana status berisiko tinggi seperti *Charged Off*, *Default*, dan *Late* dikategorikan sebagai **1 (Bad Loan)** dan sisanya **0 (Good Loan)**.
* **Model Terbaik:** **XGBoost (Tuned)**

---

## 🔄 Project Workflow & Methodology
1. **Data Pre-processing & Cleaning:**
   * Menghapus kolom yang seluruh nilainya kosong serta kolom dengan tingkat *missing value* di atas ambang batas 60%.
   * Imputasi nilai kosong menggunakan **median** untuk fitur numerik dan **modus** untuk fitur kategorikal.
   * Pembersihan kolom yang tidak memiliki nilai prediktif (*useless columns* seperti `id`, `member_id`, `url`, `title`, `emp_title`, `zip_code`) dan fitur finansial yang redundan/multikolinear (`funded_amnt`, `funded_amnt_inv`).
2. **Exploratory Data Analysis (EDA):** Analisis univariat (seperti distribusi *loan amount* dan *term*) serta analisis multivariat menggunakan *correlation heatmap*.
3. **Feature Engineering & Encoding:** 
   * Menggunakan *Label Encoding* dan *One-Hot Encoding* (`pd.get_dummies`) untuk mengubah data kategorikal menjadi numerik.
   * Pembagian data latih dan uji dengan rasio **70:30** (`train_test_split`).
4. **Handling Imbalanced Data:** Mengatasi ketidakseimbangan kelas pada data latih menggunakan teknik **SMOTE** (*Synthetic Minority Over-sampling Technique*).
5. **Feature Scaling:** Normalisasi fitur numerik utama (`loan_amnt`, `annual_inc`, `installment`, `dti`) menggunakan **StandardScaler**.
6. **Modeling & Hyperparameter Tuning:**
   * Melakukan eksperimen dengan beberapa algoritma: *Logistic Regression*, *Decision Tree*, *Random Forest*, dan *XGBoost*.
   * Melakukan *Hyperparameter Tuning* menggunakan `RandomizedSearchCV` dengan metrik evaluasi utama **F1-Score**.

---

## 📈 Model Evaluation & Comparison (After Tuning)

Berikut adalah ringkasan hasil evaluasi performa model pada data uji (*Test Set*):

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Decision Tree** | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| **XGBoost** | **0.997** | **0.973** | **1.000** | **0.986** | **1.000** |
| **Random Forest** | 0.989 | 0.996 | 0.915 | 0.954 | 0.999 |

### **Best Model: XGBoost**
* Berdasarkan stabilitas generalisasi, nilai *gap* antara data *train* dan *test* yang sangat kecil, serta metrik evaluasi yang optimal, **XGBoost** dipilih sebagai model terbaik.
* **Parameter Terbaik (`best_params`):**
  * `reg_lambda`: 10.0
  * `n_estimators`: 200
  * `max_depth`: 7
  * `learning_rate`: 0.01
  * `gamma`: 0.1

---

## 🔍 Top 10 Feature Importance (XGBoost)
Berdasarkan visualisasi *feature importance* dari model XGBoost, variabel-variabel yang paling berpengaruh dalam menentukan keputusan model meliputi:
1. `loan_status` (Fitur referensi target awal)
2. `out_prncp` (Sisa pokok pinjaman)
3. `total_rec_late_fee` (Total denda keterlambatan yang diterima)
4. `last_pymnt_d` (Tanggal pembayaran terakhir)
5. `recoveries` (Nilai pemulihan dana dari pinjaman macet)
6. Serta variabel pendukung lainnya seperti `total_rec_prncp`, `last_pymnt_amnt`, `loan_amnt`, `installment`, dan `open_acc`.

---

## 🛠️ Tech Stack & Libraries
* **Language:** Python
* **Environment:** Google Colab / Jupyter Notebook
* **Data Manipulation & Analysis:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning & Evaluation:** Scikit-Learn, XGBoost, Imbalanced-Learn (SMOTE)
* **Model Serialization:** Joblib

---

## 🚀 How to Run the Code
1. Clone repositori ini ke perangkat Anda:
   ```bash
   git clone [https://github.com/username/credit-risk-classification.git](https://github.com/username/credit-risk-classification.git)

   ---

# 👨‍💻 Author

### Fadli Nurrizky


---

# 🙏 Thank You
