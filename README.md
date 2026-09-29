# Prediksi_Volume_Kendaraan-SDG-11

# Penerapan Linear Regression untuk Prediksi Volume Kendaraan Berdasarkan Jam dan Hari dalam Mendukung Transportasi Perkotaan Berkelanjutan

## Deskripsi Project

Project ini merupakan penerapan kecerdasan buatan (Artificial Intelligence) untuk memprediksi **volume kendaraan** berdasarkan informasi waktu, khususnya **jam dan hari**, menggunakan algoritma **Linear Regression**.

Project ini berkaitan dengan **Sustainable Development Goal (SDG) 11: Sustainable Cities and Communities**, khususnya dalam mendukung terciptanya transportasi perkotaan yang lebih berkelanjutan melalui pemanfaatan data dan teknologi.

Model Machine Learning digunakan untuk mempelajari hubungan antara waktu dengan volume kendaraan. Hasil prediksi dapat digunakan sebagai informasi pendukung untuk memahami pola lalu lintas dan membantu perencanaan transportasi perkotaan.

---

## Latar Belakang

Volume kendaraan di wilayah perkotaan dapat berbeda-beda berdasarkan waktu, terutama pada jam-jam tertentu. Perubahan volume kendaraan perlu diketahui agar dapat menjadi bahan pertimbangan dalam pengelolaan transportasi perkotaan.

Oleh karena itu, project ini menggunakan data Metro Interstate Traffic Volume untuk membangun model AI yang dapat memprediksi volume kendaraan berdasarkan karakteristik waktu seperti jam dan hari.

Penerapan Linear Regression diharapkan dapat membantu memberikan perkiraan volume kendaraan sehingga dapat mendukung pengelolaan transportasi yang lebih terencana dan sejalan dengan SDG 11: Sustainable Cities and Communities.

---
## Kelompok: 11
## Anggota Kelompok

| No. | Nama                | NIM       |
| --- | ------------------  | ----------|
| 1   | Sindi Aulia         | F1G125077 |
| 2   | Kallyn Renanda Putri | F1G125035 |
| 3   | Muhammad Fajar M    | F1G125040 |

---

## Rumusan Masalah

1. Bagaimana melakukan preprocessing dan mengolah data waktu pada dataset **Metro Interstate Traffic Volume** untuk memprediksi volume kendaraan?

2. Bagaimana penerapan algoritma **Linear Regression** untuk memprediksi volume kendaraan berdasarkan jam dan hari?

3. Bagaimana performa model **Linear Regression** dalam memprediksi volume kendaraan berdasarkan hasil evaluasi **MAE, RMSE, dan R² Score**?


---

## 🎯 Tujuan

Tujuan project ini adalah:

1. Mengolah dan membersihkan dataset **Metro Interstate Traffic Volume**.

2. Melakukan preprocessing pada data waktu untuk memperoleh informasi **jam dan hari**.

3. Membuat model prediksi volume kendaraan menggunakan algoritma **Linear Regression**.

4. Mengukur performa model menggunakan metrik **MAE, MSE, RMSE, dan R² Score**.

5. Melakukan simulasi prediksi volume kendaraan berdasarkan jam dan hari tertentu.

---

## 📊 Dataset

Dataset yang digunakan dalam project ini adalah:

**Metro Interstate Traffic Volume Dataset**

Dataset berisi data volume lalu lintas kendaraan beserta beberapa informasi yang berkaitan dengan kondisi dan waktu pengamatan.

Beberapa variabel yang terdapat dalam dataset antara lain:

* `holiday`
* `temp`
* `rain_1h`
* `snow_1h`
* `clouds_all`
* `weather_main`
* `weather_description`
* `date_time`
* `traffic_volume`

Variabel utama yang digunakan dalam project ini adalah:

* **`date_time`** → digunakan untuk mendapatkan informasi jam dan hari.
* **`traffic_volume`** → digunakan sebagai target atau nilai yang akan diprediksi.

Jumlah data pada dataset adalah **48.204 baris dengan 9 kolom**.

Dataset Kaggle

https://www.kaggle.com/datasets/pooriamst/metro-interstate-traffic-volume
---

## ⚙️ Preprocessing Data

Tahapan preprocessing data yang dilakukan adalah:

1. Memasukkan dataset CSV ke Google Colab.
2. Mengubah dataset menjadi DataFrame menggunakan Pandas.
3. Memeriksa data awal.
4. Memeriksa informasi dan tipe data.
5. Memeriksa nilai kosong pada dataset.
6. Mengubah kolom `date_time` menjadi format datetime.
7. Mengekstrak informasi **jam** dari `date_time`.
8. Mengekstrak informasi **hari dalam minggu** dari `date_time`.
9. Menentukan fitur yang digunakan untuk model.
10. Menentukan `traffic_volume` sebagai target prediksi.

Fitur utama yang digunakan dalam model adalah:

* `hour`
* `day_of_week`

Sedangkan target yang diprediksi adalah:

* `traffic_volume`

---

## 🕐 Pembentukan Fitur Waktu

Kolom `date_time` diolah menjadi beberapa informasi waktu.

### Jam

Fitur `hour` menunjukkan jam pengamatan dalam rentang:

**00.00 – 23.00**

### Hari

Fitur `day_of_week` menunjukkan hari dalam satu minggu:

| Nilai | Hari   |
| ----: | ------ |
|     0 | Senin  |
|     1 | Selasa |
|     2 | Rabu   |
|     3 | Kamis  |
|     4 | Jumat  |
|     5 | Sabtu  |
|     6 | Minggu |

Informasi tersebut digunakan sebagai input bagi model Linear Regression.

---

## Exploratory Data Analysis

Sebelum membuat model, dilakukan analisis terhadap pola volume kendaraan.

Analisis yang dilakukan meliputi:

1. Rata-rata volume kendaraan berdasarkan jam.
2. Rata-rata volume kendaraan berdasarkan hari.
3. Visualisasi hubungan waktu dengan volume kendaraan.
4. Analisis korelasi variabel numerik.

Analisis ini dilakukan untuk mengetahui pola volume kendaraan berdasarkan waktu sebelum model Machine Learning dibuat.

---

## ✂️ Pembagian Data

Dataset dibagi menjadi dua bagian:

* **80% data training**
* **20% data testing**

Data training digunakan untuk melatih model Linear Regression, sedangkan data testing digunakan untuk menguji kemampuan model dalam melakukan prediksi terhadap data yang belum digunakan saat proses training.

Karena dataset memiliki urutan waktu, pembagian data dilakukan berdasarkan urutan data sehingga data masa sebelumnya digunakan untuk training dan data setelahnya digunakan untuk testing.

---

## Algoritma

### Linear Regression

Linear Regression merupakan algoritma Machine Learning yang digunakan untuk memodelkan hubungan antara variabel input dengan variabel target.

Dalam project ini, Linear Regression digunakan untuk mempelajari hubungan antara:

**Jam + Hari → Volume Kendaraan**

Input model:

* `hour`
* `day_of_week`

Target:

* `traffic_volume`

Model kemudian digunakan untuk menghasilkan prediksi volume kendaraan berdasarkan kombinasi jam dan hari tertentu.

---

## Evaluasi Model

Performa model Linear Regression dievaluasi menggunakan beberapa metrik, yaitu:

### MAE (Mean Absolute Error)

MAE digunakan untuk mengetahui rata-rata selisih absolut antara nilai aktual dan nilai hasil prediksi.

### MSE (Mean Squared Error)

MSE menghitung rata-rata kuadrat kesalahan antara nilai aktual dan hasil prediksi.

### RMSE (Root Mean Squared Error)

RMSE merupakan akar dari MSE dan digunakan untuk mengetahui besarnya kesalahan prediksi dalam satuan yang sama dengan target.

### R² Score

R² Score digunakan untuk mengetahui seberapa besar variasi pada volume kendaraan dapat dijelaskan oleh fitur yang digunakan dalam model.

---

## Prediksi Data Baru

Setelah model selesai dilatih, dilakukan simulasi menggunakan data baru.

Contohnya adalah melakukan prediksi volume kendaraan pada:

* **Hari:** Senin
* **Jam:** 17.00

Model menerima informasi jam dan hari tersebut sebagai input dan menghasilkan estimasi volume kendaraan.

Simulasi ini menunjukkan bagaimana model dapat digunakan untuk melakukan prediksi pada kondisi waktu tertentu.

---

## Kaitan dengan SDG 11

Project ini berkaitan dengan **SDG 11: Sustainable Cities and Communities**, khususnya pada aspek transportasi perkotaan.

Prediksi volume kendaraan dapat memberikan informasi mengenai pola lalu lintas berdasarkan waktu. Informasi tersebut dapat menjadi salah satu bahan pendukung dalam memahami kondisi lalu lintas dan perencanaan transportasi.

Dengan memanfaatkan Machine Learning, data historis lalu lintas dapat diolah menjadi informasi prediktif yang dapat membantu proses pengambilan keputusan terkait transportasi perkotaan.

Namun, hasil prediksi dalam project ini merupakan **informasi pendukung**, bukan satu-satunya dasar dalam menentukan kebijakan transportasi.

---

## Kesimpulan

Project ini menerapkan algoritma **Linear Regression** untuk memprediksi volume kendaraan berdasarkan informasi **jam dan hari** menggunakan dataset **Metro Interstate Traffic Volume**.

Data `date_time` diolah untuk memperoleh fitur `hour` dan `day_of_week`, sedangkan `traffic_volume` digunakan sebagai target prediksi.

Model kemudian dilatih menggunakan data training dan diuji menggunakan data testing. Performa model dievaluasi menggunakan **MAE, MSE, RMSE, dan R² Score**.

Hasil prediksi dapat digunakan sebagai informasi pendukung untuk memahami pola volume kendaraan berdasarkan waktu. Pemanfaatan informasi tersebut berkaitan dengan upaya mendukung **transportasi perkotaan yang lebih berkelanjutan** sebagai bagian dari **SDG 11**.

---

## Teknologi yang Digunakan

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Joblib

---

## File Project

`Project_SD G11_Traffic_Volume_Linear_Regression.ipynb` merupakan notebook Google Colab yang berisi proses:

* Pengolahan dataset
* Exploratory Data Analysis
* Preprocessing
* Pembentukan fitur
* Training Linear Regression
* Prediksi
* Evaluasi model
* Simulasi prediksi data baru
* Visualisasi hasil
