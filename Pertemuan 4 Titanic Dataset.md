---

# 🚢 Titanic Data Exploration

### 📊 Analisis Dataset Titanic

Proyek ini bertujuan untuk memahami faktor-faktor yang memengaruhi **peluang selamat penumpang Titanic** menggunakan Python (Seaborn,Matplotlib,Pandas), seperti:

* Jenis kelamin
* Kelas sosial
* Umur
* Tarif tiket
* Status perjalanan (sendiri atau bersama keluarga)

Melalui visualisasi seperti **count plot, box plot, scatter plot**, analisis ini memberikan gambaran mendalam tentang pola keselamatan di tragedi Titanic.

Dataset digunakan dari:

```python
sns.load_dataset('titanic')
```

---

# 📁 1. Eksplorasi Dataset

Dataset Titanic dari Seaborn mencakup kolom seperti:

| Kolom    | Arti                                |
| -------- | ----------------------------------- |
| survived | 0 = meninggal, 1 = selamat          |
| sex      | jenis kelamin                       |
| class    | kelas sosial (First/Second/Third)   |
| age      | umur penumpang                      |
| fare     | harga tiket                         |
| sibsp    | saudara/kakak/istri/suami yang ikut |
| parch    | orang tua/anak yang ikut            |
| alone    | apakah penumpang bepergian sendiri  |

Ditambahkan kolom baru:

```python
sex_numeric = 1 (male), 0 (female)
```
---

# 2. ⚰️ **Analisis Penumpang yang Meninggal (survived = 0)**

## A. **Distribusi berdasarkan Jenis Kelamin & Kelas (Count Plots)**

Visualisasi memperlihatkan pola yang sangat jelas:

* **Korban laki-laki jauh lebih banyak** daripada perempuan.
* Berdasarkan kelas:

  * **Third Class** memiliki korban terbanyak.
  * Disusul Second Class.
  * **First Class** memiliki jumlah korban paling sedikit.

👉 **Makna:** Laki-laki kelas rendah merupakan kelompok paling rentan.

---

## B. **Distribusi Umur Korban (Box Plots)**

Temuan utama:

### Berdasarkan jenis kelamin:

* **Laki-laki:**

  * Median usia korban: **20–35 tahun**
  * Rentang umur luas (remaja hingga lansia)

* **Perempuan:**

  * Lebih sedikit korban
  * Ada kelompok dewasa dan **anak-anak** yang menjadi korban

### Berdasarkan kelas sosial:

* Korban **Third Class**:

  * Usia lebih muda
  * Rentang umur lebih lebar (banyak anak)
* Korban First/Second Class:

  * Rata-rata lebih tua

👉 **Interpretasi:** Banyak penumpang muda dan anak-anak kelas rendah tidak mendapat akses penyelamatan.

---

## C. **Age vs Fare pada Korban (Scatter Plots)**

Pola yang muncul:

* Konsentrasi korban terbesar berada pada:

  * Usia **20–40 tahun**
  * **Fare rendah** → mayoritas Third Class
* Terdapat korban dari berbagai umur & tarif, namun densitas terbesar:
  **fare rendah + usia dewasa muda**

👉 **Insight:** Tarif tiket rendah (kelas rendah) berkaitan erat dengan risiko kematian lebih tinggi.

---

# 3. 🛟 **Analisis Penumpang yang Selamat (survived = 1)**

## A. **Distribusi berdasarkan Jenis Kelamin & Kelas (Count Plots)**

Visualisasi menunjukkan:

* **Perempuan lebih banyak selamat** daripada laki-laki.
* Penyintas terbanyak berasal dari:

  1. First Class
  2. Third Class
  3. Second Class

👉 **Kesimpulan:** “Women and children first” benar-benar diterapkan, dan kelas sosial sangat berpengaruh.

---

## B. **Distribusi Umur Penyintas (Box Plots)**

Temuan:

* **Penyintas perempuan**:

  * Banyak dari kelompok umur muda
  * Terdapat banyak anak-anak

* **Penyintas laki-laki**:

  * Didominasi kelompok usia dewasa

* **First Class penyintas** cenderung lebih tua secara rata-rata

👉 **Makna:** Usia dan kelas berinteraksi dalam peluang selamat.

---

## C. **Age vs Fare pada Penyintas (Scatter Plots)**

Insight penting:

* Banyak penyintas membayar **fare tinggi** (First Class).
* Penyintas tersebar pada berbagai umur.
* Penyintas perempuan tersebar merata pada semua fare.
* Penyintas laki-laki lebih terkonsentrasi pada fare tinggi.

👉 **Kesimpulan:** Kelas sosial adalah faktor yang sangat dominan bagi laki-laki.

---

# 4. 👨‍👩‍👧 **Analisis Status "Alone" dan Pengaruhnya terhadap Survival**

## A. **Survival Rate berdasarkan Alone Status (Bar Plot)**

Temuan:

* Penumpang yang **tidak sendirian** (bersama keluarga) memiliki **peluang selamat jauh lebih tinggi**.
* Penumpang yang **sendirian** lebih banyak meninggal.

👉 **Interpretasi:** Keterhubungan sosial meningkatkan peluang diselamatkan.

---

## B. **Box Plot: Umur & Fare berdasarkan Alone + Survival**

### **1. Age vs Alone/Survived**

* Penyintas **bersama keluarga** memiliki rentang umur lebar → termasuk banyak anak.
* Penyintas **sendirian** cenderung dewasa muda.
* Korban bersama keluarga banyak berasal dari kelompok anak-anak kelas rendah.

### **2. Fare vs Alone/Survived**

* Penyintas, baik bersama keluarga maupun sendirian, umumnya membayar **tarif lebih mahal**.
* Korban sendirian mayoritas berada di fare rendah.

👉 **Insight:** Penumpang dengan keluarga dan/atau berfare tinggi berada pada posisi yang lebih aman.

---

## C. **Scatter Plot: Age vs Fare berdasarkan Alone & Survived**

### Berdasarkan Alone:

* Penumpang bersama keluarga terkonsentrasi pada:

  * Usia muda
  * Fare tinggi
* Penumpang sendirian tersebar di semua kelompok umur & fare

### Berdasarkan Survival:

* Penyintas lebih banyak berada di area **fare tinggi**
* Anak-anak — baik bersama keluarga maupun sendirian — cukup banyak selamat

👉 **Pola kuat:** kombinasi usia + kelas + status keluarga menentukan survival.

---

# 🎯 **Kesimpulan Utama dari Seluruh Visualisasi**

Analisis komprehensif ini menemukan bahwa peluang selamat di Titanic sangat dipengaruhi oleh beberapa faktor kunci yang saling berinteraksi:

### ✔ **1. Jenis kelamin**

Perempuan memiliki peluang jauh lebih tinggi untuk selamat.

### ✔ **2. Kelas sosial**

First Class memiliki akses lebih cepat ke dek atas dan sekoci → survival rate tertinggi.

### ✔ **3. Struktur keluarga (alone status)**

Penumpang yang bepergian bersama keluarga lebih sering diperhatikan & diselamatkan.

### ✔ **4. Tarif tiket (fare)**

Fare tinggi → dek lebih tinggi → prioritas lebih besar dalam evakuasi.

### ✔ **5. Usia**

Anak-anak mendapatkan prioritas tinggi dalam penyelamatan.

---

# 🧩 **Kesimpulan Besar**

Dapat disimpulkan dari pola yang ada dalam data tersebut:

> Perempuan muda kelas atas yang bepergian bersama keluarga hampir selalu selamat,
> Laki-laki dewasa dari kelas rendah yang bepergian sendirian memiliki peluang selamat yang sangat kecil.

Visualisasi ini mmenggambarkan ketimpangan sosial dan ekonomi yang terjadi dalam proses penyelamatan penumpang pada tragedi Titanic.
---
