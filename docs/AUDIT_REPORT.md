# AUDIT REPORT - TechStore

## Step 1A - Analisis Struktur Folder & File

**Temuan:**
- File gambar/media tersebar di root, folder `images/`, `img/`, `photos/`, `pics/` → perlu dipindahkan ke `assets/images/`.
- CSS tersebar di root, `css/`, `styles/`, `assets/css/` → perlu dikonsolidasikan.
- File HTML backup/duplikat: `index-old.html`, `index_backup.html`, `temp.html` → perlu dihapus.
- Log file: `debug.log`, `error.log`, `application.log` masih ada di repo → berisi informasi sensitif.
- Dokumentasi `.md` tersebar di root, `docs/`, `documentation/` → perlu dikonsolidasikan.

---

## Step 1B - Bug Visual (CSS Tidak Render)

**Temuan:**
1. Halaman `index.html` tidak muncul styling.
   - Penyebab: tag `<link>` salah path atau ekstensi file CSS.
   - Contoh yang salah:
     ```html
     <link rel="stylesheet" href="style.sss">
     ```
   - File CSS sebenarnya ada di folder `assets/css/style.css`.
2. Halaman lain yang perlu diperiksa juga: `home.html`, `product.html`.
3. Semua link CSS akan diperbaiki di Step 2.

---

## Step 1C - Audit Keamanan & Riwayat

**Temuan:**
- File `debug.log` muncul pertama kali di commit `be72ca7` ("apa ya lupa").
- File berisi data sensitif (API key, konfigurasi internal).
- Risiko: data sensitif terekspos publik.
- Rekomendasi: hapus file dari seluruh riwayat Git dan masukkan ke `.gitignore`.
