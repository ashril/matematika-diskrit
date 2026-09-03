# Pertemuan 3 — Teori Himpunan dan Operasi Himpunan

## Tema
**Mengelompokkan Informasi dan Menemukan Relasi Antaranggota**

## Tujuan Pembelajaran

Mahasiswa mampu menjelaskan notasi himpunan, elemen, himpunan kosong, semesta, subset, cardinality, dan Cartesian product, serta menerapkan operasinya dalam Python.

## 1. Teori Ringkas

Himpunan adalah kumpulan objek yang terdefinisi dengan jelas. Jika `x` anggota `A`, ditulis $x ∈ A$. Himpunan kosong ditulis $∅$, himpunan semesta $U$, dan `A` subset `B` ditulis $A ⊆ B$.

| Konsep | Notasi | Python |
|---|---|---|
| Union | $A ∪ B$ | `A | B` |
| Intersection | $A ∩ B$ | `A & B` |
| Difference | $A - B$ | `A - B` |
| Complement | $A^c = U - A$ | `U - A` |
| Cardinality | $|A|$ | `len(A)` |
| Cartesian product | $A × B$ | pasangan dengan `product()` |

## 2. Praktikum — Python `set`

```python
from itertools import product

A = {1, 2, 3, 4}
B = {3, 4, 5, 6}
U = set(range(1, 9))

print("Union       :", A | B)
print("Intersection:", A & B)
print("Difference  :", A - B)
print("Complement  :", U - A)
print("Cardinality :", len(A))
print("Subset?     :", A <= U)
print("A x B       :", set(product(A, B)))
```

`set` tidak menyimpan urutan dan tidak boleh memiliki elemen duplikat.

## 3. PBL — Preferensi Teknologi Mahasiswa

```python
python = {"Ani", "Budi", "Citra"}
java = {"Budi", "Deni"}
sql = {"Ani", "Deni", "Eka"}
semua_mahasiswa = {"Ani", "Budi", "Citra", "Deni", "Eka", "Fajar"}

python_saja = python - (java | sql)
python_dan_java = python & java
minimal_satu = python | java | sql
tidak_menyukai_ketiganya = semua_mahasiswa - (python | java | sql)

print("Python saja:", python_saja)
print("Python dan Java:", python_dan_java)
print("Minimal satu teknologi:", minimal_satu)
print("Tidak menyukai ketiganya:", tidak_menyukai_ketiganya)
```

“Python saja” berarti menyukai Python tetapi tidak Java maupun SQL. “Minimal satu” berarti union ketiga himpunan.

## 4. Latihan dan Refleksi

1. Hitung `B - A` dan `A & (B | A)` secara manual.
2. Tambahkan JavaScript, lalu cari mahasiswa yang menyukai tepat dua teknologi.
3. Jelaskan perbedaan `A - B` dan `B - A`.
4. Mengapa complement harus menggunakan himpunan semesta?

## Checklist

- [ ] Notasi dan jenis himpunan
- [ ] Union, intersection, difference
- [ ] Complement dan cardinality
- [ ] Subset dan Cartesian product
- [ ] Analisis data preferensi
- [ ] Program Python dan output
