# Klasifikasi Kematangan Buah Pisang: Mentah, Matang, dan Terlalu Matang/Busuk

Proyek ini adalah tugas besar untuk praktikum mata kuliah Pengolahan Citra Digital 2025. Project ini memiliki tujuan untuk membantu pekebun atau pengkonsumsi pisang agar dapat lebih cepat dan mudah dalam mengidentifikasi tingkat kematangan pisang, sehingga aktivitasnya menjadi lebih efisien.

## Tim Pengembang

Proyek ini dikembangkan oleh tim yang terdiri dari:
1. F1D02310061	JUAN JORDAN ANUGRAH
2. F1D02310087	PINKA DIMA CALISTA
3. F1D02310106	ARYA RAYAN UTAMA
4. F1D02310135	RENGGANIS CAHYA ANDINI

## Pendahuluan

Pisang itu salah satu buah paling sering dikonsumsi di Indonesia mulai dari anak-anak sampai orang tua suka makan pisang. Tapi masalahnya, pisang itu gampang banget berubah kualitas. misalnya hari ini masih hijau, dua hari lagi langsung matang, eh besoknya udah busuk. Nah, buat pengkonsumsi pisang, ini bikin bingung. Kadang mereka beli pisang, tapi belum tahu apakah udah matang sempurna, atau justru udah kelewat waktu makan. Padahal rasa, tekstur, dan bahkan nilai gizinya beda-beda tergantung tingkat kematangan.

Di sisi lain, buat pekebun atau pedagang pisang, penting untuk tahu kapan waktu yang pas untuk panen atau dijual, supaya nggak rugi karena pisangnya busuk di jalan atau malah dijual terlalu mentah. Dengan klasifikasi citra berdasarkan tampilan visual (warna kulit pisang, bintik, tekstur), sistem bisa bantu mengidentifikasi apakah pisang itu masih mentah, udah matang sempurna, atau mulai busuk. Nah, Teknologi ini bisa bantu pengambilan keputusan seperti kapan panen, kapan jual, dan kapan konsumsi. Simpel, tapi dampaknya besar untuk bisa ngurangin pisang yang dibuang sia-sia, bantu distribusi buah ke pasar dengan tepat, dan pastinya ningkatin kepuasan konsumen. Proyek ini menggunakan teknik pembelajaran mesin untuk menganalisis citra pisang dan mengklasifikasikannya ke dalam kategori berikut:
* Unripe (mentah)
* Ripe (Matang)
* Overripe/Rotten (Terlalu Matang/Busuk)

## Dataset

Dataset yang digunakan dalam proyek ini bersumber dari Kaggle:

* *Nama Dataset:* Banana Classification
* *Tautan:* [https://www.kaggle.com/datasets/atrithakar/banana-classification]
* *Deskripsi:* Dataset ini berisi kumpulan gambar pisang yang telah dikategorikan berdasarkan tingkat kematangan. 
* *Jumlah Gambar:* Sekitar 562+- gambar.
* *Jumlah Gambar Total Setelah Filter:* Sekitar 330 gambar.

## PreProcessing

V-channel HSV : proses ini berguna untuk mengonversi citra RGB menjadi channel V (Value) dari model HSV, yang mana mewakili kecerahan maksimum tiap piksel. Channel V digunakan untuk menekankan intensitas cahaya pisang sehingga memudahkan pemrosesan lanjutan.

Ekualisasi Histogram : proses ini berguna melakukan distribusi kecerahan pada channel V dengan metode histogram equalization. Tujuannya untuk meningkatkan kontras citra pisang sehingga ciri khas warna dari pisang lebih terlihat jelas.

konvolusi kernel sharpening : proses ini menerapkan operasi konvolusi pada citra dengan kernel sharpening (penajaman).. Proses ini membantu dalam menajamkan citra pisang agar dapat terlihat lebih jelas.

Gaussian blur : proses ini mengaburkan atau memblurkan citra menggunakan kernel Gaussian untuk mengurangi noise dan detail kecil. proses ini membuat fitur utama pisang (warna dan bentuk besar) lebih mudah dideteksi dalam klasifikasi.

Deteksi tepi Sobel : proses ini mendeteksi tepi pada citra dengan operator Sobel untuk menonjolkan batas antara area pixel yang berbeda. Deteksi tepi ini penting karena untuk memahami bentuk atau corak dari busuk pisang saat klasifikasi.

Contrast stretching : proses ini meningkatkan kontras citra dengan merentangkan nilai intensitas piksel dari minimum hingga maksimum (0-255). Proses ini mempermudah pengenalan warna dan tekstur pisang yang khas untuk setiap kelas.

## Akurasi

* Tanpa augmentasi dan tanpa preprocessing
Random Forest
![image](https://github.com/user-attachments/assets/f55f1f91-5bd7-44b8-8301-06208bb2a640)
SVM
![image](https://github.com/user-attachments/assets/4b278bb5-30ae-4d2f-bc10-52f2206ebb8e)
KNN
![image](https://github.com/user-attachments/assets/31514aa3-fba0-46f7-bac9-1ce65121f6fe)

* augmentasi dan preprocessing v-channel & ekualisasi histogram
Random Forest
![image](https://github.com/user-attachments/assets/369a85a6-58a8-415c-ba47-bf5da3b4e59c)
SVM
![image](https://github.com/user-attachments/assets/3767b744-d5a9-473d-bfe6-125f3c30a1f7)
KNN
![image](https://github.com/user-attachments/assets/c071fa4b-1311-4728-b905-e9e04802b700)

* augmentasi dan preprocessing v-channel & ekualisasi histogram & sharpening & gaussian blur
Random Forest
![image](https://github.com/user-attachments/assets/97dde717-0b53-41ed-81be-87a3c2894322)
SVM
![image](https://github.com/user-attachments/assets/5d624dfa-46be-424e-9f5e-bcf21e6aa8da)
KNN
![image](https://github.com/user-attachments/assets/637fd16f-e3a5-4e1b-bc0e-de10afa5f4c1)

* augmentasi dan preprocessing v-channel & ekualisasi histogram & deteksi tepi sobel & contrast stretching
Random Forest
![image](https://github.com/user-attachments/assets/610c569f-0a29-4dbd-9d04-1826a0c8c5b4)
SVM
![image](https://github.com/user-attachments/assets/82ff7f26-019f-4174-81b6-fbb21e105735)
KNN
![image](https://github.com/user-attachments/assets/e08501b1-afe1-4590-a2e5-7cfb71606109)

