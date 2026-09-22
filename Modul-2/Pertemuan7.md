# Pertemuan 7 — Teori Bilangan dan Algoritma

## Tema
**Membangun Algoritma dari Konsep Bilangan: Prima, FPB, dan KPK**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menjelaskan konsep faktor, kelipatan, ganjil/genap, modulus, dan bilangan prima;
2. menerapkan algoritma Euclidean untuk menghitung FPB;
3. menghitung KPK menggunakan relasi FPB × KPK = a × b;
4. mengimplementasikan algoritma dengan `def`, `for`, dan `while` di Python;
5. menganalisis efisiensi sederhana dari algoritma yang dibuat;
6. memodelkan masalah penjadwalan menggunakan KPK.

---

## 1. Teori Ringkas

### 1.1 Konsep Dasar

| Konsep | Definisi | Contoh |
|--------|----------|--------|
| **Faktor** | a adalah faktor dari b jika b mod a = 0 | Faktor dari 12: {1,2,3,4,6,12} |
| **Kelipatan** | Kelipatan a adalah {a, 2a, 3a, …} | Kelipatan 4: {4, 8, 12, 16, …} |
| **Ganjil/Genap** | Genap jika n mod 2 = 0 | 4 genap, 7 ganjil |
| **Modulus** | n mod m = sisa pembagian n oleh m | 17 mod 5 = 2 |

### 1.2 Bilangan Prima

**Bilangan prima** adalah bilangan bulat > 1 yang hanya memiliki dua faktor: 1 dan dirinya sendiri.

Contoh: 2, 3, 5, 7, 11, 13, 17, 19, …

**Algoritma pemeriksaan primality:**

```text
ALGORITMA adalah_prima(n)
INPUT : bilangan bulat n
OUTPUT: True jika prima, False jika bukan

START
    JIKA n <= 1 MAKA kembalikan False
    UNTUK i dari 2 hingga √n:
        JIKA n mod i == 0 MAKA kembalikan False
    kembalikan True
END
```

> **Mengapa hanya sampai √n?**  
> Jika n memiliki faktor > √n, maka pasangan faktornya pasti < √n.  
> Sehingga cukup memeriksa hingga √n.

### 1.3 FPB dan Algoritma Euclidean

**FPB (Faktor Persekutuan Terbesar)** adalah bilangan terbesar yang membagi habis dua bilangan.

**Algoritma Euclidean:**

$$\text{FPB}(a, b) = \text{FPB}(b,\ a\ \text{mod}\ b) \quad \text{jika } b \neq 0$$
$$\text{FPB}(a, 0) = a$$

**Contoh: FPB(48, 18)**

```text
FPB(48, 18) = FPB(18, 48 mod 18) = FPB(18, 12)
FPB(18, 12) = FPB(12, 18 mod 12) = FPB(12, 6)
FPB(12,  6) = FPB( 6, 12 mod  6) = FPB( 6, 0)
FPB( 6,  0) = 6
```

### 1.4 KPK

**KPK (Kelipatan Persekutuan Terkecil)** menggunakan relasi:

$$\text{KPK}(a, b) = \frac{a \times b}{\text{FPB}(a, b)}$$

**Contoh: KPK(12, 18)**

$$\text{KPK}(12, 18) = \frac{12 \times 18}{\text{FPB}(12, 18)} = \frac{216}{6} = 36$$

---

## 2. Praktikum

### 2.1 Operasi Dasar Bilangan

Buat file `pertemuan-07/teori_bilangan.py`:

```python
import math

# --- Ganjil / Genap ---
def adalah_genap(n):
    return n % 2 == 0

# --- Modulus ---
def hitung_modulus(n, m):
    return n % m

# --- Faktor-faktor ---
def cari_faktor(n):
    faktor = []
    for i in range(1, n + 1):
        if n % i == 0:
            faktor.append(i)
    return faktor

# --- Bilangan prima ---
def adalah_prima(n):
    if n <= 1:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    i = 3
    while i * i <= n:
        if n % i == 0:
            return False
        i += 2
    return True

# --- FPB (Algoritma Euclidean) ---
def fpb(a, b):
    while b != 0:
        a, b = b, a % b
    return a

# --- KPK ---
def kpk(a, b):
    return abs(a * b) // fpb(a, b)

# --- Tampilkan hasil ---
bilangan_uji = [1, 2, 7, 12, 17, 24, 36, 97, 100]

print("=" * 55)
print(f"{'Bilangan':>10} {'Genap?':>8} {'Prima?':>8} {'Faktor'}")
print("=" * 55)
for n in bilangan_uji:
    print(f"{n:>10} {str(adalah_genap(n)):>8} {str(adalah_prima(n)):>8}  {cari_faktor(n)}")

print()
pasangan = [(12, 18), (48, 36), (7, 13), (100, 75)]
print(f"{'(a, b)':>12} {'FPB':>6} {'KPK':>8}")
print("-" * 30)
for a, b in pasangan:
    print(f"({a:>3}, {b:>3})  {fpb(a, b):>6} {kpk(a, b):>8}")
```

### 2.2 Mencari Semua Bilangan Prima hingga N (Sieve of Eratosthenes)

```python
def sieve_of_eratosthenes(batas):
    """Mencari semua bilangan prima dari 2 hingga batas."""
    prima = [True] * (batas + 1)
    prima[0] = prima[1] = False

    p = 2
    while p * p <= batas:
        if prima[p]:
            # Tandai semua kelipatan p sebagai bukan prima
            for i in range(p * p, batas + 1, p):
                prima[i] = False
        p += 1

    return [n for n in range(2, batas + 1) if prima[n]]

prima_100 = sieve_of_eratosthenes(100)
print(f"Bilangan prima hingga 100 ({len(prima_100)} bilangan):")
print(prima_100)
```

---

## 3. PBL — Penjadwalan Server

### Skenario

Sebuah data center memiliki dua server yang melakukan proses backup secara rutin:

- **Server A** melakukan backup setiap **12 menit**
- **Server B** melakukan backup setiap **18 menit**

Keduanya mulai beroperasi pada waktu yang sama (menit ke-0).

**Pertanyaan:** Pada menit keberapa mereka pertama kali melakukan backup secara **bersamaan** setelah menit ke-0?

### Model Matematika

```text
Server A : backup pada menit ke-0, 12, 24, 36, ...
Server B : backup pada menit ke-0, 18, 36, ...
Bersamaan : Kelipatan Persekutuan Terkecil dari 12 dan 18
Jawaban   : KPK(12, 18)
```

### Pseudocode

```text
ALGORITMA jadwal_bersama(a, b)
INPUT : interval Server A (a), interval Server B (b)
OUTPUT: menit pertama kali keduanya backup bersamaan

START
    hitung FPB(a, b) menggunakan algoritma Euclidean
    hitung KPK = (a × b) / FPB(a, b)
    tampilkan KPK
END
```

### Implementasi

Buat file `pertemuan-07/penjadwalan_server.py`:

```python
def fpb(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def kpk(a, b):
    return abs(a * b) // fpb(a, b)

def jadwal_backup(interval_a, interval_b, durasi_pantau=120):
    """
    Menentukan jadwal backup bersama dua server.
    Menampilkan semua momen backup dalam rentang durasi pantau.
    """
    waktu_bersama = kpk(interval_a, interval_b)

    # Buat jadwal backup masing-masing server
    jadwal_a = set(range(0, durasi_pantau + 1, interval_a))
    jadwal_b = set(range(0, durasi_pantau + 1, interval_b))

    # Momen backup bersamaan
    bersamaan = sorted(jadwal_a & jadwal_b)

    print(f"Server A: backup setiap {interval_a} menit")
    print(f"Server B: backup setiap {interval_b} menit")
    print()
    print(f"FPB({interval_a}, {interval_b}) = {fpb(interval_a, interval_b)}")
    print(f"KPK({interval_a}, {interval_b}) = {waktu_bersama}")
    print()
    print(f"Pertama kali backup bersamaan: menit ke-{waktu_bersama}")
    print()
    print(f"Jadwal backup bersamaan dalam {durasi_pantau} menit ke depan:")
    print(bersamaan)

# Kasus utama: Server A = 12 menit, Server B = 18 menit
jadwal_backup(12, 18)

print()
print("=" * 50)
print()

# Kasus tambahan: Server C = 15 menit, Server D = 20 menit
jadwal_backup(15, 20)
```

### Skenario Tambahan

Sistem keamanan juga harus memverifikasi apakah nomor identitas perangkat merupakan **bilangan prima** (bilangan prima digunakan sebagai kunci enkripsi sederhana).

```python
def periksa_id_perangkat(daftar_id):
    print("\nVerifikasi ID Perangkat:")
    print(f"{'ID':>8} {'Prima?':>8} {'Keterangan'}")
    print("-" * 35)
    for id_perangkat in daftar_id:
        status = adalah_prima(id_perangkat)
        ket = "Dapat digunakan sebagai kunci" if status else "Bukan bilangan prima"
        print(f"{id_perangkat:>8} {str(status):>8}  {ket}")

daftar_id_uji = [7, 11, 15, 23, 49, 97, 100, 101]
periksa_id_perangkat(daftar_id_uji)
```

---

## 4. Latihan dan Refleksi

### Latihan 1
Hitung FPB(84, 56) menggunakan algoritma Euclidean secara manual, langkah demi langkah.

### Latihan 2
Tiga lampu kilat menyala bersamaan pada detik ke-0:
- Lampu Merah: setiap 6 detik
- Lampu Kuning: setiap 10 detik
- Lampu Hijau: setiap 15 detik

Kapan ketiganya menyala bersamaan pertama kali?

> Petunjuk: KPK tiga bilangan = KPK(KPK(a, b), c)

### Latihan 3
Modifikasi fungsi `adalah_prima` agar lebih efisien dengan hanya memeriksa bilangan ganjil setelah angka 2.

### Latihan 4
Buktikan secara matematis bahwa FPB(a, b) × KPK(a, b) = a × b dengan contoh angka konkret.

### Refleksi
1. Mengapa algoritma Euclidean lebih efisien dari cara mencari semua faktor?
2. Bagaimana hubungan antara bilangan prima dan kriptografi?
3. Apa dampaknya jika kita mengubah `while i * i <= n` menjadi `while i <= n` pada fungsi `adalah_prima`?
4. Dalam masalah nyata, kapan KPK lebih berguna daripada FPB?

---

## Checklist

- [ ] Konsep faktor, kelipatan, ganjil/genap, modulus
- [ ] Bilangan prima dan algoritma primality
- [ ] Sieve of Eratosthenes
- [ ] Algoritma Euclidean untuk FPB
- [ ] KPK menggunakan FPB
- [ ] Implementasi semua fungsi dengan `def`, `for`, `while`
- [ ] Program penjadwalan server
- [ ] Verifikasi ID perangkat (prima)
- [ ] Minimal 6 test case
