Data Online Shoppers Purchasing Intention

Pada Dataset ini terdiri dari 12330 baris dan tidak memiliki missing values. Terdapat 4 jenis tipe data, yaitu integer, float, string, dan boolean. Tidak ada issue yang mecolok pada tiap kolom dan tipe datanya pada dataset ini.
Ketika ingin memilhat insight dari dataset ini, dibagi menjadi 2 kategori, yaitu Numerikal dan Kategorikal.
Untuk Data numerikal terdiri dari : 'Administrative', 'Administrative_Duration', 'Informational', 'Informational_Duration', 'ProductRelated', 'ProductRelated_Duration', 'BounceRates', 'ExitRates', 'PageValues', 'SpecialDay'.
Sedangkan untuk data Kategorikal terdiri dari :  'Month', 'OperatingSystems', 'Browser', 'Region', 'TrafficType', 'VisitorType', 'Weekend', 'Revenue'.
Ketika dilakukan proses statistik terhadap kategori numerikal, menghasilkan positive skewde(skew ke akanan) yang perlu dilakukan proses selanjutnya pada kolom-kolom tersebut.
Pada grafik Boxplot, terlihat jelas outlier yang sangat banyak dan jauh dari IQR sehingga perlu dilakukan proses handling outlier atau log conversion.
Apabila jika dilihat dari nilai maximum pada setiaap kolomnya, sebagian besar memiliki nilai yang sangat jauh dengan nilai medan atau mean.
Pada data kategorikal, juga dilakukan proses statistik. Pada data ini, ditemukan feature dengan unique value cukup banyak >5,
sehingga akan menjadi pertimbangan apakah digunakan (dengan diolah, dikelompokkan misalnya dengan range per kategori) atau diabaikan.
Pada dataset ini diambil Revenue sebagai targetnya.

Setelah dilakukan pengamatan pertama kali dari dataset tersebut, dilakukannya data cleansing untuk dataset ini.
Pada dataset ini, terdapat data duplicate sebesar 125 data. Jika dilakukannya drop dari dataset, maka terdapat lebih dari 1% dari jumlah total data yang dimiliki.
Maka dari itu, tidak dilakukannya drop data duplicated dengan asumsi bahwa data duplicated tersebut terjadi karena ada user yang secara tidak snegaja sama-sama melakukan hal yang sama dengan user lainnya (beda user).
Handling outliers dilakukan dengan menggunakan z-score apabila menggunakan IQR akan banyak baris yang akan terhapus. Jumlah outlier pada dataset ini sebesar 10683.
Untuk feature Untuk feature 'Administrative_Duration', 'Informational_Duration', 'ProductRelated','ProductRelated_Duration', 'BounceRates', 'ExitRates', 'PageValues' menggunakan log transformation menghasilkan distribusi yang mendekati normal.
Sedangkan untuk feature Administrative, Informational, dan Special Day menggunakan transformasi normalization dikarenakan jika menggunakan log-transformation hasil distribusi menjadi bimodal.
Pada penggunaan Log ditambahkan epsilon dikarenakan data yang didaptakan ketika melakukan log, minus infinite.
Pada dataset ini juga diperlukan feature encoding, karena ada data yang berbentuk kategorik dan ada beberapa data yang memiliki kardinalitas yang tinggi.
Untuk menangani data dengan kardinalitas yang tinggi digunakan fungsi agregasi sederhana dengan membiarkan instance memiliki nilai dengan frekuensi tinggi aoa adanya dan diganti dengan instance lain dengan kategori baru yang akan disebut sebagai other(0).
Langkahnya sebagai berikut:
  1. Pilih ambang batas (pada data kami menggunakan 75%).
  2. Urutkan nilai unik di kolom berdasarkan frekuensinya dalam urutan
    menurun.
  3. Terus tambahkan frekuensi nilai unik yang diurutkan secara menurun ini
    hingga mendpaatkan nilai ambang tercapai.
  4. Hasil kategori unik pada proses 2 & 3 yang akan disimpan dan contoh dari
    semua katogorik lainnya akan diganti dengan 0.

Setelah melakukan data preprocessing, dilakukan feature selection. Pada dataset ini, diambil threshold sebesar 0.1
Kolom yang akan dipertahankan adalah:
  • Log Product Related
  • Log product Related Duration
  • Log Bounce Rates
  • Log Exit Rates
  • Log PageValues
  • Administrative norm
  • Agg month nov
