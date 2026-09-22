# Pertemuan 11 — Algoritma Graf dan Shortest Path

## Tema
**Menemukan Jalur Terpendek: BFS, DFS, dan Algoritma Dijkstra**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menjelaskan strategi traversal BFS (Breadth-First Search) dan DFS (Depth-First Search);
2. mengimplementasikan BFS dan DFS menggunakan Python;
3. menjelaskan konsep greedy dan penerapannya pada pencarian jalur;
4. memahami konsep relaksasi edge pada algoritma Dijkstra;
5. mengimplementasikan algoritma Dijkstra untuk mencari shortest path;
6. menerapkan Dijkstra untuk navigasi kampus.

---

## 1. Teori Ringkas

### 1.1 Graph Traversal

**Traversal** adalah proses mengunjungi semua vertex dalam graf secara sistematis.

#### BFS (Breadth-First Search)

BFS menggunakan **antrian (queue)**. Ia mengunjungi semua tetangga satu level terlebih dahulu sebelum melanjutkan ke level berikutnya — seperti menyebar gelombang dari titik awal.

```text
Mulai dari A:
Level 0: A
Level 1: B, C
Level 2: D, E, F
```

**Kegunaan:**
- Menemukan path terpendek (dalam jumlah edge) pada graf tak berbobot
- Cek keterhubungan graf

#### DFS (Depth-First Search)

DFS menggunakan **stack (atau rekursi)**. Ia menjelajah sejauh mungkin sebelum kembali (backtrack).

```text
Mulai dari A (urutan alfabetis):
A → B → D → (kembali) → E → (kembali) → C → F
```

**Kegunaan:**
- Deteksi cycle
- Topological sort
- Komponen terhubung

### 1.2 Strategi Greedy

**Greedy** adalah strategi yang selalu memilih opsi terbaik **secara lokal** pada setiap langkah, berharap menghasilkan solusi optimal secara global. Algoritma Dijkstra menggunakan strategi greedy.

### 1.3 Algoritma Dijkstra

Dijkstra mencari **jalur terpendek** dari satu sumber ke semua vertex lain pada **graf berbobot dengan bobot non-negatif**.

**Konsep Relaksasi Edge:**

> Jika kita menemukan path ke vertex v melalui u yang **lebih pendek** dari jarak v yang diketahui saat ini, maka kita "relaksasi" (perbarui) jarak v.

$$\text{jika } dist[u] + w(u,v) < dist[v] \text{ maka } dist[v] = dist[u] + w(u,v)$$

**Langkah-langkah Dijkstra:**

```text
ALGORITMA Dijkstra(G, sumber)
INPUT : Graf G berbobot, vertex sumber
OUTPUT: Jarak terpendek dari sumber ke semua vertex

START
    inisialisasi dist[v] = ∞ untuk semua v (kecuali sumber = 0)
    inisialisasi set S = {} (vertex yang sudah final)
    inisialisasi prev[v] = None (untuk rekonstruksi path)

    SELAMA ada vertex yang belum final:
        u = vertex belum final dengan dist terkecil
        tambahkan u ke S

        UNTUK setiap tetangga v dari u:
            JIKA dist[u] + w(u,v) < dist[v]:
                dist[v] = dist[u] + w(u,v)
                prev[v] = u   # catat vertex sebelumnya

    kembalikan dist, prev
END
```

---

## 2. Praktikum

### 2.1 Implementasi BFS

Buat file `pertemuan-11/bfs.py`:

```python
from collections import deque

def bfs(graf, awal):
    """
    Breadth-First Search.
    Mengembalikan urutan vertex yang dikunjungi dan jarak dari awal.
    """
    dikunjungi = set()
    antrian = deque([(awal, 0)])   # (vertex, jarak)
    urutan = []
    jarak = {awal: 0}

    while antrian:
        vertex, d = antrian.popleft()
        if vertex in dikunjungi:
            continue
        dikunjungi.add(vertex)
        urutan.append(vertex)

        for tetangga in sorted(graf.get(vertex, [])):
            if tetangga not in dikunjungi:
                antrian.append((tetangga, d + 1))
                if tetangga not in jarak:
                    jarak[tetangga] = d + 1

    return urutan, jarak

# Graf contoh
graf = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E'],
}

urutan_bfs, jarak_bfs = bfs(graf, 'A')
print("BFS dari A:")
print("  Urutan kunjungan:", urutan_bfs)
print("  Jarak dari A:")
for v, j in sorted(jarak_bfs.items()):
    print(f"    A → {v} = {j} edge")
```

### 2.2 Implementasi DFS

Buat file `pertemuan-11/dfs.py`:

```python
def dfs(graf, awal, dikunjungi=None, urutan=None):
    """
    Depth-First Search (rekursif).
    Mengembalikan urutan vertex yang dikunjungi.
    """
    if dikunjungi is None:
        dikunjungi = set()
        urutan = []

    dikunjungi.add(awal)
    urutan.append(awal)

    for tetangga in sorted(graf.get(awal, [])):
        if tetangga not in dikunjungi:
            dfs(graf, tetangga, dikunjungi, urutan)

    return urutan

graf = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E'],
}

urutan_dfs = dfs(graf, 'A')
print("DFS dari A:")
print("  Urutan kunjungan:", urutan_dfs)
```

### 2.3 Implementasi Dijkstra

Buat file `pertemuan-11/dijkstra.py`:

```python
import heapq

def dijkstra(graf_berbobot, sumber):
    """
    Algoritma Dijkstra untuk shortest path.
    graf_berbobot: dict { vertex: [(tetangga, bobot), ...] }
    Mengembalikan (jarak, prev) untuk rekonstruksi path.
    """
    # Inisialisasi: semua jarak = tak hingga
    jarak = {v: float('inf') for v in graf_berbobot}
    jarak[sumber] = 0
    prev = {v: None for v in graf_berbobot}

    # Priority queue: (jarak, vertex)
    pq = [(0, sumber)]

    while pq:
        d, u = heapq.heappop(pq)

        # Abaikan jika sudah ada jarak yang lebih baik
        if d > jarak[u]:
            continue

        # Relaksasi setiap tetangga
        for v, bobot in graf_berbobot[u]:
            jarak_baru = jarak[u] + bobot
            if jarak_baru < jarak[v]:
                jarak[v] = jarak_baru
                prev[v] = u
                heapq.heappush(pq, (jarak_baru, v))

    return jarak, prev


def rekonstruksi_path(prev, sumber, tujuan):
    """Merekonstruksi path dari sumber ke tujuan menggunakan dict prev."""
    path = []
    node = tujuan
    while node is not None:
        path.append(node)
        node = prev[node]
    path.reverse()

    # Pastikan path valid (dimulai dari sumber)
    if path[0] == sumber:
        return path
    return []   # tidak ada path


# Graf navigasi kampus
kampus = {
    'Rektorat'    : [('Fakultas', 3), ('Perpustakaan', 7)],
    'Fakultas'    : [('Rektorat', 3), ('Laboratorium', 5), ('Masjid', 4)],
    'Perpustakaan': [('Rektorat', 7), ('Masjid', 2), ('Laboratorium', 8)],
    'Masjid'      : [('Fakultas', 4), ('Perpustakaan', 2), ('Laboratorium', 6)],
    'Laboratorium': [('Fakultas', 5), ('Perpustakaan', 8), ('Masjid', 6)],
}

# Cari jalur terpendek dari Rektorat ke semua gedung
sumber = 'Rektorat'
jarak, prev = dijkstra(kampus, sumber)

print(f"Jalur terpendek dari {sumber}:")
print("=" * 50)
for tujuan in kampus:
    if tujuan != sumber:
        path = rekonstruksi_path(prev, sumber, tujuan)
        path_str = " → ".join(path) if path else "Tidak ada path"
        print(f"  {sumber} → {tujuan}")
        print(f"    Path  : {path_str}")
        print(f"    Jarak : {jarak[tujuan]} menit")
        print()
```

Jalankan:

```bash
python dijkstra.py
```

---

## 3. PBL — Navigasi Kampus

### Skenario

Sistem navigasi kampus membantu mahasiswa menemukan rute terpendek antar gedung. Setiap jalan antara gedung memiliki jarak dalam menit berjalan kaki.

**Peta Kampus:**

```text
Rektorat ─3─ Fakultas ─5─ Laboratorium
    │             │              │
    7             4              6
    │             │              │
Perpustakaan ─2─ Masjid ────────┘
    │
    8
    └──────────────────────────────┘
```

**Pertanyaan Utama:** Berapa rute terpendek dari **Rektorat** ke **Laboratorium**?

### Visualisasi Graf

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()

edges = [
    ('Rektorat', 'Fakultas', 3),
    ('Rektorat', 'Perpustakaan', 7),
    ('Fakultas', 'Laboratorium', 5),
    ('Fakultas', 'Masjid', 4),
    ('Perpustakaan', 'Masjid', 2),
    ('Perpustakaan', 'Laboratorium', 8),
    ('Masjid', 'Laboratorium', 6),
]

G.add_weighted_edges_from(edges)

pos = nx.spring_layout(G, seed=10)
edge_labels = nx.get_edge_attributes(G, 'weight')

plt.figure(figsize=(10, 6))
nx.draw(G, pos,
        with_labels=True,
        node_color='steelblue',
        node_size=1500,
        font_color='white',
        font_weight='bold',
        edge_color='gray',
        width=2)
nx.draw_networkx_edge_labels(G, pos, edge_labels=edge_labels, font_size=10)
plt.title("Peta Navigasi Kampus (bobot = menit berjalan)")
plt.tight_layout()
plt.savefig("navigasi_kampus.png", dpi=150)
plt.show()
```

### Analisis Lanjutan

```python
# Bandingkan BFS vs Dijkstra
# BFS hanya menghitung jumlah edge, bukan bobot total
# Dijkstra menghitung total bobot minimum

# Konversi graf berbobot ke adjacency list tanpa bobot untuk BFS
from collections import deque

graf_tanpa_bobot = {k: [v for v, _ in vals] for k, vals in kampus.items()}

def bfs_jarak(g, awal, tujuan):
    antrian = deque([(awal, [awal])])
    dikunjungi = {awal}
    while antrian:
        v, path = antrian.popleft()
        if v == tujuan:
            return path
        for tetangga in g.get(v, []):
            if tetangga not in dikunjungi:
                dikunjungi.add(tetangga)
                antrian.append((tetangga, path + [tetangga]))
    return []

path_bfs = bfs_jarak(graf_tanpa_bobot, 'Rektorat', 'Laboratorium')
path_dijkstra = rekonstruksi_path(prev, 'Rektorat', 'Laboratorium')

print("Perbandingan BFS vs Dijkstra (Rektorat → Laboratorium):")
print(f"  BFS      : {' → '.join(path_bfs)} ({len(path_bfs)-1} langkah)")
print(f"  Dijkstra : {' → '.join(path_dijkstra)} ({jarak['Laboratorium']} menit)")
print("\nKesimpulan: BFS memberikan path dengan edge terpendek, Dijkstra memberikan bobot total minimum.")
```

---

## 4. Latihan dan Refleksi

### Latihan 1
Lakukan BFS dan DFS dari vertex 'Perpustakaan' pada peta kampus. Bandingkan urutan kunjungan kedua algoritma.

### Latihan 2
Tambahkan gedung "Kantin" dengan koneksi:
- Kantin — Masjid: 1 menit
- Kantin — Laboratorium: 3 menit

Jalankan ulang Dijkstra. Apakah rute dari Rektorat ke Laboratorium berubah?

### Latihan 3
Modifikasi Dijkstra untuk mengembalikan **semua jalur terpendek** dari satu sumber ke semua tujuan sekaligus (sudah dilakukan). Buat format output yang lebih rapi berupa tabel.

### Refleksi
1. Apa perbedaan utama antara BFS dan DFS dalam hal urutan kunjungan?
2. Mengapa Dijkstra tidak bekerja dengan baik jika ada edge berbobot negatif?
3. Apa yang dimaksud dengan "relaksasi edge"? Berikan contoh konkret.
4. Kapan BFS lebih tepat digunakan daripada Dijkstra?

---

## Checklist

- [ ] BFS — prinsip antrian (queue), implementasi Python
- [ ] DFS — prinsip stack/rekursi, implementasi Python
- [ ] Perbandingan BFS vs DFS
- [ ] Strategi greedy
- [ ] Konsep relaksasi edge
- [ ] Algoritma Dijkstra — implementasi dengan priority queue
- [ ] Rekonstruksi path dari `prev`
- [ ] Visualisasi graf kampus
- [ ] Analisis navigasi kampus
- [ ] Perbandingan BFS vs Dijkstra
