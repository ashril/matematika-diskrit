# Pertemuan 10 — Representasi Graf

## Tema
**Menyimpan Graf di Komputer: Matriks dan List**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. merepresentasikan graf menggunakan **adjacency matrix** dan **adjacency list**;
2. membangun dan mengoperasikan adjacency matrix menggunakan **NumPy**;
3. menjelaskan perbedaan efisiensi antara adjacency matrix dan adjacency list;
4. menghitung degree matrix dari adjacency matrix;
5. merepresentasikan graf berbobot dalam matriks;
6. memodelkan jaringan router kampus menggunakan NumPy.

---

## 1. Teori Ringkas

### 1.1 Adjacency Matrix

**Adjacency Matrix** A adalah matriks n × n di mana n = |V|.

$$A[i][j] = \begin{cases} 1 & \text{jika ada edge antara vertex } i \text{ dan } j \\ 0 & \text{jika tidak ada edge} \end{cases}$$

**Graf tidak berarah:** matriks simetris (A[i][j] = A[j][i])  
**Graf berarah:** matriks tidak harus simetris

**Contoh:**

```text
Graf:         Adjacency Matrix:
  A — B         A  B  C  D
  |   |      A [0, 1, 1, 0]
  C — D      B [1, 0, 0, 1]
             C [1, 0, 0, 1]
             D [0, 1, 1, 0]
```

### 1.2 Graf Berbobot

Untuk graf berbobot, ganti nilai 1 dengan bobot edge dan 0 dengan ∞ (atau 0 jika tidak ada edge):

$$A[i][j] = \begin{cases} w_{ij} & \text{jika ada edge dengan bobot } w \\ 0 \text{ atau } \infty & \text{jika tidak ada edge} \end{cases}$$

### 1.3 Adjacency List

**Adjacency List** menyimpan daftar tetangga setiap vertex menggunakan dictionary atau list of lists.

```python
# Adjacency List (dictionary)
graf = {
    'A': ['B', 'C'],
    'B': ['A', 'D'],
    'C': ['A', 'D'],
    'D': ['B', 'C'],
}
```

### 1.4 Perbandingan

| Aspek | Adjacency Matrix | Adjacency List |
|-------|-----------------|----------------|
| **Ruang memori** | O(V²) — selalu besar | O(V + E) — efisien untuk jarang |
| **Cek edge (u,v)** | O(1) — sangat cepat | O(degree(u)) |
| **Iterasi tetangga** | O(V) — harus scan baris | O(degree(v)) — langsung |
| **Cocok untuk** | Graf padat (dense) | Graf jarang (sparse) |

---

## 2. Praktikum

### 2.1 Adjacency Matrix dengan NumPy

Buat file `pertemuan-10/representasi_graf.py`:

```python
import numpy as np

# Definisikan vertex
vertex = ['A', 'B', 'C', 'D', 'E']
n = len(vertex)
idx = {v: i for i, v in enumerate(vertex)}

# Definisikan edge (graf tidak berarah)
edges = [('A','B'), ('A','C'), ('B','D'), ('C','D'), ('D','E')]

# Buat adjacency matrix (numpy array)
adj_matrix = np.zeros((n, n), dtype=int)

for u, v in edges:
    i, j = idx[u], idx[v]
    adj_matrix[i][j] = 1
    adj_matrix[j][i] = 1   # tidak berarah → simetris

# Tampilkan adjacency matrix
print("Adjacency Matrix:")
print(f"{'':>4}", end="")
for v in vertex:
    print(f"{v:>4}", end="")
print()

for i, v in enumerate(vertex):
    print(f"{v:>4}", end="")
    for val in adj_matrix[i]:
        print(f"{val:>4}", end="")
    print()

# Degree setiap vertex (jumlah 1 di setiap baris)
print("\nDegree setiap vertex:")
degrees = np.sum(adj_matrix, axis=1)
for i, v in enumerate(vertex):
    print(f"  degree({v}) = {degrees[i]}")

print(f"\nTotal degree = {np.sum(degrees)}")
print(f"2 × |E|     = {2 * len(edges)}")

# Degree Matrix
degree_matrix = np.diag(degrees)
print("\nDegree Matrix D:")
print(degree_matrix)

# Laplacian Matrix L = D - A (berguna untuk analisis graf lanjut)
laplacian = degree_matrix - adj_matrix
print("\nLaplacian Matrix L = D - A:")
print(laplacian)
```

### 2.2 Graf Berbobot

```python
import numpy as np

vertex = ['A', 'B', 'C', 'D', 'E']
n = len(vertex)
idx = {v: i for i, v in enumerate(vertex)}

# Graf berbobot (u, v, bobot)
edges_berbobot = [
    ('A', 'B', 4),
    ('A', 'C', 2),
    ('B', 'D', 5),
    ('C', 'D', 1),
    ('D', 'E', 3),
    ('B', 'E', 6),
]

# Gunakan np.inf untuk "tidak ada edge"
adj_berbobot = np.full((n, n), np.inf)
np.fill_diagonal(adj_berbobot, 0)   # jarak ke diri sendiri = 0

for u, v, w in edges_berbobot:
    i, j = idx[u], idx[v]
    adj_berbobot[i][j] = w
    adj_berbobot[j][i] = w   # tidak berarah

print("Adjacency Matrix Berbobot (∞ = tidak terhubung):")
print(f"{'':>4}", end="")
for v in vertex:
    print(f"{v:>7}", end="")
print()

for i, v in enumerate(vertex):
    print(f"{v:>4}", end="")
    for val in adj_berbobot[i]:
        s = "∞" if np.isinf(val) else str(int(val))
        print(f"{s:>7}", end="")
    print()
```

### 2.3 Konversi Adjacency Matrix ke Adjacency List

```python
def matrix_ke_list(adj_matrix, vertex):
    """Konversi adjacency matrix ke adjacency list (dictionary)."""
    adj_list = {}
    for i, u in enumerate(vertex):
        adj_list[u] = []
        for j, v in enumerate(vertex):
            if adj_matrix[i][j] != 0 and not np.isinf(adj_matrix[i][j]):
                adj_list[u].append(v)
    return adj_list

adj_list = matrix_ke_list(adj_matrix, vertex)
print("\nAdjacency List:")
for v, tetangga in adj_list.items():
    print(f"  {v}: {tetangga}")
```

---

## 3. PBL — Jaringan Router Kampus

### Skenario

Tim IT kampus memetakan koneksi antar router. Setiap router terhubung dengan kabel fiber optik yang memiliki kapasitas bandwidth berbeda (dalam Mbps).

**Topologi:**

```text
Router:  R1, R2, R3, R4, R5

Koneksi dan bandwidth (Mbps):
  R1 — R2 : 100
  R1 — R3 : 50
  R2 — R3 : 75
  R2 — R4 : 200
  R3 — R5 : 60
  R4 — R5 : 150
```

**Tugas:**
1. Buat adjacency matrix berbobot menggunakan NumPy.
2. Hitung degree setiap router.
3. Temukan router dengan konektivitas tertinggi (degree terbesar).
4. Tentukan apakah ada koneksi langsung antara R1 dan R5.

### Implementasi

Buat file `pertemuan-10/jaringan_router.py`:

```python
import numpy as np

router = ['R1', 'R2', 'R3', 'R4', 'R5']
n = len(router)
idx = {r: i for i, r in enumerate(router)}

# Koneksi dan bandwidth (Mbps)
koneksi = [
    ('R1', 'R2', 100),
    ('R1', 'R3',  50),
    ('R2', 'R3',  75),
    ('R2', 'R4', 200),
    ('R3', 'R5',  60),
    ('R4', 'R5', 150),
]

# Buat adjacency matrix berbobot
adj = np.zeros((n, n), dtype=float)
for u, v, w in koneksi:
    i, j = idx[u], idx[v]
    adj[i][j] = w
    adj[j][i] = w

# Tampilkan matrix
print("Adjacency Matrix Jaringan Router (bandwidth Mbps):")
print(f"{'':>5}", end="")
for r in router:
    print(f"{r:>7}", end="")
print()
for i, r in enumerate(router):
    print(f"{r:>5}", end="")
    for val in adj[i]:
        s = str(int(val)) if val > 0 else "-"
        print(f"{s:>7}", end="")
    print()

# Degree setiap router (jumlah koneksi aktif)
print("\nDegree setiap router:")
for i, r in enumerate(router):
    degree = int(np.sum(adj[i] > 0))
    print(f"  {r}: degree = {degree}")

# Router dengan konektivitas tertinggi
degree_list = [int(np.sum(adj[i] > 0)) for i in range(n)]
max_degree = max(degree_list)
router_terbaik = [router[i] for i, d in enumerate(degree_list) if d == max_degree]
print(f"\nRouter dengan degree tertinggi ({max_degree}): {router_terbaik}")

# Cek koneksi langsung R1 — R5
i_r1, i_r5 = idx['R1'], idx['R5']
print(f"\nKoneksi langsung R1 — R5: {'Ada' if adj[i_r1][i_r5] > 0 else 'Tidak ada'}")

# Total bandwidth dalam jaringan
total_bw = np.sum(adj) / 2   # dibagi 2 karena matriks simetris
print(f"Total bandwidth jaringan: {int(total_bw)} Mbps")
```

---

## 4. Latihan dan Refleksi

### Latihan 1
Diberikan adjacency matrix berikut:
```python
A = np.array([
    [0, 1, 0, 1],
    [1, 0, 1, 0],
    [0, 1, 0, 1],
    [1, 0, 1, 0],
])
```
- Gambarkan grafnya.
- Berapa degree setiap vertex?
- Apakah graf ini connected?

### Latihan 2
Tambahkan router baru "R6" yang terhubung ke R3 (bandwidth 80 Mbps) dan R4 (bandwidth 120 Mbps).
- Update adjacency matrix.
- Hitung ulang degree setiap router.

### Latihan 3
Buat fungsi `cek_koneksi(adj, v1, v2, vertex)` yang mengembalikan bandwidth koneksi antara dua router, atau 0 jika tidak terhubung langsung.

### Refleksi
1. Kapan sebaiknya menggunakan adjacency matrix vs adjacency list?
2. Apa keuntungan menggunakan NumPy untuk adjacency matrix dibanding list 2D biasa?
3. Apa arti nilai pada diagonal adjacency matrix (A[i][i])? Kapan nilainya bukan 0?
4. Mengapa Laplacian Matrix penting dalam analisis jaringan?

---

## Checklist

- [ ] Adjacency matrix (graf tidak berbobot)
- [ ] Adjacency matrix (graf berbobot)
- [ ] Implementasi dengan NumPy
- [ ] Degree matrix
- [ ] Laplacian matrix
- [ ] Adjacency list (dictionary)
- [ ] Konversi matrix ↔ list
- [ ] Perbandingan efisiensi matrix vs list
- [ ] Program jaringan router kampus
- [ ] Minimal 4 query analisis
