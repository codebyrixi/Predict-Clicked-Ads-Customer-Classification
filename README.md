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
5. Melakukan split pada data training dan data testing
Hasilnya tertera pada tabel dibawah.<br>
| Tahapan            | Penyelesaian                                                                                      |
|--------------------|---------------------------------------------------------------------------------------------------|
| Data Cleaning      | Melakukan handling pada missing value                                                             |
| Adding New Feature | 1. Melakukan ekstraksi feature `datetime`<br> 2. Penambahan feature `pulau`                       |
| Feature Encoding   | 1. Label encoding pada feature `male`<br> 2. One hot encoding pada feature `pulau` dan `category` |
| Feature Selection  | Melakukan drop pada feature yang tidak dibutuhkan                                                 |
| Split Data         | Membagi data dengan perbandingan train:test = 70:30                                               |
