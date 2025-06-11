---
title: "N-Queens Problem"
date: 2025-06-10 00:00:00 +0800
categories: [desain dan analisis algoritma, N-Queens]
tags: [belajar]
description: Apa itu N-Queens Problem dan bagaimana cara menyelesaikannya dengan algoritma backtracking?
---

# N-Queens Problem 

## 1. Definisi Masalah N-Queens

**N-Queens Problem** adalah permasalahan klasik dalam bidang ilmu komputer dan matematika kombinatorik yang melibatkan penempatan N buah ratu catur pada sebuah papan catur berukuran N × N, sedemikian rupa sehingga tidak ada dua ratu yang saling menyerang.

### Aturan Ratu Catur:
- Ratu dapat bergerak secara **horizontal** (baris)
- Ratu dapat bergerak secara **vertikal** (kolom)  
- Ratu dapat bergerak secara **diagonal**

### Contoh Terkenal:
**8-Queens Problem** - menempatkan 8 ratu di papan catur 8×8 tanpa saling menyerang.

---

## 2. Tujuan Masalah N-Queens

1. **Menemukan semua konfigurasi** penempatan ratu yang memenuhi syarat tidak saling menyerang
2. **Mengembangkan dan menguji algoritma** pencarian dan optimasi seperti:
   - Backtracking
   - DFS (Depth First Search)
   - Heuristic search
   - Algoritma genetika
3. **Melatih logika pemrograman** dan pemecahan masalah dalam konteks Constraint Satisfaction Problem (CSP)

---

## 3. Pentingnya Masalah N-Queens

### 3.1 Sebagai Studi Kasus dalam AI dan Algoritma
- Digunakan secara luas untuk mengajarkan teknik pencarian
- Menjadi landasan dalam studi artificial intelligence dan operations research
- Mengajarkan konsep backtracking, branch and bound, serta algoritma heuristic

### 3.2 Model Permasalahan Constraint Satisfaction
- Contoh ideal dari masalah CSP
- Menetapkan nilai (posisi ratu) ke dalam variabel (baris/kolom) tanpa melanggar kendala (serangan)

### 3.3 Aplikasi dalam Dunia Nyata
Prinsip N-Queens dapat diterapkan dalam:
- **Penjadwalan tugas** (menghindari konflik)
- **Penempatan modul** dalam sirkuit elektronik
- **Pengalokasian sumber daya** yang saling eksklusif

### 3.4 Kompleksitas dan Skalabilitas
- Menunjukkan bagaimana kompleksitas meningkat secara eksponensial dengan bertambahnya nilai N
- Cocok sebagai bahan evaluasi efisiensi algoritma dalam skala besar

---

## 4. Relevansi dalam Design and Analysis of Algorithms (DAA)

### 4.1 Studi Kasus Teknik Backtracking
- Contoh klasik untuk mengilustrasikan konsep backtracking secara sistematis
- Membantu mahasiswa belajar menyusun solusi bertahap dan menghindari eksplorasi solusi yang tidak mungkin

### 4.2 Analisis Kompleksitas Algoritma
- Membantu memahami analisis waktu dan ruang
- Perbandingan antara algoritma brute-force vs backtracking yang lebih efisien
- Meskipun backtracking memiliki kompleksitas eksponensial dalam worst case, tetap jauh lebih cepat dari brute-force

### 4.3 Pengenalan Constraint Satisfaction Problem (CSP)
- Memperkenalkan mahasiswa pada CSP
- Teknik backtracking dapat diperluas menjadi:
  - Backtracking dengan forward checking
  - Backjumping

---

## 5. Mengapa N-Queens Masalah Backtracking

### 5.1 Pendekatan Rekursif dan Bertahap
- Menempatkan ratu satu per satu, dimulai dari baris pertama
- Untuk setiap baris, mencoba meletakkan ratu di setiap kolom
- Memeriksa apakah posisi aman (tidak diserang ratu sebelumnya)
- Jika aman, lanjut ke baris berikutnya
- Jika tidak ada posisi aman, kembali ke baris sebelumnya (backtracking)

### 5.2 Pohon Pencarian Solusi
- Setiap penempatan ratu = satu simpul dalam pohon pencarian
- Jalur dari akar ke daun = satu kemungkinan solusi
- Jika jalur tidak menghasilkan solusi valid, prune (pangkas) jalur tersebut

### 5.3 Sifat Non-deterministik
- Banyak kemungkinan posisi untuk setiap ratu
- Tidak diketahui posisi yang benar sejak awal
- Harus mencoba semua kemungkinan secara sistematis

---

## 6. Algoritma Backtracking

**Backtracking** adalah teknik penyelesaian masalah yang mencoba membangun solusi langkah demi langkah dan "mundur" (backtrack) ketika menemui jalan buntu (dead end).

### Langkah-langkah Algoritma Backtracking:

#### 1. Pilih Keputusan (Decision Choice)
- Pada setiap langkah, pilih opsi yang mungkin dari kandidat solusi
- **Contoh**: Dalam N-Queens, pilih kolom untuk menempatkan ratu di baris berikutnya

#### 2. Batasan (Constraint Check)
- Periksa apakah pilihan valid berdasarkan aturan masalah
- Jika valid, lanjut ke langkah berikutnya
- Jika tidak valid, abaikan opsi ini dan coba opsi lain (backtrack)

#### 3. Rekursi (Recursive Exploration)
- Jika pilihan valid, rekursif melanjutkan pencarian solusi dengan keputusan ini

#### 4. Backtrack (Kembali jika Dead End)
- Jika tidak ada solusi ditemukan setelah memilih opsi tertentu
- Batalkan keputusan terakhir (undo) dan coba opsi lain

#### 5. Basis Kasus (Base Case)
- Jika semua keputusan mengarah ke solusi lengkap
- Catat solusinya atau kembalikan solusi

---

## 7. Contoh Backtracking dalam Permutasi

### Mencari Semua Permutasi dari [1, 2, 3]

**Langkah Algoritma:**
1. **Pilih angka pertama: 1**
   - Subproblem: Cari permutasi [2,3] → [1, 2, 3], [1, 3, 2]
   - Backtrack: Kembali ke []

2. **Pilih angka pertama: 2**
   - Subproblem: Cari permutasi [1,3] → [2, 1, 3], [2, 3, 1]
   - Backtrack: Kembali ke []

3. **Pilih angka pertama: 3**
   - Subproblem: Cari permutasi [1,2] → [3, 1, 2], [3, 2, 1]

**Solusi Akhir:**
[[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]]

---

## 8. Contoh Aplikasi Dunia Nyata: Penempatan Karyawan

### Skenario:
Perusahaan dengan n karyawan ingin menempatkan mereka dalam n ruang kerja di kantor.

### Aturan:
1. **Ruang berdekatan** tidak boleh digunakan oleh dua karyawan yang sama
2. **Karyawan dalam ruang berdekatan** tidak boleh berada dalam garis lurus yang sama
3. **Tujuan**: Menempatkan setiap karyawan di ruang berbeda tanpa ada yang bertabrakan

### Langkah-langkah Penempatan:
1. **Ruang pertama**: Tempatkan karyawan pertama (tidak ada masalah)
2. **Ruang kedua**: Tempatkan karyawan kedua di ruang yang tidak bertabrakan
3. **Ruang ketiga**: Cari ruang yang tidak bertabrakan dengan dua karyawan sebelumnya
4. **Proses berlanjut**: Lanjutkan untuk semua karyawan dengan aturan yang sama

### Kasus Backtracking:
- Jika tidak ada ruang valid untuk karyawan ke-n
- Mundur (backtrack) dan coba posisi berbeda untuk karyawan sebelumnya
- Terus mundur sampai menemukan solusi yang valid

### Analogi Dunia Nyata:
- Pengaturan tempat duduk
- Penempatan karyawan dalam ruang terbatas
- Pengaturan sumber daya yang terbatas

---

## 9. Kesimpulan

**Backtracking** adalah pendekatan exhaustive search dengan optimasi, dimana:
- Solusi dibangun bertahap dan dibatalkan jika tidak valid
- Melibatkan eksplorasi rekursif, pemeriksaan batasan, dan pengembalian (undo) jika gagal
- N-Queens Problem adalah contoh ideal untuk memahami konsep backtracking
- Memiliki aplikasi luas dalam AI, optimasi, dan pemecahan masalah constraint satisfaction

**N-Queens Problem** tidak hanya penting sebagai latihan akademis, tetapi juga memberikan fondasi yang kuat untuk memahami algoritma pencarian dan optimasi yang digunakan dalam berbagai aplikasi dunia nyata.
