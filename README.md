<h1> Tugas 7 Big Data </h1>
Nama : Raja Permata Boy <br>
NRP : 05111740000070 <br>

<h1> Analisis kebutuhan listrik di Irlandia</h1>
Keseluruhan workflow :
<img src="/tugas7bd/workflow.jpg"><br>
<h2>Business Understanding</h2>
Dataset bisa digunakan untuk proses berikut :<br>
- Melakukan pengelompokan/kluster<br>
- Mencari informasi seperti total konsumsi energi dan sebagainya <br>

<h2> Data Understanding</h2>
Dataset yang digunakan adalah Irish Energy Meter. <br>
- Data set ini terdiri dari 3 kolom : <br> 
- meterID, merupakan integer ID untuk tiap meteran yang ada.<br>
- enc_datetime, sebuah integer yang berisi informasi waktu penggunaan.<br>
- reading, sebuah float yang berisi informasi penggunaan KWh pada meterID dan waktu tertentu.<br>

<h2>Data Preparation </h2>
<img src="/tugas7bd/dataprep.jpg"><br>
Pertama, kita akan menggunakan node File Reader untuk membaca Irish Energy Meter dataset. <br>
<img src="/tugas7bd/conffilereader.jpg"><br>
Lalu, kita buat spark local context menggunakan node Create Local Big Data Environment <br>
Lalu kita jalankan componen Load Data yang terdiri dari beberapa node : <br>
<img src="/tugas7bd/loaddata.jpg"><br>
Node DB Table Creator berfungsi untuk membuat demo table pada hive dan node DB Loader berfungsi untuk meload table yang sudah dibuat<br>
Hasil dari table yang sudah dibuat : <br>
<img src="/tugas7bd/dbloader.jpg"><br>
Lalu, selanjutnya dari metanode Load Data, ada node Hive To Spark yang mengubah hive menjadi spark. Beriku hasilnya :<br>
<img src="/tugas7bd/hivetospark.jpg"><br>
<h2>Modelling</h2>
<img src="/tugas7bd/modelling.jpg"><br>
Selanjutnya adalah proses modelling dalam CRISP-DM. Kita akan menjalankan metanode Extract date-time attributes. Berikut adalah isi dari metanode Extract date-time attributes : <br>
<img src="/tugas7bd/extractddate.jpg"><br>
Ada 4 proses. Yang pertama adalah konversi enc_datetime. Berikut konfigurasi Spark SQL Querynya : <br>
<img src="/tugas7bd/datetimeconversion.jpg"><br>
Hasil dari konversi date time:<br>
<img src="/tugas7bd/convresult.jpg"><br>
Dari proses sebelumnya didapatkan kolom eventDate, kita akan mengekstrak tahun, bulan, minggu, hari dan jam dengan Spark SQL Query yang kedua. Berikut konfigurasi SQL nya : <br>
<img src="/tugas7bd/extract.jpg"><br>
Berikut hasil ekstraksinya : <br>
<img src="/tugas7bd/extractresult.jpg"><br>
Selanjutnya, akan ada pengklasifikasian dari kolom dayOfWeek.Jika Saturday dan Sunday maka memiliki nilai 'WE', selain dari itu akan bernilai 'BD'. berikut adalah konfigurasi SQLnya:<br>
<img src="/tugas7bd/confday.jpg"><br>
Berikut hasilnya:<br>
<img src="/tugas7bd/dayresult.jpg"><br>
Yang terakhir adalah pembagian kolom jam, konfigurasi query sqlnya :<br>
<img src="/tugas7bd/hourconf.jpg"><br>
Hour akan dibuat menjadi daySegment dan memiliki 5 nilai. Berikut hasilnya:<br>
 <img src="/tugas7bd/hourresult.jpg"><br>
 Berikutnya akan masuk ke metanode Aggregation and time series. Berikut komponennya: <br>
  <img src="/tugas7bd/aggre1.jpg">
   <img src="/tugas7bd/aggre2.jpg"><br>
