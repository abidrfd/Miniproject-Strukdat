# Mini Project – Struktur Data Bioinformatika (BIF1223)

**Pipeline Analisis GC Content DNA dengan Python**  
IPB University · Semester Genap 2025/2026

---

## Dataset

| Atribut   | Detail |
|-----------|--------|
| Organisme | Hantaan virus (segment RNA) |
| Tipe data | Genom virus |
| Sumber    | RCSB PDB / NCBI Nucleotide |
| Format    | FASTA |
| Ukuran    | ~6–7 kb per sekuens |

**Alasan pemilihan:** Genom virus berukuran relatif kecil, mudah dianalisis, dan variasi GC Content antar segmen dapat memberikan informasi biologis yang relevan.

---

## Struktur Folder

```
Miniproject-Strukdat/
├── strukdat_mini_project.py   # Script utama pipeline analisis
├── Data/
│   └── rcsb_pdb_5FSG.fasta    # File input FASTA
├── Output/
│   ├── hantaan_gc_content.csv # Hasil analisis tabular
│   └── Grafik.png             # Visualisasi GC Content
├── requirements.txt
└── README.md
```
---

## Cara Menjalankan

```bash
# Langkah 1 – Install library
pip install -r requirements.txt

# Langkah 2 – Jalankan pipeline analisis
python strukdat_mini_project.py
Program akan menghasilkan:

Output/hantaan_gc_content.csv – hasil analisis tabular GC Content

Output/Grafik.png – grafik distribusi GC Content
```
Dependensi
| Library | Kegunaan |
| --- | --- |
| ``biopython`` | Membaca file FASTA (SeqIO) |
| ``pandas`` | DataFrame + ekspor CSV |
| ``matplotlib`` | Visualisasi histogram |

Kontak

Nama  : Abid Rafad

NIM   : G0401241029
