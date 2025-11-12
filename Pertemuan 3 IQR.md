---

## 🧾 **Laporan Preprocessing Data**

### Dataset: *TGM_2020–2023_eng.csv*

### Topik: *Minat Baca Orang Indonesia (2020–2023)*

---

### **1. Latar Belakang**

Dataset ini berisi informasi mengenai *tingkat kegemaran membaca* masyarakat Indonesia selama periode 2020–2023, termasuk variabel seperti:

* Frekuensi membaca per minggu
* Jumlah bacaan per kuartal
* Durasi membaca harian (menit)
* Frekuensi akses internet per minggu
* Durasi penggunaan internet harian (menit)
* Nilai indeks minat baca

Namun, ditemukan adanya **outlier** pada beberapa kolom numerik. Outlier ini dapat mengganggu hasil analisis statistik dan visualisasi data. Oleh karena itu, dilakukan **proses pembersihan data (data preprocessing)** menggunakan metode **IQR (Interquartile Range)** untuk mendeteksi dan menghapus outlier.

---

### **2. Apa itu IQR (Interquartile Range)?**

**IQR** adalah metode statistik untuk mengukur sebaran data di antara kuartil pertama (Q1) dan kuartil ketiga (Q3).

[
**IQR** = Q3 - Q1
]

* **Q1 (Kuartil 1):** nilai di bawah 25% data
* **Q3 (Kuartil 3):** nilai di bawah 75% data
* **Outlier** adalah data yang berada di luar rentang:

[
[Q1 - 1.5 x IQR,\ Q3 + 1.5 x IQR]
]

Metode ini sangat berguna untuk mendeteksi nilai ekstrem yang tidak wajar tanpa mengasumsikan distribusi tertentu.

---

### **3. Kode Program (Python / Jupyter Notebook)**

Kode untuk memproses data outlier (data cleansing):
https://colab.research.google.com/drive/1B-MS3k3-uDiJcxUhhnwBGRY1A0dN8sNk?usp=sharing

---

### **4. Visualisasi**

Untuk melihat perbandingan distribusi data sebelum dan sesudah:
![Gambar 1](https://drive.google.com/uc?export=view&id=1MPGjD-R0ewgw7VbunzDJIwG9xbtQcsi9)
![Gambar 2](https://drive.google.com/uc?export=view&id=1UlQ0y747xrPr2o4_R3E-4Sl-hGcJDwbw)
![Gambar 3](https://drive.google.com/uc?export=view&id=18sEKE5AreXRs7txQToy2wBwwrKCNgyeE)
![Gambar 4](https://drive.google.com/uc?export=view&id=1xHkqrG7wAUEI6h7gYvfv2zoRF1C1gDL5)
![Gambar 5](https://drive.google.com/uc?export=view&id=1AHxFpg0gijkr5y6RaK-flC4-L2Pg7eOL)
![Gambar 6](https://drive.google.com/uc?export=view&id=1uK3XVIGFnn4uPBGS5Cka9jBVJqvw0QT4)


---

### **5. Kesimpulan**

* Metode **IQR** berhasil mendeteksi dan menghapus outlier dari kolom numerik dataset.
* Penghapusan outlier meningkatkan representasi data sehingga lebih akurat untuk analisis statistik dan visualisasi.
* Jumlah baris dataset berkurang setelah pembersihan, menandakan adanya data ekstrem yang dihapus.

---
