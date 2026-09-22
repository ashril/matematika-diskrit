# Pertemuan 9 — Konsep Dasar Graf

## Tema
**Jaringan di Sekitar Kita: Memodelkan Hubungan sebagai Graf**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menjelaskan definisi graf beserta elemen-elemennya (vertex, edge, degree);
2. membedakan graf berarah, tidak berarah, berbobot, sederhana, dan lengkap;
3. menjelaskan konsep path, cycle, dan keterhubungan graf;
4. merepresentasikan graf sederhana dalam Python menggunakan dictionary;
5. menghitung degree setiap vertex;
6. memodelkan jaringan laboratorium komputer sebagai graf.

---

## 1. Teori Ringkas

### 1.1 Definisi Graf

**Graf** G = (V, E) terdiri dari:
- **V** (*Vertex* / Simpul): himpunan titik/node
- **E** (*Edge* / Sisi): himpunan pasangan vertex yang terhubung

**Contoh sederhana:**

```text
     A
    / \
   B   C
    \ /
     D

V = {A, B, C, D}
E = {(A,B), (A,C), (B,D), (C,D)}
```

### 1.2 Jenis-Jenis Graf

| Jenis | Keterangan | Contoh Aplikasi |
|-------|-----------|-----------------|
| **Graf tidak berarah** | Edge tidak punya arah; (u,v) = (v,u) | Jaringan pertemanan |
| **Graf berarah (digraph)** | Edge punya arah; (u,v) ≠ (v,u) | Web links, Twitter follow |
| **Graf berbobot** | Setiap edge punya nilai/bobot | Peta jalan dengan jarak |
| **Graf sederhana** | Tidak ada self-loop dan multi-edge | Kebanyakan model jaringan |
| **Graf lengkap (Kₙ)** | Setiap pasangan vertex terhubung | Jaringan fully connected |
| **Graf terhubung** | Ada path antara semua pasangan vertex | Jaringan yang berfungsi |

### 1.3 Degree

**Degree** dari vertex v adalah jumlah edge yang terhubung ke v.

- Dalam graf tidak berarah: degree(v) = jumlah tetangga v
- Dalam graf berarah:
  - **In-degree**: jumlah edge masuk ke v
  - **Out-degree**: jumlah edge keluar dari v

> **Teorema Handshaking:**  
> Jumlah seluruh degree semua vertex = 2 × |E|  
> Karena setiap edge menghubungkan dua vertex.

### 1.4 Path dan Cycle

| Konsep | Definisi |
|--------|----------|
| **Path** | Urutan vertex v₁, v₂, …, vₙ di mana setiap pasangan berurutan terhubung edge |
| **Simple path** | Path tanpa pengulangan vertex |
| **Cycle** | Path tertutup (v₁ = vₙ) |
| **Connected graph** | Terdapat path antara setiap pasangan vertex |

---

## 2. Praktikum

### 2.1 Membuat Graf dengan Dictionary

Buat file `pertemuan-09/graf_dasar.py`:

```python
# Graf tidak berarah direpresentasikan sebagai adjacency list (dictionary)
# Kunci: vertex, Nilai: daftar tetangga

graf = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E'],
}

# Menampilkan informasi dasar graf
def info_graf(g):
    vertices = list(g.keys())
    edges = []
    for u in g:
        for v in g[u]:
            if (v, u) not in edges:   # hindari duplikasi (graf tidak berarah)
                edges.append((u, v))

    print("Vertex (V):", vertices)
    print("Jumlah vertex |V| =", len(vertices))
    print()
    print("Edge (E):", edges)
    print("Jumlah edge |E| =", len(edges))
    print()
    print(f"{'Vertex':>8} {'Degree':>8} {'Tetangga'}")
    print("-" * 40)
    for v in vertices:
        tetangga = g[v]
        print(f"{v:>8} {len(tetangga):>8}  {tetangga}")
    print()

    # Verifikasi Teorema Handshaking
    total_degree = sum(len(g[v]) for v in g)
    print(f"Total degree semua vertex = {total_degree}")
    print(f"2 × |E| = {2 * len(edges)}")
    print(f"Teorema Handshaking terpenuhi: {total_degree == 2 * len(edges)}")

info_graf(graf)
```

### 2.2 Menentukan Path

```python
def ada_path(g, awal, tujuan, dikunjungi=None):
    """Memeriksa apakah ada path dari awal ke tujuan (rekursif DFS)."""
    if dikunjungi is None:
        dikunjungi = set()
    if awal == tujuan:
        return True
    dikunjungi.add(awal)
    for tetangga in g.get(awal, []):
        if tetangga not in dikunjungi:
            if ada_path(g, tetangga, tujuan, dikunjungi):
                return True
    return False

# Uji path
pasangan_uji = [('A', 'F'), ('D', 'C'), ('D', 'D'), ('A', 'Z')]
for awal, tujuan in pasangan_uji:
    print(f"Ada path dari {awal} ke {tujuan}? {ada_path(graf, awal, tujuan)}")
```

### 2.3 Visualisasi Graf (dengan NetworkX)

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_edges_from([('A','B'), ('A','C'), ('B','D'), ('B','E'), ('C','F'), ('E','F')])

plt.figure(figsize=(8, 5))
pos = nx.spring_layout(G, seed=42)
nx.draw(G, pos,
        with_labels=True,
        node_color='steelblue',
        node_size=800,
        font_color='white',
        font_weight='bold',
        edge_color='gray',
        width=2)
plt.title("Graf Tidak Berarah Sederhana")
plt.tight_layout()
plt.savefig("graf_dasar.png", dpi=150)
plt.show()
```

---

## 3. PBL — Jaringan Laboratorium Komputer

### Skenario

Laboratorium komputer kampus memiliki beberapa perangkat yang saling terhubung melalui kabel jaringan (LAN). Setiap perangkat dianggap sebagai **vertex** dan setiap koneksi kabel sebagai **edge**.

**Topologi jaringan:**

```text
   Server
   /    \
 PC-1   Switch
   \    /   \
   PC-2    PC-3
             |
           Printer
```

**Pertanyaan:**
1. Berapa degree setiap vertex?
2. Apakah jaringan ini connected?
3. Apakah terdapat cycle?
4. Jika kabel antara PC-2 dan Switch putus, apakah Printer masih terhubung ke Server?

### Implementasi

Buat file `pertemuan-09/jaringan_lab.py`:

```python
# Pemodelan jaringan laboratorium sebagai graf tidak berarah
jaringan = {
    'Server' : ['PC-1', 'Switch'],
    'PC-1'   : ['Server', 'PC-2'],
    'PC-2'   : ['PC-1', 'Switch'],
    'Switch' : ['Server', 'PC-2', 'PC-3'],
    'PC-3'   : ['Switch', 'Printer'],
    'Printer': ['PC-3'],
}

def analisis_jaringan(g):
    print("=" * 50)
    print("ANALISIS JARINGAN LABORATORIUM")
    print("=" * 50)

    # Hitung edge unik
    edges = []
    for u in g:
        for v in g[u]:
            if (v, u) not in edges:
                edges.append((u, v))

    print(f"\nJumlah perangkat (vertex) : {len(g)}")
    print(f"Jumlah koneksi (edge)     : {len(edges)}")

    print(f"\n{'Perangkat':<12} {'Degree':>8} {'Terhubung ke'}")
    print("-" * 50)
    for v, tetangga in g.items():
        print(f"{v:<12} {len(tetangga):>8}  {tetangga}")

    # Cek keterhubungan (BFS sederhana)
    semua_vertex = list(g.keys())
    awal = semua_vertex[0]
    dikunjungi = set()
    antrian = [awal]
    while antrian:
        node = antrian.pop(0)
        dikunjungi.add(node)
        for tetangga in g.get(node, []):
            if tetangga not in dikunjungi:
                antrian.append(tetangga)

    terhubung = len(dikunjungi) == len(semua_vertex)
    print(f"\nJaringan connected: {terhubung}")
    if not terhubung:
        terisolasi = set(semua_vertex) - dikunjungi
        print(f"Perangkat terisolasi: {terisolasi}")

    # Simulasi: putus koneksi PC-2 — Switch
    print("\n--- Simulasi: Kabel PC-2 ↔ Switch putus ---")
    jaringan_rusak = {k: [x for x in v if not (k == 'PC-2' and x == 'Switch')
                                           and not (k == 'Switch' and x == 'PC-2')]
                     for k, v in g.items()}

    awal2 = 'Server'
    dikunjungi2 = set()
    antrian2 = [awal2]
    while antrian2:
        node = antrian2.pop(0)
        dikunjungi2.add(node)
        for tetangga in jaringan_rusak.get(node, []):
            if tetangga not in dikunjungi2:
                antrian2.append(tetangga)

    printer_terhubung = 'Printer' in dikunjungi2
    print(f"Printer masih terhubung ke Server: {printer_terhubung}")

analisis_jaringan(jaringan)
```

---

## 4. Latihan dan Refleksi

### Latihan 1
Gambar graf berikut dan hitung degree setiap vertex:
```
V = {1, 2, 3, 4, 5}
E = {(1,2), (1,3), (2,4), (3,4), (4,5)}
```
Verifikasi Teorema Handshaking.

### Latihan 2
Tambahkan vertex "Laptop" ke jaringan laboratorium yang terhubung ke Switch dan PC-1.
- Berapa degree Switch sekarang?
- Apakah masih connected jika Laptop dihapus?

### Latihan 3
Buatlah program Python yang menentukan apakah dua vertex dalam sebuah graf merupakan **tetangga langsung** (adjacent).

### Refleksi
1. Apa perbedaan utama antara graf berarah dan tidak berarah dalam konteks jaringan komputer?
2. Mengapa Teorema Handshaking berguna untuk memverifikasi representasi graf?
3. Dalam situasi apa sebuah jaringan yang tidak connected menjadi masalah serius?
4. Bagaimana cara mendeteksi cycle dalam sebuah graf?

---

## Checklist

- [ ] Definisi graf (vertex, edge, degree)
- [ ] Jenis-jenis graf (berarah, tidak berarah, berbobot, lengkap)
- [ ] Path dan cycle
- [ ] Teorema Handshaking
- [ ] Implementasi graf dengan dictionary (adjacency list)
- [ ] Menghitung degree setiap vertex
- [ ] Pemeriksaan path
- [ ] Visualisasi graf dengan NetworkX
- [ ] Pemodelan dan analisis jaringan laboratorium
- [ ] Simulasi kerusakan koneksi
