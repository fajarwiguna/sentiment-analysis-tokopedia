# Sentiment Analysis of Tokopedia App Reviews 🇮🇩📱

Proyek ini melakukan **web scraping** review aplikasi Tokopedia dari Google Play Store dan membangun model **analisis sentimen** menggunakan beberapa pendekatan machine learning dan deep learning.

---

## 📁 Struktur Proyek

- `scraping.ipynb`  
  Notebook untuk melakukan scraping data review dari Google Play Store menggunakan `google-play-scraper`.
  
- `sentiment_model.ipynb`  
  Notebook yang memuat:
  - Eksplorasi data
  - Labeling sentimen otomatis berdasarkan rating
  - Preprocessing teks
  - Implementasi dan evaluasi 3 skema model:
    - **TF-IDF + SVM**
    - **Word2Vec + Random Forest**
    - **LSTM (Deep Learning)**

---

## 🛠️ Teknologi & Library

- Python
- `pandas`, `numpy`, `re`, `string`
- `nltk` (stopwords)
- `scikit-learn`
- `gensim` (Word2Vec)
- `tensorflow` / Keras (LSTM)
- `google_play_scraper`

---

## 🔍 Langkah-Langkah

### 1. Scraping Review Tokopedia

Menggunakan `google_play_scraper` untuk mengambil hingga 10.000 review dari pengguna Tokopedia di Google Play Store (lokalisasi Indonesia).

```python
from google_play_scraper import reviews
```

> Output disimpan dalam file `data_tokopedia_reviews.csv`.

---

### 2. Preprocessing & Labeling

- Menghapus karakter tidak penting, angka, tanda baca, dan stopwords.
- Label sentimen ditentukan berdasarkan rating:

  - ⭐ 1–2 → **Negatif**  
  - ⭐ 3 → **Netral**  
  - ⭐ 4–5 → **Positif**

---

### 3. Skema Model yang Dibangun

#### ✅ Skema 1: TF-IDF + SVM

- TF-IDF vectorization
- Linear Support Vector Classifier (SVM)
- Evaluasi: akurasi & classification report (`sklearn`)

#### 🌳 Skema 2: Word2Vec + Random Forest

- Word embedding menggunakan Word2Vec (`gensim`)
- Setiap review direpresentasikan sebagai rata-rata vektor kata
- Model klasifikasi: Random Forest

#### 🧠 Skema 3: LSTM (Deep Learning)

- Tokenisasi dan padding sequence
- Arsitektur: LSTM + Bidirectional + Dropout
- Aktivasi akhir: Softmax untuk 3 kelas

---

## 📈 Contoh Hasil (Dummy Output)

```
Akurasi TF-IDF + SVM     : 0.83
Akurasi Word2Vec + RF    : 0.81
Akurasi LSTM             : 0.85
```

> Hasil dapat bervariasi tergantung dataset & random state.

---

## 🧪 Contoh Inference

```python
# TF-IDF + SVM
"produk ini sangat mengecewakan dan tidak sesuai deskripsi" → Prediksi: NEGATIF

# Word2Vec + RF
"pelayanan cepat dan ramah" → Prediksi: POSITIF

# LSTM
"produk ini sangat keren" → Prediksi: POSITIF
```

---

## 📌 Catatan

- Dataset bersifat dinamis dan bergantung pada review terbaru.
- LSTM cocok untuk skala besar, tetapi membutuhkan waktu training lebih lama.
- Word2Vec cocok untuk menghasilkan embedding reusable dalam proyek lain.

---

## 📂 Output

- `data_tokopedia_reviews.csv` — Dataset hasil scraping
- Model inference tersedia di akhir masing-masing skema pada notebook

---

## 📄 Lisensi

Proyek ini dibuat untuk tujuan edukasi dan riset.  
Data diambil secara publik melalui Google Play Store. Gunakan dengan bijak.
