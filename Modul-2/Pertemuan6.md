# Pertemuan 6 — Sistem Bilangan dan Algoritma

## Tema
**Bahasa Komputer: Bilangan Biner, Oktal, dan Heksadesimal**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menjelaskan sistem bilangan desimal, biner, oktal, dan heksadesimal;
2. mengonversi bilangan antar basis secara manual menggunakan algoritma pembagian berulang;
3. mengimplementasikan algoritma konversi dalam Python menggunakan `def`, `for`, dan `while`;
4. membandingkan hasil algoritma buatan sendiri dengan fungsi bawaan Python `bin()`, `oct()`, `hex()`;
5. menulis pseudocode sebelum membuat program;
6. memodelkan masalah identifikasi perangkat menggunakan konversi bilangan.

---

## 1. Teori Ringkas

### 1.1 Sistem Bilangan

Sistem bilangan mendefinisikan cara bilangan direpresentasikan menggunakan digit-digit tertentu dengan basis (radix) tertentu.

| Sistem | Basis | Digit yang Digunakan | Contoh |
|--------|-------|---------------------|--------|
| **Desimal** | 10 | 0–9 | 42 |
| **Biner** | 2 | 0, 1 | 101010 |
| **Oktal** | 8 | 0–7 | 52 |
| **Heksadesimal** | 16 | 0–9, A–F | 2A |

### 1.2 Konversi Desimal → Basis Lain

**Algoritma pembagian berulang:**

1. Bagi bilangan desimal dengan basis tujuan.
2. Catat sisa pembagian (remainder).
3. Ulangi dengan hasil bagi (quotient) hingga quotient = 0.
4. Baca sisa pembagian dari bawah ke atas.

**Contoh: 42 → Biner (basis 2)**

```text
42 ÷ 2 = 21  sisa 0
21 ÷ 2 = 10  sisa 1
10 ÷ 2 =  5  sisa 0
 5 ÷ 2 =  2  sisa 1
 2 ÷ 2 =  1  sisa 0
 1 ÷ 2 =  0  sisa 1
               ↑ baca dari bawah ke atas
Hasil: 101010₂
```

### 1.3 Konversi Basis Lain → Desimal

Kalikan setiap digit dengan basis dipangkatkan posisinya (dari kanan, mulai 0):

$$101010_2 = 1 \times 2^5 + 0 \times 2^4 + 1 \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 0 \times 2^0 = 32+8+2 = 42$$

### 1.4 Pseudocode dan Flowchart

Sebelum membuat program, tuliskan **pseudocode** terlebih dahulu:

```text
ALGORITMA desimal_ke_biner(n)
INPUT : bilangan bulat n >= 0
OUTPUT: string representasi biner

START
    hasil = ""
    JIKA n == 0 MAKA kembalikan "0"
    SELAMA n > 0:
        sisa   = n MOD 2
        hasil  = str(sisa) + hasil
        n      = n DIV 2
    kembalikan hasil
END
```

---

## 2. Praktikum

### 2.1 Konversi Manual dengan Python

Buat file `pertemuan-06/konversi.py`:

```python
def desimal_ke_biner(n):
    """Konversi bilangan desimal ke biner (basis 2)."""
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        sisa = n % 2
        hasil = str(sisa) + hasil
        n = n // 2
    return hasil


def desimal_ke_oktal(n):
    """Konversi bilangan desimal ke oktal (basis 8)."""
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        sisa = n % 8
        hasil = str(sisa) + hasil
        n = n // 8
    return hasil


def desimal_ke_hex(n):
    """Konversi bilangan desimal ke heksadesimal (basis 16)."""
    digit_hex = "0123456789ABCDEF"
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        sisa = n % 16
        hasil = digit_hex[sisa] + hasil
        n = n // 16
    return hasil


def biner_ke_desimal(biner_str):
    """Konversi bilangan biner (string) ke desimal."""
    hasil = 0
    pangkat = 0
    for digit in reversed(biner_str):
        hasil += int(digit) * (2 ** pangkat)
        pangkat += 1
    return hasil


# Pengujian
bilangan = [0, 10, 42, 255, 1024]

print(f"{'Desimal':>10} {'Biner (manual)':>15} {'bin()':>12} {'Oktal (manual)':>15} {'oct()':>8} {'Hex (manual)':>13} {'hex()':>8}")
print("-" * 85)
for n in bilangan:
    biner_manual = desimal_ke_biner(n)
    oktal_manual = desimal_ke_oktal(n)
    hex_manual   = desimal_ke_hex(n)
    print(f"{n:>10} {biner_manual:>15} {bin(n)[2:]:>12} {oktal_manual:>15} {oct(n)[2:]:>8} {hex_manual:>13} {hex(n)[2:].upper():>8}")
```

Jalankan:

```bash
python konversi.py
```

### 2.2 Algoritma Umum: Konversi ke Basis Sembarang

```python
def desimal_ke_basis(n, basis):
    """Konversi desimal ke basis sembarang (2–16)."""
    digit = "0123456789ABCDEF"
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        hasil = digit[n % basis] + hasil
        n //= basis
    return hasil


# Uji
angka = 100
for basis in [2, 8, 10, 16]:
    print(f"100 dalam basis {basis:>2}: {desimal_ke_basis(angka, basis)}")
```

---

## 3. PBL — Sistem Identifikasi Perangkat

### Skenario

Sebuah sistem jaringan menyimpan ID perangkat dalam format desimal. Namun, sistem juga harus menampilkan ID tersebut dalam berbagai format:

- **Biner** → untuk keperluan hardware dan debugging tingkat rendah
- **Oktal** → digunakan pada sistem Unix/Linux (izin file)
- **Heksadesimal** → digunakan pada alamat memori dan MAC address

### Aturan

```text
ID Perangkat (desimal) → Tampilkan dalam Biner, Oktal, dan Heksadesimal
```

### Model Algoritmik

```text
INPUT  : daftar ID perangkat (integer desimal)
PROSES : untuk setiap ID, konversi ke biner, oktal, dan heksadesimal
OUTPUT : tabel lengkap representasi setiap ID
```

### Implementasi

Buat file `pertemuan-06/sistem_identifikasi.py`:

```python
def desimal_ke_biner(n):
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        hasil = str(n % 2) + hasil
        n //= 2
    return hasil

def desimal_ke_oktal(n):
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        hasil = str(n % 8) + hasil
        n //= 8
    return hasil

def desimal_ke_hex(n):
    digit_hex = "0123456789ABCDEF"
    if n == 0:
        return "0"
    hasil = ""
    while n > 0:
        hasil = digit_hex[n % 16] + hasil
        n //= 16
    return hasil


# Data perangkat jaringan
perangkat = [
    {"nama": "Router-A",  "id": 192},
    {"nama": "Switch-B",  "id": 255},
    {"nama": "Server-01", "id": 1024},
    {"nama": "PC-Lab",    "id": 42},
    {"nama": "AP-Wifi",   "id": 0},
]

print(f"{'Nama':<12} {'Desimal':>8} {'Biner':>12} {'Oktal':>8} {'Heksadesimal':>14}")
print("=" * 58)

for p in perangkat:
    nama = p["nama"]
    n    = p["id"]
    print(f"{nama:<12} {n:>8} {desimal_ke_biner(n):>12} {desimal_ke_oktal(n):>8} {desimal_ke_hex(n):>14}")

print("\nVerifikasi menggunakan fungsi bawaan Python:")
for p in perangkat:
    n = p["id"]
    print(f"  {p['nama']}: bin={bin(n)}, oct={oct(n)}, hex={hex(n).upper()}")
```

---

## 4. Latihan dan Refleksi

### Latihan 1
Konversikan bilangan berikut ke biner secara manual, kemudian verifikasi dengan Python:
- 13, 64, 127, 200

### Latihan 2
Konversikan bilangan biner berikut ke desimal secara manual:
- `1101`, `10000000`, `11111111`

### Latihan 3
Mengapa heksadesimal sering digunakan dalam pemrograman komputer? Berikan minimal dua contoh penggunaannya.

### Latihan 4
Modifikasi program `sistem_identifikasi.py` agar pengguna bisa memasukkan ID perangkat melalui input:
```python
id_input = int(input("Masukkan ID perangkat: "))
```

### Refleksi
1. Mengapa komputer menggunakan sistem biner?
2. Apa hubungan antara biner dan heksadesimal (mengapa satu digit hex = 4 digit biner)?
3. Apa peran pseudocode sebelum menulis program?
4. Kapan Anda akan memilih algoritma iteratif (`while`) vs. rekursif?

---

## Checklist

- [ ] Sistem bilangan: desimal, biner, oktal, heksadesimal
- [ ] Konversi desimal → biner, oktal, hex (manual)
- [ ] Konversi biner → desimal
- [ ] Perbandingan dengan `bin()`, `oct()`, `hex()`
- [ ] Pseudocode konversi
- [ ] Implementasi algoritma umum ke basis sembarang
- [ ] Program sistem identifikasi perangkat
- [ ] Minimal 5 test case (termasuk angka 0)
