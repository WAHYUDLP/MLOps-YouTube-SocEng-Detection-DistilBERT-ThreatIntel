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
Struktur repositori ini diorganisasikan mengikuti standar industri (*Cookiecutter Data Science*) agar sistematis, *reproducible*, dan mudah dikelola:

```text
├── .devcontainer/     # Konfigurasi environment GitHub Codespaces (devcontainer.json)
├── config/            # File konfigurasi sistem dan parameter pipeline eksperimen
├── data/              # Penyimpanan data mentah (Raw Data Lake) dan terproses (Feature Store)
├── models/            # Penyimpanan artefak model DistilBERT yang telah dilatih
├── notebooks/         # Jupyter notebooks untuk eksplorasi data (EDA) dan eksperimen awal
├── src/               # Source code utama (data ingestion, preprocessing, training, inference)
├── .gitignore         # Daftar file/folder yang diabaikan oleh Git (konfigurasi Python)
├── LICENSE            # Lisensi proyek (MIT License)
├── README.md          # Dokumentasi utama repositori
└── requirements.txt   # Daftar dependensi library Python yang dibutuhkan sistem
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

