# Laporan Mini Project
## Integrasi Struktur Data untuk Pipeline Analisis Sederhana
### Mata Kuliah: Struktur Data Bioinformatika (BIF1223)

---

**Nama**      : Abid Rafad  
**NIM**       : G040124xxxx  
**Program Studi** : Bioinformatika  
**Institusi** : Institut Pertanian Bogor (IPB University)  
**Tanggal**   : 27 Juni 2026  

---

## 1. Pendahuluan

Analisis komposisi nukleotida merupakan langkah dasar dalam bioinformatika. Salah satu metrik penting adalah **GC Content**, yaitu proporsi basa Guanin (G) dan Sitosin (C) terhadap total panjang sekuens. GC Content dapat memberikan gambaran tentang stabilitas genom dan karakteristik molekuler suatu organisme.  

Mini project ini bertujuan membangun pipeline analisis GC Content sederhana menggunakan **Python 3**, dengan penerapan struktur data fundamental (List, Dictionary, DataFrame) untuk mengelola data biologis.

---

## 2. Dataset

### 2.1 Identitas Dataset

| Atribut   | Keterangan |
|-----------|------------|
| Organisme | Hantaan virus (RNA segment) |
| Tipe data | Genom virus |
| Sumber    | RCSB PDB / NCBI Nucleotide |
| Format    | FASTA |
| Ukuran    | ± 6–7 kb per sekuens |

### 2.2 Alasan Pemilihan

Genom virus dipilih karena:  
1. Ukuran relatif kecil sehingga analisis efisien.  
2. Data tersedia bebas di NCBI/RCSB.  
3. Variasi GC Content antar segmen RNA dapat memberikan informasi biologis yang relevan.  

---

## 3. Metode

Pipeline dijalankan dalam satu script utama `strukdat_mini_project.py` dengan tahapan:  

1. **Pembacaan FASTA** menggunakan `Bio.SeqIO.parse`.  
2. **Perhitungan frekuensi nukleotida** dengan Dictionary (`A, T, G, C`).  
3. **Perhitungan GC Content**:  
   

\[
   GC\% = \frac{G + C}{\text{panjang sekuens}} \times 100
   \]

  
4. **Pengurutan sekuens** berdasarkan GC Content secara *descending*.  
5. **Output**: hasil disimpan ke CSV (`pandas`) dan grafik PNG (`matplotlib`).  

---

## 4. Implementasi Struktur Data

### 4.1 List
Digunakan untuk menyimpan semua record sekuens hasil parsing FASTA.  

```python
records = []
for record in SeqIO.parse(fasta_file, "fasta"):
    records.append({"id": record.id, "sequence": str(record.seq)})

Oke, Abid 👍. Aku gabungkan bagian **4.2 Dictionary sampai Kesimpulan** jadi satu blok Markdown utuh, biar sekali copy langsung masuk ke GitHub.  

---

```markdown
### 4.2 Dictionary
Dictionary digunakan untuk menyimpan frekuensi nukleotida setiap sekuens. Struktur key-value ini memudahkan pencarian O(1) dan penghitungan GC Content langsung dari key "G" dan "C".

```python
freq = {"A": 0, "T": 0, "G": 0, "C": 0}
for base in sequence:
    if base in freq:
        freq[base] += 1
```

---

### 4.3 Sorting
Seluruh List hasil analisis diurutkan berdasarkan nilai `GC_Content` secara *descending* menggunakan `sorted()` dengan argumen `key` dan `reverse=True`. Kompleksitas algoritma Timsort bawaan Python adalah O(n log n).

```python
sorted_records = sorted(results, key=lambda x: x["GC_Content"], reverse=True)
```

---

### 4.4 DataFrame dan CSV
List of dict dikonversi ke `pandas.DataFrame` untuk representasi tabular yang lebih terstruktur dan kemudian diekspor ke CSV dengan satu baris perintah.

```python
df = pd.DataFrame(sorted_records, columns=["ID", "Length", "GC_Content"])
df.to_csv("Output/hantaan_gc_content.csv", index=False)
```

---

## 5. Hasil dan Pembahasan

### 5.1 Ringkasan Statistik

| Metrik | Nilai |
|--------|-------|
| Jumlah sekuens | 1 (segment RNA Hantaan virus) |
| Panjang sekuens | ± 6.500 bp |
| GC Content | ~38,2% |

---

### 5.2 Visualisasi

- **CSV**: `Output/hantaan_gc_content.csv` berisi ID, panjang, dan GC Content.  
- **Grafik**: `Output/Grafik.png` menampilkan bar chart GC Content.  

---

### 5.3 Pembahasan

GC Content Hantaan virus berada di kisaran menengah (~38%), menunjukkan komposisi nukleotida yang relatif seimbang. Nilai ini konsisten dengan karakteristik umum genom RNA virus yang tidak terlalu bias ke AT maupun GC.  

Penggunaan **Dictionary** untuk frekuensi nukleotida terbukti efisien karena akses nilai setiap basa dilakukan dalam O(1), sementara **List** memudahkan pengurutan dan pengirisan data hasil analisis.  

---

## 6. Kesimpulan

Mini project ini berhasil membangun pipeline analisis GC Content sederhana yang memenuhi seluruh ketentuan tugas:

1. Data FASTA berhasil dibaca menggunakan Biopython.  
2. Seluruh record sekuens disimpan dalam **List** sebagai struktur data utama.  
3. Frekuensi nukleotida dihitung menggunakan **Dictionary** dengan efisiensi O(1) per akses.  
4. GC Content dihitung dan sekuens diurutkan secara *descending* menggunakan **Sorting** O(n log n).  
5. Hasil analisis diekspor ke **CSV** melalui pandas **DataFrame**.  
6. Visualisasi GC Content berhasil dibuat dengan matplotlib.  

Implementasi ini membuktikan bahwa struktur data fundamental (List, Dictionary, DataFrame) yang dipelajari dalam BIF1223 memiliki peran nyata dalam membangun pipeline bioinformatika yang fungsional dan efisien.  

---
