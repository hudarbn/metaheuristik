# Strategi Optimasi Task Scheduling: Sine Cosine Algorithm (SCA) & Moth-Flame Optimization (MFO)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)

| No. | Nama Lengkap | NRP |
|---|---|---|
| 1 | Putu Yudi Nandanjaya Wiraguna | 5027241080 |
| 2 | Danuja Prasasta Bastu | 5027241037 |
| 3 | Muhammad Huda Rabbani | 5027241098 |
| 4 | I Gede Bagus Saka Sinatrya | 5027241088 |
| 5 | Raynard Carlent | 5027241109 |

Aplikasi web interaktif untuk memvisualisasikan dan membandingkan cara kerja algoritma metaheuristik **Sine Cosine Algorithm (SCA)** dan **Moth-Flame Optimization (MFO)** dalam menyelesaikan permasalahan **Cloud Task Scheduling** (pemetaan *Cloudlets/Tasks* ke *Virtual Machines/VMs*).

Proyek ini dikembangkan sebagai media demonstrasi interaktif pendamping presentasi **Kelompok 3 — Mata Kuliah Sistem Operasi & Komputasi Awan (SOKA)**, Departemen Teknologi Informasi, Institut Teknologi Sepuluh Nopember (ITS).

---

## Daftar Isi

- [Latar Belakang](#latar-belakang)
- [Fitur Utama](#fitur-utama)
- [Konsep Algoritma & Alur Kerja](#konsep-algoritma--alur-kerja)
- [Metrik Evaluasi](#metrik-evaluasi)
- [Perbandingan Karakteristik SCA vs MFO](#perbandingan-karakteristik-sca-vs-mfo)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Struktur Proyek](#struktur-proyek)
- [Cara Menjalankan](#cara-menjalankan)
- [Anggota Kelompok 3 SOKA](#anggota-kelompok-3-soka)

---

## Latar Belakang

Penjadwalan tugas (*Task Scheduling*) pada lingkungan *Cloud Computing* bertujuan mendistribusikan sekumpulan beban kerja (*Tasks/Cloudlets*) dengan ukuran instruksi berbeda ke sejumlah mesin virtual (*Virtual Machines/VMs*) yang memiliki kapasitas komputasi beragam. Permasalahan ini tergolong **NP-Hard**, sehingga pencarian solusi eksak menjadi tidak efisien ketika jumlah tugas dan mesin virtual meningkat pesat.

Pendekatan **metaheuristik berbasis populasi** seperti **Sine Cosine Algorithm (SCA)** dan **Moth-Flame Optimization (MFO)** menawarkan solusi pencarian ruang global yang efisien. Karena kedua algoritma tersebut secara alami beroperasi pada **ruang pencarian kontinu (bilangan desimal)** sementara penugasan mesin virtual membutuhkan **keputusan diskrit (indeks bilangan bulat VM)**, aplikasi ini dirancang untuk memperagakan secara transparan:

1. Pola pergerakan posisi kandidat solusi di ruang kontinu menuju titik optimal.
2. Mekanisme **Decoding** dari representasi kontinu ke pemetaan indeks VM diskrit pada setiap iterasi.
3. Evaluasi komparatif performa **SCA** dan **MFO** terhadap berbagai skenario infrastruktur server dan beban kerja.

---

## Fitur Utama

### 1. Visualisasi Trajektori Pergerakan Agen (Animasi Canvas)
Ilustrasi animasi *real-time* menggunakan HTML5 Canvas pada bagian pembuka halaman untuk membandingkan karakteristik matematis kedua algoritma dalam mendekati target solusi optimal:
- **SCA (Fungsi Sinus/Cosinus)**: Agen bergerak berosilasi mengikuti gelombang trigonometri dengan amplitudo $r_1$ yang mengecil secara linear guna beralih dari fase eksplorasi luas ke eksploitasi area target.
- **MFO (Logarithmic Spiral)**: Agen (*Moth*) bergerak memutar membentuk lintasan spiral logaritmik yang mengerucut mendekati posisi target acuan (*Flame*).

### 2. Diagram Siklus Alur Decoding & Evaluasi Fitness
Penjelasan terstruktur mengenai 4 tahapan utama siklus iterasi metaheuristik ($T < T_{\text{maks}}$):
1. **Inisialisasi Kandidat Solusi** (populasi agen bernilai desimal acak).
2. **Decoding Kontinu ke Diskrit** (pembatasan rentang & pembulatan ke indeks VM terdekat).
3. **Perhitungan Fungsi Objektif / Fitness** (evaluasi kualitas jadwal pemetaan).
4. **Pembaruan Posisi & Parameter** (eksekusi persamaan SCA atau MFO berdasarkan solusi terbaik).

### 3. Simulasi Mini Step-by-Step (5 Tasks ke 3 VMs)
Studi kasus mikro interaktif untuk mengamati proses pembaruan posisi dan *decoding* pada satu kandidat jadwal secara bertahap (`+1 Iterasi` maupun `Reset`):
- **Skenario Beban**: 5 Tugas (`7000`, `5000`, `3000`, `2000`, `1000` MI) pada 3 VM heterogen (`VM 0: 1000 MIPS`, `VM 1: 2000 MIPS`, `VM 2: 4000 MIPS`).
- **Mode Pilihan**: Dapat dijalankan menggunakan persamaan **SCA** maupun **MFO**.
- **Pemantauan Langsung**: Menampilkan perubahan nilai posisi desimal, hasil pembulatan `[ VM x ]`, waktu eksekusi per tugas, *bar* akumulasi beban tiap VM, hingga pembaruan nilai *Makespan*, *Resource Utilization*, dan *Load Balancing (StdDev)*.

### 4. Simulator Komparasi Skala Besar
Panel eksperimen untuk menguji dan membandingkan performa **SCA** dan **MFO** secara berdampingan dengan konfigurasi fleksibel:
- **Preset & Kustomisasi Infrastruktur VM**:
  - `8 VM (Topologi Paper/Proposal)`: `1000, 1000, 2000, 3000, 2500, 4000, 4000, 4000` MIPS (4 Host fisik)
  - `18 VM Heterogen`: kombinasi `[1000, 2500, 4000]` MIPS $\times 6$ (6 Host fisik)
  - `32 VM (Skala Menengah)`: kombinasi `[1000, 2000, 3000, 4000]` MIPS $\times 8$ (8 Host fisik)
  - `8 VM Homogen (Setara)`: `2500` MIPS $\times 8$ (4 Host fisik)
  - Dukungan pengeditan manual daftar MIPS, jumlah *Host* fisik, dan daya maksimum server $P_{\max}$ (Watt).
- **Generator Beban Kerja (Tasks)**:
  - Pilihan skala beban: `15`, `40`, `100`, hingga `500` tugas.
  - Pilihan distribusi data: **Format GoCJ (Google Cloud Jobs) Dataset** (`15.000` – `275.000` MI) atau **Tugas Ringan** (`1.000` – `15.000` MI), lengkap dengan tombol *Regenerate Task Acak* dan kolom input manual.
- **Kontrol Parameter Metaheuristik**:
  - Ukuran Populasi ($N$ / Agen): `10` – `100` (default: `30`).
  - Iterasi Maksimum ($T$): `20` – `500` (default: `100`).
- **Grafik & Kesimpulan Otomatis**:
  - **Grafik Pencarian Optimum Global** (*Line Chart*): Menampilkan kurva konvergensi penurunan *Makespan* sepanjang iterasi.
  - **Grafik Distribusi Load Balancing pada VM** (*Bar Chart*): Menampilkan perbandingan beban kerja yang diterima masing-masing VM.
  - **Kesimpulan Hasil Pengujian Dinamis**: Merangkum algoritma pemenang berdasarkan hasil pengujian serta mengaitkannya dengan *No Free Lunch Theorem*.

### 5. Analisis Teoritis Metaheuristik
Ringkasan komparatif mengenai kelebihan dan keterbatasan masing-masing algoritma ketika diterapkan pada permasalahan *Cloud Task Scheduling*.

---

## Konsep Algoritma & Alur Kerja

### Representasi & Decoding Solusi
Setiap agen dalam populasi direpresentasikan sebagai vektor berdimensi $D$ (jumlah tugas), di mana setiap elemen $X_i \in [0, M-1]$ bernilai riil/kontinu ($M$ adalah jumlah VM). Untuk mengevaluasi penjadwalan, posisi kontinu dikonversi menjadi indeks VM bilangan bulat melalui tahap **Decoding**:

$$\text{VM\_Index}_i = \min\left(M - 1,\; \max\left(0,\; \text{round}(X_i)\right)\right)$$

### 1. Sine Cosine Algorithm (SCA)
SCA memperbarui posisi setiap kandidat solusi menggunakan osilasi fungsi trigonometri sinus dan cosinus terhadap posisi solusi terbaik saat ini ($P$):

$$X_i^{t+1} = \begin{cases} X_i^t + r_1 \cdot \sin(r_2) \cdot |r_3 P_i^t - X_i^t|, & r_4 < 0.5 \\ X_i^t + r_1 \cdot \cos(r_2) \cdot |r_3 P_i^t - X_i^t|, & r_4 \geq 0.5 \end{cases}$$

Parameter amplitudo $r_1 = a - t \frac{a}{T}$ menurun secara linear seiring bertambahnya iterasi $t$ hingga maksimum $T$, sehingga menjaga transisi dari fase eksplorasi menuju eksploitasi.

### 2. Moth-Flame Optimization (MFO)
MFO meniru mekanisme navigasi *transverse orientation* ngengat (*Moth*) terhadap sumber cahaya (*Flame*). Posisi tiap *Moth* $M_i$ diperbarui mengelilingi *Flame* $F_j$ menggunakan persamaan spiral logaritmik:

$$S(M_i, F_j) = D_i \cdot e^{bt} \cdot \cos(2\pi t) + F_j$$

dengan $D_i = |F_j - M_i|$ menyatakan jarak antara *Moth* ke-*i* dan *Flame* ke-*j*, $b$ merupakan konstanta bentuk spiral, dan $t$ adalah parameter jarak kedekatan ke target.

---

## Metrik Evaluasi

Kualitas penjadwalan diukur menggunakan empat metrik utama komputasi awan:

| Metrik | Arah Optimasi | Formula / Definisi | Keterangan |
| :--- | :---: | :--- | :--- |
| **Makespan (Detik)** | Minimasi ($\downarrow$) | $\max_{j \in \{0..M-1\}} \left( \sum_{i \in \text{VM}_j} \frac{\text{MI}_i}{\text{MIPS}_j} \right)$ | Waktu penyelesaian paling akhir dari seluruh VM. Semakin kecil nilainya, semakin cepat seluruh tugas diselesaikan. |
| **Utilisasi Server (%)** | Maksimasi ($\uparrow$) | $\frac{\sum_{j=0}^{M-1} \text{Load}_j}{\text{Makespan} \times M} \times 100\%$ | Persentase rata-rata waktu sibuk seluruh VM selama siklus eksekusi. Semakin mendekati `100%`, semakin sedikit waktu *idle* server. |
| **Load Balancing (StdDev)** | Minimasi ($\downarrow$) | $\sqrt{\frac{1}{M}\sum_{j=0}^{M-1}\left(\text{Load}_j - \overline{\text{Load}}\right)^2}$ | Standar deviasi beban kerja antar VM. Semakin mendekati `0`, semakin merata pembagian tugas di seluruh VM. |
| **Konsumsi Energi (kWh)** | Minimasi ($\downarrow$) | $\frac{\text{Makespan} \times N_{\text{host}} \times P_{\max}}{3.600.000}$ | Estimasi total konsumsi energi infrastruktur fisik dalam satuan kWh. Semakin kecil nilainya, semakin hemat daya. |

---

## Perbandingan Karakteristik SCA vs MFO

| Aspek | Sine Cosine Algorithm (SCA) | Moth-Flame Optimization (MFO) |
| :--- | :--- | :--- |
| **Mekanisme Pergerakan** | Osilasi gelombang fungsi $\sin$ dan $\cos$ | Lintasan *Logarithmic Spiral* mengelilingi *Flame* |
| **Memori Target** | Mengacu pada satu solusi terbaik global tunggal ($P$) | Matriks ganda (*Moth* sebagai pencari & daftar *Flame* terurut) |
| **Kelebihan Utama** | Struktur matematis sederhana, minim parameter kontrol, bebas gradien, dan ringan secara komputasi | Keseimbangan eksplorasi-eksploitasi terukur dan penajaman lokal kuat berkat memori multi-*Flame* |
| **Keterbatasan** | Rawan terjebak *local optima* pada dimensi besar karena penurunan $r_1$ linear dan acuan tunggal | Beban komputasi pengurutan matriks *Flame* lebih berat serta sensitif terhadap *tuning* populasi ($N$) dan iterasi ($T$) |

---

## Teknologi yang Digunakan

- **HTML5 & CSS3**: Struktur halaman semantik dan animasi transisi sel tabel.
- **JavaScript (Vanilla ES6+)**: Logika simulasi iterasi, proses *decoding*, kalkulasi metrik evaluasi, serta penggambaran animasi trajektori pada `<canvas>`.
- **[Tailwind CSS](https://tailwindcss.com/) (via CDN)**: *Styling* antarmuka modern dan responsif di berbagai ukuran layar.
- **[Chart.js](https://www.chartjs.org/) (via CDN)**: Visualisasi interaktif grafik konvergensi *Makespan* dan diagram batang distribusi beban VM.
- **[Google Fonts](https://fonts.google.com/)**: Tipografi menggunakan keluarga huruf *Plus Jakarta Sans* dan *JetBrains Mono*.

---

## Struktur Proyek

```text
metaheuristik/
├── index.html   # Aplikasi utama (UI, animasi Canvas, studi kasus mini, & simulator skala besar)
└── README.md    # Dokumentasi lengkap proyek
```

---

## Cara Menjalankan

Aplikasi ini dibangun sebagai halaman web statis mandiri (*zero-build*) sehingga tidak memerlukan instalasi *package manager* atau *build tool* tambahan.

### Prasyarat
- Peramban web modern (Google Chrome, Mozilla Firefox, Microsoft Edge, atau Safari).
- Koneksi internet aktif untuk memuat pustaka eksternal melalui CDN (Tailwind CSS, Chart.js, dan Google Fonts).

### Menjalankan secara Lokal

1. **Clone repositori ini:**
   ```bash
   git clone https://github.com/hudarbn/metaheuristik.git
   cd metaheuristik
   ```

2. **Buka aplikasi di peramban:**
   - **Cara Langsung**: Klik dua kali berkas `index.html` pada *File Explorer* / *Finder*.
   - **Menggunakan VS Code Live Server**: Klik kanan pada `index.html` lalu pilih **"Open with Live Server"**.
   - **Menggunakan Python HTTP Server (opsional)**:
     ```bash
     python -m http.server 8000
     ```
     Kemudian buka `http://localhost:8000` di peramban Anda.

---

## Anggota Kelompok 3 SOKA

| Nama Lengkap | NRP |
| :--- | :---: |
| **Danuja Prasasta B.** | `5027241037` |
| **Putu Yudi N. W.** | `5027241080` |
| **I Gede Bagus S.** | `5027241088` |
| **M. Huda Rabbani** | `5027241098` |
| **Raynard Carlent** | `5027241109` |

---

<p align="center">
  <strong>Departemen Teknologi Informasi &bull; Institut Teknologi Sepuluh Nopember (ITS)</strong>
</p>
