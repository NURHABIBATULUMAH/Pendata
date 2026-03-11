# Dataset Student Performance

Dataset yang digunakan dalam perhitungan jarak adalah Student Performance Dataset yang berisi informasi mengenai karakteristik siswa serta faktor-faktor yang mempengaruhi performa akademik mereka. Dataset ini digunakan untuk menganalisis perilaku belajar dan prestasi siswa.

Dataset ini memiliki berbagai atribut yang menggambarkan kondisi demografis, dukungan keluarga, serta kebiasaan belajar siswa. Namun, tidak semua atribut digunakan dalam perhitungan jarak ini. Untuk mempermudah proses analisis dan perhitungan jarak antar data, hanya beberapa atribut yang dipilih sebagai representasi dari beberapa tipe data.

Atribut yang digunakan dalam penelitian ini terdiri dari atribut numerik, ordinal, kategorikal, dan biner. Pemilihan atribut ini bertujuan untuk menunjukkan bagaimana metode perhitungan jarak dapat diterapkan pada data dengan tipe atribut yang berbeda.

Link Kaggle dari Dataset ini:
https://www.kaggle.com/datasets/uciml/student-alcohol-consumption


## Atribut Yang Digunakan

| Atribut   | Tipe Data   | Keterangan                        |
| --------- | ----------- | --------------------------------- |
| age       | Numerik     | Umur siswa                        |
| studytime | Ordinal     | Waktu belajar siswa (1–4)         |
| school    | Kategorikal | Sekolah siswa (GP atau MS)        |
| sex       | Biner       | Jenis kelamin siswa               |
| internet  | Biner       | Akses internet di rumah           |
| famsup    | Biner       | Dukungan pendidikan dari keluarga |
| G3        | Numerik     | Nilai akhir siswa                 |


Selanjutnya, data yang telah dipilih akan melalui tahap transformasi data sebelum dilakukan perhitungan jarak antar objek.

## Transformasi Data

### Data Numerik

Pada dataset ini atribut yang memiliki tipe data numerik adalah **age** dan **G3**. **age** merepresentasikan umur dari siswa dan **G3** merepresentasikan nilai akhir dari siswa. Berikut 10 data pertama dari atribut numerik.

![Foto Saya](img/numerik-student.png)

Sebelum menghitung jarak akan dilakukan normalisasi pada data bertipe numerik terlebih dahulu, supaya setiap atribut memiliki skala yang sebanding. Normalisasi akan dilakukan menggunakan Z-score.

![Foto Saya](img/z-score.png)

Keterangan :

$z_i$ : nilai hasil normalisasi data ke-$i$  

$x_i$ : nilai data ke-$i$  

$\mu$ : mean (rata-rata) dari atribut  

$\sigma$ : standard deviation dari atribut

#### age

Normalisasi age menggunakan z-score, sebagai berikut:

**Mean**

$\mu = \frac{1}{n}\sum_{i=1}^{n} x_i$

Dari perhitungan yang telah dilakukan pada atribut age yang memiliki jumlah data 395 diperoleh mean $16.70$

**Standart Deviasi**

$\sigma = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(x_i-\mu)^2}$

Dari perhitungan standart deviasi yang telah dilakukan pada atribut age, mendapatkan nilai $1.27$

#### Normalisasi atribut age:

**Data 1**

$x_1 = 18$

$\mu = 16.70$

$\sigma = 1.27$

$$z = \frac{x-\mu}{\sigma}$$

$$z = \frac{18-16.7}{1.27}$$

$$z = \frac{1.3}{1.27}$$

$$z = 1.02$$

**Data 2**

$x_2 = 17$

$\mu = 16.70$

$\sigma = 1.27$

$$z = \frac{x-\mu}{\sigma}$$

$$z = \frac{17-16.7}{1.27}$$

$$z = \frac{0.3}{1.27}$$

$$z = 0.23$$

#### Perhitungan Jarak Atribut age

$$d(x,y) = \sqrt{(x_1 - y_1)^2 +(x_i - y_i)^2}$$

$$d(1,2) = \sqrt{(1.02 - 0.23)^2}$$

$$d(1,2) = \sqrt{(0.79)^2}$$

$$d(1,2) = \sqrt{0.6241}$$

$$d(1,2) = {0.79}$$

#### G3

Normalisasi G3 menggunakan z-score, sebagai berikut:

**Mean**

$\mu = \frac{1}{n}\sum_{i=1}^{n} x_i$

Dari perhitungan yang telah dilakukan pada atribut G3 yang memiliki jumlah data 395 diperoleh mean $10.42$

**Standart Deviasi**

$\sigma = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(x_i-\mu)^2}$

Dari perhitungan standart deviasi yang telah dilakukan pada atribut age, mendapatkan nilai $4.58$

Setelah diperoleh nilai mean dan standart deviasi pada atribut age dan G3, langkah selanjutnya akan dilakukan normalisasi pada beberapa data age dan G3 menggunakan metode z-score.


#### Normalisasi atribut G3:

**Data 1**

$x_1 = 6$

$\mu = 10.42$

$\sigma = 4.58$

$$z = \frac{x-\mu}{\sigma}$$

$$z = \frac{6 - 10.42}{4.58}$$

$$z = \frac{-4.42}{4.58}$$

$$z = -0.96$$

**Data 2**

$x_2 = 6$

$\mu = 10.42$

$\sigma = 4.58$

$$z = \frac{x-\mu}{\sigma}$$

$$z = \frac{6 - 10.42}{4.58}$$

$$z = \frac{-4.42}{4.58}$$

$$z = -0.96$$

#### Perhitungan Jarak Atribut G3

$$d(x,y) = \sqrt{(x_1 - y_1)^2 +(x_i - y_i)^2}$$

$$d(1,2) = \sqrt{((-0.96) - (-0.96))^2}$$

$$d(1,2) = \sqrt{(0)^2}$$

$$d(1,2) = {0}$$

#### Hasil Normalisasi :

| Data   | Age | Z-score Age | G3 | Z-score G3 |
| ------ | --- | ----------- | -- | ---------- |
| Data 1 | 18  | 1.02        | 6  | -0.96      |
| Data 2 | 17  | 0.23        | 6  | -0.96      |

### Data Ordinal

Atribut ordinal adalah atribut yang memiliki tingkatan atau urutan, sehingga nilainya dapat dibandingkan berdasarkan tingkatannya. Pada dataset Student Performance, atribut yang bersifat ordinal adalah **Studytime**.

$$z_{if} = \frac{r_{if}-1}{M_f-1}$$

Keterangan :

$r_{if}$ : ranking dari nilai ordinal

$M_f$ : jumlah kategori pada atribut ordinal

$z_{if}$ : nilai hasil transformasi

Untuk $r_{if}$ adalah menggantikan $x_{if}$ yaitu nilai atribut ke $f$ pada data ke $i$.

Pada atribut **Studytime** ini memiliki 4 tingkatan, yaitu 1 - 4.

####  Perhitungan Atribut Ordinal

Pada dataset Student Performance atribut Studytime untuk data ke 1 - data ke 3 memiliki nilai yang sama yaitu $2$, jadi untuk contoh perhitungan ini akan menggunakan data yang berbeda.

**Data 1**

$r_{if} =2$ 

$M_{if} =4$ 

$$z_{1} = \frac{r_{if}-1}{M_f-1}$$

$$z_{1} = \frac{2-1}{4-1}$$

$$z_{1} = \frac{1}{3}$$

$$z_{1} = 0.33$$

**Data 2**

$r_{if} =2$ 

$M_{if} =4$ 

$$z_{2} = \frac{r_{if}-1}{M_f-1}$$

$$z_{2} = \frac{2-1}{4-1}$$

$$z_{2} = \frac{1}{3}$$

$$z_{2} = 0.33$$

**Hasil Perhitungan:**

| Data   | (r_{if}) | (z_{if}) |
| ------ | -------- | -------- |
| Data 1 | 2        | 0.33     |
| Data 2 | 2        | 0.33     |

#### Perhitungan Jarak Atribut Ordinal

$$d(x,y) = \sqrt{(x_1 - y_1)^2 +(x_i - y_i)^2}$$

$$d(1,2) = \sqrt{(0.33 - 0.33)^2}$$

$$d(1,2) = \sqrt{(0)^2}$$

$$d(1,2) = {0}$$

### Data Kategorical

Pada atribut **school** memiliki tipe data kategorical, dan ini akan dihitung menggunakan simple matching.

$$
d(i,j) = \frac{p-m}{p}
$$

Keterangan:

$d(i,j)$ = jarak antara objek $i$ dan $j$

$p$ = jumlah atribut nominal yang dibandingkan

$m$ = jumlah atribut yang nilainya sama (matching)

Karena kita hanya menggunakan 1 atribut yaitu school, maka $p = 1$.

Untuk atribut school data ke 1 - data ke 349 memiliki kategori $GP$, jadi untuk memperhitungkan supaya hasilnya beda nanti juga akan memperhitungkan dengan data ke 350.

#### Perhitungan Atribut Kategorical:

#### Perhitungan Jarak Data 1 dan Data 2

school sama (**GP = GP**)

$m = 1$

$p = 1$

$$d(1,2) = \frac{1-1}{1}$$

$$d(1,2) = \frac{0}{1}$$

$$d(1,2) = 0$$

Artinya **tidak ada perbedaan**

**Hasil Perhitungannya:**

| Pasangan Data     | School  | Jarak (d) | Interpretasi        |
| ----------------- | ------- | --------- | ------------------- |
| Data 1 & Data 2   | GP = GP | (0)       | Tidak ada perbedaan |

### Data Biner

Pada dataset Student Performance yang memiliki atribut bertipe data biner adalah **sex**, **famsup**, dan **internet**. Untuk atribut **sex** yang memiliki nilai **F/M** ini merupakan **symmetric binary**, atribut **famsup dan internet** yang memiliki nilai **yes/no** ini merupakan **asymmetric binary**.

Untuk menghitung jarak menggunakan rumus symmetric dan asymmetric harus dirubah menjadi encoding dulu ke 0/1.

**Encoding Data**

| Atribut  | Tipe       | Data Asli              | Encoding 0/1 |
| -------- | ---------- | ---------------------- | ------------ |
| Sex      | symmetric  | F = Data 1, M = Data 6 | F=1, M=0     |
| Famsup   | asymmetric | Yes / No               | Yes=1, No=0  |
| Internet | asymmetric | Yes / No               | Yes=1, No=0  |

Jarak untuk symmetric binary (perbedaan 0 sama pentingnya dengan 1) sedangkan Jarak untuk asymmetric binary (hanya 1 yang penting)

**Rumus perhitungan:**

![Foto Saya](img/rumus-biner.png)

| Kondisi | Arti                               |
| ------- | ---------------------------------- |
| **q**   | kedua data sama dan bernilai **1** |
| **r**   | data i =1 dan data j =0            |
| **s**   | data i =0 dan data j =1            |
| **t**   | kedua data sama dan bernilai **0** |

#### Perhitungan Atribut Biner

**Data 1**

Di sini akan dibandingkan data ke 1 dengan data ke 2

| Atribut  | Data 1 | Data 2 |
| -------- | ------ | ------ |
| Sex      | F      | F     |
| Famsup   | No    | Yes    |
| Internet | No    | Yes     |

**Data setelah konversi dengan encoding**

| Atribut  | Tipe       | Data 1 | Data 2 |
| -------- | ---------- | ------ | ------ |
| Sex      | symmetric  | 1      | 1      |
| Famsup   | asymmetric | 0      | 1      |
| Internet | asymmetric | 0      | 1      |

#### Perhitungan Symmetris (sex)

$$
d_{\text{sym}}(i,j) = \frac{r+s}{q+r+s+t}
$$

$$
d_{\text{sym}}(1,2) = \frac{0+0}{1+0+0+0}
$$

$$
d_{\text{sym}}(1,2) = \frac{0}{1}
$$

$$
d_{\text{sym}}(1,2) = 0
$$

Jadi, jarak Symmetris pada data ke 1 dan data ke 2 = $0$

#### Perhitungan Asymmetris (famsup dan internet)

$$
d_{\text{asym}}(1,2) = \frac{r+s}{q+r+s}
$$

$$
d_{\text{asym}}(1,2) = \frac{0+2}{0+0+2}
$$

$$
d_{\text{asym}}(1,2) = \frac{2}{2}
$$

$$
d_{\text{asym}}(1,2) = 1
$$

Jadi, jarak Asymmetris pada data ke 1 dan data ke 2 = $1$

## Perhitungan Jarak

Setelah seluruh atribut ditransformasikan ke dalam bentuk numerik, langkah selanjutnya adalah menghitung jarak antar data menggunakan Euclidean Distance. Metode ini digunakan untuk mengukur tingkat kemiripan antara dua objek berdasarkan seluruh atribut yang dimiliki.

Rumus Euclidean Distance :

$$
d(i,j) = \sqrt{\sum_{f=1}^{p}(x_{if}-x_{jf})^2}
$$

Keterangan :

$d(i,j)$ : jarak antara data ke-$i$ dan data ke-$j$

$x_{if}$ : nilai atribut ke-$f$ pada data ke-$i$

$x_{jf}$ : nilai atribut ke-$f$ pada data ke-$j$

$p$ : jumlah atribut

Perhitungan jarak dari setiap atribut pada data 1 dan data 2:

| Atribut   | Jarak |
| --------- | ----- |
| Age       | 0.79  |
| G3        | 0     |
| Studytime | 0     |
| School    | 0     |
| Sex       | 0     |
| Famsup    | 1     |
| Internet  | 1     |

Selanjutnya, subtitusikan ke rumus euclidean distance untuk mendapatkan jarak dari keseluruhannya

$$
d(1,2) = \sqrt{\sum_{f=1}^{p}(x_{if}-x_{jf})^2}
$$

$$
d(1,2) = \sqrt{(0.79)^2 + (0)^2 + (0)^2 + (0)^2 + (0)^2 + (1)^2 + (1)^2}
$$

$$
d(1,2) = \sqrt{(0.6241) + (0) + (0) + (0) + (0) + (1) + (1)}
$$

$$
d(1,2) = \sqrt{2.6241}
$$

$$
d(1,2) = 1.62
$$

Hasil akhir jarak Euclidean antara data 1 dan data 2 adalah sekitar $1.62$

## Implementasi Orange

Setelah dilakukannya perhitungan manual untuk menghitung jarak dari dataset Student Performance dari data 1 dan data 2, maka berikut implementasi dari orangenya.

![Foto Saya](img/orange.png)

Matriks Jaraknya diperoleh:

![Foto Saya](img/student-jarak.png)

Pada orange untuk matriks $d(1,2)$ diperoleh $1.617$ tetapi pada perhitungan manual kemarin mendapatkan nilai $1.62$ ini dikarenakan pada orange untuk atribut **studytime** yang bertipe data ordinal terhitung sebagai tipe data numerik, jadi dihitung normalisasi menggunakan z-score.