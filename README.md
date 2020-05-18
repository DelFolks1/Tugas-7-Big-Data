<h1> Tugas 7 Big Data </h1>
Nama : Raja Permata Boy <br>
NRP : 05111740000070 <br>

<h1> Analisis kebutuhan listrik di Irlandia</h1>
Keseluruhan workflow :
<img src="/tugasbd7/workflow.jpg"><br>
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
<img src="/tugasbd7/dataprep.jpg"><br>
Pertama, kita akan menggunakan node File Reader untuk membaca Irish Energy Meter dataset. <br>
<img src="/tugasbd7/conffilereader.jpg"><br>
Lalu, kita buat spark local context menggunakan node Create Local Big Data Environment <br>
Lalu kita jalankan componen Load Data yang terdiri dari beberapa node : <br>
<img src="/tugasbd7/loaddata.jpg"><br>
Node DB Table Creator berfungsi untuk membuat demo table pada hive dan node DB Loader berfungsi untuk meload table yang sudah dibuat<br>
Hasil dari table yang sudah dibuat : <br>
<img src="/tugasbd7/dbloader.jpg"><br>
Lalu, selanjutnya dari metanode Load Data, ada node Hive To Spark yang mengubah hive menjadi spark. Beriku hasilnya :<br>
 <img src="/tugasbd7/hivetospark.jpg"><br>
  
