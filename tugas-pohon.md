# Tugas Decission Tree

## Eksplorasi Dataset

Data yang digunakan pada tugas ini adalah Data Play Tennis. Dataset Play Tennis digunakan untuk memprediksi apakah suatu kondisi cuaca memungkinkan untuk bermain tenis atau tidak.

Jumlah Data : 14 

Jumlah Atribut : 5 Atribut (4 identifier dan 1 class/target)

## Implementasi Pada Knime

Workflow ini dirancang menggunakan tools KNIME untuk membangun model klasifikasi Decision Tree. Tujuannya untuk memprediksi apakah seseorang akan bermain tenis atau tidak berdasarkan kondisi cuaca (Outlook, Temperature, Humidity, dan Windy).

Berikut merupakan nodes yang diimplementasikan:

![Foto Saya](img/pohon1.png)

### 1. Excel Reader

Pada nodes ini digunakan untuk mengimpor file dataset **"Play Tennis"** yang berisi 14 data.

![Foto Saya](img/pohon2.png)

### 2. Tabel Partitioner

Pada nodes partitioner ini digunakan untuk mempartisi berapa banyak data untuk training dan testing. Pada tugas ini, partisi dibuat 90% data training dan 10% untuk data testing. Jadi jumlah data yang di training ada 12 data dan untuk testing ada 2 data.

Data Training (80%):

![Foto Saya](img/pohon3.png)

Data Testing (20%):

![Foto Saya](img/pohon4.png)

### 3. Color Manager

Pada nodes ini digunakan untuk memberikan pengaturan warna yang berbeda pada atribut kelas/target.  Bertujuan untuk mempermudah visualisasi pengelompokan data pada tahapan selanjutnya.

![Foto Saya](img/pohon5.png)

### 4. Color Appender

Pada nodes ini digunakan untuk meneruskan dan menerapkan skema warna yang telah dibuat di Color Manager ke dalam sekumpulan data testing. Visualisasi ini supaya data tetap konsisten antara data training dan data testing.

![Foto Saya](img/pohon6.png)

### 5. Decission Tree Learner

Pada nodes ini digunakan untuk membangun dan melatih (training) model pohon keputusan menggunakan 12 data training yang telah dipartisi. Model akan mempelajari pola dan aturan dari atribut kondisi cuaca untuk menentukan target klasifikasinya.

Pada nodes ini diatur:
- quality measure : Gain ratio

- Prunning Method : No Prunning

- Mencentang Reduced error prunning supaya tidak di pangkas

- Minimum number of records per node  di berikan nilai 1 supaya node yang memiliki nilai lebih dari 1 ditampilkan

- Force root split column di atur kolom Outlook untuk dijadikan sebagai akar

![Foto Saya](img/pohon7.png)

### 6. Decission Tree Predictor

Pada nodes ini digunakan untuk menguji kemampuan model tersebut. Node ini akan menerapkan aturan logika yang telah dipelajari ke dalam 2 data testing untuk memprediksi apakah hasilnya "Yes" atau "No".

Berikut merupakan hasil prediksinya:

![Foto Saya](img/pohon8.png)

### 7. Model Writer

Pada nodes ini digunakan untuk menyimpan model klasifikasi Decision Tree yang sudah jadi ke dalam bentuk file. Tujuannya adalah agar model yang sudah pintar ini dapat langsung digunakan kembali di lain waktu tanpa harus memproses atau melatih ulang data dari awal.

![Foto Saya](img/pohon9.png)

### 8. Scorer

Confusion Matriks

![Foto Saya](img/pohon10.png)

Acuracy 

![Foto Saya](img/pohon11.png)

### 9. Decission Tree View

Pada nodes ini digunakan untuk menampilkan hasil dari model secara visual dalam bentuk struktur pohon keputusan (tree diagram). Dari node ini, kita dapat melihat dengan jelas alur logika (aturan Jika-Maka) yang dibentuk oleh sistem berdasarkan dataset Play Tennis.

![Foto Saya](img/pohon12.png)