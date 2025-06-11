---
title: "Dijkstra's Algorithm"
date: 2025-06-10 00:00:00 +0800
categories: [desain dan analisis algoritma, graph traversal]
tags: [belajar]
description: Penjelasan dan implementasi Dijkstra's Algorithm
---

## Definisi

Dijkstra's Algorithm adalah sebuah metode yang digunakan untuk mencari jalur terpendek antara dua titik dalam sebuah graf. Graf ini bisa berupa jaringan yang terdiri dari simpul (titik) dan sisi (hubungan antar titik) dengan bobot tertentu pada sisi-sisinya. Algoritma ini membantu kita menentukan jalur terpendek dari titik awal ke titik tujuan.

---

## Cara Kerja Dijkstra's Algorithm

1. **Buat tabel dan kolom** sebagai tempat nilai atau jarak dari simpul, sedangkan baris sebagai posisi simpul.

2. **Pilih simpul awal dan simpul tujuan**, dengan syarat simpul tersebut harus terhubung secara langsung.

3. **Hitung jarak** beberapa simpul tujuan yang telah dipilih.

4. **Setelah semua simpul diuji**, lalu pilih jarak yang terpendek.

5. **Simpul yang dipilih** akan menjadi acuan untuk tahap selanjutnya, ulangi seperti sebelumnya sampai semua simpul telah diuji.

---

## Contoh Permasalahan

**Soal:** Carilah nilai dan lintasan terpendek dari simpul A ke F!

**Graf yang diberikan:**
```
    B ---- D
   /|      |\
  / |      | \
 A  |      |  F
  \ |      | /
   \|      |/
    C ---- E
```

**Hasil:** Lintasan terpendek adalah ABEF/ABDF = 4

---

## Contoh Penggunaan

### 1. Navigasi Jalan
Misalnya kita ingin mencari rute terpendek dari rumah ke sekolah. Dijkstra's Algorithm akan membantu kita menentukan jalan mana yang lebih pendek dengan mempertimbangkan semua jalan yang ada dan menghitung jarak yang terpendek dari rumah ke sekolah.

### 2. Pengiriman Barang
Sebuah perusahaan ekspedisi ingin mengirim paket dari gudang ke beberapa pelanggan. Dijkstra's Algorithm akan membantu menentukan rute pengiriman yang paling efisien agar paket bisa sampai lebih cepat dan tidak boros bensin atau tenaga.

---

## Kelebihan Dijkstra's Algorithm

### 🎯 Menjamin Jalur Terpendek
Dijkstra selalu menemukan solusi yang optimal (jalur terpendek) dari titik asal ke semua titik lain, selama semua bobot edge (jarak/biaya) bernilai positif.

### ⚡ Efisien untuk Banyak Aplikasi
Sangat cocok untuk graf yang padat dan sering digunakan dalam aplikasi nyata seperti GPS, routing jaringan, dan sistem navigasi.

### 🎯 Dapat Menyelesaikan Banyak Tujuan Sekaligus
Sekali dijalankan dari satu titik, bisa memberikan informasi jarak terpendek ke semua titik lainnya dalam graf.

---

## Kekurangan Dijkstra's Algorithm

### ❌ Tidak Bekerja dengan Bobot Negatif
Tidak bisa digunakan jika ada edge dengan bobot negatif.

### 🐌 Kurang Efisien untuk Graf Besar yang Jarang Terhubung
Pada graf yang sangat besar dan sparse (jarang terhubung), Dijkstra bisa menjadi lambat jika tidak dioptimalkan dengan struktur data seperti priority queue (misalnya heap).

### 🔄 Perhitungan Bisa Terlalu Luas
Jika kita hanya ingin jalur dari titik A ke titik B, Dijkstra tetap menghitung semua kemungkinan ke titik lain, yang kadang tidak efisien. Dalam kasus seperti ini, algoritma A* (A Star) bisa lebih baik karena memperhitungkan arah tujuan.

---

## Kesimpulan

Algoritma Dijkstra merupakan salah satu algoritma pencarian jalur terpendek yang paling efisien dan banyak digunakan dalam teori graf. Algoritma ini bekerja dengan cara mencari jalur terpendek dari satu simpul sumber ke semua simpul lainnya dalam graf berbobot non-negatif. 

Melalui pendekatan greedy, Dijkstra memastikan bahwa setiap langkahnya mendekatkan solusi menuju hasil optimal. Keunggulan utama algoritma ini terletak pada keakuratannya dan efisiensinya, terutama jika dikombinasikan dengan struktur data seperti priority queue atau min-heap. 

Dalam implementasi praktis, algoritma Dijkstra sangat berguna dalam berbagai bidang seperti jaringan komputer, sistem navigasi, dan pemodelan transportasi.
