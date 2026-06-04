# Deteksi Aksara Ulu Rejang (Kaganga) Menggunakan YOLOv12

## Kelompok 5

**Mata Kuliah:** Computer Vision  
**Program Studi:** Informatika

| Nama | NPM |
|------|------|
| Adelia Nurazizah Omega Putri | G1A023022 |
| Carissa Nabilah Putri Rozi | G1A023026 |
| Filya Chiara Amanda | G1A023034 |

---

## Tentang Proyek

Proyek ini merupakan implementasi teknologi **Computer Vision** untuk mendeteksi dan mengklasifikasikan karakter **Aksara Ulu Rejang (Kaganga)** menggunakan algoritma **YOLOv12 (You Only Look Once)**. Sistem dikembangkan dengan pendekatan **Object Detection** yang memungkinkan komputer tidak hanya mengenali karakter aksara, tetapi juga menentukan lokasi setiap karakter pada citra menggunakan *bounding box*.

Aksara Ulu Rejang merupakan salah satu warisan budaya masyarakat Bengkulu yang termasuk dalam keluarga aksara Kaganga. Sebagai bagian dari identitas budaya lokal, aksara ini memiliki nilai sejarah yang tinggi. Namun, seiring perkembangan teknologi dan perubahan pola komunikasi masyarakat, penggunaan aksara tradisional semakin berkurang sehingga diperlukan upaya pelestarian yang lebih adaptif terhadap perkembangan zaman.

Melalui pemanfaatan teknologi Deep Learning dan Computer Vision, penelitian ini bertujuan membangun sistem yang mampu mengenali karakter Aksara Ulu Rejang secara otomatis dari citra digital. Model YOLOv12 dilatih menggunakan dataset yang telah dianotasi sehingga mampu mempelajari pola visual setiap karakter aksara dan melakukan deteksi secara otomatis dengan tingkat akurasi yang baik.

---

## Tujuan Proyek

Proyek ini dikembangkan dengan beberapa tujuan utama, yaitu:

- Mengimplementasikan algoritma YOLOv12 pada kasus deteksi karakter Aksara Ulu Rejang.
- Mengembangkan sistem pengenalan aksara berbasis Computer Vision.
- Melatih model menggunakan dataset karakter aksara yang telah dianotasi.
- Menguji kemampuan model dalam mengenali berbagai karakter Aksara Ulu Rejang secara otomatis.
- Mengevaluasi performa model menggunakan metrik Object Detection.
- Mendukung pelestarian budaya daerah melalui pemanfaatan teknologi kecerdasan buatan.

---

## Dataset

Dataset yang digunakan berasal dari workspace **Noval Rizkiansyah** pada platform **Roboflow** dengan nama proyek **Aksara Ulu Rejang Versi 4**. Dataset telah dikonversi ke format YOLO sehingga dapat digunakan secara langsung dalam proses pelatihan model.

Setiap citra telah dilengkapi anotasi berupa *bounding box* yang digunakan sebagai referensi selama proses training agar model dapat mempelajari bentuk, pola, dan karakteristik masing-masing aksara.

### Pembagian Dataset

| Dataset | Jumlah Data | Fungsi |
|----------|------------|---------|
| Train | 1437 | Melatih model |
| Validation | 167 | Memvalidasi performa model selama training |
| Test | 65 | Menguji model setelah training selesai |

---

## Preprocessing dan Augmentasi Data

Sebelum proses training dilakukan, dataset telah melalui tahap augmentasi untuk meningkatkan variasi data dan mengurangi risiko overfitting.

### Teknik Augmentasi

- Rotation
- Noise Injection

### Tujuan Augmentasi

- Menambah keberagaman data
- Mengurangi risiko overfitting
- Meningkatkan kemampuan generalisasi model
- Membantu model mengenali karakter dalam berbagai kondisi dan variasi tampilan

Seluruh gambar diproses menggunakan ukuran:

```python
imgsz = 640
```

Ukuran tersebut dipilih untuk menjaga keseimbangan antara kualitas detail gambar dan efisiensi komputasi selama proses pelatihan.

---

## Teknologi yang Digunakan

| Teknologi | Fungsi |
|------------|---------|
| Python | Bahasa pemrograman utama |
| YOLOv12 | Model deteksi objek |
| Ultralytics | Framework YOLO |
| Roboflow | Pengelolaan dataset |
| OpenCV | Pengolahan citra |
| Matplotlib | Visualisasi hasil |
| Google Colab | Lingkungan pengembangan |

---

## Arsitektur Model

Model yang digunakan dalam proyek ini adalah **YOLO12s (YOLOv12 Small)**.

YOLO (*You Only Look Once*) merupakan algoritma Object Detection berbasis Deep Learning yang mampu melakukan proses lokalisasi objek dan klasifikasi objek dalam satu kali proses prediksi. Pendekatan ini membuat YOLO memiliki keunggulan dalam hal kecepatan, efisiensi, dan kemampuan deteksi yang tinggi.

Varian **YOLO12s** dipilih karena memiliki keseimbangan yang baik antara akurasi deteksi dan kebutuhan komputasi sehingga cocok digunakan untuk proses pengenalan karakter aksara.

---

## Parameter Training

| Parameter | Nilai |
|------------|---------|
| Model | YOLO12s |
| Epoch | 50 |
| Image Size | 640 × 640 |
| Batch Size | 16 |

Pada proses training, model mempelajari pola karakter aksara melalui beberapa komponen utama:

- **Box Loss** → Mengukur ketepatan posisi bounding box.
- **Classification Loss** → Mengukur kesalahan klasifikasi karakter.
- **DFL Loss (Distribution Focal Loss)** → Mengukur ketelitian deteksi objek.

Semakin kecil nilai loss yang diperoleh, maka semakin baik kemampuan model dalam mengenali karakter aksara.

---

## Fitur Sistem

### Deteksi Karakter Otomatis
Sistem mampu mendeteksi keberadaan karakter Aksara Ulu Rejang pada sebuah gambar secara otomatis menggunakan model YOLOv12.

### Klasifikasi Karakter
Setiap karakter yang berhasil dideteksi akan diklasifikasikan sesuai dengan kelas aksara yang telah dipelajari selama proses pelatihan.

### Bounding Box Detection
Model menghasilkan *bounding box* pada setiap karakter yang terdeteksi sehingga lokasi objek dapat diketahui secara jelas.

### Confidence Score
Setiap hasil prediksi dilengkapi dengan nilai *confidence* yang menunjukkan tingkat keyakinan model terhadap hasil klasifikasi yang diberikan.

### Multi-Object Detection
Sistem mampu mendeteksi beberapa karakter dalam satu gambar secara bersamaan.

### Pengujian Tulisan Tangan
Model juga diuji menggunakan sampel tulisan tangan untuk melihat kemampuan generalisasi terhadap data baru di luar dataset pelatihan.

---

## Alur Kerja Sistem

```text
Dataset Aksara Ulu Rejang
            │
            ▼
     Anotasi Dataset
            │
            ▼
     Training YOLOv12
            │
            ▼
     Evaluasi Model
            │
            ▼
      Model Terbaik
         (best.pt)
            │
            ▼
       Prediksi Data
            │
            ├── Bounding Box
            ├── Label Karakter
            └── Confidence Score
```

---

## Evaluasi Model

### Confusion Matrix

Hasil confusion matrix menunjukkan bahwa sebagian besar prediksi berada pada diagonal utama. Hal ini menandakan bahwa model mampu mengenali karakter Aksara Ulu Rejang dengan baik dan menghasilkan tingkat klasifikasi yang tinggi.

### Confusion Matrix Normalized

Pada confusion matrix normalized, sebagian besar nilai berada mendekati angka **1 (100%)**, yang menunjukkan bahwa model memiliki tingkat akurasi klasifikasi yang sangat baik dengan tingkat kesalahan yang rendah.

Secara keseluruhan, hasil evaluasi menunjukkan bahwa model mampu melakukan proses deteksi dan klasifikasi karakter aksara secara optimal.

---

## Hasil Deteksi

Model berhasil melakukan deteksi dan klasifikasi karakter Aksara Ulu Rejang pada berbagai citra uji.

Output yang dihasilkan meliputi:

- Bounding Box
- Label Karakter
- Confidence Score

Contoh hasil prediksi:

```text
day 0.85
pay 0.91
be 0.56
he 0.59
```

Semakin tinggi nilai confidence, semakin besar tingkat keyakinan model terhadap hasil prediksi yang diberikan.

Model juga menunjukkan kemampuan yang baik dalam mendeteksi berbagai karakter aksara serta mampu melakukan generalisasi terhadap tulisan tangan dengan hasil yang cukup akurat.

---

## Struktur Repository

```text
ComputerVision_Kelompok5/
│
├── Computer_Vision_Aksara_Ulu_Rejang.ipynb
├── README.md
└── runs/
    ├── train/
    └── detect/
```

---

## Instalasi

```bash
git clone https://github.com/AdeliaNurazizahOP/ComputerVision_Kelompok5.git

cd ComputerVision_Kelompok5

pip install ultralytics
pip install roboflow
pip install opencv-python
pip install matplotlib
pip install numpy
```

---

## Cara Menjalankan

1. Buka notebook menggunakan Google Colab.
2. Install seluruh library yang dibutuhkan.
3. Unduh dataset dari Roboflow.
4. Jalankan proses training YOLOv12.
5. Lakukan evaluasi model.
6. Jalankan proses prediksi pada gambar uji.
7. Amati hasil deteksi berupa bounding box, label karakter, dan confidence score.

---

## Kesimpulan

Penelitian ini berhasil mengimplementasikan algoritma YOLOv12 untuk mendeteksi dan mengklasifikasikan karakter Aksara Ulu Rejang berdasarkan citra digital. Model YOLO12s yang digunakan mampu melakukan proses deteksi secara cepat, efisien, dan akurat pada berbagai citra aksara, termasuk tulisan tangan.

Berdasarkan hasil evaluasi menggunakan confusion matrix, confusion matrix normalized, dan hasil prediksi pada data uji, model menunjukkan performa yang baik dalam proses deteksi maupun klasifikasi karakter. Hasil tersebut menunjukkan bahwa teknologi Computer Vision dapat dimanfaatkan sebagai salah satu solusi untuk mendukung pelestarian dan digitalisasi aksara daerah melalui pengenalan karakter berbasis citra digital.

---

## Repository

GitHub Repository:

https://github.com/AdeliaNurazizahOP/ComputerVision_Kelompok5
