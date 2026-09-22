# Pertemuan 14 — Project Development

## Tema
**Membangun Solusi: Dari Model Matematika ke Program Python**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menerjemahkan model matematika menjadi algoritma yang konkret;
2. menulis pseudocode lengkap sebelum mengimplementasikan program;
3. mengimplementasikan solusi dalam Python yang terstruktur dan terdokumentasi;
4. mengintegrasikan minimal dua konsep matematika diskrit dalam satu program;
5. menghasilkan prototipe fungsional yang siap diuji.

---

## 1. Alur Pengembangan Wajib

Setiap kelompok **wajib** mengikuti alur berikut. Dokumentasikan setiap tahap dalam laporan:

```text
┌─────────────────────────────────────────────────────┐
│  1. MASALAH                                         │
│     Apa yang ingin diselesaikan?                    │
└─────────────────┬───────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────────────────┐
│  2. MODEL MATEMATIKA                                │
│     Tulis notasi formal: G=(V,E), himpunan,         │
│     fungsi, relasi, ekspresi logika                 │
└─────────────────┬───────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────────────────┐
│  3. ALGORITMA                                       │
│     Langkah-langkah penyelesaian dalam bahasa       │
│     natural (belum tergantung bahasa pemrograman)   │
└─────────────────┬───────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────────────────┐
│  4. PSEUDOCODE                                      │
│     Tulis dalam format pseudocode terstruktur       │
│     (INPUT, PROSES, OUTPUT)                         │
└─────────────────┬───────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────────────────┐
│  5. PYTHON                                          │
│     Implementasikan pseudocode menjadi kode Python  │
│     yang bersih dan terdokumentasi                  │
└─────────────────┬───────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────────────────┐
│  6. OUTPUT                                          │
│     Pastikan program menghasilkan output yang        │
│     dapat diverifikasi kebenarannya                 │
└─────────────────────────────────────────────────────┘
```

---

## 2. Panduan per Jenis Proyek

### 2.1 Proyek Berbasis Graf (Smart Campus Navigation / Analisis Jaringan)

**Model:**
```text
G = (V, E, W)
V = himpunan node (gedung/perangkat)
E = himpunan edge (jalur/koneksi)
W: E → ℝ⁺ (fungsi bobot)
```

**Algoritma yang digunakan:**
- Dijkstra untuk shortest path
- BFS/DFS untuk traversal dan analisis keterhubungan

**Struktur kode yang disarankan:**

```python
# Struktur program berbasis graf

# 1. Definisi data
vertex = [...]
edges = [(u, v, w), ...]

# 2. Bangun representasi graf
def buat_graf(vertex, edges):
    """Buat adjacency list berbobot."""
    graf = {v: [] for v in vertex}
    for u, v, w in edges:
        graf[u].append((v, w))
        graf[v].append((u, w))
    return graf

# 3. Algoritma utama
def dijkstra(graf, sumber):
    ...

def rekonstruksi_path(prev, sumber, tujuan):
    ...

# 4. Antarmuka / tampilan hasil
def tampilkan_hasil(jarak, prev, vertex, sumber):
    ...

# 5. Program utama
if __name__ == "__main__":
    graf = buat_graf(vertex, edges)
    jarak, prev = dijkstra(graf, sumber)
    tampilkan_hasil(jarak, prev, vertex, sumber)
```

---

### 2.2 Proyek Berbasis Himpunan dan Relasi (Rekomendasi Matkul)

**Model:**
```text
M  = himpunan semua mata kuliah
L  = himpunan mata kuliah yang sudah lulus
P  = relasi prasyarat: P ⊆ M × M
     (a, b) ∈ P berarti a adalah prasyarat b

Matkul yang bisa diambil:
  Tersedia(x) = x ∉ L  ∧  ∀p ∈ prasyarat(x): p ∈ L
```

**Algoritma:**
```text
ALGORITMA rekomendasi(L, P, Minat)
INPUT : L (lulus), P (prasyarat), Minat (himpunan topik diminati)
OUTPUT: himpunan matkul yang direkomendasikan

START
    kandidat = {}
    UNTUK setiap matkul x di M:
        JIKA x ∉ L:
            prasyarat_terpenuhi = semua prasyarat x ada di L
            JIKA prasyarat_terpenuhi:
                tambahkan x ke kandidat
    rekomendasi = kandidat ∩ Minat
    kembalikan rekomendasi
END
```

---

### 2.3 Proyek Berbasis Teori Bilangan (Penjadwalan / Verifikasi Data)

**Model:**
```text
Penjadwalan:
  Jadwal bersama = KPK(interval₁, interval₂, ..., intervalₙ)

Verifikasi (checksum sederhana):
  checksum(data) = (Σ digit) mod K
  Data valid jika checksum == nilai_referensi
```

**Struktur kode:**

```python
def fpb(a, b):
    while b:
        a, b = b, a % b
    return a

def kpk(a, b):
    return abs(a * b) // fpb(a, b)

def kpk_banyak(*args):
    """KPK dari banyak bilangan."""
    from functools import reduce
    return reduce(kpk, args)

def checksum(data_str, modulus=10):
    """Hitung checksum sederhana dari string angka."""
    return sum(int(c) for c in data_str if c.isdigit()) % modulus
```

---

## 3. Standar Kualitas Kode

Semua kode yang dikumpulkan harus memenuhi standar berikut:

### 3.1 Struktur File

```text
nama_proyek/
├── main.py          ← program utama
├── model.py         ← definisi data dan struktur
├── algoritma.py     ← implementasi algoritma
└── laporan.md       ← dokumentasi
```

### 3.2 Komentar dan Dokumentasi

Setiap fungsi **wajib** memiliki docstring:

```python
def dijkstra(graf, sumber):
    """
    Mencari jalur terpendek dari sumber ke semua vertex.

    Parameters
    ----------
    graf   : dict — adjacency list berbobot {v: [(u, w), ...]}
    sumber : str  — vertex asal

    Returns
    -------
    jarak : dict — jarak terpendek dari sumber ke setiap vertex
    prev  : dict — vertex sebelumnya pada jalur terpendek
    """
    ...
```

### 3.3 Pemisahan Fungsi

- Satu fungsi = satu tanggung jawab.
- Hindari fungsi yang terlalu panjang (> 30 baris).
- Beri nama yang deskriptif: `hitung_degree`, `cari_rute_terpendek`, bukan `f1`, `proses`.

### 3.4 Penanganan Kasus Khusus

```python
# Selalu tangani kasus edge (kasus batas):
def dijkstra(graf, sumber):
    if sumber not in graf:
        raise ValueError(f"Vertex '{sumber}' tidak ada dalam graf.")
    ...
```

---

## 4. Pertanyaan Panduan Pengembangan

Selama pengembangan, setiap anggota kelompok harus bisa menjawab:

> **"Konsep matematika diskrit apa yang digunakan di sini, dan mengapa konsep itu dipilih?"**

Untuk setiap bagian kode, tanyakan:
1. Apa tujuan fungsi/bagian ini?
2. Konsep matematika diskrit apa yang diimplementasikan?
3. Apa input dan output yang diharapkan?
4. Bagaimana cara menguji kebenarannya?

---

## 5. Checklist Progres Pertemuan 14

Isi tabel berikut di akhir pertemuan:

| Komponen | Status | Catatan |
|----------|--------|---------|
| Model matematika (formal) | ☐ Selesai / ☐ Dalam Proses | |
| Algoritma (bahasa natural) | ☐ Selesai / ☐ Dalam Proses | |
| Pseudocode semua fungsi | ☐ Selesai / ☐ Dalam Proses | |
| Implementasi Python (draft) | ☐ Selesai / ☐ Dalam Proses | |
| Program bisa dijalankan | ☐ Ya / ☐ Belum | |
| Minimal 1 fungsi utama bekerja | ☐ Ya / ☐ Belum | |

---

## Checklist Pertemuan 14

- [ ] Model matematika dituliskan secara formal
- [ ] Algoritma dijabarkan langkah per langkah
- [ ] Pseudocode ditulis untuk semua fungsi utama
- [ ] Implementasi Python mengikuti standar kualitas
- [ ] Program bisa dijalankan tanpa error kritis
- [ ] Semua anggota bisa menjelaskan kode yang dibuat
- [ ] Rencana testing untuk Pertemuan 15 sudah disusun
