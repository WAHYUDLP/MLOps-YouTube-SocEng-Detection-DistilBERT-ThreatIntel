# MLOps: Automated Detection and Continual Adaptation of Social Engineering Attacks in YouTube Comments using DistilBERT-based NLP and Threat Intelligence APIs 

**Author:** Wahyu Dwi Laksana Putri  
**Program Studi:** Teknik Informatika, Universitas Brawijaya  

## 📌 Deskripsi Proyek
Proyek ini merupakan implementasi sistem *AI Production* berbasis MLOps untuk mendeteksi ancaman *social engineering* (seperti promosi judi online, penipuan investasi, dan *phishing*) pada kolom komentar YouTube. 

Sistem ini dirancang untuk mengatasi kelemahan moderasi statis dengan menggunakan pendekatan *hybrid verification* yang menggabungkan:
1. **DistilBERT**: Model NLP berbasis *transformer* untuk menganalisis konteks linguistik komentar secara mendalam dan mengenali pola bahasa yang disamarkan (*obfuscation*).
2. **Threat Intelligence API (VirusTotal)**: Untuk memvalidasi reputasi URL eksternal yang disematkan dalam komentar secara *real-time*.

Selain itu, proyek ini merancang mekanisme *Continual Learning* agar model dapat beradaptasi terhadap *concept drift* (perubahan pola serangan yang sangat cepat) di lingkungan produksi.

## 📁 Struktur Direktori
Struktur repositori ini diorganisasikan mengikuti standar industri (**Cookiecutter Data Science**) yang dipadukan dengan konfigurasi **MLOps (Codespaces)** agar sistematis, *reproducible*, dan siap produksi:

```text
├── .devcontainer/     # Konfigurasi environment GitHub Codespaces (devcontainer.json)
├── config/            # File konfigurasi sistem MLOps dan parameter pipeline
├── data/              # Direktori penyimpanan data
│   ├── external/      # Data dari pihak ketiga (misal: kamus bahasa, external threat feeds)
│   ├── interim/       # Data sementara yang sedang dalam proses transformasi
│   ├── processed/     # Data final (Feature Store) yang siap untuk pemodelan
│   └── raw/           # Data mentah original (Raw Data Lake) yang bersifat immutable
│
├── docs/              # Direktori default untuk dokumentasi proyek (contoh: mkdocs)
├── models/            # Penyimpanan artefak model DistilBERT yang telah dilatih
├── notebooks/         # Jupyter notebooks untuk eksplorasi data (EDA) dan eksperimen awal
├── references/        # Kamus data, manual, dan material referensi tambahan
│
├── reports/           # Hasil analisis yang di-generate (HTML, PDF, dll)
│   └── figures/       # Grafik dan gambar visualisasi yang digunakan dalam pelaporan
│
├── src/               # Source code utama untuk pipeline proyek
│   ├── modeling/      # Direktori khusus untuk model machine learning
│   │   ├── predict.py # Script untuk menjalankan inferensi dengan model terlatih
│   │   └── train.py   # Script untuk melatih/fine-tuning model DistilBERT
│   ├── config.py      # Menyimpan variabel konfigurasi internal
│   ├── dataset.py     # Script untuk mengumpulkan data (misal: dari YouTube API)
│   ├── features.py    # Script untuk feature engineering NLP
│   └── plots.py       # Script untuk menghasilkan visualisasi data
│
├── .gitignore         # Daftar file/folder yang diabaikan oleh Git
├── LICENSE            # Lisensi open-source proyek (MIT License)
├── Makefile           # Kumpulan perintah otomatisasi (contoh: `make data`, `make train`)
├── README.md          # Dokumentasi utama repositori
├── pyproject.toml     # Konfigurasi proyek modern dan metadata untuk package Python
├── requirements.txt   # Daftar dependensi environment proyek
└── setup.cfg          # Konfigurasi tambahan untuk code linter (seperti flake8)

```

## 📄 Cara Menjalankan Lingkungan Pengembangan (Codespaces)

Proyek ini dirancang agar dapat dijalankan secara instan menggunakan **GitHub Codespaces** tanpa memerlukan instalasi manual di laptop (*zero-setup environment*). Seluruh dependensi MLOps telah dikonfigurasi menggunakan Dev Container agar konsisten bagi siapa pun yang mengakses repositori ini.

Berikut adalah langkah-langkah untuk menjalankan Codespaces:

1. Buka halaman repositori proyek ini di GitHub.
2. Klik tombol hijau **`<> Code`** di pojok kanan atas.
3. Pilih tab **`Codespaces`**.
4. Klik tombol **`Create codespace on main`** (atau pada *branch* eksperimen yang sedang aktif).
5. Tunggu beberapa saat hingga proses *building container* selesai. Visual Studio Code akan otomatis terbuka langsung di *browser*.
6. Lingkungan Python 3.10 beserta ekstensi VS Code pendukung akan otomatis disiapkan berdasarkan konfigurasi di dalam folder `.devcontainer`.
7. Lingkungan pengembangan siap digunakan!

## 💡 Branching Strategy

Pengembangan repositori ini menerapkan **GitHub Flow**:
- Eksperimen awal dan fitur baru (seperti inisiasi *environment*) dikerjakan di *branch* terpisah (`feat/initial-eda`).
- *Merge* ke *branch* `main` hanya dilakukan melalui *Pull Request* (PR) setelah divalidasi.

