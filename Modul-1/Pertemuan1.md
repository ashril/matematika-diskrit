# Pertemuan 1 — Logika Proposisional

## Tema
**Logika dalam Sistem Komputer: Dari Pernyataan ke Program**

## Tujuan Pembelajaran
Mahasiswa mampu:
1. menjelaskan proposisi dan nilai kebenaran;
2. membedakan proposisi atomik dan majemuk;
3. menggunakan `NOT`, `AND`, `OR`, dan `XOR`;
4. menerjemahkan kondisi logis menjadi Boolean;
5. mengimplementasikan logika menggunakan Python;
6. melakukan testing.

## 1. Pengantar Matematika Diskrit

Matematika diskrit mempelajari objek yang terpisah atau dapat dihitung, seperti bilangan bulat, graf, algoritma, proposisi, dan himpunan. Dalam ilmu komputer, matematika diskrit membantu merancang algoritma, memvalidasi program, memodelkan data, serta menganalisis jaringan dan sistem digital.

Komputasi menerjemahkan aturan formal menjadi langkah yang dapat dijalankan mesin. Karena itu, kemampuan mengubah pernyataan sehari-hari menjadi model logika merupakan dasar penting pemrograman.

## 2. Praktikum Dasar Python

Pastikan Python 3.10 atau lebih baru terpasang, lalu verifikasi melalui terminal:

```bash
python --version
```

Variabel menyimpan data. Tipe data dasar yang digunakan pada pertemuan ini adalah `str`, `int`, `float`, dan `bool`.

```python
nama = "Sari"       # str
umur = 19            # int
ipk = 3.75           # float
mahasiswa_aktif = True  # bool

print(nama, umur, ipk, mahasiswa_aktif)
```

Operator perbandingan menghasilkan Boolean:

```python
nilai = 78
print(nilai >= 60)
print(nilai == 78)
print(nilai != 100)
```

## 3. Konsep Dasar

Proposisi adalah pernyataan yang dapat bernilai **benar (True)** atau **salah (False)**.

Contoh:

```text
P = Username benar
Q = Password benar
R = Akun aktif
```

Dalam Python:

```python
True
False
```

### Operator Logika

| Operator | Simbol | Python |
|---|---|---|
| Negasi | ¬P | `not P` |
| Konjungsi | P ∧ Q | `P and Q` |
| Disjungsi | P ∨ Q | `P or Q` |
| XOR | P ⊕ Q | `P != Q` |

Contoh:

```python
P = True
Q = False

print(not P)
print(P and Q)
print(P or Q)
print(P != Q)
```

## 4. Studi Kasus PBL — Sistem Login

Pengguna hanya boleh login jika:
- username benar;
- password benar;
- akun aktif.

Model:

```text
Login = P ∧ Q ∧ R
```

Python:

```python
username_benar = True
password_benar = True
akun_aktif = True

login = username_benar and password_benar and akun_aktif

print("Status login:", login)
```

## 5. Algorithmic Thinking

**Input:** username, password, status akun.  
**Proses:** `Login = P AND Q AND R`  
**Output:** berhasil atau ditolak.

Pseudocode:

```text
START
    input username_benar
    input password_benar
    input akun_aktif

    login = username_benar AND password_benar AND akun_aktif

    tampilkan login
END
```

## 6. Praktikum

Buat:

```text
pertemuan-01/studi_kasus.py
```

Jalankan:

```bash
python studi_kasus.py
```

Uji minimal empat kondisi:

| Username | Password | Aktif | Hasil |
|---|---|---|---|
| True | True | True | ? |
| True | True | False | ? |
| True | False | True | ? |
| False | True | True | ? |

## 7. Latihan

### Latihan 1
Tentukan hasil:

```python
P = True
Q = False

not P
P and Q
P or Q
P != Q
```

### Latihan 2
Buat sistem kelayakan ujian:

```text
kehadiran >= 75% AND administrasi_lunas
```

### Latihan 3
Tambahkan syarat `mahasiswa_aktif`.

## 8. Challenge

Buat simulasi akses laboratorium dengan syarat:

```text
Mahasiswa terdaftar
AND kartu aktif
AND laboratorium buka
```

Buat model logika, pseudocode, program Python, dan minimal 4 test case.

## 9. Refleksi
1. Apa itu proposisi?
2. Apa perbedaan `and` dan `or`?
3. Mengapa logika dimodelkan sebelum diprogram?
4. Apa hubungan logika proposisional dengan sistem komputer?

## Checklist
- [ ] Proposisi
- [ ] Boolean
- [ ] Operator logika
- [ ] Model logika
- [ ] Pseudocode
- [ ] Python
- [ ] Testing
- [ ] Refleksi
