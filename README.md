
# 📦 Dataset Pemrosesan Teks Deskripsi Makanan

Proyek ini merupakan hasil dari proses ekstraksi, terjemahan, dan generasi deskripsi makanan berbasis dataset nutrisi Indonesia dan internasional. Dataset akhir disusun untuk keperluan Natural Language Processing (NLP), khususnya dalam bidang _text generation_ dan _classification_.

## 📁 Struktur File

| Nama File | Deskripsi |
|-----------|-----------|
| `TKPI-2020.pdf` | Dokumen referensi berisi data makanan Indonesia, digunakan sebagai sumber utama data makanan lokal. |
| `data_makanan.csv` | Dataset hasil ekstraksi dari dokumen `TKPI-2020.pdf`. |
| `test.csv` | Dataset akhir berisi 200 data makanan Indonesia, tiap baris berisi nama makanan, deskripsi nutrisi, dan dua kalimat unik yang menggambarkan makanan tersebut. Kalimat dipisah dengan tanda `/`. |
| `fndds_nutrient_data3.json` | Dataset hasil kurasi dari USDA World Dataset (makanan internasional) yang sudah diseleksi dan disederhanakan. |
| `terjemah.json` | File hasil terjemahan makanan internasional dari bahasa Inggris ke Indonesia menggunakan notebook `train.ipynb`. |
| `train.ipynb` | Notebook utama untuk memproses data makanan internasional, menerjemahkan, lalu membuat deskripsi nutrisi dengan pola kalimat terstruktur. |
| `train.csv` | Dataset akhir makanan internasional, berisi nama makanan, deskripsi nutrisi, dan dua kalimat unik (dipisah dengan `/`). |
| `test.ipynb` | Notebook tambahan untuk analisis, pengecekan, atau visualisasi hasil `test.csv`. |

## 🛠️ Proses yang Dilakukan

1. **Ekstraksi Data Lokal**:
   - Mengambil informasi makanan dari `TKPI-2020.pdf`.
   - Mengolahnya menjadi `data_makanan.csv`, lalu menyusunnya ke `test.csv` dengan:
     - Nama makanan
     - Kandungan nutrisi
     - Dua kalimat unik representatif (dipisahkan dengan `/`)

2. **Pemrosesan Data Internasional**:
   - Dataset dari USDA diambil dan diseleksi menjadi `fndds_nutrient_data3.json`.
   - Diterjemahkan ke Bahasa Indonesia menggunakan model translasi → menghasilkan `terjemah.json`.

3. **Penyusunan Deskripsi**:
   - Format deskripsi nutrisi dibuat menggunakan kode:
     ```python
     kalimat = f"{nama_makanan} memiliki kandungan nutrisi seperti: {kalimat_nutrisi}."
     ```
   - Deskripsi disimpan dalam bentuk JSON → lalu dikonversi ke `train.csv` dengan tambahan dua kalimat unik untuk tiap makanan.

## 🧠 Tujuan Dataset

Dataset ini bisa digunakan untuk:
- Pelatihan model NLP seperti text summarization, classification, atau generation.
- Evaluasi model bahasa dalam konteks deskripsi makanan.
- Pengembangan chatbot nutrisi atau sistem rekomendasi makanan.

## ✅ Format CSV

Baik `train.csv` maupun `test.csv` memiliki format sebagai berikut:

| makanan | deskripsi_nutrisi | kalimat_unik |
|---------|-------------------|---------------|
| Nasi Goreng | Nasi Goreng memiliki kandungan nutrisi seperti: energi, protein, ... | [kalimat 1]/[kalimat 2] |

---

## 📌 Catatan Tambahan

- Jumlah data:
  - `test.csv`: 200 makanan lokal
  - `train.csv`: hasil pemrosesan makanan internasional (jumlah tergantung kurasi)
- Deskripsi nutrisi bersifat terstruktur dan informatif.
- Kalimat unik disusun secara manual/semi-otomatis untuk memperkaya konteks data.

---

## 📜 Lisensi

Proyek ini untuk keperluan riset dan pembelajaran. Dataset berasal dari sumber terbuka dan hasil olahan manual.
