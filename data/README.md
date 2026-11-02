
# Data Tugas 1

## Dataset yang Dipilih

Dataset yang digunakan dalam tugas ini adalah **Indonesian DFK Domain CPT Corpus**, yang diperoleh dari Hugging Face. Dataset ini berisi kumpulan teks berbahasa Indonesia dari berbagai sumber untuk mendukung pengembangan Natural Language Processing (NLP), khususnya Continued Pre-Training (CPT).

| Item | Isi |
|---|---|
| Nama dataset | Indonesian DFK Domain CPT Corpus |
| Sumber | [Hugging Face - Indonesian DFK CPT Dataset](https://huggingface.co/datasets/aikathata/indonesian-dfk-cpt-dataset) |
| Konfigurasi | `by_source_domain` |
| Lisensi/ketentuan pakai | Lisensi tercantum sebagai `other`. Ketentuan penggunaan perlu dikonfirmasi kepada pembuat dataset sebelum redistribusi atau penggunaan komersial. |
| Ukuran | Keseluruhan repositori sekitar 1,67 GB (perlu verifikasi berdasarkan file yang diunduh). |
| Jumlah baris | 374.930 baris pada konfigurasi `by_source_domain`. |
| Periode data | Tidak memiliki satu rentang periode yang ditentukan. Sumber berita mencakup periode yang beragam, sedangkan Wikipedia dan jurnal memiliki cakupan waktu masing-masing. |
| Unit analisis | Satu dokumen atau entri teks berbahasa Indonesia pada setiap baris. |
| Format data | JSON Lines (JSONL) |

## Deskripsi Dataset

Indonesian DFK Domain CPT Corpus merupakan dataset kumpulan teks berbahasa Indonesia yang digunakan untuk kebutuhan pengembangan model Natural Language Processing (NLP), terutama Continued Pre-Training (CPT).

Dataset ini mencakup berbagai topik yang berkaitan dengan disinformasi, fitnah, dan kebencian (DFK), seperti:

- Politik dan pemerintahan.
- Hukum dan kriminalitas.
- Agama dan kepercayaan.
- Kesehatan.
- Konflik dan isu sosial.
- Ekonomi.

Dataset terdiri dari beberapa kategori sumber, yaitu berita formal, berita nonformal sintetis, Wikipedia, dan jurnal.

## Komposisi Dataset

Konfigurasi `by_source_domain` memiliki enam subset sebagai berikut:

| Nama Subset | Jumlah Baris | Keterangan |
|---|---:|---|
| `news_dfk_formal` | 147.060 | Berita formal domain DFK |
| `news_dfk_nonformal` | 89.715 | Berita nonformal hasil sintesis |
| `wikipedia_dfk` | 10.402 | Wikipedia domain DFK |
| `wikipedia_general` | 14.000 | Wikipedia umum |
| `jurnal_dfk` | 63.753 | Jurnal domain DFK |
| `jurnal_general` | 50.000 | Jurnal umum |
| **Total** | **374.930** | |

**Catatan:** Jumlah 374.930 baris merupakan total konfigurasi `by_source_domain`, bukan keseluruhan dataset pada semua konfigurasi. Ukuran repositori keseluruhan dan ukuran konfigurasi yang diunduh perlu dibedakan.

## Cara Memperoleh Data

Dataset diperoleh menggunakan library `datasets` dari Hugging Face.

### 1. Instalasi Library

```bash
pip install datasets
```

### 2. Mengunduh Dataset

```python
from datasets import load_dataset

ds = load_dataset(
    "aikathata/indonesian-dfk-cpt-dataset",
    "by_source_domain"
)
```

### 3. Memeriksa Struktur Dataset

```python
print(ds)

for split in ds:
    print(f"{split}: {len(ds[split]):,} baris")
```

### 4. Memeriksa Jumlah Seluruh Baris

```python
total_rows = sum(len(ds[split]) for split in ds)

print("Total seluruh baris:", f"{total_rows:,}")
```

### 5. Melihat Contoh Data

```python
print(ds["news_dfk_formal"][0])
```

## Struktur Penyimpanan Proyek

Dataset dikelola menggunakan struktur direktori berikut:

```text
project/
│
├── data/
│   ├── raw/
│   │   └── indonesian-dfk-cpt-dataset/
│   │
│   └── processed/
│
├── notebooks/
│   └── 01_data_profiling.ipynb
│
├── README.md
└── requirements.txt
```

Keterangan:

- `data/raw/` : Menyimpan data mentah yang diperoleh dari sumber asli tanpa perubahan.
- `data/processed/` : Menyimpan data yang telah melalui proses pembersihan dan transformasi.
- `notebooks/` : Menyimpan notebook untuk proses eksplorasi dan profiling data.

## Aturan Penyimpanan

1. Dataset mentah tidak boleh diubah secara langsung.
2. Data hasil transformasi disimpan pada folder `data/processed/`.
3. Dataset mentah dan hasil olahan berukuran besar tidak boleh diunggah ke GitHub.
4. Sumber dataset harus dicantumkan agar data dapat ditelusuri kembali.
5. Proses pengolahan data harus dapat direproduksi melalui notebook.

## Kesimpulan

Dataset Indonesian DFK Domain CPT Corpus dipilih karena menyediakan kumpulan teks berbahasa Indonesia dari berbagai sumber dan domain. Dataset ini dapat digunakan untuk kegiatan eksplorasi, profiling, pembersihan, dan analisis data teks menggunakan Python.

Dataset memiliki total 374.930 baris pada konfigurasi `by_source_domain`. Oleh karena itu, jumlah baris konfigurasi ini belum memenuhi ketentuan lebih dari 1.000.000 baris. Kelayakan berdasarkan ukuran minimal 500 MB perlu diverifikasi menggunakan ukuran data yang benar-benar diunduh.

## Referensi

- Hugging Face Dataset: https://huggingface.co/datasets/aikathata/indonesian-dfk-cpt-dataset
- Hugging Face Documentation: https://huggingface.co/docs/datasets/
