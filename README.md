# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[I MADE SURYA DARMA KRISNA]`
- **NIM:** `[2515091038]`
- **Program Studi:** `[SISTEM INFORMASI]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_startup_saas.csv` yang berisi infomasi tentang `File data_startup_saas.csv berisi data beberapa startup yang bergerak di bidang SaaS. Data yang ditampilkan meliputi nama startup, jenis layanan yang ditawarkan, pendapatan tahunan, biaya langganan, nilai pelanggan, serta tingkat churn pelanggan. Data ini digunakan untuk membantu analisis statistik, seperti membandingkan pendapatan antar layanan dan melihat tingkat keberlanjutan pelanggan pada setiap startup.`. Variabel kunci dalam dataset ini meliputi `pendapatan_Tahunan_Miliar_IDR`, `Biaya_Akuisisi_Pelanggan_Juta_IDR`, dan `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `pendapatan_Tahunan_Miliar_IDR` dan `Biaya_Akuisisi_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...
  - Mean = 31.88"
  - Median =  31.3"
  - Modus = 1.87"
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Jawab : Nilai mean sebesar 31,88 menunjukkan rata-rata dari seluruh data yang ada. Median 31,3 berarti posisi tengah data berada di angka tersebut, sehingga setengah data nilainya di bawah 31,3 dan setengahnya lagi di atas. Sementara itu, modus 1,87 adalah nilai yang paling sering muncul. Dari perbedaan nilai mean, median, dan modus ini dapat dilihat bahwa penyebaran data tidak sepenuhnya merata dan kemungkinan ada beberapa data yang nilainya cukup jauh dari yang lain.

- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Standar Deviasi = 19.79"
  - Range   = 1 - 66.89"
  - Kuartil = Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
              1.00   14.31   31.30   31.88   49.04   66.89 
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
  - Jawab : Nilai standar deviasi sebesar 19,79 menunjukkan bahwa data cukup menyebar dari nilai rata-ratanya. Range dari 1 hingga 66,89 menandakan selisih antara nilai terendah dan tertinggi cukup besar, sehingga variasi datanya tergolong tinggi. Berdasarkan nilai kuartil, terlihat bahwa sebagian besar data berada di rentang 14,31 hingga 49,04, dengan median di sekitar 31,30. Hal ini menunjukkan penyebaran data tidak terlalu rapat dan terdapat perbedaan nilai yang cukup jauh antar data.

- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/suryadarma-sys/UAS_SDP_SEMESTER1/blob/main/results/boxplot_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Jawab : Berdasarkan boxplot, terlihat bahwa data pendapatan tahunan memiliki sebaran yang cukup luas. Posisi median berada di bagian tengah, yang menunjukkan bahwa nilai pendapatan tidak terlalu condong ke satu sisi. Jarak antar kuartil yang cukup besar menandakan perbedaan pendapatan antar startup cukup signifikan. Selain itu, garis atas dan bawah yang cukup panjang menunjukkan adanya selisih yang jauh antara pendapatan paling rendah dan paling tinggi. Hal ini mengindikasikan bahwa distribusi pendapatan startup SaaS cenderung bervariasi dan tidak merata.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  -  p-value = 1.497e-14
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Jawab : Nilai p-value sebesar 1,497 × 10⁻¹⁴ jauh lebih kecil dari tingkat signifikansi yang umum digunakan (misalnya 0,05). Hal ini menunjukkan bahwa data tidak terdistribusi normal. Implikasinya, analisis statistik yang mengasumsikan distribusi normal sebaiknya tidak digunakan secara langsung. Oleh karena itu, lebih tepat menggunakan metode nonparametrik atau melakukan transformasi data agar hasil analisis menjadi lebih akurat.

- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/suryadarma-sys/UAS_SDP_SEMESTER1/blob/main/results/qqplot_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - jawab : Berdasarkan Q-Q plot, titik-titik data tidak sepenuhnya mengikuti garis lurus. Pada bagian awal dan akhir terlihat penyimpangan yang cukup jelas dari garis referensi. Hal ini menunjukkan bahwa distribusi data tidak normal. Artinya, data pendapatan tahunan memiliki pola sebaran yang menyimpang dari distribusi normal, sehingga analisis yang mengasumsikan normalitas perlu dipertimbangkan kembali atau diganti dengan metode yang lebih sesuai.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - "Koefisien Korelasi (r) = 0.996"
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - jawab : Nilai koefisien korelasi r = 0,996 menunjukkan adanya hubungan yang sangat kuat dan searah (positif) antara kedua variabel yang diuji. Artinya, ketika nilai salah satu variabel meningkat, variabel lainnya juga cenderung ikut meningkat. Besarnya nilai r yang mendekati 1 menandakan bahwa hubungan antar variabel hampir sempurna dan perubahan pada satu variabel sangat berkaitan dengan perubahan pada variabel lainnya.

- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/suryadarma-sys/UAS_SDP_SEMESTER1/blob/main/results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - Jawab : Dari scatter plot terlihat bahwa titik-titik data membentuk pola yang cenderung meningkat dari kiri bawah ke kanan atas. Hal ini menunjukkan adanya hubungan positif antara pendapatan tahunan dan biaya akuisisi pelanggan. Garis tren linear yang naik juga memperkuat bahwa semakin besar pendapatan, maka biaya akuisisi pelanggan cenderung ikut meningkat. Dengan demikian, pola pada grafik ini sudah sesuai dan mendukung hasil koefisien korelasi yang bernilai positif.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  -  (b0) = -1.06
  -  (b1) = 0.98
  -  Y = -1,6 + 0,98X
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  -  Jawaban : Nilai intercept (b0) = −1,6 menunjukkan nilai biaya akuisisi pelanggan saat pendapatan tahunan bernilai nol. Nilai ini lebih bersifat matematis dan kurang bermakna secara nyata karena pendapatan tidak mungkin nol. Sementara itu, slope (b1) = 0,98 berarti setiap kenaikan pendapatan tahunan sebesar 1 satuan akan diikuti kenaikan biaya akuisisi pelanggan sebesar 0,98 satuan, yang menunjukkan hubungan positif yang sangat kuat.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - Adjusted R-squared = 0.991 atau 99.1 %"
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - Jawaban : Nilai Adjusted R-squared sebesar 0,991 atau 99,1% menunjukkan bahwa model regresi mampu menjelaskan sekitar 99,1% variasi pada variabel dependen. Artinya, hampir seluruh perubahan pada variabel dependen dapat dijelaskan oleh variabel independen dalam model, sedangkan sisanya sekitar 0,9% dipengaruhi oleh faktor lain di luar model.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/suryadarma-sys/UAS_SDP_SEMESTER1/blob/main/results/plot_regresi_Biaya_Akuisisi_Pelanggan_Juta_IDR_vs_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Jawab : Garis regresi pada grafik menunjukkan adanya hubungan linear yang positif antara biaya akuisisi pelanggan dan pendapatan tahunan. Garis yang cenderung naik menandakan bahwa semakin besar biaya yang dikeluarkan untuk akuisisi pelanggan, maka pendapatan tahunan juga cenderung meningkat. Nilai Adjusted R-squared yang sangat tinggi menunjukkan bahwa model regresi ini mampu menjelaskan sebagian besar perubahan pendapatan berdasarkan biaya akuisisi, sehingga hubungan antara kedua variabel dapat dikatakan kuat.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
Jawab: Berdasarkan hasil analisis yang sudah dilakukan, dapat disimpulkan bahwa terdapat hubungan yang positif dan cukup kuat antara biaya akuisisi pelanggan dan pendapatan tahunan. Hasil korelasi menunjukkan bahwa semakin besar biaya yang dikeluarkan untuk akuisisi pelanggan, maka pendapatan yang diperoleh juga cenderung meningkat. Hal ini juga didukung oleh pola pada scatter plot yang menunjukkan tren naik. Selain itu, hasil analisis regresi linear menunjukkan bahwa biaya akuisisi pelanggan berpengaruh besar terhadap pendapatan tahunan. Nilai Adjusted R-squared yang tinggi menandakan bahwa model regresi mampu menjelaskan sebagian besar variasi pendapatan. Secara keseluruhan, hasil ini menunjukkan bahwa biaya akuisisi pelanggan memiliki peran penting dalam memengaruhi pendapatan berdasarkan data yang dianalisis.
