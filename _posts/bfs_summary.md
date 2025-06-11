# Breadth-First Search (BFS) - Kelompok 7

**Anggota Kelompok:**
- (H071241033) Muh. Hanif Nurmahdin
- (H071241093) Moch. Syech Yusuf. M
- (H071241005) Raihan Ramadhan
- (H071241021) Kevin Anugrah Somakila'

---

## Pengertian

Breadth-First Search (BFS) adalah metode untuk menjelajahi graph atau pohon dengan menelusuri simpul-simpul berdasarkan jaraknya dari titik awal. Secara sederhana, BFS akan mengeksplorasi semua simpul yang paling dekat terlebih dahulu, baru kemudian beralih ke simpul yang lebih jauh. Jadi pendekatannya menyebar ke seluruh arah secara merata dari pusat.

### Ilustrasi Sederhana
Bayangkan kita sedang mencari ruang kelas di sebuah gedung kampus berlantai 3. Kita pasti akan memeriksa seluruh ruangan dari lantai pertama sebelum lanjut ke lantai atas. Itulah cara kerja BFS: menjelajah secara mendatar.

BFS banyak digunakan dalam berbagai aplikasi, mulai dari pencarian rute tercepat dalam game, penelusuran jaringan sosial, hingga pencarian jalur optimal dalam sistem navigasi dan peta digital.

---

## Konsep Dasar

1. **BFS menggunakan struktur queue (antrian)**
2. **Mulai dari simpul awal** → kunjungi semua tetangga → lanjut ke tetangga dari tetangga
3. **Bersifat level-order traversal** (per lapisan)

---

## Langkah-Langkah Algoritma BFS

1. **Tentukan simpul awal** (start node)

2. **Masukkan simpul** ke dalam antrian (queue)

3. **Ambil simpul dari queue** terdepan, tandai bahwa simpul telah dikunjungi, dan cek apakah merupakan solusi/tujuan

4. **Selama antrian tidak kosong** atau simpul aktif bukan merupakan tujuan, lakukan:
   - Keluarkan simpul dari antrian (dequeue)
   - Untuk setiap tetangga dari simpul (jika ada):
     - Kunjungi semua tetangga yang belum dikunjungi lalu tandai sebagai dikunjungi
     - Tambahkan ke antrian (enqueue)

5. **Ulangi proses** pencarian mulai langkah ke-2 sampai ke-3

6. **Ulangi sampai** simpul tujuan (goal node) ditemukan atau queue sudah kosong

---

## Cara Kerja BFS (Contoh)

Dari graf dengan simpul S (start) sampai G (goal):

| Queue | Simpul Aktif | Visited |
|-------|--------------|---------|
| S | S | S |
| A, B | A | SA |
| B, C, D | B | SAB |
| C, D, E, F | C | SABC |
| D, E, F | D | SABCD |
| E, F | E | SABCDE |
| F, H, G | F | SABCDEF |
| H, G | H | SABCDEFH |
| G | G | SABCDEFHG |

---

## Aplikasi Nyata BFS

### 1. BFS dalam Labirin
- Digunakan untuk mencari jalan terpendek dari titik awal ke tujuan
- **Contoh:** Game Pac-Man menghitung rute terpendek untuk mengejar pemain
- **Cara kerja:** Mengeksplorasi semua jalur level demi level (tetangga terdekat dulu) hingga menemukan exit

### 2. BFS di Media Sosial
- Platform seperti Facebook atau LinkedIn menggunakan BFS untuk menemukan teman atau koneksi dalam jarak tertentu (misal: "Orang yang mungkin Anda kenal")
- **Cara kerja:** Menelusuri teman langsung (level 1), lalu temannya teman (level 2), dst

### 3. BFS dalam Jaringan Komputer
- Memetakan semua perangkat (PC, server, router) dalam jaringan
- **Cara Kerja:**
  - Mulai dari router utama, telusuri perangkat yang terhubung per level:
  - Level 1: Switch langsung terhubung ke router
  - Level 2: PC/server yang terhubung ke switch tersebut

### 4. BFS dalam Transportasi & Navigasi (Google Maps, Grab, Gojek)
- BFS digunakan untuk menemukan rute terpendek dari titik A ke B dengan asumsi semua edge memiliki bobot yang sama (misal: jumlah jalan, bukan jarak)
- **Contoh:** Mencari jalur dengan paling sedikit persimpangan

---

## Kelebihan dan Kekurangan

### ✅ Kelebihan
- **Menjamin ditemukannya solusi yang paling baik** (optimal dan lengkap)

### ❌ Kekurangan  
- **Membutuhkan memori dan waktu yang cukup banyak**

---

## Kesimpulan

1. **BFS adalah algoritma penelusuran** graf atau pohon yang menjelajahi simpul secara berlapis, dimulai dari simpul awal.

2. **Menggunakan struktur data queue** untuk memastikan semua simpul dengan jarak terdekat dijelajahi lebih dulu.

3. **BFS cocok untuk mencari jalur terpendek** pada graf tak berbobot.

4. **Efektif digunakan** dalam berbagai aplikasi seperti game, peta, dan pencarian data.