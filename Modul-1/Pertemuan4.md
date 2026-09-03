# Pertemuan 4 — Asesmen Modul 1

## Problem Challenge — Sistem Seleksi Pelatihan

### Skenario dan Aturan

Panitia memilih mahasiswa untuk pelatihan pemrograman. Peserta lolos jika statusnya aktif, nilai logika minimal 60, kehadiran minimal 75%, tidak memiliki sanksi, dan menyukai Python atau SQL.

```text
Lolos(x) = Aktif(x) AND Nilai(x) >= 60
          AND Kehadiran(x) >= 75 AND NOT Sanksi(x)
          AND (Python(x) OR SQL(x))
```

## Tahapan Penyelesaian

1. **Masalah:** tentukan siapa yang lolos dan jelaskan alasannya.
2. **Identifikasi variabel:** status, nilai, kehadiran, sanksi, dan preferensi teknologi.
3. **Model:** gunakan ekspresi Boolean dan himpunan preferensi.
4. **Algoritma:** tulis pseudocode sebelum program.
5. **Implementasi:** proses data mahasiswa dengan Python.
6. **Testing:** uji kasus batas dan kasus gagal pada setiap syarat.
7. **Dokumentasi:** sertakan tabel hasil dan analisis.

## Starter Code

```python
peserta = [
    {"nama": "Ani", "aktif": True, "nilai": 80, "kehadiran": 90,
     "sanksi": False, "teknologi": {"Python"}},
    {"nama": "Budi", "aktif": True, "nilai": 59, "kehadiran": 88,
     "sanksi": False, "teknologi": {"SQL"}},
    {"nama": "Citra", "aktif": True, "nilai": 75, "kehadiran": 75,
     "sanksi": False, "teknologi": {"Java"}},
    {"nama": "Deni", "aktif": False, "nilai": 90, "kehadiran": 95,
     "sanksi": False, "teknologi": {"Python", "SQL"}},
]

def lolos(data):
    return (
        data["aktif"]
        and data["nilai"] >= 60
        and data["kehadiran"] >= 75
        and not data["sanksi"]
        and bool(data["teknologi"] & {"Python", "SQL"})
    )

for data in peserta:
    print(data["nama"], "lolos" if lolos(data) else "tidak lolos")
```

## Produk yang Dikumpulkan

- analisis masalah dan asumsi;
- identifikasi variabel serta model logika/himpunan;
- algoritma atau pseudocode;
- program Python yang rapi;
- minimal 8 test case, termasuk nilai 60 dan kehadiran 75;
- tabel hasil, interpretasi, dan dokumentasi singkat.

## Rubrik Penilaian

| Komponen | Bobot |
|---|---:|
| Analisis dan pemodelan | 25% |
| Algoritma/pseudocode | 15% |
| Implementasi Python | 30% |
| Testing dan ketepatan hasil | 20% |
| Dokumentasi dan presentasi | 10% |

## Refleksi

1. Syarat mana yang paling menentukan hasil seleksi?
2. Bagaimana perubahan `OR` menjadi `AND` memengaruhi peserta yang lolos?
3. Mengapa test case batas penting dalam sistem seleksi?
