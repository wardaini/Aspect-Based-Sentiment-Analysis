# ABSA pada Ulasan Peserta VINIX7 Batch 3

**Aspect-Based Sentiment Analysis (ABSA)** untuk mengevaluasi program Magang & Studi Independen VINIX7 berdasarkan 230 ulasan peserta. Proyek ini dikembangkan sebagai tugas akhir mata kuliah **Natural Language Processing**.

## 📌 Tentang Proyek

Dataset berisi 230 ulasan dari peserta VINIX7 Batch 3. Proyek ini bertujuan untuk:
- Mengekstrak aspek-aspek yang dibahas dalam ulasan (Mentor, Materi, Project, Skill, Karier, Program)
- Mengukur sentimen (Positif, Netral, Negatif) untuk setiap aspek per divisi
- Menyediakan visualisasi yang mudah diinterpretasikan

## 🔧 Metode yang Digunakan

- **Preprocessing**: case folding, cleaning (hapus URL, angka, karakter khusus), tokenisasi, stopword removal (Sastrawi)
- **Representasi teks**: TF-IDF (500 fitur, unigram + bigram)
- **Deteksi aspek**: rule-based keyword matching
- **Scoring sentimen**: kamus domain khusus program pelatihan (bukan InSet karena InSet salah mengklasifikasikan 30+ kata positif dalam konteks ini)
- **Evaluasi**: manual spot-check 30 sampel → akurasi **66%**, F1-score **63%**

## 📊 Hasil Utama

| Metrik | Nilai |
|--------|-------|
| Total ulasan | 230 |
| Total kalimat | 984 |
| Aspek terpositif | **Mentor** (87%) |
| Aspek perlu perhatian | **Project** (69%) |

### Per Divisi (% Positif per Aspek)

| Divisi | Mentor | Materi | Project | Skill | Karier | Program |
|--------|--------|--------|---------|-------|--------|---------|
| Data Science & ML | 90 | 76 | 77 | 86 | 84 | 86 |
| Financial & Banking | 100 | 92 | 83 | 82 | 100 | 83 |
| Web Dev & UI/UX | 83 | 71 | 81 | 75 | 78 | 75 |
| Brand & Marketing | 71 | 92 | 64 | 57 | 64 | 86 |
| Human Resources | 100 | 71 | 67 | 100 | 83 | 77 |
| Bisnis & Manajemen | 83 | 75 | 57 | 83 | 100 | 80 |

## 📁 Struktur File
```
├── README.md
├── analisis_vinix7.ipynb          # Notebook utama
├── datasetulasanvinix.csv         # Dataset mentah
├── hasil_preprocessing.csv        # Hasil setelah preprocessing
├── hasil_absa_kalimat.csv         # Hasil ABSA per kalimat
├── ringkasan_per_divisi.csv
├── ringkasan_per_aspek.csv
├── top_tfidf.png                  # Visualisasi TF-IDF
├── confusion_matrix.png
├── sentimen_per_aspek.png
├── heatmap_divisi.png
├── radar_chart.png
└── wordcloud_divisi.png
```

## Cara Menjalankan

1. Pastikan Python 3.8+ terinstal.
2. Instal dependensi:
   ```bash
   pip install pandas numpy matplotlib seaborn wordcloud scikit-learn PySastrawi
Buka notebook analisis_vinix7.ipynb di Jupyter atau VSCode.

Jalankan semua cell secara berurutan.

## Interpretasi
##### Mentor mendapat sentimen tertinggi (87% positif) → peran mentor sangat dihargai.

##### Project mendapat sentimen terendah (69% positif) → beberapa peserta merasa proyek kurang sesuai ekspektasi.

##### Divisi Human Resources dan Financial & Banking memiliki sentimen mentor 100% positif.

##### Divisi Bisnis & Manajemen memiliki sentimen karier 100% positif, tetapi project hanya 57%.

## Catatan Teknis
##### Kamus domain dibangun khusus untuk konteks program pelatihan (tidak menggunakan InSet karena banyak kata positif seperti sangat, membantu, seru dinilai negatif oleh InSet).

##### Sistem mencapai akurasi 66% pada evaluasi manual – cukup baik untuk pendekatan unsupervised.

##### Sentimen negatif sangat jarang (hanya 0.4% dari total kalimat).

## Kontributor
Wardatul A'ani – analisis dan implementasi

## Lisensi
[MIT]

