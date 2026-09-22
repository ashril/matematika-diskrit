# Modul Praktikum 2 — Relasi, Fungsi, Sistem Bilangan & Teori Bilangan

**Tema besar:** Dari Model Matematika Menuju Algoritma<br>
**Cakupan:** Pertemuan 5–8

## Deskripsi

Modul ini menjadi jembatan antara matematika diskrit dan algoritma pemrograman. Mahasiswa mempelajari cara merepresentasikan hubungan antara objek (relasi dan fungsi), memahami bagaimana komputer menyimpan bilangan (sistem bilangan), dan menerapkan algoritma klasik teori bilangan. Setiap pertemuan memadukan teori, praktikum, problem based learning (PBL), latihan, dan refleksi.

## Capaian Pembelajaran

Setelah menyelesaikan modul, mahasiswa mampu:

- menjelaskan definisi relasi, sifat-sifat relasi, dan konsep fungsi (injektif, surjektif, bijektif);
- mengimplementasikan relasi dan fungsi matematis dalam Python;
- mengonversi bilangan antar basis (desimal, biner, oktal, heksadesimal) secara manual dan menggunakan Python;
- menulis pseudocode dan algoritma sebelum mengimplementasikan program;
- menentukan ganjil/genap, bilangan prima, FPB, dan KPK menggunakan algoritma yang efisien;
- memodelkan masalah nyata menggunakan relasi, fungsi, dan teori bilangan.

## Prasyarat dan Perangkat

- Python 3.10 atau lebih baru
- VSCode
- Matplotlib (`pip install matplotlib`)
- NumPy (`pip install numpy`)
- Terminal untuk menjalankan program

Verifikasi instalasi:

```bash
python --version
pip install matplotlib numpy
```

## Alur Pengerjaan

```text
Masalah → Identifikasi variabel → Model matematika
→ Algoritma → Pseudocode → Implementasi Python → Testing → Dokumentasi
```

## Struktur Folder

```text
Modul-2/
├── README.md
├── Pertemuan5.md   — Relasi dan Fungsi
├── Pertemuan6.md   — Sistem Bilangan dan Algoritma
├── Pertemuan7.md   — Teori Bilangan dan Algoritma
└── Pertemuan8.md   — Asesmen Modul 2
```

## Ketentuan Pengumpulan

Setiap pekerjaan dikumpulkan dalam folder pertemuan terkait dan minimal memuat:

- analisis masalah dan asumsi;
- model matematika (relasi, fungsi, atau notasi bilangan);
- pseudocode;
- program Python;
- bukti pengujian dan kesimpulan.

## Commit

```bash
git add Modul-2/
git commit -m "Add Modul 2 — Relasi, Fungsi, Sistem Bilangan & Teori Bilangan"
git push origin main
```
