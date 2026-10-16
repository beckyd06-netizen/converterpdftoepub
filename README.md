# Converter EPUB

Ubah PDF jadi EPUB yang rapi, langsung di browser. Tidak ada server: PDF diproses di perangkat pengunjung dan tidak diunggah ke mana pun.

## Fitur

- **Teks reflowable**: baris disambung jadi paragraf utuh. Pemenggalan kata diperbaiki (`perusa-` + `haan` → `perusahaan`), sedangkan kata ulang seperti `anak-anak` dan `sehari-hari` tetap utuh.
- **Header, footer, dan nomor halaman dibuang otomatis.**
- **Judul bab dan subbab dikenali** dari ukuran dan ketebalan huruf serta bookmark PDF, lalu dipakai untuk daftar isi dan bab terpisah. `BAB 1` + `Pendahuluan` digabung menjadi satu judul.
- **Dua kolom** dibaca dengan urutan yang benar.
- **Gambar dipotong rapi.** Logo yang berulang dibuang, dan keterangan "Gambar 1.1 …" menjadi caption. Denah atau diagram dari garis vektor ikut utuh bersama labelnya.
- **OCR Bahasa Indonesia** (Tesseract) untuk halaman scan, dengan pelurusan halaman miring. Gambar garis hasil scan dibersihkan sampai latarnya putih.
- **Tipografi**: “tanda kutip”, elipsis …, tanda pisah —, *miring*, **tebal**, catatan kaki, dan daftar butir.
- **Pratinjau per bab** sebelum EPUB diunduh. PDF bisa dipilih dengan seret-lepas atau klik.

## Pasang di GitHub Pages

1. Buat repository baru di GitHub, misalnya `converter-epub`.
2. Unggah **semua isi folder ini**, termasuk folder `tessdata/` dan file `.nojekyll`:
   - lewat web: **Add file → Upload files**, seret semua file dan folder, lalu **Commit changes**; atau
   - lewat terminal:
     ```
     git init
     git add .
     git commit -m "Converter EPUB"
     git branch -M main
     git remote add origin https://github.com/NAMA-ANDA/converter-epub.git
     git push -u origin main
     ```
3. Buka **Settings → Pages**. Pada *Build and deployment*, pilih **Deploy from a branch**, branch **main**, folder **/ (root)**, lalu **Save**.
4. Tunggu 1–2 menit. Situsnya akan tersedia di `https://NAMA-ANDA.github.io/converter-epub/`.

## Struktur

```
index.html                     aplikasi (HTML + CSS + JS dalam satu file)
tessdata/ind.traineddata.gz    data OCR Bahasa Indonesia (±1,2 MB)
.nojekyll                      agar GitHub Pages menyajikan file apa adanya
```

Pustaka **pdf.js**, **tesseract.js**, dan **JSZip** dimuat dari CDN (cdnjs dan jsDelivr). Data OCR dimuat dari folder `tessdata/`; kalau gagal, data diambil dari CDN tesseract.js.

## Catatan

- OCR berjalan di perangkat pengunjung. Kecepatannya kira-kira 3–10 detik per halaman di komputer dan 15–40 detik per halaman di HP.
- Untuk buku scan yang sangat tebal di HP, isi kolom **Halaman** (misalnya `1-50`) supaya memori tidak habis.
- File `index.html` tidak bisa dibuka langsung dengan klik dua kali (`file://`), karena browser memblokir pemuatan data OCR. Jalankan lewat GitHub Pages, atau untuk mencoba di komputer sendiri: `python -m http.server`, lalu buka `http://localhost:8000`.

## Lisensi pihak ketiga

- [pdf.js](https://github.com/mozilla/pdf.js): Apache-2.0
- [tesseract.js](https://github.com/naptha/tesseract.js) dan tesseract.js-core: Apache-2.0
- [JSZip](https://github.com/Stuk/jszip): MIT
- Data OCR `ind.traineddata` dari [tessdata](https://github.com/tesseract-ocr/tessdata): Apache-2.0
- Font: Literata, Plus Jakarta Sans, IBM Plex Mono (Google Fonts, OFL)
