---
title: "Subset Sum Problem"
date: 2025-06-10 00:00:00 +0800
categories: [desain dan analisis algoritma, subset sum problem]
tags: [belajar]
description: Apa itu Subset Sum Problem dan bagaimana cara menyelesaikannya?
---

# Subset Sum Problem

## Konsep Subset Sum Problem

### 🎯 Apa itu Subset Sum Problem?

Subset Sum Problem adalah masalah klasik dalam ilmu komputer yang termasuk dalam kategori **NP-Complete**. Diberikan sebuah himpunan bilangan bulat dan sebuah nilai target, tugasnya adalah menentukan apakah ada subset dari himpunan tersebut yang jumlah elemennya sama dengan nilai target.

### 🧩 Definisi Formal

**Contoh 1:**
- Set = {1, 2, 3}, Target = 3
- **Jawaban:** YA
- **Penjelasan:** Terdapat subset {1, 2} yang jumlahnya 3

**Contoh 2:**
- Set = {1, 2, 3}, Target = 25
- **Jawaban:** TIDAK
- **Penjelasan:** Tidak ada subset yang jumlahnya 25

### Karakteristik
- Subset Sum Problem (SSP) termasuk dalam **decision problem**, yaitu jenis masalah yang hanya membutuhkan jawaban "ya" atau "tidak"
- Inti dari masalah ini adalah mencari apakah mungkin memilih sejumlah angka dari sekumpulan bilangan bulat sehingga totalnya pas sama dengan angka target
- Dalam implementasinya di dunia nyata bisa ditemukan dalam bidang kriptografi, pengelolaan keuangan, perencanaan sumber daya, bahkan kecerdasan buatan

---

## Variasi Masalah Subset Sum

### 1. Bounded Subset Sum Problem
Setiap elemen dalam himpunan hanya dapat digunakan sekali untuk membentuk subset yang jumlahnya sama dengan target.

**Contoh Kasus:**
- Set = {3, 34, 4, 12, 5, 2}, Target = 9
- **Apakah mungkin?** Ya. Subset {4, 5} menghasilkan total 9
- Kita tidak boleh menggunakan 4 atau 5 lebih dari sekali
- Cocok untuk kasus di mana barang atau sumber daya hanya tersedia satu unit

### 2. Partition Problem
Masalah membagi sebuah himpunan bilangan bulat menjadi dua subset yang memiliki jumlah total yang sama.

**Contoh Kasus:**
- Set = {1, 5, 11, 5}
- Total = 22 → Target subset = 11
- **Ya.** Kita bisa buat dua subset: {11} dan {1, 5, 5} → keduanya berjumlah 11
- Penting dalam manajemen sumber daya, seperti membagi beban server, tugas antar tim, atau membagi file secara seimbang

### 3. Exact k Elements Subset Sum
Mencari subset yang jumlahnya sama dengan target dan terdiri dari tepat k elemen.

**Contoh Kasus:**
- Set = {1, 2, 3, 4, 5}, Target = 9, k = 2
- **Apakah mungkin?** Ya. Subset {4, 5} terdiri dari 2 elemen dan jumlahnya 9
- Subset {2, 3, 4} juga jumlahnya 9, tapi terdiri dari 3 elemen (tidak valid)
- Cocok untuk memilih tim beranggotakan k orang dengan total nilai tertentu

### 4. Unbounded Subset Sum Problem
Setiap elemen boleh digunakan berulang kali untuk mencapai target.

**Contoh Kasus:**
- Set = {1, 3, 4}, Target = 6
- **Apakah mungkin?** Ya. Beberapa kemungkinan:
  - 1 + 1 + 1 + 3 = 6
  - 3 + 3 = 6
  - 2 × 1 + 4 = 6

### 5. Multi-target Subset Sum Problem
Mencari subset yang memenuhi lebih dari satu kriteria, misalnya jumlah total dan batas berat.

**Contoh Kasus:**
- Set barang:
  - Barang A: harga = 40, berat = 1 kg
  - Barang B: harga = 60, berat = 1.5 kg
  - Barang C: harga = 30, berat = 0.5 kg
- Target: total harga ≤ 100 dan total berat ≤ 2 kg
- Kombinasi A + C → total harga 70, berat 1.5 kg → valid
- Tapi A + B → harga 100, berat 2.5 kg → tidak valid karena melebihi berat

### 6. Approximate Subset Sum
Tidak ada subset yang jumlahnya tepat sama dengan target, jadi dicari subset terbaik yang mendekati target.

**Contoh Kasus:**
- Set = {2, 5, 10, 14}, Target = 15
- **Apakah mungkin?** {5, 10} = 15 ✅ (tepat)
- Kalau target = 16, dan tidak ada kombinasi pas, kita bisa ambil {14} atau {10, 5} = 15 → solusi terbaik

---

## Pendekatan Penyelesaian

### 🔁 Pendekatan Rekursif (Recursive Approach)
- Cek semua subset secara eksplisit
- **Untuk setiap elemen:** ✅ Sertakan ATAU ❌ Abaikan
- **Basis kasus:**
  - Jika sum == 0 → ✅ True
  - Jika n == 0 && sum != 0 → ❌ False
- **Kompleksitas:** O(2ⁿ)
- **Kekurangan:** Tidak efisien untuk array besar

### 🧠 Dynamic Programming Approach

#### A. Memoization (Top-Down DP)
- Kombinasi rekursi + penyimpanan hasil submasalah
- Gunakan struktur dp[n][sum] → cache hasil
- Kurangi pemanggilan ulang fungsi yang sama
- Efisien untuk input sedang, tetap butuh stack rekursi
- **Kompleksitas Waktu:** O(n × sum)
- **Kompleksitas Memori:** O(n × sum)

#### B. Tabulation (Bottom-Up DP)
- Iteratif → mulai dari kasus paling kecil
- Buat tabel dp[n+1][sum+1]
- dp[i][j] = True jika subset arr[0..i-1] bisa menghasilkan j
- **Inisialisasi:**
  - dp[i][0] = True (karena subset kosong = 0)
  - dp[0][j] = False (tidak bisa dapat sum ≠ 0 tanpa elemen)
- Iterasi solusi dari bawah ke atas

#### C. Optimasi Ruang (Space Optimization)
- Hanya membutuhkan baris sebelumnya (i-1) untuk menghitung baris saat ini
- Menghemat ruang dari O(n × sum) menjadi O(sum)
- Menggunakan dua array 1D: prev dan curr
- **Aturan pengisian:**
  - Jika j < arr[i]: curr[j] = prev[j]
  - Jika j ≥ arr[i]: curr[j] = prev[j] or prev[j - arr[i]]
- **Kompleksitas Waktu:** O(n × sum)
- **Kompleksitas Ruang:** O(sum)

---

## Contoh Dynamic Programming

### Tabulation (Bottom-Up)
**Contoh:** arr = {1, 2, 3}, target = 3

| i | Elemen | dp[i][0] | dp[i][1] | dp[i][2] | dp[i][3] |
|---|--------|----------|----------|----------|----------|
| 0 | {} | True | False | False | False |
| 1 | {1} | True | True | False | False |
| 2 | {1,2} | True | True | True | False |
| 3 | {1,2,3} | True | True | True | **True** |

**Hasil:** dp[3][3] = True → Ada subset dengan jumlah 3 (yaitu {1,2})

---

## Aplikasi Permasalahan Subset Sum di Dunia Nyata

1. **Kriptografi:** Digunakan dalam sistem kriptografi berbasis ransel, di mana kesulitan menyelesaikan Permasalahan Subset Sum menjadi dasar keamanan kunci publik.

2. **Alokasi Sumber Daya:** Membantu memilih subset proyek atau item agar sesuai dengan anggaran atau target tertentu.

3. **Genetika dan Bioinformatika:** Digunakan untuk menganalisis kombinasi gen atau fragmen DNA dengan total ekspresi atau panjang tertentu.

4. **Keuangan dan Investasi:** Membantu menentukan apakah target investasi dapat dicapai dengan memilih kombinasi aset yang tepat.

5. **Perancangan Permainan dan Teka-Teki:** Muncul dalam permainan atau teka-teki yang melibatkan pencarian kombinasi angka sesuai skor target.

---

## Kesimpulan

Subset Sum Problem (SSP) adalah masalah dalam ilmu komputer yang bertujuan untuk menentukan apakah terdapat subset dari sekumpulan bilangan bulat yang jumlahnya sama dengan nilai target tertentu. Masalah ini tergolong dalam kategori NP-Complete dan memiliki berbagai variasi, seperti bounded, unbounded, exact k elements, partition, multi-target, hingga approximate subset sum, yang masing-masing memiliki aplikasi dan batasan berbeda.

Untuk menyelesaikan SSP, digunakan pendekatan rekursif yang sederhana namun kurang efisien, serta dynamic programming yang lebih optimal baik dari segi waktu maupun ruang. Subset Sum memiliki aplikasi nyata dalam bidang kriptografi, keuangan, pengelolaan sumber daya, hingga kecerdasan buatan, menjadikannya masalah penting yang tidak hanya teoritis, tetapi juga rele
