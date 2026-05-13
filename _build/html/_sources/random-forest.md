# Tugas Random Forest dan Classifier

## Analisis Prediksi "Play Tennis" Menggunakan Random Forest di KNIME

## Apa itu Random Forest?

Random Forest adalah algoritma pembelajaran mesin (machine learning) yang termasuk dalam kategori Ensemble Learning. Pada Random Forest ini hanya mengandalkan satu pohon keputusan (Decision Tree), Random Forest membangun banyak pohon secara acak dan menggabungkan hasilnya (biasanya melalui voting untuk klasifikasi) untuk mendapatkan prediksi yang lebih akurat dan stabil.

## Model Classifier

Pada data  **Play Tennis** klasifikasi yang digunakan ada pada atribut class/target yaitu **Play Tennis** yang nilainya berupa (yes atau no)

## Implementasi Pada Knime

Untuk mengetahui model classifier dan random forest, digunakan tools knime untuk perhitungannya. 

Berikut workflow dari knime yang digunakan:

![Foto Saya](img/random1.png)

### 1. Excel Reader

Pada nodes ini digunakan untuk mengimpor file dataset **"Play Tennis"** yang berisi 14 data.

![Foto Saya](img/random2.png)

### 2. Tabel Partitioner

Pada nodes partitioner ini digunakan untuk mempartisi berapa banyak data untuk training dan testing. Pada tugas ini, partisi dibuat 70% data training dan 30% untuk data testing. Jadi jumlah data yang di training ada 9 data dan untuk testing ada 5 data.

Data Training (70%):

![Foto Saya](img/random3.png)

Data Testing (30%):

![Foto Saya](img/random4.png)


### 3. Random Forest Learner
