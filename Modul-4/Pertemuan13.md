# Pertemuan 13 — Project Initiation

## Tema
**Mulai dari Masalah: Identifikasi, Analisis, dan Pemodelan Proyek**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. mengidentifikasi masalah nyata yang relevan dengan matematika diskrit;
2. menganalisis kebutuhan dan batasan masalah;
3. memilih konsep matematika diskrit yang sesuai untuk menyelesaikan masalah;
4. membangun model matematika dari masalah yang dipilih;
5. menyusun proposal proyek yang terstruktur;
6. bekerja secara efektif dalam tim.

---

## 1. Panduan Pemilihan Proyek

### 1.1 Kriteria Masalah yang Baik

Sebuah masalah layak dijadikan proyek jika memenuhi kriteria berikut:

| Kriteria | Keterangan |
|----------|-----------|
| **Relevan** | Berkaitan dengan dunia TI atau kehidupan kampus |
| **Termodelkan** | Dapat dinyatakan secara matematis menggunakan konsep Modul 1–3 |
| **Realistis** | Dapat diselesaikan dalam 4 pertemuan |
| **Terukur** | Hasil dapat diuji dan diverifikasi |

### 1.2 Konsep yang Dapat Digunakan

Setiap proyek harus menggunakan **minimal 2 konsep** dari Modul 1–3:

| Modul | Konsep Tersedia |
|-------|----------------|
| **Modul 1** | Logika proposisional, tabel kebenaran, himpunan, operasi himpunan |
| **Modul 2** | Relasi, fungsi, sistem bilangan, FPB, KPK, bilangan prima |
| **Modul 3** | Graf, adjacency matrix, BFS, DFS, shortest path (Dijkstra) |

---

## 2. Contoh Proyek

### Proyek 1 — Smart Campus Navigation

**Deskripsi:** Sistem navigasi antar gedung kampus yang menemukan rute terpendek.

| Komponen | Konsep |
|----------|--------|
| Model jaringan gedung | Graf berbobot |
| Penyimpanan topologi | Adjacency Matrix |
| Pencarian rute terpendek | Algoritma Dijkstra |
| Filter berdasarkan kondisi (jam buka) | Logika proposisional |

**Input:** Titik awal, titik tujuan, kondisi gedung (buka/tutup)  
**Output:** Rute terpendek dan total waktu tempuh

---

### Proyek 2 — Sistem Rekomendasi Mata Kuliah

**Deskripsi:** Sistem yang merekomendasikan mata kuliah berdasarkan prasyarat dan minat mahasiswa.

| Komponen | Konsep |
|----------|--------|
| Himpunan matkul yang sudah lulus | Himpunan |
| Prasyarat matkul | Relasi |
| Cocok/tidaknya mahasiswa mengambil matkul | Fungsi logika |
| Kesesuaian minat | Operasi himpunan (intersection) |

**Input:** Daftar matkul yang sudah lulus, minat mahasiswa  
**Output:** Daftar matkul yang direkomendasikan

---

### Proyek 3 — Sistem Penjadwalan Otomatis

**Deskripsi:** Sistem penjadwalan yang mengatur waktu maintenance server atau jadwal dosen.

| Komponen | Konsep |
|----------|--------|
| Interval jadwal | KPK, FPB |
| Konflik jadwal | Himpunan, operasi irisan |
| Urutan prioritas | Relasi terurut |
| Validasi slot waktu | Logika proposisional |

**Input:** Daftar jadwal dengan interval, jumlah sumber daya  
**Output:** Jadwal optimal tanpa konflik

---

### Proyek 4 — Analisis Jaringan Komputer

**Deskripsi:** Analisis topologi jaringan kampus, termasuk ketahanan dan efisiensi.

| Komponen | Konsep |
|----------|--------|
| Topologi jaringan | Graf berbobot |
| Koneksi antar perangkat | Adjacency Matrix |
| Derajat keterhubungan | Degree analysis |
| Rute backup | Shortest path alternatif |
| Identifikasi perangkat | Sistem bilangan (hex) |

**Input:** Topologi jaringan, bobot koneksi  
**Output:** Analisis ketahanan, rute terpendek, identifikasi titik kritis

---

### Proyek 5 — Sistem Verifikasi Data

**Deskripsi:** Sistem yang memverifikasi integritas data menggunakan checksum berbasis modulus.

| Komponen | Konsep |
|----------|--------|
| Validasi format ID | Logika proposisional |
| Checksum sederhana | Modulus, teori bilangan |
| Representasi data | Sistem bilangan (hex/biner) |
| Klasifikasi data | Fungsi, himpunan |

**Input:** Daftar ID/data yang akan diverifikasi  
**Output:** Status valid/tidak valid, laporan anomali

---

## 3. Alur Pengerjaan Pertemuan 13

### Langkah 1 — Pembentukan Kelompok
- Kelompok terdiri dari **3–4 mahasiswa**.
- Tentukan pembagian peran: koordinator, desainer model, programmer, dokumenter.

### Langkah 2 — Identifikasi Masalah

Gunakan template berikut untuk mendefinisikan masalah:

```text
IDENTIFIKASI MASALAH

1. Pernyataan masalah:
   "Kami ingin membuat sistem yang ..."

2. Mengapa masalah ini penting?
   ...

3. Siapa pengguna sistem ini?
   ...

4. Apa batasan masalah?
   - Batasan 1: ...
   - Batasan 2: ...

5. Apa yang BUKAN bagian dari masalah ini?
   ...
```

### Langkah 3 — Analisis Kebutuhan

```text
ANALISIS KEBUTUHAN

INPUT:
  - Data apa yang dibutuhkan sistem?
  - Dalam format apa?
  - Dari mana sumbernya?

PROSES:
  - Transformasi apa yang perlu dilakukan?
  - Algoritma apa yang mungkin digunakan?

OUTPUT:
  - Apa yang harus dihasilkan sistem?
  - Bagaimana format outputnya?
```

### Langkah 4 — Model Matematika

Pilih konsep dan bangun model awal:

```text
MODEL MATEMATIKA

Konsep yang digunakan:
  1. [nama konsep] → untuk menyelesaikan [bagian masalah]
  2. [nama konsep] → untuk menyelesaikan [bagian masalah]

Notasi formal:
  - Definisi himpunan: ...
  - Relasi / fungsi: ...
  - Struktur graf: G = (V, E) di mana ...
  - Ekspresi logika: ...
```

### Langkah 5 — Susun Proposal

---

## 4. Template Proposal Proyek

```markdown
# Proposal Proyek: [Judul]

## Anggota Kelompok
| Nama | NIM | Peran |
|------|-----|-------|
| ... | ... | ... |

## Pernyataan Masalah
[Deskripsi masalah secara jelas dan singkat]

## Tujuan
[Apa yang ingin dicapai proyek ini]

## Batasan
- ...

## Konsep Matematika Diskrit yang Digunakan
| No | Konsep | Digunakan untuk |
|----|--------|----------------|
| 1 | | |
| 2 | | |

## Model Matematika Awal
[Notasi formal, definisi objek matematis]

## Rencana Pengerjaan
| Pertemuan | Aktivitas | Target |
|-----------|-----------|--------|
| 14 | Pengembangan | Prototipe awal |
| 15 | Testing | Program final |
| 16 | Presentasi | Produk + slide |

## Ekspektasi Output
[Deskripsi output akhir program]
```

---

## 5. Pertanyaan Panduan Diskusi

Gunakan pertanyaan berikut untuk memandu diskusi kelompok:

1. **Konsep mana yang paling relevan?**  
   "Apakah masalah ini melibatkan hubungan antar objek? → Graf/Relasi"  
   "Apakah ada kondisi benar/salah? → Logika"  
   "Apakah ada pengelompokan? → Himpunan"

2. **Bagaimana cara memvalidasi solusi?**  
   "Apa test case yang paling sederhana?"  
   "Apa test case yang paling ekstrem (edge case)?"

3. **Apa ukuran keberhasilan proyek?**  
   "Kapan kita bisa menyatakan proyek berhasil?"

---

## Checklist Pertemuan 13

- [ ] Kelompok terbentuk (3–4 mahasiswa)
- [ ] Masalah dipilih dan didefinisikan
- [ ] Analisis kebutuhan (input, proses, output)
- [ ] Minimal 2 konsep matematika diskrit diidentifikasi
- [ ] Model matematika awal dibangun
- [ ] Proposal dikumpulkan
- [ ] Rencana pengerjaan Pertemuan 14–16 disusun
