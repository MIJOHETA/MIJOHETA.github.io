# Rangkuman Materi Depth First Search (DFS)

## 1. Pengertian Depth First Search (DFS)

Depth First Search (DFS) adalah algoritma pencarian dan traversal yang digunakan untuk menjelajahi atau mencari node dalam struktur data graph atau tree. DFS mengeksplorasi sejauh mungkin sepanjang setiap cabang sebelum backtracking (mundur).

## 2. Karakteristik DFS

- **Strategi Pencarian**: Mengunjungi node secara mendalam (depth) terlebih dahulu
- **Struktur Data**: Menggunakan Stack (LIFO - Last In First Out)
- **Kompleksitas Waktu**: O(V + E) dimana V = jumlah vertex, E = jumlah edge
- **Kompleksitas Ruang**: O(V) untuk menyimpan visited nodes

## 3. Algoritma DFS

### Pseudocode:
```
DFS(graph, start_vertex):
    create a stack
    create a set to store visited vertices
    
    push start_vertex to stack
    
    while stack is not empty:
        current_vertex = pop from stack
        
        if current_vertex not in visited:
            mark current_vertex as visited
            process current_vertex
            
            for each neighbor of current_vertex:
                if neighbor not visited:
                    push neighbor to stack
```

### Implementasi Rekursif:
```
DFS_Recursive(graph, vertex, visited):
    mark vertex as visited
    process vertex
    
    for each neighbor of vertex:
        if neighbor not visited:
            DFS_Recursive(graph, neighbor, visited)
```

## 4. Langkah-langkah Pelaksanaan DFS

1. **Inisialisasi**: Pilih node awal dan tandai sebagai visited
2. **Eksplorasi**: Kunjungi node tetangga yang belum dikunjungi
3. **Rekursi/Iterasi**: Lanjutkan DFS dari node yang baru dikunjungi
4. **Backtracking**: Jika tidak ada tetangga yang belum dikunjungi, kembali ke node sebelumnya
5. **Terminasi**: Berhenti ketika semua node telah dikunjungi atau target ditemukan

## 5. Contoh Implementasi

### Implementasi dalam Python:
```python
def dfs_iterative(graph, start):
    visited = set()
    stack = [start]
    result = []
    
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            result.append(vertex)
            
            # Tambahkan tetangga ke stack
            for neighbor in graph[vertex]:
                if neighbor not in visited:
                    stack.append(neighbor)
    
    return result

def dfs_recursive(graph, vertex, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(vertex)
    print(vertex)
    
    for neighbor in graph[vertex]:
        if neighbor not in visited:
            dfs_recursive(graph, neighbor, visited)
```

## 6. Aplikasi DFS

### Kegunaan Utama:
- **Pencarian Path**: Menemukan jalur antara dua node
- **Deteksi Siklus**: Mengidentifikasi cycle dalam graph
- **Topological Sorting**: Mengurutkan node berdasarkan dependensi
- **Connected Components**: Menemukan komponen yang terhubung
- **Maze Solving**: Menyelesaikan labirin
- **Tree Traversal**: Traversal pohon (preorder, postorder)

### Contoh Kasus:
- Navigasi website (web crawling)
- Analisis jaringan sosial
- Pencarian dalam game (AI pathfinding)
- Analisis dependensi dalam software

## 7. Kelebihan dan Kekurangan

### Kelebihan:
- Sederhana untuk diimplementasikan
- Efisien untuk graph yang tidak terlalu dalam
- Menggunakan memori yang relatif sedikit
- Cocok untuk mencari solusi yang berada jauh dari root

### Kekurangan:
- Dapat terjebak dalam infinite loop pada graph dengan cycle
- Tidak optimal untuk mencari jalur terpendek
- Bisa lambat pada graph yang sangat dalam
- Tidak menjamin solusi optimal

## 8. Perbandingan dengan BFS

| Aspek | DFS | BFS |
|-------|-----|-----|
| Struktur Data | Stack | Queue |
| Strategi | Depth-first | Breadth-first |
| Memori | O(h) dimana h = tinggi | O(w) dimana w = lebar |
| Jalur Terpendek | Tidak dijamin | Dijamin untuk unweighted graph |
| Implementasi | Lebih sederhana | Sedikit lebih kompleks |

## 9. Variasi DFS

### DFS Tree:
- Spanning tree yang dibentuk dari hasil DFS traversal
- Edges dibagi menjadi: tree edges, back edges, forward edges, cross edges

### DFS dengan Timestamp:
- Memberikan discovery time dan finishing time pada setiap node
- Berguna untuk aplikasi seperti topological sort

## 10. Kesimpulan

DFS adalah algoritma fundamental dalam computer science yang sangat berguna untuk berbagai aplikasi graph traversal. Meskipun tidak selalu optimal untuk semua kasus, DFS menyediakan pendekatan yang efisien dan mudah dipahami untuk eksplorasi graph secara sistematis.

---

*Catatan: Rangkuman ini dibuat berdasarkan konsep umum DFS. Untuk detail spesifik sesuai dengan materi kelompok, silakan bagikan konten dokumen yang lebih lengkap.*