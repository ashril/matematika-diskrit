# Pertemuan 16 — Final Project Presentation

## Tema
**Puncak Pembelajaran: Mempresentasikan Solusi Berbasis Matematika Diskrit**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. mempresentasikan proyek secara sistematis dan komunikatif;
2. menjelaskan hubungan antara masalah, model matematika, algoritma, dan implementasi;
3. mendemonstrasikan program yang berfungsi di depan audiens;
4. menjawab pertanyaan kritis tentang desain dan implementasi solusi;
5. mengevaluasi proyek kelompok lain secara objektif.

---

## 1. Panduan Presentasi

### 1.1 Alokasi Waktu

| Sesi | Durasi | Keterangan |
|------|--------|-----------|
| Presentasi kelompok | 10–12 menit | Slide + demo |
| Tanya jawab | 3–5 menit | Dari dosen dan mahasiswa lain |
| Feedback | 2–3 menit | Dari dosen |

### 1.2 Urutan Presentasi Wajib

Setiap kelompok **harus** menyampaikan poin-poin berikut secara berurutan:

```text
1. PERMASALAHAN
   ↓
2. TUJUAN
   ↓
3. MODEL MATEMATIKA
   ↓
4. ALGORITMA
   ↓
5. IMPLEMENTASI (DEMO)
   ↓
6. HASIL PENGUJIAN
   ↓
7. EVALUASI
   ↓
8. KESIMPULAN
```

---

## 2. Pertanyaan Wajib yang Harus Dijawab

Setiap kelompok **harus mampu** menjawab 9 pertanyaan inti berikut. Persiapkan jawaban sebelum presentasi:

### Pertanyaan 1: Masalah
> **"Apa masalah yang diselesaikan oleh proyek ini?"**

Panduan jawaban:
- Jelaskan masalah dalam 2–3 kalimat sederhana.
- Sebutkan konteks nyata di mana masalah ini muncul.
- Mengapa masalah ini penting untuk diselesaikan?

---

### Pertanyaan 2: Relevansi Matematika Diskrit
> **"Mengapa masalah ini dapat dimodelkan menggunakan matematika diskrit?"**

Panduan jawaban:
- Identifikasi elemen diskrit dalam masalah (objek yang terhitung, hubungan antar objek, kondisi logis).
- Jelaskan mengapa pendekatan matematis lebih baik dari sekadar "trial and error".

---

### Pertanyaan 3: Konsep yang Digunakan
> **"Konsep matematika diskrit apa saja yang digunakan?"**

Panduan jawaban:
- Sebutkan minimal 2 konsep secara eksplisit.
- Jelaskan peran setiap konsep dalam solusi.
- Contoh: "Kami menggunakan *graf berbobot* untuk merepresentasikan jaringan, dan *Dijkstra* untuk mencari jalur terpendek."

---

### Pertanyaan 4: Model Matematika
> **"Bagaimana model matematikanya?"**

Panduan jawaban:
- Tampilkan notasi formal (definisi himpunan, relasi, fungsi, atau graf).
- Jelaskan apa yang direpresentasikan oleh setiap elemen model.

Contoh format:
```text
G = (V, E, W)
V = {Rektorat, Fakultas, Perpustakaan, Masjid, Laboratorium}
E ⊆ V × V (himpunan koneksi antar gedung)
W: E → ℝ⁺ (fungsi yang memetakan setiap edge ke bobotnya dalam menit)
```

---

### Pertanyaan 5: Algoritma
> **"Bagaimana algoritmanya?"**

Panduan jawaban:
- Jelaskan langkah-langkah algoritma dalam bahasa yang mudah dipahami.
- Tunjukkan pseudocode atau flowchart utama.
- Jelaskan mengapa algoritma ini dipilih.

---

### Pertanyaan 6: Alasan Pemilihan Algoritma
> **"Mengapa algoritma tersebut dipilih, bukan algoritma lain?"**

Panduan jawaban:
- Bandingkan dengan alternatif (misal: Dijkstra vs BFS, fungsi rekursif vs iteratif).
- Jelaskan kelebihan algoritma yang dipilih untuk masalah ini.
- Sebutkan trade-off yang ada.

---

### Pertanyaan 7: Implementasi
> **"Bagaimana implementasinya dalam Python?"**

Panduan jawaban:
- Demo program secara langsung (jalankan program).
- Jelaskan struktur program (file, fungsi utama).
- Tunjukkan bagaimana model matematika diterjemahkan ke kode.

---

### Pertanyaan 8: Validasi Hasil
> **"Bagaimana memvalidasi bahwa hasilnya benar?"**

Panduan jawaban:
- Tunjukkan tabel testing.
- Jelaskan bagaimana test case dipilih (normal, edge, error).
- Tunjukkan bahwa hasil program cocok dengan perhitungan manual.

---

### Pertanyaan 9: Keterbatasan
> **"Apa keterbatasan solusi yang dibuat?"**

Panduan jawaban:
- Sebutkan secara jujur kondisi di mana solusi tidak bekerja.
- Jelaskan apa yang akan dilakukan jika ada lebih banyak waktu.
- Tunjukkan pemahaman akan ruang untuk perbaikan.

---

## 3. Rubrik Penilaian Final Project

### 3.1 Rubrik Keseluruhan

| Komponen | Bobot | Indikator |
|----------|------:|----------|
| **Identifikasi masalah** | 10% | Masalah didefinisikan dengan jelas, relevan, terukur |
| **Model matematika** | 20% | Notasi formal benar, mencakup ≥2 konsep, relevan dengan masalah |
| **Algoritma** | 20% | Algoritma tepat, pseudocode lengkap, dapat menjelaskan alasan pemilihan |
| **Implementasi Python** | 20% | Kode berfungsi, terstruktur, terdokumentasi, mengikuti standar |
| **Testing & evaluasi** | 10% | ≥10 test case (normal+edge+error), analisis keterbatasan |
| **Dokumentasi** | 10% | Laporan lengkap, terstruktur, dan mudah dipahami |
| **Presentasi** | 10% | Komunikatif, menjawab pertanyaan dengan baik, demo berjalan |

### 3.2 Rubrik Detail per Komponen

#### Model Matematika (20%)

| Skor | Deskripsi |
|------|-----------|
| 18–20 | Notasi formal benar dan lengkap, ≥2 konsep terintegrasi dengan baik, hubungan dengan masalah sangat jelas |
| 14–17 | Notasi sebagian benar, 2 konsep digunakan, hubungan dengan masalah cukup jelas |
| 10–13 | Notasi ada tapi kurang tepat, hanya 1 konsep digunakan secara bermakna |
| 0–9 | Model matematika tidak ada atau tidak relevan |

#### Implementasi Python (20%)

| Skor | Deskripsi |
|------|-----------|
| 18–20 | Program berjalan sempurna, kode bersih, semua fungsi terdokumentasi, penanganan error ada |
| 14–17 | Program berjalan untuk normal case, kode cukup rapi, sebagian besar fungsi terdokumentasi |
| 10–13 | Program berjalan tapi ada bug minor, kode kurang terstruktur |
| 0–9 | Program tidak berjalan atau sangat tidak terstruktur |

---

## 4. Lembar Peer Review

Setiap mahasiswa mengisi lembar ini untuk **2 kelompok lain**:

```markdown
## Lembar Peer Review

**Reviewer (Nama/NIM):** _______________
**Kelompok yang direview:** _______________
**Judul proyek:** _______________

### Penilaian

| Aspek | Skor (1–5) | Komentar |
|-------|-----------|---------|
| Kejelasan masalah | | |
| Kesesuaian model matematika | | |
| Kualitas algoritma | | |
| Demo implementasi | | |
| Kemampuan menjawab pertanyaan | | |
| Kejelasan presentasi | | |

### Skor Total: ___ / 30

### Umpan Balik Konstruktif
**Yang sudah baik:**
1. ...
2. ...

**Yang perlu ditingkatkan:**
1. ...
2. ...

**Pertanyaan yang ingin diajukan:**
1. ...
```

---

## 5. Refleksi Akhir Mata Kuliah

Setelah presentasi, tuliskan refleksi pribadi (dikumpulkan secara individual):

```markdown
## Refleksi Akhir — Matematika Diskrit

**Nama / NIM:** _______________

### 1. Konsep mana yang paling berdampak?
Dari 16 pertemuan, konsep apa yang menurut Anda paling berguna
dan dapat langsung diterapkan? Mengapa?

### 2. Tantangan terbesar
Apa bagian yang paling sulit selama mata kuliah ini?
Bagaimana Anda mengatasinya?

### 3. Koneksi dengan bidang TI
Berikan satu contoh nyata di bidang teknologi informasi yang
menggunakan konsep dari mata kuliah ini. Jelaskan hubungannya.

### 4. Kemampuan yang berkembang
Selain memahami matematika diskrit, kemampuan apa lagi yang
berkembang? (Contoh: pemrograman Python, berpikir algoritmik,
kerja tim, dsb.)

### 5. Jika mengulang
Jika mengulang mata kuliah ini dari awal, apa yang akan Anda
lakukan berbeda?
```

---

## Checklist Pertemuan 16

- [ ] Slide presentasi sudah siap (minimal 8 slide)
- [ ] Program siap di-demo (sudah diuji coba sebelumnya)
- [ ] Semua anggota hafal bagian masing-masing
- [ ] Jawaban untuk 9 pertanyaan wajib sudah disiapkan
- [ ] Laporan `laporan.md` sudah dikumpulkan
- [ ] Kode sumber sudah dikumpulkan/di-push ke repositori
- [ ] Lembar peer review diisi untuk 2 kelompok lain
- [ ] Refleksi akhir ditulis dan dikumpulkan

---

## Penutup

Selamat! Setelah 16 pertemuan, Anda telah menempuh perjalanan dari:

```text
Logika & Himpunan
        ↓
Relasi & Fungsi
        ↓
Sistem Bilangan & Teori Bilangan
        ↓
Teori Graf & Algoritma Graf
        ↓
Pemecahan Masalah Nyata
```

Kompetensi yang seharusnya sudah tercapai:

> **"Mampu memodelkan permasalahan komputasi menggunakan konsep matematika diskrit, merancang algoritma penyelesaian, mengimplementasikan solusi menggunakan Python, dan mengevaluasi hasilnya."**

Matematika diskrit bukan sekadar teori — ia adalah bahasa yang digunakan ilmuwan komputer untuk berbicara tentang masalah secara presisi dan mencari solusi secara sistematis.
