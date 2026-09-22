# Pertemuan 5 — Relasi dan Fungsi

## Tema
**Memetakan Hubungan: Dari Diagram Panah ke Kode Python**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. menjelaskan definisi relasi dan cara merepresentasikannya;
2. membedakan sifat relasi: refleksif, simetris, antisimetris, dan transitif;
3. mendefinisikan fungsi beserta domain, kodomain, dan range-nya;
4. membedakan fungsi injektif, surjektif, dan bijektif;
5. merepresentasikan relasi dan fungsi dalam Python;
6. memvisualisasikan fungsi matematis dengan Matplotlib.

---

## 1. Teori Ringkas

### 1.1 Relasi

**Relasi** dari himpunan A ke himpunan B adalah himpunan bagian dari **Cartesian product** A × B.

$$A \times B = \{(a, b) \mid a \in A,\ b \in B\}$$

Contoh: A = {1, 2, 3}, B = {a, b}

$$A \times B = \{(1,a),(1,b),(2,a),(2,b),(3,a),(3,b)\}$$

Relasi R = {(1, a), (2, b), (3, a)} adalah himpunan bagian dari A × B.

#### Cara Representasi Relasi

| Cara | Keterangan |
|------|-----------|
| **Diagram panah** | Gambar panah dari elemen A ke elemen B |
| **Himpunan pasangan berurutan** | R = {(1, a), (2, b)} |
| **Matriks relasi** | Baris = A, Kolom = B, isi 1 jika ada relasi |

#### Sifat-Sifat Relasi (pada himpunan A ke A)

| Sifat | Definisi | Contoh |
|-------|----------|--------|
| **Refleksif** | Setiap elemen berelasi dengan dirinya sendiri: $(a,a) \in R$ untuk semua $a$ | "sama dengan" |
| **Simetris** | Jika $(a,b) \in R$ maka $(b,a) \in R$ | "berteman" |
| **Antisimetris** | Jika $(a,b) \in R$ dan $(b,a) \in R$ maka $a = b$ | "≤" |
| **Transitif** | Jika $(a,b) \in R$ dan $(b,c) \in R$ maka $(a,c) \in R$ | "lebih kecil dari" |

### 1.2 Fungsi

**Fungsi** f: A → B adalah relasi khusus di mana **setiap elemen A dipetakan ke tepat satu elemen B**.

- **Domain**: himpunan input (A)
- **Kodomain**: himpunan output yang mungkin (B)
- **Range**: himpunan output yang benar-benar dihasilkan, Range ⊆ Kodomain

#### Jenis Fungsi

| Jenis | Definisi | Ciri |
|-------|----------|------|
| **Injektif (one-to-one)** | Setiap elemen B dipetakan dari paling banyak satu elemen A | Tidak ada dua input yang menghasilkan output sama |
| **Surjektif (onto)** | Setiap elemen B dipetakan oleh minimal satu elemen A | Range = Kodomain |
| **Bijektif** | Injektif dan surjektif sekaligus | Korespondensi satu-satu |

---

## 2. Praktikum

### 2.1 Representasi Relasi dengan Python

Buat file `pertemuan-05/relasi.py`:

```python
# Cartesian product
from itertools import product

A = {1, 2, 3}
B = {'a', 'b'}

cartesian = set(product(A, B))
print("A × B:", cartesian)

# Definisikan relasi sebagai himpunan pasangan
R = {(1, 'a'), (2, 'b'), (3, 'a')}
print("Relasi R:", R)

# Matriks relasi
A_list = sorted(A)
B_list = sorted(B)

print("\nMatriks Relasi R:")
print(f"{'':>4}", end="")
for b in B_list:
    print(f"{b:>4}", end="")
print()

for a in A_list:
    print(f"{a:>4}", end="")
    for b in B_list:
        print(f"{1 if (a, b) in R else 0:>4}", end="")
    print()
```

### 2.2 Memeriksa Sifat Relasi

```python
# Memeriksa sifat relasi pada A ke A
A = {1, 2, 3}

# Relasi "kurang dari atau sama dengan"
R = {(a, b) for a in A for b in A if a <= b}
print("Relasi R (a ≤ b):", R)

# Refleksif: setiap (a, a) ada dalam R
refleksif = all((a, a) in R for a in A)
print("Refleksif:", refleksif)

# Simetris: jika (a,b) ada, maka (b,a) juga ada
simetris = all((b, a) in R for (a, b) in R)
print("Simetris:", simetris)

# Antisimetris: jika (a,b) dan (b,a) ada, maka a == b
antisimetris = all(a == b for (a, b) in R if (b, a) in R)
print("Antisimetris:", antisimetris)

# Transitif: jika (a,b) dan (b,c) ada, maka (a,c) juga ada
transitif = all((a, c) in R for (a, b) in R for (b2, c) in R if b == b2)
print("Transitif:", transitif)
```

### 2.3 Fungsi dengan `def` dan Visualisasi

Buat file `pertemuan-05/fungsi.py`:

```python
import matplotlib.pyplot as plt
import numpy as np

# Mendefinisikan fungsi matematis
def f_linear(x):
    return 2 * x + 1        # f(x) = 2x + 1

def f_kuadrat(x):
    return x ** 2 - 3 * x  # f(x) = x² - 3x

def f_kubik(x):
    return x ** 3 - x      # f(x) = x³ - x

# Membuat data
x = np.linspace(-4, 4, 200)

# Visualisasi
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

axes[0].plot(x, f_linear(x), color='royalblue', linewidth=2)
axes[0].set_title('f(x) = 2x + 1 (Linear)')
axes[0].set_xlabel('x')
axes[0].set_ylabel('f(x)')
axes[0].axhline(0, color='gray', linewidth=0.8)
axes[0].axvline(0, color='gray', linewidth=0.8)
axes[0].grid(True, alpha=0.3)

axes[1].plot(x, f_kuadrat(x), color='tomato', linewidth=2)
axes[1].set_title('f(x) = x² − 3x (Kuadrat)')
axes[1].set_xlabel('x')
axes[1].axhline(0, color='gray', linewidth=0.8)
axes[1].axvline(0, color='gray', linewidth=0.8)
axes[1].grid(True, alpha=0.3)

axes[2].plot(x, f_kubik(x), color='seagreen', linewidth=2)
axes[2].set_title('f(x) = x³ − x (Kubik)')
axes[2].set_xlabel('x')
axes[2].axhline(0, color='gray', linewidth=0.8)
axes[2].axvline(0, color='gray', linewidth=0.8)
axes[2].grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig('grafik_fungsi.png', dpi=150)
plt.show()
print("Grafik disimpan sebagai grafik_fungsi.png")
```

Jalankan:

```bash
python fungsi.py
```

---

## 3. PBL — Pemetaan Mahasiswa dan Mata Kuliah

### Skenario

Sistem akademik mencatat mata kuliah yang diambil setiap mahasiswa. Kita perlu menentukan apakah hubungan **Mahasiswa → Mata Kuliah** merupakan relasi, fungsi, injektif, atau surjektif.

### Data

```text
Mahasiswa : {Ani, Budi, Citra, Deni}
Mata Kuliah: {MatDis, Algoritma, Basis Data, Jaringan}

Hubungan  :
  Ani   → MatDis
  Budi  → Algoritma
  Citra → MatDis
  Deni  → Basis Data
```

### Implementasi

Buat file `pertemuan-05/pemetaan_matkul.py`:

```python
# Domain: mahasiswa, Kodomain: mata kuliah
mahasiswa   = {"Ani", "Budi", "Citra", "Deni"}
mata_kuliah = {"MatDis", "Algoritma", "Basis Data", "Jaringan"}

# Hubungan sebagai dictionary (setiap mahasiswa → satu matkul)
pemetaan = {
    "Ani"  : "MatDis",
    "Budi" : "Algoritma",
    "Citra": "MatDis",
    "Deni" : "Basis Data",
}

# Apakah ini sebuah fungsi?
# Fungsi: setiap elemen domain dipetakan ke tepat satu elemen kodomain
adalah_fungsi = len(pemetaan) == len(mahasiswa) and \
                all(v in mata_kuliah for v in pemetaan.values())
print("Apakah merupakan fungsi?", adalah_fungsi)

# Range (output yang benar-benar dihasilkan)
range_fungsi = set(pemetaan.values())
print("Range:", range_fungsi)
print("Kodomain:", mata_kuliah)

# Injektif: tidak ada dua mahasiswa → matkul yang sama
values = list(pemetaan.values())
injektif = len(values) == len(set(values))
print("Injektif (one-to-one)?", injektif)

# Surjektif: range = kodomain
surjektif = range_fungsi == mata_kuliah
print("Surjektif (onto)?", surjektif)

# Bijektif
bijektif = injektif and surjektif
print("Bijektif?", bijektif)

# Analisis
print("\n--- Analisis ---")
for mhs, mk in pemetaan.items():
    print(f"  {mhs:6} → {mk}")
```

### Pertanyaan Analisis

1. Mengapa hubungan ini disebut fungsi?
2. Mengapa tidak injektif? Siapa yang menjadi buktinya?
3. Mata kuliah mana yang tidak di-cover (ada di kodomain tapi bukan range)?
4. Apa yang harus diubah agar fungsi menjadi bijektif?

---

## 4. Latihan dan Refleksi

### Latihan 1
Diberikan A = {1, 2, 3, 4} dan relasi R = {(1,2), (2,3), (3,4), (1,1), (2,2), (3,3), (4,4)}.
- Apakah R refleksif? simetris? antisimetris? transitif?
- Tuliskan matriks relasinya.

### Latihan 2
Buatlah fungsi Python `kuadrat(x)` yang mengembalikan nilai $x^2$. Hitung f(0), f(1), f(2), f(−1), f(−2).
- Apakah fungsi ini injektif jika domain = bilangan bulat?

### Latihan 3
Tambahkan mahasiswa "Eka → Jaringan" pada studi kasus di atas.
- Apakah sekarang surjektif? Apakah bijektif?

### Refleksi
1. Apa perbedaan relasi dan fungsi?
2. Mengapa setiap fungsi adalah relasi, tetapi tidak sebaliknya?
3. Apa hubungan domain, kodomain, dan range?
4. Dalam pemrograman, kapan sebuah prosedur (`def`) disebut fungsi matematis?

---

## Checklist

- [ ] Cartesian product
- [ ] Representasi relasi (pasangan, matriks)
- [ ] Sifat refleksif, simetris, antisimetris, transitif
- [ ] Definisi fungsi dan jenis-jenisnya
- [ ] Domain, kodomain, range
- [ ] Implementasi relasi dan fungsi dalam Python
- [ ] Visualisasi grafik fungsi dengan Matplotlib
- [ ] Analisis pemetaan mahasiswa–matkul
- [ ] Minimal 4 test case
