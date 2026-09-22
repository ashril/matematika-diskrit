# Pertemuan 12 — Asesmen Modul 3

## Graph Challenge — Analisis Jaringan Berbobot

---

## Skenario

Sebuah perusahaan teknologi memiliki **5 kantor** (A, B, C, D, E) yang dihubungkan oleh jaringan WAN. Setiap koneksi memiliki **latency** (dalam milidetik) yang berbeda-beda. Tim jaringan harus menganalisis topologi ini dan mencari jalur komunikasi yang paling efisien.

**Topologi jaringan:**

```text
    A ─── B
    │     │
    │     │
    C ─── D ─── E
```

**Bobot setiap koneksi (latency dalam ms):**

| Koneksi | Latency (ms) |
|---------|-------------|
| A — B   | 4 |
| A — C   | 2 |
| B — D   | 5 |
| C — D   | 1 |
| D — E   | 3 |
| B — E   | 8 |

---

## Tahapan Penyelesaian Wajib

Selesaikan semua tahapan berikut secara berurutan dan dokumentasikan setiap langkah:

```text
1. Identifikasi Masalah
        ↓
2. Pemodelan Graf
        ↓
3. Representasi Graf (Matrix + List)
        ↓
4. Analisis Struktur Graf
        ↓
5. Implementasi Algoritma
        ↓
6. Pengujian dan Validasi
        ↓
7. Analisis dan Kesimpulan
```

---

## Starter Code

```python
# ============================================================
# ASESMEN MODUL 3 — Graph Challenge
# Nama   :
# NIM    :
# Kelas  :
# Tanggal:
# ============================================================

import numpy as np
import heapq

# -----------------------------------------------------------
# Data Graf
# -----------------------------------------------------------
vertex = ['A', 'B', 'C', 'D', 'E']
n = len(vertex)
idx = {v: i for i, v in enumerate(vertex)}

# Daftar edge berbobot (u, v, bobot)
edges = [
    ('A', 'B', 4),
    ('A', 'C', 2),
    ('B', 'D', 5),
    ('C', 'D', 1),
    ('D', 'E', 3),
    ('B', 'E', 8),
]


# -----------------------------------------------------------
# Bagian 1: Buat Adjacency Matrix (NumPy)
# -----------------------------------------------------------
def buat_adj_matrix(vertex, edges):
    """
    Buat adjacency matrix berbobot menggunakan NumPy.
    Posisi tanpa edge diisi dengan 0.
    """
    n = len(vertex)
    idx = {v: i for i, v in enumerate(vertex)}
    adj = np.zeros((n, n), dtype=int)
    # TODO: isi matrix berdasarkan edges
    return adj, idx

adj_matrix, idx = buat_adj_matrix(vertex, edges)


# -----------------------------------------------------------
# Bagian 2: Tampilkan Adjacency Matrix
# -----------------------------------------------------------
def tampilkan_matrix(adj, vertex):
    """Tampilkan adjacency matrix dengan label vertex."""
    # TODO: tampilkan matrix dengan header baris dan kolom
    pass


# -----------------------------------------------------------
# Bagian 3: Hitung Degree Setiap Vertex
# -----------------------------------------------------------
def hitung_degree(adj, vertex):
    """
    Hitung degree setiap vertex dari adjacency matrix.
    Degree = jumlah koneksi aktif (nilai > 0) per baris.
    """
    # TODO: implementasikan dan tampilkan
    pass


# -----------------------------------------------------------
# Bagian 4: Tentukan Path dari A ke E
# -----------------------------------------------------------
def cari_semua_path(graf_list, awal, tujuan):
    """
    Mencari semua simple path dari awal ke tujuan menggunakan DFS.
    Mengembalikan list of list (setiap elemen = satu path).
    """
    # TODO: implementasikan
    pass


# -----------------------------------------------------------
# Bagian 5: Implementasi Dijkstra
# -----------------------------------------------------------
def dijkstra(graf_berbobot, sumber):
    """
    Algoritma Dijkstra untuk shortest path.
    graf_berbobot: dict { vertex: [(tetangga, bobot), ...] }
    """
    # TODO: implementasikan
    pass

def rekonstruksi_path(prev, sumber, tujuan):
    """Rekonstruksi path dari sumber ke tujuan."""
    # TODO: implementasikan
    pass


# -----------------------------------------------------------
# Buat adjacency list berbobot untuk Dijkstra
# -----------------------------------------------------------
graf_berbobot = {v: [] for v in vertex}
for u, v, w in edges:
    graf_berbobot[u].append((v, w))
    graf_berbobot[v].append((u, w))   # tidak berarah


# -----------------------------------------------------------
# Jalankan dan Tampilkan Semua Hasil
# -----------------------------------------------------------
print("=" * 60)
print("GRAPH CHALLENGE — ANALISIS JARINGAN BERBOBOT")
print("=" * 60)

print("\n[1] Adjacency Matrix:")
tampilkan_matrix(adj_matrix, vertex)

print("\n[2] Degree Setiap Vertex:")
hitung_degree(adj_matrix, vertex)

print("\n[3] Semua Path dari A ke E:")
# TODO: panggil cari_semua_path dan tampilkan

print("\n[4] Shortest Path (Dijkstra) dari A ke semua vertex:")
# TODO: panggil dijkstra dan tampilkan

print("\n[5] Shortest Path dari A ke E:")
# TODO: tampilkan path dan total latency
```

---

## Produk yang Dikumpulkan

### 1. Pemodelan Graf
- Gambarkan topologi jaringan (boleh manual atau dengan NetworkX).
- Identifikasi: jumlah vertex, edge, degree setiap vertex.
- Apakah graf ini connected? Apakah ada cycle?

### 2. Representasi Graf
- Adjacency matrix (NumPy) — lengkap dengan label.
- Adjacency list — dalam format dictionary Python.

### 3. Analisis Struktur
- Degree setiap vertex, vertex dengan degree tertinggi.
- Total latency seluruh jaringan.

### 4. Implementasi Algoritma
- Semua path dari A ke E (menggunakan DFS).
- Shortest path dari A ke semua vertex (Dijkstra).
- Rekonstruksi path A → E beserta total latency-nya.

### 5. Tabel Pengujian

| Query | Hasil yang Diharapkan | Hasil Program | Status |
|-------|-----------------------|---------------|--------|
| Degree A | 2 | | |
| Degree D | 3 | | |
| Koneksi A—E langsung? | Tidak ada | | |
| Shortest path A→E | A→C→D→E | | |
| Latency A→E terpendek | 6 ms | | |
| Shortest path A→B | A→C→D→B atau A→B? | | |

### 6. Dokumentasi dan Analisis
- Penjelasan langkah-langkah Dijkstra pada graf ini.
- Visualisasi graf dengan bobot dan highlight shortest path.
- Kesimpulan: koneksi mana yang paling kritis dalam jaringan?

---

## Rubrik Penilaian

| Komponen | Bobot |
|----------|------:|
| Pemodelan graf (vertex, edge, degree, path) | 15% |
| Representasi (adjacency matrix + list) | 20% |
| Implementasi algoritma (DFS + Dijkstra) | 30% |
| Pengujian dan validasi | 20% |
| Dokumentasi dan visualisasi | 15% |

---

## Refleksi Asesmen

1. Mengapa jalur A → C → D → E lebih pendek dari A → B → D → E, padahal tampak lebih "tidak langsung"?
2. Apa yang terjadi jika bobot koneksi A—C berubah dari 2 ms menjadi 10 ms? Apakah shortest path berubah?
3. Dalam konteks jaringan komputer nyata, apa dampak dari latency yang tinggi pada suatu edge?
4. Bagaimana Dijkstra berbeda dengan pendekatan bruteforce (mencoba semua path)?
