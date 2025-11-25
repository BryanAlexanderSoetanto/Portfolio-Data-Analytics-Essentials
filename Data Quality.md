---

# 📊 **Ringkasan Eksplorasi Data Komprehensif — Dataset ww2ships.csv.xlsx**

Analisis ini dilakukan untuk memahami kualitas, struktur, serta karakteristik dataset **ww2ships.csv.xlsx**. Proses eksplorasi mencakup pemeriksaan awal data, analisis nilai hilang, evaluasi tipe data, pendeteksian outlier, serta peninjauan kolom kategorikal. Berikut adalah rangkuman temuan penting dari seluruh proses eksplorasi data.

---

## 1. 📁 **Pemuatan Data Awal**

Dataset dimuat dari file Excel ke dalam DataFrame pandas. Setelah pemuatan, lima baris pertama diperiksa untuk memastikan struktur data.

**Temuan awal:**

* Data berhasil dimuat tanpa error.
* Kolom yang muncul antara lain: *Unnamed: 0*, *Name*, *Class*, *Country*, dan *Launch Year*.
* Terlihat adanya nilai kosong (`NaN`) pada kolom **Launch Year**, mengindikasikan adanya informasi yang hilang sejak awal.

---

## 2. 🧱 **Ikhtisar Struktur Data (Initial Overview)**

Data kemudian diperiksa untuk mengetahui ukuran dataset, tipe data, serta jumlah nilai non-null pada setiap kolom menggunakan `df.info()`.

**Hasil utama:**

* Dataset berisi **1786 baris** dan **5 kolom**.
* Tipe data:

  * `Unnamed: 0`: int64 (kemungkinan hanya kolom indeks).
  * `Name`, `Class`, `Country`: object/string.
  * `Launch Year`: object, dengan **1128 nilai terisi** dan **658 nilai hilang**.
* Launch Year seharusnya numerik, tetapi terbaca sebagai string → ada masalah kualitas data.

---

## 3. ⚠️ **Analisis Nilai Hilang (Missing Values)**

Jumlah dan persentase nilai hilang dihitung untuk tiap kolom, lalu divisualisasikan dalam bentuk heatmap.

**Temuan:**

* Satu-satunya kolom dengan nilai hilang besar adalah **Launch Year**, yaitu **36.84%** dari total baris.
* Heatmap memperlihatkan bahwa celah data hanya terpusat pada kolom ini, sementara kolom lain relatif lengkap.

👉 **Dampak:** Analisis yang menggunakan tahun peluncuran harus dilakukan dengan hati-hati.

---

## 4. 📈 **Statistik Deskriptif**

Agar dapat dianalisis secara numerik, kolom Launch Year dikonversi ke tipe `float64`. Setelah dikonversi, dihitung statistik dasar untuk kolom numerik serta ringkasan kategori untuk kolom string.

### **Launch Year (Numerik):**

* `count`: 1061 nilai valid
* `mean`: 1934.38
* `std`: 60.04
* `min`: **0** ← *outlier tidak logis, bukan tahun peluncuran sebenarnya*
* `max`: 1946

### **Class (Kategorikal):**

* Jumlah kategori unik: **292** → kategori dengan *high cardinality*
* Nilai paling sering:

  * M-class Minesweeper (293 kapal)
  * Type VII-class Submarine (143 kapal)
  * dan beberapa lainnya
* Ada nilai **“No Classification”** yang cukup banyak.

### **Country (Kategorikal):**

* 15 kategori unik
* Negara terbanyak:

  * Germany (957 kapal)
  * United States (473 kapal)
  * Japan (154 kapal)

👉 **Insight:** Data sangat didominasi oleh negara Poros dan Sekutu besar WW2.

---

## 5. 🧬 **Pemeriksaan Duplikasi**

Dataset diperiksa untuk mengetahui apakah ada baris yang benar-benar identik.

**Hasil:**

* Tidak ditemukan baris duplikat.
* Ini menandakan setiap baris mewakili satu kapal yang unik.

---

## 6. 🔍 **Validasi Tipe Data**

Setelah konversi Launch Year:

* `Name`, `Class`, `Country` tetap bertipe object dan sudah sesuai.
* `Launch Year` kini bertipe `float64`, ideal untuk analisis numerik serta dapat menyimpan nilai NaN.

Namun, karena tahun seharusnya bilangan bulat:

* Disarankan menggunakan tipe **Int64 (nullable integer)** setelah data dibersihkan.

---

## 7. 🗂️ **Analisis Kolom Kategorikal**

Setiap kolom kategorikal diperiksa dari sisi kualitas data dan variasi nilai.

### **Kolom Class:**

* Memiliki jumlah kategori unik yang sangat banyak.
* Terdapat masalah **encoding teks**, contohnya:
  `'La Galissonnière-class Light Cruiser'` muncul sebagai
  `'La GalissonniÃƒÂ¨re-class Light Cruiser'`.
* Ada kategori "No Classification" yang kemungkinan merepresentasikan data tidak lengkap.

### **Kolom Country:**

* Nilai relatif bersih dan konsisten.
* Bar plot menunjukkan dominasi kuat negara:

  * Jerman,
  * Amerika Serikat,
  * Jepang.

👉 **Temuan:** Perang laut WW2 sangat terkonsentrasi pada negara besar dengan armada besar.

---

## 8. 📉 **Deteksi Outlier**

Outlier dianalisis menggunakan box plot.

**Temuan utama:**

* Nilai **Launch Year = 0** muncul sebagai outlier yang ekstrem.
  Tahun 0 tidak mungkin → ini adalah error data mentah.
* Ada beberapa titik yang berada di ujung distribusi bawah (tahun sangat kecil), namun tidak se-signifikan nilai 0.

👉 **Kesimpulan:** Launch Year = 0 harus dibersihkan atau diimputasi.

---

# 🧠 **Ringkasan Kualitas Data & Rekomendasi Pembersihan**

## **Temuan Kunci**

### ✔ **1. Nilai Hilang**

* Launch Year memiliki 36.84% nilai yang hilang → isu terbesar dataset.

### ✔ **2. Tidak Ada Duplikasi**

* Semua baris unik → kualitas bagus untuk identifikasi kapal.

### ✔ **3. Tipe Data**

* Sebagian besar kolom sudah tepat.
* Launch Year seharusnya diubah menjadi integer setelah dibersihkan.

### ✔ **4. Outlier**

* Launch Year = 0 adalah anomali dan harus ditangani.

### ✔ **5. Masalah Encoding**

* Kolom Class memiliki karakter rusak → perlu perbaikan.

### ✔ **6. Struktur Kategorikal**

* Banyak kategori unik pada Class → mungkin memerlukan standarisasi.

---

# 🧽 **Rekomendasi Pembersihan Data**

### 🟦 1. Penanganan Launch Year

* Ganti nilai 0 → NaN
* Imputasi menggunakan:

  * Median, atau
  * Pendekatan model, atau
  * Menghapus baris jika proporsinya kecil untuk analisis tertentu

### 🟦 2. Perbaikan Encoding Teks

* Standarisasi karakter menggunakan:

  * `str.encode('latin1').decode('utf-8')`
  * atau metode pembersihan khusus

### 🟦 3. Penanganan Kategori "No Classification"

* Tentukan apakah:

  * Dibiarkan sebagai kategori sendiri
  * Diimputasi berdasarkan pola kapal lain
  * Dikelompokkan ke kategori “Unknown / Missing”

### 🟦 4. Konversi Tipe Data

* Setelah imputasi, ubah Launch Year → `Int64` agar lebih representatif.

---

# 🎯 **Kesimpulan Akhir**

Secara keseluruhan, dataset **ww2ships.csv.xlsx** memiliki struktur dasar yang baik (tidak ada duplikasi dan sebagian besar kolom konsisten), namun memerlukan pembersihan pada beberapa aspek penting, terutama **Launch Year** dan **encoding teks Class**. Dengan pembersihan yang tepat, dataset ini akan jauh lebih siap digunakan untuk analisis historis, eksplorasi pola armada WW2, dan pemodelan lebih lanjut.

---
