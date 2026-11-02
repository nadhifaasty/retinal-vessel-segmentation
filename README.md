# Segmentasi dan Analisis Pembuluh Darah Retina (DRIVE Dataset)
**Mata Kuliah:** Analisis Data Citra Biomedik (ADCB) — S1 Sains Data, Universitas Sebelas Maret (UNS)

## 👥 Anggota Kelompok 5
* **Nadhifa Sakha Tri Yasmin (Nad)** — NIM: L0224036 (Kelas B)
* **Kayla Maharani Muzaki (Kayo)** — NIM: L0224050 (Kelas B)

---

## 📌 Ringkasan Proyek
Proyek ini mengimplementasikan teknik pengolahan citra digital klasik untuk segmentasi pembuluh darah retina pada dataset DRIVE. Evaluasi dilakukan secara kuantitatif terhadap *ground truth* manual dalam wilayah *Field of View* (FOV) retina.

### Rancangan Tiga Alur Percobaan:
1. **Percobaan A (Baseline):** Kanal Hijau $\rightarrow$ Bottom-Hat ($r=5$) $\rightarrow$ Otsu dalam FOV.
2. **Percobaan B:** Kanal Hijau $\rightarrow$ CLAHE $\rightarrow$ Filter Median $\rightarrow$ Bottom-Hat $\rightarrow$ Otsu dalam FOV.
3. **Percobaan C (Alur Lengkap):** Alur B $\rightarrow$ Morfologi Closing Biner $\rightarrow$ Penghapusan Komponen Kecil.

---

## 📁 Struktur Repositori
```text
retinal-vessel-segmentation/
├── README.md
├── requirements.txt
├── .gitignore
├── segmentasi_retina.ipynb         # Notebook utama proyek
├── datasets retina drive/           # Dataset resmi DRIVE
│   ├── training/
│   │   ├── images/                 # 20 citra fundus training (.tif)
│   │   ├── 1st_manual/             # 20 anotasi ground truth pembuluh (.gif)
│   │   └── mask/                   # 20 mask FOV retina (.gif)
│   └── test/
│       ├── images/                 # 20 citra fundus test (.tif)
│       └── mask/                   # 20 mask FOV test (.gif)
└── hasil/
    ├── gambar/                     # Output visual (fig01_tahapan_21_A.png, overlay, mask)
    └── tabel/                      # Output numerik & manifest CSV
```

---

## 🚀 Cara Menjalankan
1. Pastikan dependensi terpasang:
   ```bash
   pip install -r requirements.txt
   ```
2. Buka dan jalankan Jupyter Notebook:
   ```bash
   jupyter notebook segmentasi_retina.ipynb
   ```
   Atau buka langsung melalui VS Code / Jupyter Lab dan jalankan secara berurutan (*Restart Kernel & Run All*).

---

## 📊 Hasil Minggu 1 (Progres Saat Ini)
* **Audit Data:** 20 pasangan data training dan 20 pasangan test telah diverifikasi valid (tersimpan di `hasil/tabel/manifest_data.csv`).
* **Pembagian Data:** 20 citra training dibagi menjadi 12 pengembangan (*dev*) dan 8 penilaian (*eval*) menggunakan seed 42 (tersimpan di `hasil/tabel/pembagian_data.csv`).
* **Fungsi Evaluasi:** Fungsi metrik dalam FOV (Dice, IoU, Sensitivity, Specificity, Accuracy, Proporsi Area) lulus unit test sintetis.
* **Hasil Percobaan A:** Telah dieksekusi pada 12 data pengembangan (tersimpan di `hasil/tabel/metrik_pengembangan_A.csv`).
