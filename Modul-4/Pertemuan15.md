# Pertemuan 15 — Testing, Evaluation, dan Dokumentasi

## Tema
**Membuktikan Kebenaran: Testing Sistematis dan Dokumentasi Ilmiah**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. merancang dan melaksanakan strategi testing yang sistematis;
2. melakukan debugging dan memperbaiki kode berdasarkan hasil testing;
3. memvalidasi bahwa algoritma yang diimplementasikan menghasilkan output yang benar;
4. mengevaluasi efisiensi dan keterbatasan algoritma yang dibuat;
5. menyusun dokumentasi proyek yang lengkap dan terstruktur;
6. mempersiapkan bahan presentasi yang efektif.

---

## 1. Strategi Testing

### 1.1 Jenis Test Case

Setiap program harus diuji dengan setidaknya tiga kategori test case:

| Kategori | Keterangan | Contoh |
|----------|-----------|--------|
| **Normal case** | Input tipikal yang diharapkan bekerja | Graf dengan 5 vertex dan bobot wajar |
| **Edge case (kasus batas)** | Input di batas kondisi | Graf dengan 1 vertex, bobot = 0 |
| **Error case** | Input yang tidak valid | Vertex tidak ada, bobot negatif |

### 1.2 Template Tabel Testing

Gunakan tabel berikut untuk mendokumentasikan setiap pengujian:

```markdown
## Tabel Pengujian

| No | Fungsi/Fitur | Input | Output Diharapkan | Output Aktual | Status | Catatan |
|----|-------------|-------|-------------------|---------------|--------|---------|
| 1  | | | | | ✅/❌ | |
| 2  | | | | | ✅/❌ | |
...
```

**Minimal 10 test case** mencakup normal, edge, dan error case.

### 1.3 Cara Menulis Test Sederhana di Python

```python
# test_proyek.py — pengujian manual

def jalankan_test(nama_test, hasil_aktual, hasil_diharapkan):
    """Helper function untuk menjalankan test dan melaporkan hasilnya."""
    status = "✅ LULUS" if hasil_aktual == hasil_diharapkan else "❌ GAGAL"
    print(f"  {status} | {nama_test}")
    if hasil_aktual != hasil_diharapkan:
        print(f"    Diharapkan : {hasil_diharapkan}")
        print(f"    Aktual     : {hasil_aktual}")


# Contoh pengujian untuk proyek navigasi kampus
print("=" * 55)
print("LAPORAN TESTING — [Nama Proyek]")
print("=" * 55)

# Test 1: Normal case
jarak, prev = dijkstra(graf_kampus, 'Rektorat')
jalankan_test(
    "Shortest path Rektorat → Laboratorium",
    jarak['Laboratorium'],
    10  # nilai yang diharapkan
)

# Test 2: Path reconstruction
path = rekonstruksi_path(prev, 'Rektorat', 'Laboratorium')
jalankan_test(
    "Rekonstruksi path A → E",
    path[0],   # harus dimulai dari sumber
    'Rektorat'
)

# Test 3: Edge case — sumber = tujuan
jarak2, _ = dijkstra(graf_kampus, 'Rektorat')
jalankan_test(
    "Jarak dari Rektorat ke dirinya sendiri",
    jarak2['Rektorat'],
    0
)

# Test 4: Vertex terisolasi
# ... dan seterusnya

print()
print("Testing selesai.")
```

---

## 2. Proses Debugging

### 2.1 Langkah Debugging Sistematis

```text
1. REPRODUKSI: Pastikan bug dapat direproduksi secara konsisten
        ↓
2. LOKALISASI: Identifikasi fungsi/baris yang menyebabkan bug
        ↓
3. HIPOTESIS: Formulasikan dugaan penyebab bug
        ↓
4. VERIFIKASI: Uji hipotesis dengan print debugging atau test kecil
        ↓
5. PERBAIKAN: Perbaiki kode
        ↓
6. KONFIRMASI: Jalankan ulang semua test untuk memastikan bug terselesaikan
```

### 2.2 Teknik Print Debugging

```python
def dijkstra(graf, sumber):
    jarak = {v: float('inf') for v in graf}
    jarak[sumber] = 0
    pq = [(0, sumber)]

    while pq:
        d, u = heapq.heappop(pq)

        # DEBUG: cetak state saat ini
        print(f"[DEBUG] Memproses vertex {u}, jarak={d}")

        for v, w in graf[u]:
            jarak_baru = jarak[u] + w
            if jarak_baru < jarak[v]:
                jarak[v] = jarak_baru
                # DEBUG: cetak relaksasi
                print(f"[DEBUG]   Relaksasi: jarak[{v}] = {jarak_baru}")
                heapq.heappush(pq, (jarak_baru, v))

    return jarak
```

> **Tips:** Setelah debugging selesai, hapus atau nonaktifkan print DEBUG agar output bersih.

---

## 3. Evaluasi Algoritma

### 3.1 Pertanyaan Evaluasi Wajib

Setiap kelompok harus menjawab pertanyaan berikut dalam dokumentasi:

**A. Kebenaran (Correctness)**
- Apakah semua test case menghasilkan output yang benar?
- Adakah kasus yang menghasilkan output salah? Mengapa?

**B. Efisiensi (Efficiency)**
- Apa kompleksitas waktu algoritma yang dibuat? (O(n), O(n²), O(n log n), dst.)
- Jika ukuran input diperbesar 10×, apakah program masih dapat berjalan dalam waktu wajar?

**C. Keterbatasan (Limitations)**
- Apa batasan-batasan solusi yang dibuat?
- Kondisi apa yang membuat solusi ini tidak bekerja?

**D. Pengembangan (Future Work)**
- Apa yang bisa ditingkatkan jika ada lebih banyak waktu?

### 3.2 Template Analisis Kompleksitas

```markdown
## Analisis Kompleksitas

### Fungsi: dijkstra(graf, sumber)
- **Waktu**: O((V + E) log V) dengan priority queue binary heap
  - V kali operasi pop dari priority queue: O(V log V)
  - E kali operasi push ke priority queue: O(E log V)
- **Ruang**: O(V) untuk menyimpan jarak dan prev

### Fungsi: buat_adj_matrix(vertex, edges)
- **Waktu**: O(V²) untuk inisialisasi matrix + O(E) untuk pengisian
- **Ruang**: O(V²) untuk menyimpan matrix

### Kesimpulan:
Algoritma ini efisien untuk jaringan berukuran sedang (V < 1000).
Untuk jaringan sangat besar, disarankan menggunakan struktur data yang lebih efisien.
```

---

## 4. Dokumentasi Proyek

### 4.1 Struktur Laporan Wajib

Setiap kelompok mengumpulkan `laporan.md` dengan struktur berikut:

```markdown
# Laporan Proyek: [Judul]

**Kelompok:**
| Nama | NIM |
|------|-----|
| ... | ... |

---

## 1. Pernyataan Masalah
[Deskripsi masalah yang diselesaikan]

## 2. Model Matematika
[Notasi formal: himpunan, relasi, fungsi, graf, ekspresi logika]

## 3. Algoritma
[Langkah-langkah algoritma dalam bahasa natural]

## 4. Pseudocode
```text
ALGORITMA [nama]
INPUT  : ...
OUTPUT : ...
START
  ...
END
```

## 5. Implementasi
[Penjelasan singkat struktur kode, fungsi-fungsi utama]

## 6. Hasil Pengujian
[Tabel testing dengan minimal 10 test case]

## 7. Analisis
- Kebenaran: ...
- Efisiensi: ...
- Keterbatasan: ...

## 8. Kesimpulan
[Apa yang berhasil dicapai? Apa yang masih bisa dikembangkan?]
```

---

## 5. Persiapan Presentasi

### 5.1 Struktur Slide Presentasi

Presentasi dibatasi **10–15 menit** per kelompok, mencakup:

| Slide | Konten |
|-------|--------|
| 1 | Judul proyek dan anggota kelompok |
| 2 | Permasalahan — apa yang ingin diselesaikan? |
| 3 | Tujuan — apa yang diharapkan dari solusi? |
| 4 | Model matematika — notasi formal |
| 5 | Algoritma — flowchart atau langkah utama |
| 6 | Demo implementasi — screenshot atau live demo |
| 7 | Hasil pengujian — tabel atau grafik |
| 8 | Evaluasi — keberhasilan dan keterbatasan |
| 9 | Kesimpulan dan saran pengembangan |

### 5.2 Demo Program

Siapkan skenario demo yang menunjukkan:

1. Program berjalan tanpa error pada **normal case**.
2. Program menangani **edge case** dengan benar.
3. Output yang dihasilkan **mudah dipahami** audiens.

### 5.3 Pertanyaan yang Mungkin Ditanyakan

Persiapkan jawaban untuk pertanyaan-pertanyaan berikut:

- "Mengapa menggunakan Dijkstra dan bukan BFS?"
- "Apa yang terjadi jika ada edge berbobot negatif?"
- "Bagaimana cara program Anda mendeteksi jika input tidak valid?"
- "Jika ada 1000 vertex, apakah program masih efisien?"
- "Konsep matematika diskrit mana yang paling krusial dalam proyek ini?"

---

## Checklist Pertemuan 15

- [ ] Minimal 10 test case dijalankan dan didokumentasikan
- [ ] Semua bug kritis sudah diperbaiki
- [ ] Program berjalan pada semua normal case dan edge case
- [ ] Analisis kompleksitas algoritma ditulis
- [ ] Keterbatasan solusi diidentifikasi
- [ ] Laporan `laporan.md` selesai
- [ ] Slide presentasi selesai (minimal 8 slide)
- [ ] Skenario demo disiapkan
- [ ] Seluruh anggota bisa menjelaskan semua bagian proyek
