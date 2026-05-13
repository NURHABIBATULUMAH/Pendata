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

Pada nodes ini digunakan untuk mengimpor file dataset **"Play Tennis"** yang berisi 14 data. Node ini digunakan untuk membaca dataset yang berasal dari file Excel agar data dapat dimasukkan ke dalam KNIME. Setelah file berhasil dibaca, seluruh isi tabel akan tampil dan siap digunakan pada tahap selanjutnya. 

![Foto Saya](img/random2.png)

### 2. Tabel Partitioner

Setelah data berhasil dibaca, maka dilanjutkan proses pada node **Table Partitioner**. Node ini digunakan untuk membagi dataset menjadi dua bagian, yaitu data training dan data testing. Pada workflow ini 70% untuk data training dan 30% untuk data testing. Pembagian ini bertujuan agar model dapat belajar menggunakan sebagian data, kemudian diuji menggunakan data lain yang belum pernah dipelajari sebelumnya.

Data Training (70%):

![Foto Saya](img/random3.png)

Data Testing (30%):

![Foto Saya](img/random4.png)


### 3. Random Forest Learner

Selanjutnya menggunakan node **Random Forest Learner**. Node ini berfungsi untuk melatih model Random Forest menggunakan data training. Pada proses ini sistem membangun banyak pohon keputusan berdasarkan data training. 

Setiap pohon dibuat menggunakan kombinasi data dan atribut yang dipilih secara acak sehingga model menjadi lebih stabil. Pada workflow ini menggunakan metode **Information Gain Ratio** sebagai dasar dalam menentukan pemisahan data pada setiap pohon keputusan. Pada tahap ini menghasilkan model Random Forest yang sudah siap digunakan untuk melakukan prediksi.

![Foto Saya](img/random5.png)

### 4. Random Forest Predictor

Node selanjutnya yaitu **Random Forest Predictor**. Node ini menerima dua input, yaitu model Random Forest dari proses training dan testing dari Table Partitioner. Kemudia akan melakukan prediksi terhadap data testing berdasarkan pola yang telah dipelajari sebelumnya. Hasil dari node ini berupa tabel yang berisi data asli beserta hasil prediksi yang dihasilkan oleh model Random Forest.

![Foto Saya](img/random12.png)

### 5. Scorer

Node **Scorer** pada Random Forest Predictor. Node ini digunakan untuk mengevaluasi performa model klasifikasi. Proses evaluasi dilakukan dengan membandingkan nilai asli (*actual*) dengan hasil prediksi (*prediction*) yang dihasilkan model. 

Dari proses tersebut diperoleh informasi seperti nilai accuracy, precision, recall, serta confusion matrix. Nilai accuracy menunjukkan seberapa baik model dalam melakukan klasifikasi terhadap data testing.

Pemilihan kolom Actual dan Prediction:

![Foto Saya](img/random6.png)

Confusion Matriks:

![Foto Saya](img/random7.png)

Accuracy yang didapatkan:

![Foto Saya](img/random8.png)

### 6. Scorer

Selain digunakan untuk membentuk model klasifikasi, node Random Forest Learner juga menghasilkan data *Out-of-Bag* (OOB). Data tersebut kemudian dievaluasi menggunakan node Scorer yang terhubung langsung dari learner. 

Evaluasi ini digunakan untuk mengetahui performa awal model selama proses training tanpa menggunakan data testing. Namun, evaluasi utama tetap dilakukan pada hasil prediksi data testing menggunakan node Scorer setelah Random Forest Predictor.

Pemilihan kolom aktual dan prediksi: 

![Foto Saya](img/random9.png)

Confusion Matrik:

![Foto Saya](img/random10.png)

Accuracy yang didapatkan: 

![Foto Saya](img/random11.png)

