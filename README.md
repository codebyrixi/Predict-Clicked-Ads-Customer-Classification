# Predict Customer Clicked Ads Classification by Using Machine Learning
Project ini merupakan project yang bertujuan untuk memprediksi jumlah klik suatu ads/iklan berdsasarkan klasifikasi pelanggannya. Project ini dibuat menggunakan bahasa pemrograman Python 

## Daftar Isi
- Jenis Pelanggan dan Analisis Perilaku pada Iklan
- Data Cleaning & Preprocessing
- Data Modelling
- Rekomendasi Bisnis & Simulasi

## Bagian 0: Pendahuluan
**Background**<br>
Sebuah perusahaan di Indonesia ingin mengetahui efektifitas sebuah iklan yang mereka tayangkan, hal ini penting bagi perusahaan agar dapat mengetahui seberapa besar ketercapainnya iklan yang dipasarkan sehingga dapat menarik pelanggan untuk melihat iklan.
Dengan mengolah data historis iklan tersebut serta menemukan insight dan pola yang terjadi, maka dapat membantu perusahaan dalam menentukan target pemsarannya. Case ini memfokuskan kepada pembuatan model machine learning classification yang berfungsi menentukan target pelanggan yang tepat.

**Goals**<br>
Membuat model machine learning yang dapat mendeteksi user yang berpotensi untuk tertarik pada sebuah iklan, sehingga perusahaan bisa mengoptimalkan cost dalam beriklan.

**Objective**<br>
- Memprediksi user yang memiliki potensi untuk melakukan klik pada iklan atau tidak dengan akurasi 90%
- Mendapatkan insight mengenai pola potensial user yang melakukan klik pada iklan
- Memberikan rekomendasi bisnis berdasarkan hasil analisis dan modelnya

**Business Metric**: Click-through rate

**Deskripsi Data**
| Feature | Description |
| :- | :- |
| Unnamed: 0 | ID Customers|
| Daily Time Spent on a Site | Time spent by the customers on a site in minutes. |
| Age  | Customer's age in years. |
| Area Income  | Average income of geographical area of costumers. |
| Daily Internet Usage | Time spent by customers on the internet in one day in minutes. |
| Male | Whether or not a constumer was male. |
| Timestamp | What time customers clicked on an Ad or the closed window. |
| Clicked on Ad  | 'No' or 'Yes' is indicated clicking on an Ad. |
| city | City of the costumers. |
| province | Province of the costumers. |
| category | Category of the advertisement. |

## Bagian 1: Jenis Pelanggan dan Analisis Perilaku pada Iklan
![image](https://github.com/user-attachments/assets/28d2304e-68bf-4364-8275-fe0b536965bc)
![image](https://github.com/user-attachments/assets/73cca69e-4781-4e12-b18d-86c5ab088228)<br>
Menurut analisis plot Daily Time Spent, orang yang jarang menghabiskan waktu di sebuah situs (kurang dari satu jam) memiliki kemungkinan yang lebih besar untuk melakukan klik pada iklan. Sementara itu, analisis penggunaan internet harian menunjukkan bahwa orang yang jarang menggunakan internet memiliki kemungkinan yang lebih besar untuk melakukan klik pada iklan dibandingkan dengan orang yang sering menggunakan internet. Kemudian, analisis usia menunjukkan bahwa pengguna yang lebih tua memiliki kemungkinan yang lebih besar untuk melakukan klik pada iklan.<br>
![image](https://github.com/user-attachments/assets/b478b5ea-7605-4480-aa05-9eaaf6c0934e)<br>
Pengguna dapat dibagi menjadi dua kelompok: pengguna aktif dan non-aktif, berdasarkan plot korelasi antara Daily Time Spent on Site dengan Internet Usage terhadap Target. Terlihat bahwa pengguna yang aktif cenderung menghabiskan lebih banyak waktu di situs web dan menggunakan internet lebih banyak secara keseluruhan. Namun menariknya, pengguna aktif biasanya tidak terlalu suka melakukan klik pada iklan.<br>
![image](https://github.com/user-attachments/assets/f3251acb-cadd-4435-8c03-59feef87b385)<br>
Berdasarkan analisis tentang bagaimana pengguna mengklik iklan pada hari-hari tertentu, Senin dan Jumat adalah hari-hari di mana jumlah klik iklan yang paling sedikit. Namun, Rabu adalah hari di mana jumlah klik iklan yang paling banyak.<br>
![image](https://github.com/user-attachments/assets/5de63a06-919d-4e0c-894e-aa7f21d1191e)<br>
Analisis berdasarkan waktu jam menunjukkan bahwa terdapat potensi pengguna untuk mengklik iklan dan memiliki konversi pembelian yang tinggi pada jam-jam tertentu, yaitu pukul 00.00, 09.00, 11.00, dan 18.00.

## Bagian 2: Data Cleaning & Preprocessing
Pada proses ini dilakukan pemrosesan data, yang terdiri dari:
1. Cleaning data
2. Penambahan feature baru
3. Feature encoding
4. Feature selection
5. Melakukan split pada data training dan data testing<br><br>

Sehingga didapatkan hasil sebagai berikut
 Tahapan  | Penyelesaian  
---|---
 Data Cleaning  | Melakukan handling pada missing value  
 Adding New Feature  | Melakukan ekstraksi feature `datetime` dan penambahan feature `pulau` 
 Feature Encoding  | Label encoding pada feature `Male` dan One hot encoding pada feature `pulau` dan `category` 
 Feature Selection  | Melakukan drop pada feature yang tidak dibutuhkan  
 Split Data  | Membagi data dengan perbandingan train:test = 70:30

## Bagian 3: Data Modelling
Pada bagian ini, akan dicari dan dibangun suatu model dengan keakurasian yang tinggi. Karena jumlah kategori pada target yang digunakan seimbang inilah, matriks akurasi akan digunakan. Percobaan di Eksperimen 1 akan menggunakan data train default, dan Percobaan 2 akan menggunakan standarisasi.

**Tabel 1: Eksperimen Tanpa Normalisasi**
|   | Model               | Accuracy | Precision | Recall   | F1       | Duration |
|---|---------------------|----------|-----------|----------|----------|----------|
| 4 | Random Forest       | 0.960000 | 0.993056  | 0.928571 | 0.959732 | 0.200129 |
| 6 | Gradient Boosting   | 0.953333 | 0.986111  | 0.922078 | 0.953020 | 0.238536 |
| 8 | XGBoost             | 0.953333 | 0.979452  | 0.928571 | 0.953333 | 0.134795 |
| 9 | LGBM                | 0.950000 | 0.986014  | 0.915584 | 0.949495 | 0.130329 |
| 2 | Decision Tree       | 0.946667 | 0.966216  | 0.928571 | 0.947020 | 0.012987 |
| 5 | AdaBoost            | 0.940000 | 0.978873  | 0.902597 | 0.939189 | 0.102607 |
| 3 | SVC                 | 0.686667 | 0.800000  | 0.519481 | 0.629921 | 0.052675 |
| 1 | KNN                 | 0.650000 | 0.689922  | 0.577922 | 0.628975 | 0.025848 |
| 0 | Logistic Regression | 0.486667 | 0.000000  | 0.000000 | 0.000000 | 0.035244 |
| 7 | MLP                 | 0.486667 | 0.000000  | 0.000000 | 0.000000 | 0.104576 |

**Tabel 2: Eksperimen dengan Normalisasi**
|   | Model               | Accuracy | Precision | Recall   | F1       | Duration |
|---|---------------------|----------|-----------|----------|----------|----------|
| 4 | Random Forest       | 0.960000 | 0.986301  | 0.935065 | 0.960000 | 0.225412 |
| 8 | XGBoost             | 0.956667 | 0.979592  | 0.935065 | 0.956811 | 0.082322 |
| 3 | SVC                 | 0.953333 | 0.986111  | 0.922078 | 0.953020 | 0.045166 |
| 6 | Gradient Boosting   | 0.953333 | 0.979452  | 0.928571 | 0.953333 | 0.194056 |
| 7 | MLP                 | 0.953333 | 0.979452  | 0.928571 | 0.953333 | 0.928606 |
| 0 | Logistic Regression | 0.950000 | 0.972789  | 0.928571 | 0.950166 | 0.021258 |
| 9 | LGBM                | 0.950000 | 0.979310  | 0.922078 | 0.949833 | 0.163605 |
| 2 | Decision Tree       | 0.943333 | 0.959732  | 0.928571 | 0.943894 | 0.006328 |
| 5 | AdaBoost            | 0.936667 | 0.959184  | 0.915584 | 0.936877 | 0.104253 |
| 1 | KNN                 | 0.886667 | 0.968750  | 0.805195 | 0.879433 | 0.030646 |

Dapat dilihat pada tabel eksperimen 1 bahwa model tanpa standardisasi yang memiliki nilai akurasi tertinggi adalah Random Forest. Didapat pula bahwa algoritma lain yang juga memiliki akurasi yang tinggi adalah Gradient Boosting, XGBoost, dan LGBM degan nilai 95%. Sebaliknya, algoritma Logistic Regression dan MLP memiliki akurasi yang sangat rendah, hal tersebut dapat mengakibatkan hasil prediksi yang kurang bagus.

Sedangkan pada tabel eksperimen 2, terlihat bahwa model yang paling akurat ditunjukkan menggunakan standardisasi algoritma Random Forest. Selain itu, diperhatikan bahwa nilai akurasinya yang mencapai 96%, tidak berubah secara signifikan dari hasil eksperimen pertama. Untuk algoritma XBoost, Gradient Boosting, dan LGBM, nilai akurasi juga tidak berubah secara signifikan. Lalu untuk algoritma SVC dan Logistic Regression, standardisasi meningkatkan hasil akurasi secara signifikan.

![image](https://github.com/user-attachments/assets/6acf15fd-aeb7-4586-8a45-e7f01313c5bc)<br>
Berdasarkan evaluasi algoritma Random Forest dari confussion matrix terlihat bahwa model sangat baik memprediksi user yang melakukan klik pada iklan atau tidak dengan nilai kesalahan prediksi yang kecil.
- Terdapat 145 prediksi benar yang diklasifikasikan sebagai bukan klik iklan (True Negatives/TN).
- Terdapat 1 prediksi salah yang diklasifikasikan sebagai klik iklan padahal sebenarnya bukan (False Positives/FP).
- Terdapat 11 prediksi salah yang diklasifikasikan sebagai bukan klik iklan padahal sebenarnya adalah klik iklan (False Negatives/FN).
- Terdapat 143 prediksi benar yang diklasifikasikan sebagai klik iklan (True Positives/TP).

![image](https://github.com/user-attachments/assets/3b8461c3-e0aa-44eb-944b-4a4c2f865c1e)<br>
Dapat terlihat bahwa Daily Internet Usage, Daily Time Spent on Site, Area Income, dan Age merupakan fitur yang mempengaruhi prediksi klik pada iklan, seperti yang ditunjukkan dalam plot SHAP.<br>
Korelasi negatif antara Daily Internet Usage, Daily Time Spent on Site, dan Area Income menunjukkan bahwa pengguna yang tidak sering menggunakan internet dan memiliki pendapatan menengah kebawah memiliki kemungkinan lebih besar untuk mengklik iklan, yang ditunjukkan dengan warna merah di sebelah kiri. Namun, fitur Age menunjukkan korelasi positif. Artinya, semakin tua usia pengguna, semakin tinggi kemungkinan klik iklan.

## Bagian 4: Rekomendasi Bisnis & Simulasi
Beberapa hal yang dapat dilakukan yaitu sebagai berikut.

1. Perusahaan dapat mentargetkan iklan pada pengguna internet yang tidak aktif, yaitu mereka yang jarang menghabiskan waktu di situs web (kurang dari 1 jam) dan yang jarang menggunakan internet (kurang dari 2,5 jam setiap hari). Di antaranya yang dapat digunakan yaitu sebagai berikut.
  - Iklan harus singkat dan menarik karena pengguna non-aktif memiliki keterbatasan waktu.Pesan yang padat dan jelas dengan kata yang dipilih dengan benar dapat menarik perhatian mereka dalam waktu singkat.
  - Gunakan teknik retargeting untuk tetap berhubungan dengan pengguna non-aktif. Tampilkan iklan yang relevan secara berulang kali di berbagai platform yang mereka kunjungi, seperti situs web, aplikasi, atau media sosial, setelah mereka mengklik iklan pertama. Ini dapat meningkatkan kesadaran pengguna.
2. Strategi pemasaran dan iklan perusahaan dapat disesuaikan dengan demografi usia >40 tahun. Beberapa strategi yang dapat digunakan termasuk:
  - Memfokuskan kampanye iklan yang berdampak atau relevan dengan kehidupan dan kebutuhan kelompok usia di atas 40 tahun.
  - Desain iklan harus sederhana dan mudah dibaca oleh kelompok usia di atas 40 tahun.
  - Kelompok usia di atas 40 tahun cenderung kurang terlibat dalam media sosial dibandingkan dengan kelompok usia yang lebih muda.
3. Strategi iklan dan pemasaran perusahaan dapat ditargetkan pada kelompok dengan pendapatan menengah kebawah (< 400 juta USD per tahun). Untuk mendorong pengguna untuk melaukukan klik pada iklan, dapat menggunakan strategi seperti memberikan iklan dengan harga terjangkau sesuai dengan anggaran pengguna dalam rentang waktu tertentu, seperti diskon khusus, bundel, ataupun promosi.
