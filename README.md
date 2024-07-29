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
![image](https://github.com/user-attachments/assets/73cca69e-4781-4e12-b18d-86c5ab088228)

