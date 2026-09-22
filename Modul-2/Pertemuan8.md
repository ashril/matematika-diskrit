# Pertemuan 8 — Asesmen Modul 2

## Algorithm Challenge — Analisis Nomor Identitas

---

## Skenario

Sebuah sistem manajemen jaringan kampus menyimpan **daftar nomor identitas** perangkat yang terhubung. Sistem tersebut membutuhkan program analitik yang mampu:

1. Menentukan apakah nomor identitas **ganjil atau genap**.
2. Memeriksa apakah nomor identitas adalah **bilangan prima** (untuk keperluan enkripsi).
3. Menghitung **FPB dan KPK** dari dua nomor identitas (untuk sinkronisasi jadwal maintenance).
4. Mengonversi nomor identitas ke format **heksadesimal** (untuk sistem pengalamatan memori).

Program ini **tidak boleh** menggunakan fungsi bawaan Python seperti `bin()`, `oct()`, `hex()`, `math.gcd()`, dsb. — semua algoritma harus dibuat sendiri.

---

## Tahapan Penyelesaian Wajib

Ikuti alur berikut secara berurutan dan dokumentasikan setiap tahap:

```text
1. Identifikasi Masalah
        ↓
2. Tentukan Input dan Output
        ↓
3. Buat Algoritma / Pseudocode
        ↓
4. Implementasikan dalam Python
        ↓
5. Lakukan Pengujian (Testing)
        ↓
6. Analisis dan Jelaskan Hasil
```

---

## Starter Code

```python
# ============================================================
# ASESMEN MODUL 2 — Analisis Nomor Identitas
# Nama   :
# NIM    :
# Kelas  :
# Tanggal:
# ============================================================

# -------------------------------------------------------
# Bagian 1: Tentukan ganjil/genap
# -------------------------------------------------------
def adalah_genap(n):
    # TODO: Implementasikan tanpa menggunakan fungsi bawaan
    pass


# -------------------------------------------------------
# Bagian 2: Tentukan bilangan prima
# -------------------------------------------------------
def adalah_prima(n):
    # TODO: Implementasikan dengan algoritma yang efisien
    # Petunjuk: hanya periksa pembagi hingga √n
    pass


# -------------------------------------------------------
# Bagian 3: FPB menggunakan algoritma Euclidean
# -------------------------------------------------------
def fpb(a, b):
    # TODO: Implementasikan algoritma Euclidean
    pass


# -------------------------------------------------------
# Bagian 4: KPK menggunakan FPB
# -------------------------------------------------------
def kpk(a, b):
    # TODO: Gunakan relasi KPK(a,b) = (a × b) / FPB(a, b)
    pass


# -------------------------------------------------------
# Bagian 5: Konversi desimal ke heksadesimal
# -------------------------------------------------------
def desimal_ke_hex(n):
    # TODO: Implementasikan algoritma pembagian berulang
    # Petunjuk: digit_hex = "0123456789ABCDEF"
    pass


# -------------------------------------------------------
# Data perangkat (nomor identitas)
# -------------------------------------------------------
perangkat = [
    {"nama": "Router-01",  "id": 97},
    {"nama": "Switch-02",  "id": 84},
    {"nama": "Server-03",  "id": 100},
    {"nama": "PC-Lab-04",  "id": 17},
    {"nama": "Printer-05", "id": 60},
    {"nama": "AP-Wifi-06", "id": 37},
]

# Pasangan perangkat untuk analisis FPB/KPK
pasangan_maintenance = [
    ("Router-01", 97, "Switch-02",  84),
    ("Server-03", 100, "PC-Lab-04", 60),
]


# -------------------------------------------------------
# Tampilkan hasil analisis
# -------------------------------------------------------
def analisis_perangkat(perangkat):
    print("=" * 65)
    print(f"{'Nama':<14} {'ID':>5} {'Genap?':>7} {'Prima?':>7} {'Hex':>8}")
    print("=" * 65)
    for p in perangkat:
        nama = p["nama"]
        n    = p["id"]
        # TODO: Panggil fungsi yang sudah dibuat
        genap = None   # ganti dengan adalah_genap(n)
        prima = None   # ganti dengan adalah_prima(n)
        hex_n = None   # ganti dengan desimal_ke_hex(n)
        print(f"{nama:<14} {n:>5} {str(genap):>7} {str(prima):>7} {str(hex_n):>8}")
    print()

def analisis_maintenance(pasangan):
    print("Jadwal Maintenance Bersama:")
    print("-" * 45)
    for nama_a, id_a, nama_b, id_b in pasangan:
        # TODO: Panggil fungsi fpb dan kpk
        hasil_fpb = None   # ganti dengan fpb(id_a, id_b)
        hasil_kpk = None   # ganti dengan kpk(id_a, id_b)
        print(f"  {nama_a} (ID={id_a}) & {nama_b} (ID={id_b})")
        print(f"    FPB = {hasil_fpb} | KPK = {hasil_kpk}")
        print()


# Jalankan
analisis_perangkat(perangkat)
analisis_maintenance(pasangan_maintenance)
```

---

## Produk yang Dikumpulkan

### 1. Dokumentasi Analisis
- Jelaskan masalah dengan kata-kata sendiri.
- Identifikasi: apa input, proses, dan output setiap fungsi?

### 2. Algoritma / Pseudocode
Tulis pseudocode untuk **setiap fungsi** sebelum mengimplementasikan kode Python. Contoh format:

```text
ALGORITMA adalah_prima(n)
INPUT : integer n
OUTPUT: True / False
...
```

### 3. Program Python Lengkap
- Kode rapi, terdokumentasi (ada komentar dan docstring).
- Semua fungsi diimplementasikan tanpa menggunakan fungsi bawaan Python yang setara.

### 4. Tabel Pengujian
Buat tabel pengujian dengan **minimal 10 test case**. Sertakan kasus-kasus batas:

| Fungsi | Input | Output yang Diharapkan | Output Program | Status |
|--------|-------|------------------------|----------------|--------|
| `adalah_genap` | 0 | True | | |
| `adalah_genap` | 7 | False | | |
| `adalah_prima` | 1 | False | | |
| `adalah_prima` | 2 | True | | |
| `adalah_prima` | 97 | True | | |
| `fpb` | 12, 18 | 6 | | |
| `kpk` | 12, 18 | 36 | | |
| `desimal_ke_hex` | 0 | "0" | | |
| `desimal_ke_hex` | 255 | "FF" | | |
| `desimal_ke_hex` | 16 | "10" | | |

### 5. Analisis dan Kesimpulan
- Apakah semua test case lulus?
- Adakah kasus yang menghasilkan output tidak terduga? Jelaskan mengapa.
- Mana algoritma yang menurut Anda paling efisien? Mengapa?

---

## Rubrik Penilaian

| Komponen | Bobot |
|----------|------:|
| Analisis masalah dan identifikasi I/O | 15% |
| Pseudocode / algoritma (setiap fungsi) | 25% |
| Implementasi Python (ketepatan & kebersihan kode) | 30% |
| Pengujian (minimal 10 test case, termasuk kasus batas) | 15% |
| Penjelasan dan analisis hasil | 15% |

---

## Refleksi Asesmen

1. Fungsi mana yang paling sulit diimplementasikan? Mengapa?
2. Apa perbedaan antara membuat algoritma terlebih dahulu dengan langsung menulis kode?
3. Jika bilangan yang diuji sangat besar (misal n = 10.000.000), apakah algoritma Anda masih efisien?
4. Apa yang dapat Anda pelajari dari modul ini tentang hubungan matematika diskrit dengan pemrograman?
