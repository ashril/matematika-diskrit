# Modul Praktikum 3 — Teori Graf dan Algoritma Graf

**Tema besar:** Memodelkan Hubungan dan Jaringan<br>
**Cakupan:** Pertemuan 9–12

## Deskripsi

Modul ini memperkenalkan **teori graf** sebagai alat untuk memodelkan hubungan dan jaringan dalam dunia nyata — mulai dari jaringan komputer, jalur transportasi, hingga sistem rekomendasi. Mahasiswa akan belajar merepresentasikan graf, menganalisis strukturnya, dan mengimplementasikan algoritma pencarian jalur terpendek menggunakan Python.

## Capaian Pembelajaran

Setelah menyelesaikan modul, mahasiswa mampu:

- menjelaskan konsep dasar graf: vertex, edge, degree, path, dan cycle;
- membedakan graf berarah, tidak berarah, dan berbobot;
- merepresentasikan graf menggunakan adjacency matrix dan adjacency list;
- melakukan traversal graf dengan BFS dan DFS;
- mengimplementasikan algoritma Dijkstra untuk shortest path;
- memodelkan masalah jaringan nyata sebagai graf dan menyelesaikannya dengan Python.

## Prasyarat dan Perangkat

- Python 3.10 atau lebih baru
- NumPy (`pip install numpy`)
- Matplotlib (`pip install matplotlib`)
- NetworkX opsional (`pip install networkx`) — untuk visualisasi
- Terminal dan VSCode

Verifikasi instalasi:

```bash
pip install numpy matplotlib networkx
```

## Alur Pengerjaan

```text
Masalah → Pemodelan Graf → Representasi (Matriks/List)
→ Algoritma Traversal/Shortest Path → Implementasi Python → Analisis
```

## Struktur Folder

```text
Modul-3/
├── README.md
├── Pertemuan9.md    — Konsep Dasar Graf
├── Pertemuan10.md   — Representasi Graf
├── Pertemuan11.md   — Algoritma Graf dan Shortest Path
└── Pertemuan12.md   — Asesmen Modul 3
```

## Ketentuan Pengumpulan

Setiap pekerjaan dikumpulkan dalam folder pertemuan terkait dan minimal memuat:

- model graf (vertex, edge, degree, path);
- representasi adjacency matrix atau adjacency list;
- implementasi algoritma dalam Python;
- visualisasi graf (jika relevan);
- analisis hasil dan kesimpulan.

## Commit

```bash
git add Modul-3/
git commit -m "Add Modul 3 — Teori Graf dan Algoritma Graf"
git push origin main
```
