## Dokumentasi Praktek ETL menggunakan KNIME

### Business Understanding
Kemungkinan proses yang dapat dilakukan pada data ini:
1. Dari data tersebut, dapat didapatkan platform game yang paling banyak memiliki game dengan penjualan lebih dari 100.000 copy
2. Dari data tersebut, dapat didapatkan perusahaan publisher yang paling banyak memiliki game dengan penjualan lebih dari 100.000 copy
3. Dari data tersebut, dapat didapatkan genre game yang paling banyak memiliki game dengan penjualan lebih dari 100.000 copy

### Data Understanding
* Dataset ini merupakan data penjualan dari game-game berbagai platform dari tahun 1980 hingga 2016
* Dataset ini terdiri dari 11 kolom yaitu:
  1. Rank - Ranking dari penjualan secara keseluruhan
  2. Name - Nama game
  3. Platform - Platform game tersebut dimainkan (Contoh: PS4, PC)
  4. Year - Tahun game tersebut dirilis
  5. Genre - Genre dari game
  6. Publisher - Publisher dari game
  7. NA_Sales - Angka penjualan di Amerika Utara (dalam juta)
  8. EU_Sales - Angka penjualan di Eropa (dalam juta)
  9. JP_Sales - Angka penjualan di Jepang (dalam juta)
  10. Other_Sales - Angka penjualan di wilayah selain ke tiga wilayah di atas pada seluruh dunia (dalam juta)
  11. Global_Sales - Angka penjualan global (dalam juta)
  
### Data Preparation
* Dataset awal
![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/dataset-awal.PNG)
Dataset di atas akan disimpan dalam bentuk CSV yang selanjutnya akan dibagi menjadi 2 bagian

* Pemisahan Dataset
Pemisahan dataset pada tugas ini dilakukan dengan KNIME dengan langkah-langkah berikut
  1. Pembacaan file CSV dataset</br>
  Pembacaan file CSV dilakukan dengan menggunakan csv reader</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/csv-reader.PNG)</br>
  Saat melakukan konfigurasi pembacaan CSV, dilakukan pengaturan sebagai berikut</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/add-file-csv.PNG)</br>
  Pada pengaturan tersebut, artinya menerangkan bahwa dataset memiliki baris judul, dan kolom "Rank" akan dianggap sebagai RowId pada KNIME sehingga dibutuhkan duplikasi kolom Rank pada tahap selanjutnya.</br>
  Hasil dari pembacaan file CSV dataset awal sebagai berikut:<br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/tabel-read.PNG)</br>
  
  2. Duplikasi kolom "Rank"</br>
  Karena saat import CSV kolom "Rank" dianggap sebagai RowId, padahal kolom "Rank" memiliki nilai berbeda dengan RowId, sehingga kolom "Rank" butuh untuk dibuat lagi dengan mengambil nilai dari kolom RowId. Pada bagian ini akan menggunakan fungsi "RowId" seperti gambar di bawah.</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/row-id.PNG)</br>
  Node tersebut digabungkan pada node CSV reader sebelumnya, dengan konfigurasi seperti berikut:</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/add-rowid.PNG)</br>
  Arti dari pengaturan di atas adalah, akan dibuat sebuah kolom baru dengan nama "Rank" dengan mengambil nilai dari kolom RowId. Hasil dari penambahan kolom dapat dilihat pada gambar di bawah.</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/tabel-rowid.PNG)</br>
  
  3. Membagi kolom-kolom tersebut menjadi dua bagian</br>
  Bagian ini dilakukan dengan menggunakan node "Column Splitter"</br>
  ![image](https://github.com/dewisekar/BigData_Tugas1/blob/master/images/split/column-splitter.PNG)</br>
  
  
  
  

### Modeling
### Evaluation
### Deployment
