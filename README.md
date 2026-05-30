# Analisis Sentimen Pengalaman Pengguna Terhadap Layanan Transportasi Publik KRL dan MRT di Indonesia Berdasarkan Data Twitter/X

Proyek ini merupakan Laporan Akhir Proyek Mata Kuliah Pemrosesan Teks (_Text Processing_) yang disusun melalui kolaborasi mahasiswa Program Studi S1 Sains Data, Universitas Negeri Surabaya dan S1 Statistika, Universitas Negeri Jakarta.

## Anggota Kelompok 14
1. **Lailil Hidayanti** - (24031554036) - Universitas Negeri Surabaya
2. **Faiz Farhan** - (1314623072) - Universitas Negeri Jakarta
3. **Nurlaila Lutfi Azizah** - (24031554205) - Universitas Negeri Surabaya

**Dosen Pengampu:** 
* Ulfa Siti Nuraini, S.Stat., M.Stat.
* Dr. Dian Handayani, M.Si

---

## 1. Latar Belakang & Deskripsi Proyek
Mobilitas masyarakat urban di wilayah Jabodetabek sangat bergantung pada transportasi publik, terutama Kereta Rel Listrik (KRL) Commuter Line dan Mass Rapid Transit (MRT) Jakarta. Pengalaman pengguna yang dinamis sering kali dituangkan dalam bentuk opini atau cuitan di platform media sosial Twitter/X, baik berupa apresiasi, keluhan fasilitas, hingga kritik ketepatan waktu.
Proyek ini mengeksplorasi teknik *Natural Language Processing* (NLP) untuk menarik informasi tersembunyi dari opini publik tersebut. Kami mengumpulkan data cuitan teks, melakukan serangkaian pipa pembersihan data teks (*text preprocessing*), lalu memodelkan sentimen (Positif, Netral, Negatif) menggunakan dua pendekatan algoritma untuk dibandingkan akurasinya:
1. **Machine Learning Tradisional:** Algoritma **Naive Bayes** yang berbasis probabilitas bersyarat.
2. **Deep Learning / Transformer:** Proses **Fine-tuning IndoBERT** (`indobenchmark/indobert-base-p2`), yaitu model bahasa transformator yang telah dilatih sebelumnya khusus untuk memahami konteks semantik Bahasa Indonesia secara mendalam.

---

## 2. Alur Pemrosesan Teks & Pemodelan (Pipeline)
Tahapan pengolahan data teks yang diimplementasikan dalam proyek ini meliputi:
1. **Data Scraping:** Mengambil cuitan publik dari Twitter/X menggunakan kata kunci relevan terkait KRL dan MRT.
2. **Text Preprocessing:**
   * **Case Folding:** Menyeragamkan seluruh teks menjadi huruf kecil (*lowercase*).
   * **Cleansing:** Menghapus *username* (@user), hashtag (#), tautan URL, angka, tanda baca, serta karakter khusus lainnya.
   * **Normalization:** Memperbaiki kata-kata tidak baku atau gaul menggunakan kamus slangwords.
   * **Filtering (Stopword Removal):** Membuang kata-kata berfrekuensi tinggi yang tidak membawa makna esensial.
   * **Stemming:** Mengembalikan kata berimbuhan ke kata dasarnya menggunakan bantuan library bahasa Indonesia (`Sastrawi`).
3. **Modeling & Fine-Tuning:**
   * Melakukan vektorisasi teks menggunakan pembobotan **TF-IDF** untuk algoritma Naive Bayes.
   * Melakukan tokenisasi khusus menggunakan tokeniser bawaan IndoBERT untuk arsitektur Deep Learning.
   * Melatih model untuk mengklasifikasikan teks ke dalam label sentimen terkait.
4. **Evaluation & Comparison:** Mengukur performa klasifikasi kedua model berdasarkan metrik *Accuracy*, *Precision*, *Recall*, dan *F1-Score* untuk mengetahui model terbaik dalam menangani sentimen transportasi publik.
