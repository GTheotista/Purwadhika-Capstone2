# **Supermarket Customers Analysis**

**Tools:** Python & Tableau<br>
**Visualizations:** Python(Matplotlib/Seaborn) & Tableau<br> 
**Dataset:** Supermarket Customers

**Table of Contents:**

- [**Supermarket Customers Analysis**](#Supermarket-Customers-Analysis)
- [**Langkah 0: Latar Belakang dan Masalah**](#Langkah-0-Latar-Belakang-dan-Masalah)
- [**Langkah 1: Data Cleaning and Understanding**](#Langkah-2-Data-Cleaning-and-Understanding)
- [**Langkah 2: Data Analysis**](#Langkah-2-Data-Analysis)
- [**Langkah 3: Kesimpulan dan Saran**](#Langkah-3-Kesimpulan-dan-Saran)
- [**Langkah 4: Visualisasi Tableau**](#Langkah-4-Visualisasi-Tableau)

---

# **Langkah 0: Latar Belakang dan Masalah**

---

## Latar Belakang

Perusahaan XYZ, yang bergerak di sektor ritel atau supermarket, dihadapkan pada tuntutan untuk memahami lebih dalam perilaku dan preferensi pelanggan. Dalam rangka meningkatkan strategi pemasaran, manajemen perusahaan perlu menggali wawasan dari data pelanggan yang dimilikinya. Data tersebut mencakup informasi demografis pelanggan, detail pembelian produk, respons terhadap kampanye pemasaran, dan keluhan pelanggan.

Dalam dunia ritel yang kompetitif, pemahaman mendalam terhadap pelanggan merupakan kunci untuk memberikan layanan yang lebih baik, meningkatkan penjualan, dan merumuskan strategi pemasaran yang lebih efektif. Dengan menganalisis data yang telah dikumpulkan, perusahaan dapat mengidentifikasi pola-pola tertentu, memahami kebutuhan pelanggan, dan mengambil langkah-langkah yang lebih tepat guna.

## Rumusan Masalah

Beberapa pertanyaan mendasar yang akan coba dipecahkan dalam project ini antara lain:

1. Bagaimana segmentasi pelanggan?
2. Bagaimana performa penjualan?
3. Bagaimana efektifitas campaign?
4. Bagaimana efektifitas website?
5. Bagaimana dengan komplain pelanggan?

Dengan merumuskan pertanyaan-pertanyaan ini, analisis data dapat memberikan pandangan yang holistik dan rekomendasi yang bermanfaat bagi perusahaan untuk meningkatkan layanan, merancang strategi pemasaran yang lebih efektif, dan menjaga kepuasan pelanggan.

---

# **Langkah 1: Data Cleaning and Understanding**

---

## Import & Understanding Data

Data yang diimport merupakan data yang ada pada respository: 

https://github.com/GTheotista/Purwadhika-Capstone2/blob/main/Supermarket%20Customers.csv

Data merupakan data supermarket customers yang berjumlah 2240 data yang diperkirakan data ini merupakan data di tahun 2013-2015. 

**Keterangan Kolom:**
1. ID: Identifikasi unik pelanggan.
2. Year_Birth: Tahun kelahiran pelanggan.
3. Education: Tingkat pendidikan pelanggan.
4. Marital_Status: Status pernikahan pelanggan.
5. Income: Pendapatan tahunan rumah tangga pelanggan.
6. Kidhome: Jumlah anak-anak dalam rumah tangga pelanggan.
7. Teenhome: Jumlah remaja dalam rumah tangga pelanggan.
8. Dt_Customer: Tanggal pendaftaran pelanggan dengan perusahaan.
9. Recency: Jumlah hari sejak pembelian terakhir oleh pelanggan.
10. Complain: 1 jika pelanggan mengajukan keluhan dalam 2 tahun terakhir, 0 sebaliknya.
11. MntWines: Jumlah uang yang dihabiskan untuk pembelian wine dalam 2 tahun terakhir.
12. MntFruits: Jumlah uang yang dihabiskan untuk pembelian buah-buahan dalam 2 tahun terakhir.
13. MntMeatProducts: Jumlah uang yang dihabiskan untuk pembelian produk meat dalam 2 tahun terakhir.
14. MntFishProducts: Jumlah uang yang dihabiskan untuk pembelian produk ikan dalam 2 tahun terakhir.
15. MntSweetProducts: Jumlah uang yang dihabiskan untuk pembelian produk kue-manis dalam 2 tahun terakhir.
16. MntGoldProds: Jumlah uang yang dihabiskan untuk pembelian produk gold dalam 2 tahun terakhir.
17. NumDealsPurchases: Jumlah pembelian yang dilakukan dengan diskon.
18. AcceptedCmp1 - AcceptedCmp5: 1 jika pelanggan menerima tawaran dalam kampanye ke-1 hingga ke-5, 0 sebaliknya.
19. Response: 1 jika pelanggan menerima tawaran dalam kampanye terakhir, 0 sebaliknya.
20. NumWebPurchases: Jumlah pembelian yang dilakukan melalui situs web perusahaan.
21. NumCatalogPurchases: Jumlah pembelian yang dilakukan menggunakan katalog.
22. NumStorePurchases: Jumlah pembelian yang dilakukan langsung di toko-toko perusahaan.
23. NumWebVisitsMonth: Jumlah kunjungan ke situs web perusahaan dalam sebulan terakhir.

## Data Cleaning

**Drop Kolom**

Melakukan drop kolom yang tidak sesuai dengan library yang menjelaskan tentang kolom apa saja yang ada.

**Mencari Duplikat**

Setelah melakukan pengecekan, tidak terdapat data yang duplikat.

**Mencari Data yang Kosong**

Setelah melakukan pengecekan, terdapat data yang kosong pada kolom 'Income'. Selanjutnya, melakukan analisa terhadap data yang memiliki nilai kosong pada kolom tersebut apakah layak dipertahankan dan diputuskan data akan dipertahankan.

**Mencari Nilai Unik dari Kolom Education**

Metode yang digunakan untuk mengisi nilai kosong pada kolom 'Income' mengisi dengan nilai rata rata dari masing masing kategori pendidikan (ini berdasarkan asumsi bahwa status pendidikan yang sama biasanya memiliki income yang tidak jauh berbeda). Karena data unik tidak ada yang aneh maka proses akan dilanjutkan.

**Imputation**

Setelah mengecek nilai unik dari kolom education, imputasi dilakukan dengan nilai rata rata dari masing masing kategori pendidikan.

**Feature Engineering: 'Age'**

Pada langkah ini dibuat fitur kolom baru yang merupakan kolom 'Age' yaitu umur seseorang menjadi costumer untuk pertama kalinya, karena diasumsikan lebih informatif dibanding kolom 'Year_Birth'. Selanjutnya dilakukan analisa mengenai fitur baru ini, ternyata data dicurigai memiliki outlier karena terdapat umur pelanggan yang berumur 121 tahun.

**Cek Outlier**

Beberapa fitur 'Age', 'Recency', 'Income' akan coba dilihat sebaran outlier dan menghilangkannya. Setelah melakukan analisa dengan boxplot, diketahui hanya 'Age' dan 'Income' yang perlu diremove outliernya

**Remove Outlier**

Dalam melakukan proses ini, digunakan aturan jarak Interquartile Range (IQR). Titik data yang berada di bawah Q1 – 1.5 IQR atau di atas Q3 + 1.5 IQR adalah outlier.

**Feature Engineering: 'Age_Labels'**

Pada langkah ini dibuat fitur kolom baru yang merupakan kolom 'Age_Labels' yaitu mengelompokan pelanggan berdasarkan umur dengan menggunakan refernsi ini: https://gaya.tempo.co/read/1724197/kategori-umur-balita-remaja-dan-dewasa-menurut-kemenkes-jangan-salah

**Mencari Nilai Unik dari Kolom 'Marital_Status'**

Melihat nilai unik pada kolom 'Marital_Status', apakah ada nilai yang aneh atau tidak. Setelah melakukan pengecekan, ternyata ada 'Marital_Status' yang tidak yang tidak relevan.

**Mengganti Data 'Marital_Status' yang Tidak Relevan**

Melanjutkan langkah sebelumnya, akibat di Indonesia tidak mengenal status "Alone", "Absurd", "Together" dan "YOLO" yang diasumsikan sama seperti "Single", kita akan merapikan data tersebut menjadi status "Single".

**Feature Engineering: 'Child_Status'**

Pada langkah ini dibuat fitur kolom baru yang merupakan kolom 'Child_Status' yang menunjukan bahwa customer memiliki anak / tidak yang didasarkan pada dua kolom yaitu kolom Kidhome dan Teenhome (kedua kolom ini menunjukan jumlah kid dan teen yang dimiliki pelanggan tersebut)

**Feature Engineering: 'Active_Cust'**

Pada langkah ini dibuat fitur kolom baru yang merupakan kolom 'Active_Cust'. Pada kolom ini pelanggan dikatakan aktif jika terakhir kali maksimal 60 hari melakukan pembelian, selebihnya dikatakan pasif. 

**Drop Kolom**

Akibat kolom-kolom seperti Kidhome, Teenhome, Year_Birth, Dt_Customer sudah dibuat menjadi feature baru, sehingga kita bisa drop semua kolom tersebut

## Cek and Save Clean Data

**Cek Clean Data**

Kita melakukan pengecekan terakhir apakah data perlu dirapikan lebih lanjut. 

**Save Clean Data**

Setelah mengecek data dan dilihat bahwa data telah rapi, maka kita save data. Data yang sudah bersih ada pada respository: 

https://github.com/GTheotista/Purwadhika-Capstone2/blob/main/CleanData_SupermarketCustomers.xlsx

---

# **Langkah 2: Data Analysis**

---

Pada bagian ini data yang sudah bersih dianalisis dengan beberapa teknik analisis berbeda. Teknik analisis yang digunakan antara lain:
1. Statistika deskriptif. 
2. Statistika inferensial.
3. Statistika deskriptif berupa graphical summary.

## Segmentasi Pelanggan

Beberapa pertanyaan yang berkaitan untuk mengenali dan memahami segmentasi pelanggan:

1. Berapakah jumlah total pelanggan yang tercatat? *
2. Bagaimanakah jumlah dan persentase pelanggan setiap kelompok? (Misalnya, kelompok umur, status pernikahan, dll.) *
3. Apakah distribusi umur pelanggan berdistribusi normal? **

## Performa Penjualan

Beberapa pertanyaan yang berkaitan untuk memahami performa penjualan:

1. Berapakah jumlah dan persentase pelanggan yang tergolong aktif / pasif? *
2. Berapakah jumlah serta rata-rata penjualan 2 tahun terakhir dan total pelanggan di masing masing komoditas? Manakah yang tertinggi? *
3. Apa preferensi pembelian produk untuk setiap kelompok pelanggan? (Misalnya, kelompok umur, status pernikahan, dll.) ***
4. Apakah terdapat korelasi positif/negatif antara income dan juga penjualan komoditas satu dengan yang lain? **
5. Apakah ada korelasi antara total penghasilan pelanggan dengan jumlah pembelian dengan diskon? **
6. Kelompok umur mana yang cenderung melakukan pembelian melalui market place Web, Catalog atau Store? ***
7. Berapakah rata-rata penjualan masing-masing market place? *
8. Apakah rata-rata pembelian antar market place yaitu Web, Catalog dan Store sama? **
9. Apakah ada korelasi antara pembelian dengan diskon dengan terakhir kali pelanggan melakukan pembelian? **

## Efektifitas Campaign

Beberapa pertanyaan yang berkaitan untuk memahami efektifitas campaign:

1. Jumlah pelanggan yang sukses mengikuti campaign 1 s/d terakhir? Manakah yang tertinggi? *
2. Bagaimana efektivitas campaign terakhir dibandingkan dengan campaign sebelumnya? **
3. Jumlah Customer yang sukses mengikuti campaign terakhir setiap kelompok umur? *
4. Apakah terdapat perbedaan proporsi kesuksesan campaign untuk masing-masing kategori umur pelanggan ('Adult', 'Pre-Senior', 'Senior')? **

## Efektifitas Website

Beberapa pertanyaan yang berkaitan untuk memahami efektifitas website:

1. Berapakah rata-rata seseorang berkunjung ke website (perbulan)? *
2. Berapakah rata-rata penjualan via website? *
3. Apakah ada korelasi antara frekuensi kunjungan situs web atau toko oleh pelanggan dengan jumlah pembelian produk via web? **
4. Berapakah rata-rata kunjungan website setiap kategori umur? *
5. Berapakah rata-rata dari total pembelian via website setiap kategori umur? *

## Komplain Pelanggan

Beberapa pertanyaan yang berkaitan untuk memahami komplain pelanggan:

1. Berapakah jumlah dan persentase pelanggan yang melakukan komplain? *
2. Kelompok mana yang cenderung melakukan komplain terkait pembelian? ***
3. Berapakah total pembelian setiap komoditas untuk konsumen yang melakukan komplain? *
4. Berapakah total pembelian setiap komoditas di semua kelompok umur yang melakukan komplain? *

<br>

**Keterangan Metode:**
1. Statistika deskriptif (*) 
2. Statistika inferensial (**) 
3. Statistika deskriptif berupa graphical summary (***) 

---

# **Langkah 3: Kesimpulan dan Saran**

## Kesimpulan
**Segmentasi Pelanggan:**
1. Total pelanggan tercatat: 2229.
2. Pelanggan terbanyak berada dalam kelompok umur "Adult", status pernikahan "Single", status pendidikan "Graduation", dan memiliki anak.
3. Pelanggan rendah berada dalam kelompok umur "Child" dan "Teenagers", status pernikahan "Widow", status pendidikan "Basic", dan tidak memiliki anak.
4. Distribusi umur pelanggan tidak berdistribusi normal.

**Performa Penjualan:**
1. 38,5% dari pelanggan tergolong pasif (lebih dari 2 bulan dari terakhir pembelian).
2. Rata-rata penjualan tertinggi untuk Wines, Meat, dan Gold (khusus untuk wines, rata-ratanya tertinggi dan hampir 2x lipat dibanding meat yang menempati urutan kedua). Pelanggan terbanyak melakukan pembelian pada kategori Wines, Meat, dan Gold.
3. Preferensi pembelian berbeda-beda untuk setiap kelompok pelanggan.
4. Teenagers adalah customer yang memiliki rata-rata pembelian tertinggi dari hampir seluruh komoditas selain Wines dan Gold (Emas) walaupun hanya 0.2% dari keseluruhan pelanggan.
5. Korelasi kuat dan positif antara pendapatan dan pembelian Wine serta Meat. Korelasi kuat dan positif antara pembelian Fruits, Meat, Fish, dan Sweet. Korelasi rendah antara pembelian komoditas selain Gold dengan Gold.
6. Tidak ada korelasi yang signifikan antara total penghasilan dan pembelian dengan diskon.

**Efektivitas Campaign:**
1. Jumlah pelanggan yang berhasil mengikuti campaign terakhir (334) lebih tinggi dibandingkan campaign sebelumnya.
2. Campaign terakhir jauh lebih berhasil dibandingkan dengan campaign sebelumnya.
3. Proporsi penerimaan campaign terakhir cukup seragam untuk kelompok umur kecuali pada kelompok 'Child' dan 'Teenagers'. Akan tetapi proporsi penerimaan campaign terakhir pada 'Teenagers' memiliki tingkat keberhasilan 50% dari total pelanggan 'Teenagers'.
4. Tidak terdapat perbedaan signifikan antara proporsi keberhasilan kampanye terakhir untuk kelompok umur 'Adult', 'Pre-Senior', dan 'Senior'.

**Efektivitas Website:**
1. Rata-rata pelanggan mengunjungi website sekitar 5 kali per bulan.
2. Rata-rata penjualan melalui website sekitar 4.1.
3. Rata-rata kunjungan website antar kategori umur tidak jauh berbeda yaitu di sekitar 5
4. Rata-rata dari total pembelian via website antar kategori umur tidak jauh berbeda yaitu di sekitar 4

**Komplain Pelanggan:**
1. Hanya 20 pelanggan (kurang dari 1%) yang melakukan komplain.
2. Kelompok usia yang lebih tua, status pernikahan single, status pendidikan graduation, dan status memiliki anak cenderung melakukan komplain.
3. Walaupun pelanggan yang melakukan komplain memiliki persentase yang kecil namun berpotensi menghilangkan pendapatan jika komplain tidak ditangani dengan benar.

## Saran
**Segmentasi Pelanggan:**
1. Fokus pada kelompok pelanggan terbanyak, yaitu yang berada dalam kelompok umur "Adult", status pernikahan "Single", status pendidikan "Graduation", dan memiliki anak.
2. Rancang strategi untuk meningkatkan kelompok pelanggan terendah, yaitu yang berada dalam kelompok umur "Child" dan "Teenagers", status pernikahan "Widow", status pendidikan "Basic", dan tidak memiliki anak.

**Performa Penjualan:**
1. Tingkatkan persediaan dan promosi untuk produk dengan rata-rata penjualan tertinggi, seperti Wines, Meat, dan Gold.
2. Merancang paket penawaran atau bundel produk yang menarik untuk meningkatkan penjualan lintas kategori seperti bundle Fruits, Meat, Fish, dan Sweet
3. Implementasikan program diskon atau poin loyalitas khusus untuk produk Fruits, Fish, dan Sweet

**Efektivitas Campaign:**
1. Lanjutkan campaign yang telah berhasil, terutama yang paling terkini.
2. Pertimbangkan untuk menyesuaikan jenis campaign atau penawaran berdasarkan preferensi dan perilaku belanja pelanggan.
3. Rancang campaign yang menyasar kepada kelompok pelanggan terendah, yaitu yang berada dalam kelompok umur "Child" dan "Teenagers", status pernikahan "Widow", status pendidikan "Basic", dan tidak memiliki anak.
4. Rancang campaign yang menyasar kepada kelompok pelanggan yang tergolong pasif.

**Efektivitas Website:**
1. Perkuat kehadiran online dengan memastikan situs web responsif, mudah dinavigasi, dan menawarkan pengalaman berbelanja yang menyenangkan.
2. Gunakan data kunjungan situs web dan pembelian online untuk merancang promosi atau rekomendasi produk yang sesuai.
3. Pertimbangkan untuk melibatkan pelanggan secara aktif melalui platform online, seperti survei kepuasan pelanggan atau ulasan produk.

**Komplain Pelanggan:**
1. Identifikasi dan tangani permasalahan yang cenderung menyebabkan keluhan pada kelompok pelanggan yang lebih tua, single, dan berpendidikan graduation.
2. Bangun hubungan komunikasi terbuka dengan pelanggan melalui saluran yang sesuai untuk memahami dan menyelesaikan keluhan dengan efektif.

---

# **Langkah 4: Visualisasi Tableau**

Berikut ini adalah link tableau project ini:  
https://public.tableau.com/app/profile/giovanny.theotista/viz/Capstone_2_GiovannyT/SupermarketCust?publish=yes

Berikut ini sekilas dari tampilan tableau project ini:  
![image](https://github.com/GTheotista/Purwadhika-Capstone2/assets/150938198/34006cd4-84a0-4909-9ab1-0109e399ae88)



