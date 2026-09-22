# Rencana Pembelajaran Semester (RPS)
# Matematika Diskrit

---

| | |
|---|---|
| **Mata Kuliah** | Matematika Diskrit |
| **Bobot** | 3 SKS (Teori: 2 SKS · Praktikum: 1 SKS) |
| **Total Pertemuan** | 16 Pertemuan |
| **UTS / UAS** | Tidak ada |
| **Asesmen Modul** | 3 kali |
| **Final Project** | 1 proyek integratif |

---

## Prinsip Dasar

Teori (2 SKS) dan praktikum (1 SKS) saling terintegrasi — bukan dipisahkan secara kaku. Praktikum adalah **implementasi langsung** dari teori yang dipelajari.

Alur besar setiap topik:

```text
Konsep Matematika → Masalah → Model Matematika
       → Algoritma → Implementasi Python → Asesmen
```

---

## Struktur Modul

| Modul | Pertemuan | Tema Besar |
|-------|-----------|------------|
| **Modul 1** | 1–4 | Berpikir Logis dan Memodelkan Informasi |
| **Modul 2** | 5–8 | Dari Model Matematika Menuju Algoritma |
| **Modul 3** | 9–12 | Memodelkan Hubungan dan Jaringan |
| **Modul 4** | 13–16 | Integrasi Matematika Diskrit dalam Pemecahan Masalah |

---

## Modul 1 — Logika dan Himpunan

**Tema:** Berpikir Logis dan Memodelkan Informasi  
**Pertemuan:** 1–4

### Pertemuan 1 — Pengantar Matematika Diskrit dan Logika Proposisional

#### Materi Teori
- Pengantar matematika diskrit
- Peran matematika diskrit dalam ilmu komputer
- Matematika diskrit dan komputasi
- Proposisi dan nilai kebenaran
- Proposisi atomik dan majemuk
- Operator logika: NOT, AND, OR, XOR, Implikasi, Biimplikasi

#### Praktikum
- Instalasi / pengenalan Python
- Variabel dan tipe data
- Operator perbandingan
- Boolean
- Operator `and`, `or`, `not`
- Ekspresi logika sederhana

#### Problem Based Learning
**Kasus: Sistem Login**

Mahasiswa menentukan apakah pengguna dapat login berdasarkan:
- username benar
- password benar
- akun aktif

Mahasiswa mengubah aturan tersebut menjadi model logika, kemudian mengimplementasikannya dalam Python.

**Output:** Program logika

---

### Pertemuan 2 — Tabel Kebenaran dan Logika Predikat

#### Materi Teori
- Tabel kebenaran
- Tautologi, kontradiksi, kontingensi
- Ekuivalensi logika
- Hukum-hukum logika
- Logika predikat: predikat, kuantor universal, kuantor eksistensial

#### Praktikum
- Membuat tabel kebenaran sederhana
- Evaluasi ekspresi Boolean
- Simulasi kondisi menggunakan Python

#### Problem Based Learning
**Kasus: Seleksi Peserta Praktikum**

Mahasiswa menentukan apakah seorang mahasiswa memenuhi syarat mengikuti praktikum berdasarkan beberapa kondisi akademik.

**Output:** Tabel kebenaran + program seleksi

---

### Pertemuan 3 — Teori Himpunan dan Operasi Himpunan

#### Materi Teori
- Pengertian dan notasi himpunan
- Elemen, himpunan kosong, himpunan semesta
- Subset, union, intersection, difference, complement
- Cardinality dan Cartesian product

#### Praktikum
Menggunakan Python `set`:
```python
A = {1, 2, 3, 4}
B = {3, 4, 5, 6}
# Operasi: A | B, A & B, A - B
```

#### Problem Based Learning
**Kasus: Preferensi Teknologi Mahasiswa**

Data mahasiswa yang menyukai Python, Java, SQL. Mahasiswa mencari:
- mahasiswa yang menyukai Python saja
- Python dan Java
- minimal satu teknologi
- tidak menyukai ketiganya

**Output:** Program himpunan

---

### Pertemuan 4 — Asesmen Modul 1

#### Problem Challenge: Sistem Seleksi Pelatihan

Mahasiswa diberikan kasus yang menggabungkan logika proposisional, Boolean, tabel kebenaran, himpunan, dan operasi himpunan.

#### Tahapan Penyelesaian

```text
Masalah
    ↓
Identifikasi Variabel
    ↓
Model Logika / Himpunan
    ↓
Algoritma
    ↓
Implementasi Python
    ↓
Testing
```

#### Produk yang Dikumpulkan
- Analisis masalah
- Algoritma / pseudocode
- Program Python
- Dokumentasi hasil

**Output:** Laporan + program

> Tidak berbentuk UTS.

---

## Modul 2 — Relasi, Fungsi, Sistem Bilangan, dan Teori Bilangan

**Tema:** Dari Model Matematika Menuju Algoritma  
**Pertemuan:** 5–8

> Modul ini sengaja menjadi jembatan antara matematika diskrit dan algoritma pemrograman.

### Pertemuan 5 — Relasi dan Fungsi

#### Materi Teori
**Relasi:**
- Definisi relasi dan Cartesian product
- Pasangan berurutan dan diagram panah
- Matriks relasi
- Sifat relasi: refleksif, simetris, antisimetris, transitif

**Fungsi:**
- Definisi fungsi
- Domain, kodomain, range
- Injektif, surjektif, bijektif

#### Praktikum
- Representasi relasi dengan Python
- Fungsi menggunakan `def`
- Fungsi linear, kuadrat, kubik
- Visualisasi fungsi dengan Matplotlib

#### Problem Based Learning
**Kasus: Pemetaan Mahasiswa dan Mata Kuliah**

Mahasiswa menentukan apakah hubungan `[Mahasiswa → MataKuliah]` merupakan relasi atau fungsi.

**Output:** Program fungsi + visualisasi

---

### Pertemuan 6 — Sistem Bilangan dan Algoritma

#### Materi Teori
**Sistem Bilangan:**
- Desimal, biner, oktal, heksadesimal
- Basis bilangan dan konversi antar basis
- Representasi data komputer

**Algoritma:**
- Pseudocode dan flowchart
- Input–process–output
- Iterasi sebagai strategi algoritmik

#### Praktikum
Implementasi konversi:
- Desimal → Biner, Oktal, Heksadesimal
- Biner → Desimal
- Perbandingan algoritma manual dengan `bin()`, `oct()`, `hex()`

#### Problem Based Learning
**Kasus: Sistem Identifikasi Perangkat**

ID perangkat (desimal) harus ditampilkan dalam biner, oktal, dan heksadesimal. Mahasiswa membuat algoritma terlebih dahulu, baru membuat program.

**Output:** Program konversi

---

### Pertemuan 7 — Teori Bilangan dan Algoritma

#### Materi Teori
- Bilangan bulat: faktor, kelipatan, ganjil/genap, modulus
- Bilangan prima dan algoritma pencarian bilangan prima
- FPB, KPK, dan Algoritma Euclidean
- Efisiensi algoritma sederhana

#### Praktikum
Menggunakan `def`, `for`, dan `while`:
- Menentukan ganjil/genap
- Menentukan bilangan prima
- Mencari FPB dan KPK
- Operasi modulus

#### Problem Based Learning
**Kasus: Penjadwalan Server**

- Server A melakukan backup setiap **12 menit**
- Server B melakukan backup setiap **18 menit**
- Kapan keduanya backup bersamaan? → KPK(12, 18)

Kasus kedua: sistem menentukan apakah nomor identitas tertentu merupakan bilangan prima.

**Output:** Program algoritma

---

### Pertemuan 8 — Asesmen Modul 2

#### Algorithm Challenge

Mahasiswa diberikan permasalahan **tanpa algoritma**:

> Sebuah sistem membutuhkan program untuk menganalisis sekumpulan nomor identitas. Program harus menentukan bilangan ganjil/genap, bilangan prima, menghitung FPB/KPK, dan mengubah bilangan ke format heksadesimal.

#### Tahapan Wajib
1. Menganalisis masalah
2. Menentukan input dan output
3. Membuat algoritma
4. Membuat pseudocode
5. Mengimplementasikan Python
6. Melakukan pengujian
7. Menjelaskan hasil

#### Fokus Asesmen

| Komponen | Bobot |
|----------|------:|
| Analisis masalah | 15% |
| Algoritma | 25% |
| Implementasi | 30% |
| Testing | 15% |
| Penjelasan | 15% |

**Output:** Program + algoritma

---

## Modul 3 — Teori Graf dan Algoritma Graf

**Tema:** Memodelkan Hubungan dan Jaringan  
**Pertemuan:** 9–12

### Pertemuan 9 — Konsep Dasar Graf

#### Materi Teori
- Pengertian graf: vertex, edge, degree
- Graf berarah, tidak berarah, berbobot
- Graf sederhana, lengkap, terhubung
- Path dan cycle

#### Praktikum
Mahasiswa membuat graf sederhana dan menentukan:
- vertex, edge, degree
- hubungan antarvertex

#### Problem Based Learning
**Kasus: Jaringan Laboratorium Komputer**

- Komputer/server = vertex
- Koneksi jaringan = edge
- Mahasiswa memodelkan jaringan laboratorium sebagai graf

**Output:** Model graf

---

### Pertemuan 10 — Representasi Graf

#### Materi Teori
- Adjacency Matrix dan Adjacency List
- Graf berbobot
- Perbandingan adjacency matrix dan adjacency list
- Representasi graf dalam komputer
- Matriks dan operasi dasar matriks

#### Praktikum
Menggunakan NumPy:
```python
import numpy as np
```
Mahasiswa membuat:
- adjacency matrix
- degree matrix sederhana
- operasi matriks
- pencarian hubungan antarvertex

#### Problem Based Learning
**Kasus: Jaringan Router Kampus**

Router = vertex, koneksi jaringan = edge. Mahasiswa membangun adjacency matrix menggunakan NumPy.

**Output:** Program matriks

---

### Pertemuan 11 — Algoritma Graf dan Shortest Path

#### Materi Teori
**Graph Traversal:**
- BFS (Breadth-First Search)
- DFS (Depth-First Search)

**Shortest Path:**
- Strategi greedy
- Algoritma Dijkstra
- Konsep relaksasi edge
- Kompleksitas algoritma (pengantar)

#### Praktikum
Implementasi:
- BFS sederhana
- DFS sederhana
- Strategi greedy
- Shortest path (Dijkstra)

#### Problem Based Learning
**Kasus: Navigasi Kampus**

Gedung: Rektorat, Fakultas, Perpustakaan, Laboratorium, Masjid.  
Setiap jalan memiliki jarak. Mahasiswa mencari rute terpendek dari **Rektorat → Laboratorium**.

**Output:** Program shortest path

---

### Pertemuan 12 — Asesmen Modul 3

#### Graph Challenge

Mahasiswa diberikan jaringan berbobot:

```text
A ---- B
|      |
C ---- D ---- E
```

Mahasiswa harus:
1. Membuat graf dari topologi yang diberikan
2. Menentukan vertex, edge, dan degree
3. Membuat adjacency matrix
4. Menentukan semua path
5. Menentukan shortest path
6. Membuat algoritma (pseudocode)
7. Mengimplementasikan Python
8. Menjelaskan hasil

**Output:** Python Notebook + visualisasi graf + analisis

---

## Modul 4 — Project Based Learning

**Tema:** Integrasi Matematika Diskrit dalam Pemecahan Masalah  
**Pertemuan:** 13–16

> Pada modul ini mahasiswa tidak diperkenalkan banyak teori baru.  
> Fokus: **mengintegrasikan konsep Modul 1–3 untuk menyelesaikan masalah nyata.**

### Pertemuan 13 — Project Initiation

#### Aktivitas: Identifikasi Masalah

Mahasiswa bekerja dalam kelompok. Tahapan:

```text
Identifikasi Masalah
        ↓
Analisis Kebutuhan
        ↓
Model Matematika
        ↓
Pemilihan Konsep
```

Mahasiswa memilih masalah yang dapat diselesaikan menggunakan matematika diskrit.

#### Contoh Proyek

| No | Judul | Konsep yang Digunakan |
|----|-------|-----------------------|
| 1 | Smart Campus Navigation | Graf, Adjacency Matrix, Shortest Path |
| 2 | Sistem Rekomendasi Mata Kuliah | Himpunan, Relasi, Fungsi |
| 3 | Sistem Penjadwalan | Himpunan, Relasi, KPK |
| 4 | Analisis Jaringan Komputer | Graf, Degree, Adjacency Matrix, Shortest Path |
| 5 | Sistem Verifikasi Data | Fungsi, Bilangan, Modulus, Hash |

**Output:** Proposal proyek

---

### Pertemuan 14 — Project Development

#### Aktivitas: Pengembangan Solusi

Mahasiswa mengembangkan solusi dengan alur wajib:

```text
Problem
   ↓
Mathematical Model
   ↓
Algorithm
   ↓
Pseudocode
   ↓
Python
   ↓
Output
```

Mahasiswa harus dapat menjelaskan:
> *"Konsep matematika diskrit apa yang digunakan untuk menyelesaikan masalah ini?"*

**Output:** Prototipe program

---

### Pertemuan 15 — Testing, Evaluation, dan Dokumentasi

#### Aktivitas

Mahasiswa melakukan:
- Testing dan debugging
- Validasi hasil
- Analisis dan evaluasi algoritma
- Penyusunan dokumentasi

#### Presentasi harus memuat:
1. Permasalahan
2. Tujuan
3. Model matematika
4. Algoritma
5. Implementasi
6. Hasil
7. Testing
8. Evaluasi
9. Kesimpulan

**Output:** Produk final + dokumentasi

---

### Pertemuan 16 — Final Project Presentation

#### Final Project

Tidak ada UAS. Mahasiswa mempresentasikan produk/proyek integratif.

#### Pertanyaan Wajib yang Harus Dijawab

Setiap kelompok harus mampu menjawab:

1. Apa masalah yang diselesaikan?
2. Mengapa masalah tersebut dapat dimodelkan menggunakan matematika diskrit?
3. Konsep apa yang digunakan?
4. Bagaimana model matematikanya?
5. Bagaimana algoritmanya?
6. Mengapa algoritma tersebut dipilih?
7. Bagaimana implementasinya?
8. Bagaimana validasi hasilnya?
9. Apa keterbatasan solusi?

**Output:** Produk + presentasi

---

## Rekap 16 Pertemuan

| Ptm | Modul | Materi Teori | Praktikum / Aktivitas | Metode | Output |
|-----|-------|--------------|-----------------------|--------|--------|
| 1 | M1 | Pengantar, logika, proposisi | Python & Boolean | PBL | Program logika |
| 2 | M1 | Tabel kebenaran & predikat | Implementasi logika | PBL | Tabel / program |
| 3 | M1 | Himpunan & operasi | Python Set | PBL | Program himpunan |
| 4 | M1 | Asesmen Modul 1 | Problem Challenge | PBL | Laporan + program |
| 5 | M2 | Relasi & fungsi | `def`, fungsi matematika | PBL | Program fungsi |
| 6 | M2 | Sistem bilangan & algoritma | Konversi bilangan | PBL | Program konversi |
| 7 | M2 | Teori bilangan & algoritma | FPB, KPK, prima | PBL | Program algoritma |
| 8 | M2 | Asesmen Modul 2 | Algorithm Challenge | PBL | Program + algoritma |
| 9 | M3 | Graf dasar | Membuat graf | PBL | Model graf |
| 10 | M3 | Representasi graf | Adjacency Matrix + NumPy | PBL | Program matriks |
| 11 | M3 | Algoritma graf | Greedy + shortest path | PBL | Program shortest path |
| 12 | M3 | Asesmen Modul 3 | Graph Challenge | PBL | Graph solution |
| 13 | M4 | Project initiation | Identifikasi masalah | PjBL | Proposal proyek |
| 14 | M4 | Project development | Model → algoritma → program | PjBL | Prototipe |
| 15 | M4 | Testing & evaluation | Testing & dokumentasi | PjBL | Produk final |
| 16 | M4 | Final Project | Presentasi | PjBL | Produk + presentasi |

---

## Hubungan Teori dan Praktikum

| Teori | Praktikum |
|-------|-----------|
| Logika | Boolean Python |
| Proposisi | Program kondisi |
| Tabel kebenaran | Evaluasi Boolean |
| Himpunan | Python `set` |
| Relasi | Representasi relasi |
| Fungsi | `def` |
| Fungsi linear / kuadrat / kubik | NumPy + Matplotlib |
| Sistem bilangan | Algoritma konversi |
| Modulus | Program modulus |
| FPB / KPK | Algoritma Euclidean |
| Prima | Algoritma primality |
| Graf | Representasi graf |
| Adjacency Matrix | NumPy |
| Greedy | Algoritma pencarian |
| Shortest Path | Dijkstra |
| Integrasi | Final Project |

> **2 SKS teori** menjawab *"mengapa dan bagaimana secara matematis"*,  
> **1 SKS praktikum** menjawab *"bagaimana mengimplementasikannya"*.

---

## Pola PBL pada Setiap Pertemuan

Dosen menggunakan pola yang konsisten:

**1. Berikan masalah terlebih dahulu** (bukan langsung definisi)
> *"Dua server melakukan backup setiap 12 dan 18 menit. Kapan keduanya backup bersamaan?"*

**2. Masuk ke konsep matematika**
> Baru diperkenalkan: KPK(12, 18)

**3. Bentuk algoritma**
```text
Input → Proses → Output
```

**4. Implementasikan**
```python
def kpk(a, b):
    ...
```

**5. Evaluasi**
> Mahasiswa menjawab: *"Apakah algoritma memberikan hasil yang benar?"*

---

## Skema Asesmen

| Komponen | Bobot |
|----------|------:|
| Asesmen Modul 1 | 15% |
| Asesmen Modul 2 | 20% |
| Asesmen Modul 3 | 20% |
| Aktivitas & Praktikum | 15% |
| Final Project | 30% |
| **Total** | **100%** |

### Rincian Final Project (30%)

| Komponen | Bobot |
|----------|------:|
| Identifikasi masalah | 10% |
| Model matematika | 20% |
| Algoritma | 20% |
| Implementasi Python | 20% |
| Testing & evaluasi | 10% |
| Dokumentasi | 10% |
| Presentasi | 10% |

---

## Alur Besar Mata Kuliah

```text
               MATEMATIKA DISKRIT
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
     LOGIKA        HIMPUNAN        RELASI
        │              │              │
        └──────────────┼──────────────┘
                       ↓
                    FUNGSI
                       ↓
               TEORI BILANGAN
                       ↓
                   ALGORITMA
                       ↓
                     GRAF
                       ↓
                ALGORITMA GRAF
                       ↓
              PEMECAHAN MASALAH
                       ↓
                 FINAL PROJECT
```

---

## Kompetensi Akhir yang Diharapkan

Setelah 16 pertemuan, mahasiswa diharapkan mencapai kompetensi:

> **"Mampu memodelkan permasalahan komputasi menggunakan konsep matematika diskrit, merancang algoritma penyelesaian, mengimplementasikan solusi menggunakan Python, dan mengevaluasi hasilnya."**

Struktur 4 modul ini cocok untuk Prodi Teknologi Informasi karena:
- **Modul 1** membangun *logical thinking*
- **Modul 2** membangun *algorithmic thinking*
- **Modul 3** membangun *computational modeling*
- **Modul 4** menguji semuanya melalui *project-based learning*
