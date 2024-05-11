# PCD_UTS_202231051_2024_ITPLN
## Pengolahan citra 
  Citra digital adalah sebuah fungsi 2D, f(x,y), yang merupakan fungsi intensitas
cahaya, dimana nilai x dan y merupakan koordinat spasial dan nilai fungsi di setiap titik
(x,y) merupakan tingkat keabuan citra pada titik tersebut. Citra digital dinyatakan dengan
sebuah matriks dimana baris dan kolomnya menyatakan suatu titik pada citra tersebut dan
elemen matriksnya (yang disebut sebagai elemen gambar atau piksel) menyatakan tingkat
keabuan pada titik tersebut. Matriks dari citra digital berukuran NxM (tinggi x lebar),
dimana:

N = jumlah baris 0 < y ≤ N – 1
M = jumlah kolom 0 ≤ x ≤ M – 1
L = derajat keabuan 0 ≤ f(x,y) ≤ L – 1

Dimana indeks baris (x) dan indeks kolom (y) menyatakan suatu koordinat titik pada
citra, sedangkan f(x,y) merupakan intensitas (derajat keabuan) pada titik (x,y).
Berdasarkan jenisnya, citra digital dapat dibagi menjadi 3 (Sutoyo, 2009), yaitu:

**1. Citra Biner (Monokrom)**
Memiliki 2 buah warna, yaitu hitam dan putih. Warna hitam bernilai 1 dan warna
putih bernilai 0. Untuk menyimpan kedua warna ini dibutuhkan 1 bit di memori.
Tahapan penyelesaian produk

**2. Citra Grayscale (skala keabuan)**
Citra grayscale mempunyai kemungkinan warna hitam untuk nilai minimal dan
warna putih untuk nilai maksimal. Banyaknya warna tergantung pada jumlah bit yang
disediakan di memori untuk menampung kebutuhan warna tersebut.
Semakin besar jumlah bit warna yang disediakan di memori, maka semakin halus
gradasi warna yang terbentuk.

**3.Citra Warna (true color)**
Setiap piksel pada citra warna mewakili warna yang merupakan kombinasi tiga warna
dasar, yaitu merah, hijau, dan biru (RGB = Red, Green, Blue). Setiap warna dasar
menggunakan penyimpanan 8 bit = 1 byte (nilai maksimum 255 warna), jadi satu piksel
pada citra warna diwakili oleh 3 byte.
Pengolahan citra digital adalah salah satu bentuk pemrosesan informasi dengan
inputan berupa citra (image) dan keluaran yang juga berupa citra atau dapat juga bagian
dari citra tersebut. Tujuan dari pemrosesan ini adalah memperbaiki kualitas citra agar
mudah diinterpretasi oleh manusia atau mesin komputer

## Konversi BGR dan RGB dengan Python, OpenCV (cvtColor)
Konversi antara BGR (Blue, Green, Red) dan RGB (Red, Green, Blue) adalah konversi antara dua model warna yang umum digunakan dalam pemrosesan citra digital.

1. **BGR (Blue, Green, Red)**:
   - Ini adalah model warna yang umum digunakan dalam OpenCV, sebuah perpustakaan populer untuk pengolahan citra dan komputer vision.
   - Urutan warna dalam BGR adalah biru, hijau, dan merah.
   - Dalam BGR, warna biru disimpan di saluran pertama, hijau di saluran kedua, dan merah di saluran ketiga.

2. **RGB (Red, Green, Blue)**:
   - Ini adalah model warna yang paling umum digunakan di dunia digital, termasuk dalam tampilan monitor, kamera digital, dan banyak lagi.
   - Urutan warna dalam RGB adalah merah, hijau, dan biru.
   - Dalam RGB, warna merah disimpan di saluran pertama, hijau di saluran kedua, dan biru di saluran ketiga.

Konversi antara BGR dan RGB melibatkan menukar posisi saluran warna. Ini perlu dilakukan ketika Anda bekerja dengan gambar menggunakan berbagai perangkat lunak atau alat yang menggunakan model warna yang berbeda. Misalnya, jika Anda ingin memproses gambar menggunakan OpenCV (yang menggunakan BGR), tetapi ingin menampilkannya di browser web atau program lain yang mengharapkan format RGB, Anda perlu melakukan konversi antara BGR dan RGB. Biasanya, algoritma yang sederhana, seperti menukar saluran atau menggunakan fungsi bawaan dari library yang Anda gunakan, dapat melakukan konversi tersebut dengan mudah.
Ambang batas (thresholding) adalah teknik pemrosesan citra yang digunakan untuk memisahkan piksel-piksel dalam citra menjadi dua kelas berdasarkan intensitasnya. Tujuan utamanya adalah untuk mengubah citra menjadi citra biner di mana piksel-pikselnya hanya memiliki nilai 0 (hitam) atau 255 (putih), tergantung pada apakah nilai intensitasnya melebihi atau kurang dari suatu ambang tertentu.

### Prinsip Thresholding:
1. **Pengukuran Intensitas**: Pertama-tama, ambang batas memerlukan pengukuran intensitas piksel dalam citra. Intensitas ini sering kali dinyatakan dalam skala abu-abu, di mana nilai-nilai lebih tinggi menunjukkan kecerahan yang lebih besar.

2. **Pemilihan Ambang**: Ambang batas memerlukan ambang yang dipilih sebelumnya. Ambang ini merupakan nilai tertentu yang digunakan untuk membedakan antara piksel yang dianggap sebagai bagian dari objek (misalnya, benda yang diinginkan untuk dikenali dalam citra) dan latar belakang (bagian lain dari citra yang tidak dianggap sebagai objek).

3. **Konversi Menjadi Citra Biner**: Setelah ambang dipilih, citra asli diperiksa piksel demi piksel. Jika intensitas piksel melebihi ambang, piksel tersebut diubah menjadi nilai 255 (putih); jika tidak, nilainya diubah menjadi 0 (hitam). Dengan demikian, kita mendapatkan citra biner di mana hanya ada dua nilai intensitas yang mungkin.

### Jenis-jenis Thresholding:
1. **Thresholding Global**: Dalam metode ini, satu ambang diterapkan pada seluruh citra. Ini adalah pendekatan yang paling sederhana tetapi mungkin tidak efektif jika citra memiliki variasi intensitas yang signifikan.

2. **Thresholding Adaptif**: Metode ini menggunakan ambang yang berbeda-beda untuk setiap bagian citra. Ini lebih efektif untuk citra yang memiliki variasi intensitas yang signifikan.

3. **Thresholding Otsu**: Metode ini secara otomatis menentukan ambang terbaik berdasarkan analisis histogram citra. Ini adalah metode yang baik jika ambang yang optimal tidak diketahui.
### Implementasi:
Di berbagai perpustakaan pemrosesan citra, seperti OpenCV (dalam bahasa pemrograman Python), terdapat fungsi-fungsi yang memudahkan implementasi thresholding. Anda dapat mengatur ambang secara manual atau menggunakan metode otomatis seperti Otsu. Kemudian, hasilnya dapat digunakan untuk tujuan tertentu, seperti segmentasi objek atau deteksi fitur.

# Tahapan Pengerjaan

## 1. Membuat Library
- Dipakai tiga library utama untuk membantu pengerjaan projek
- Yaitu cv2 (computer vision) yang digunakan untuk pengolahan gambar
- pyplot dari matplotlib yang digunakan untuk visualisasi gambar/hasil pengolahan
- numpy yang digunakan untuk membantu dalam pengolahan data matriks/array (data gambar)

## 2. Membaca gambar
- Dengan menggunakan cv2.imread, saya memasukkan/membaca gambar kedalam variabel img, untuk kemudian digunakan dan diolah.
- Setelahnya kemudian dilakukan pengecekan terhadap status quo gambar yang ada di dalam variabel img, dengan menampilkannya melalui plt.imshow()

## 3. Mengubah format gambar
- Gambar yang ditampilkan pada fungsi plt.imshow() terlihat masih aneh/tidak sesuai dengan gambar asli, dan diketahui penyebabnya adalah karena plt.imshow() menampilkan gambar dalam format RGB sedangkan gambar yang diambil dengan fungsi cv2.imread() secara default berformat BGR
- Sehingga dilakukan konversi data gambar dari BGR menjadi RGB

## 4. Pemurnian Warna/PIksel
- Sebelum dilakukan pemurnian warna, diambil besar baris dan kolom dari gambar dengan menggunakan bantuan img.shape[:2], yaitu mengambil nilai dari 2 dimensi pertama gambar [baris, kolom]
- Dibuat barisan kode pemurnian warna dengan konsep sebagai berikut (tertulis juga pada comment program)
- _Pada kode dibawah dilakukan pemurnian warna dengan mencari elemen warna (R/G/B) dengan intensitas tertinggi, dan warna dengan intensitas kedua tertinggi kemudian melakukan pembandingan keduanya dengan mencari selisih antar keduanya dan kemudian menghitung apakah mereka lebih besar dari 10 (kemungkinan bukan putih) atau kurang dari 10 (kemungkinan putih), dan apabila warna piksel kemungkinan bukan putih (>10) maka warna-warna lain (selain warna dengan intensitas maksimum) akan menjadi 0 (sehingga piksel menjadi warna yang murni R/G/B)_

## 5. Deteksi Warna Pada Citra (Soal 1)
- Deteksi warna dilakukan dengan memanggil salah satu elemen warna (R/G/B) untuk setiap piksel dan menyajikannya sebagai sebuah citra abu-abu/1 kedalaman
- Dengan syntax umum sebagai berikut:
img[:,:,0/1/2] --> dengan 0 = merah, 1 = hijau, 2 = biru

- Dalam tahapan ini, diberikan juga visualisasi dari hasil deteksi warna berupa visualisasi gambar dan histogram
- Dari gambar, dapat dilihat bahwa gambar yang warnanya di deteksi, memiliki tulisan/huruf yang warnanya merupakan warna yang sedang dideteksi, berubah menjadi putih/mendekati putih. Hal ini terjadi karena, dalam syntax pendeteksian warna yang dipakai (diatas), gambar diubah menjadi citra abu, yang intensitas warnanya ditentukan oleh intensitas warna yang sedang dideteksi, sehingga, warna yang dideteksi, yang memiliki besaran tinggi pada spektrum/elemen warna tersebut, menjadi terlihat putih, dan warna selainnya menjadi hitam (kecuali untuk putih, karena putih terdiri dari ketiga elemen warna yang nilainya relatif sudah tinggi)
- Histogram dibuat dengan menggunakan fungsi .hist, yang menghitung dan menyajikan histogram berupa data intensitas dari gambar.

## 6. Ambang Batas (Soal 2)
- Sesuai dengan instruksi soal, selanjutnya saya mencari ambang-ambang batas untuk munculnya kategori-kategori warna pada gambar dari filter threshold
- Ambang batas dicari dengan pertama-tama mengkonversi gambar dari RGB ke grayscale dengan bantuan cv2.cvtColor()
- Lalu dengan bantuan fungsi threshold, saya dapat mencoba-coba ambang batas mana yang dapat memunculkan, Blue, Red (dan Blue) serta Green (dan Red-Blue).
- Untuk detail syntax threshold (secara umum)

(thresh, binary) = cv2.threshold(gray, x, 255, cv2.THRESH_BINARY)

Dengan x sebagai threshold yang dipakai, dan dengan acuan threshold untuk kasus biner (THRESH_BINARY)

- Setelah dilakukan percobaan ambang batas, didapat ambang batas untuk kategori BLUE = 30, RED-BLUE = 60 dan RED-GREEN-BLUE = 90
- Ambang batas dikatakan ditemukan disaat huruf2 yang memiliki warna yang ingin di kategorikan 
