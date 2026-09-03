# Pertemuan 2 — Tabel Kebenaran dan Logika Predikat

## Tema
**Menguji Kebenaran Pernyataan dan Menyatakan Syarat Umum**

## Tujuan Pembelajaran

Mahasiswa mampu:

1. membuat dan membaca tabel kebenaran;
2. membedakan tautologi, kontradiksi, dan kontingensi;
3. memeriksa ekuivalensi logika dengan tabel kebenaran;
4. menjelaskan predikat serta kuantor universal dan eksistensial;
5. mengevaluasi kondisi seleksi menggunakan Python.

## 1. Teori Ringkas

Untuk dua proposisi terdapat $2^2 = 4$ kombinasi nilai.

| P | Q | P and Q | P or Q | not P |
|---|---|---------|--------|-------|
| T | T | T | T | F |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

- **Tautologi:** selalu benar, misalnya `P or not P`.
- **Kontradiksi:** selalu salah, misalnya `P and not P`.
- **Kontingensi:** kadang benar dan kadang salah, misalnya `P and Q`.
- **Ekuivalensi:** dua ekspresi bernilai sama pada semua baris. Contohnya `not (P and Q)` ekuivalen dengan `not P or not Q` (Hukum De Morgan).

Predikat adalah kalimat yang nilai kebenarannya bergantung pada variabel. Contoh: `Lulus(x): x memiliki nilai akhir >= 60`.

- `forall x P(x)` berarti setiap elemen memenuhi `P` (kuantor universal).
- `exists x P(x)` berarti setidaknya satu elemen memenuhi `P` (kuantor eksistensial).

Dalam Python, `all()` mendekati kuantor universal dan `any()` mendekati kuantor eksistensial.

## 2. Praktikum — Generator Tabel Kebenaran

Buat `pertemuan-02/tabel_kebenaran.py`:

```python
nilai = [True, False]

print("P     Q     P and Q   P or Q   not P")
for p in nilai:
    for q in nilai:
        print(f"{p!s:<5} {q!s:<5} {p and q!s:<8} {p or q!s:<8} {not p!s}")
```

Kembangkan program untuk membandingkan `not (p and q)` dengan `((not p) or (not q))` pada semua kombinasi.

## 3. PBL — Seleksi Peserta Praktikum

Mahasiswa memenuhi syarat jika sudah mengisi formulir, nilai prasyarat minimal 60, kehadiran minimal 75%, dan tidak terkena sanksi akademik.

Model:

```text
L = formulir AND (nilai >= 60) AND (kehadiran >= 75) AND (NOT sanksi)
```

```python
def memenuhi_syarat(formulir, nilai, kehadiran, sanksi):
    return formulir and nilai >= 60 and kehadiran >= 75 and not sanksi

data = (True, 72, 80, False)
print("Dapat mengikuti praktikum:", memenuhi_syarat(*data))
```

Gunakan `all()` untuk memeriksa apakah semua mahasiswa mencapai nilai minimum, dan `any()` untuk memeriksa apakah ada mahasiswa dengan nilai minimal 90.

## 4. Latihan dan Refleksi

1. Tentukan apakah `(P or Q) and not P` tautologi, kontradiksi, atau kontingensi.
2. Buat tabel kebenaran untuk `P -> Q`. Implikasi salah hanya ketika P benar dan Q salah.
3. Tambahkan alasan penolakan pada fungsi seleksi.
4. Jelaskan perbedaan makna `all()` dan `any()`.

## Checklist

- [ ] Tabel kebenaran
- [ ] Tautologi, kontradiksi, kontingensi
- [ ] Ekuivalensi dan hukum De Morgan
- [ ] Predikat dan kuantor
- [ ] Program seleksi
- [ ] Minimal 4 skenario pengujian
