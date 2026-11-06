# RAMA Journal Studio — ramalabs

Aplikasi praktik penulisan artikel ilmiah untuk mahasiswa, dosen, dan peneliti, berdasarkan presentasi pengguna **“Menulis Artikel Jurnal Terindeks Scopus Gaya Rama”** (25 slide). Peta workflow: pertanyaan riset → argumen research gap → sintesis pustaka → kontribusi → IMRaD → evaluasi jurnal → etika → submission → respons reviewer → audit dan ekspor.

**Copyright © [2026] ramalabs. All rights reserved.**

## Langsung unggah ke GitHub Pages

1. Ekstrak ZIP proyek. Pastikan **seluruh isi folder**, bukan folder pembungkusnya, diunggah ke root repository.
2. Buat repository GitHub publik, misalnya `rama-journal-studio`. Upload `index.html`, `styles.css`, `core.js`, `app.js`, `docx-export.js`, folder `assets/`, folder `.github/workflows/`, dan seluruh berkas lainnya. Berkas workflow di folder tersembunyi `.github` wajib terunggah.
3. Commit ke branch `main` (atau `master`).
4. Buka **Settings → Pages → Build and deployment → Source: GitHub Actions**. Workflow `Publish RAMA Journal Studio` akan otomatis berjalan saat push atau dapat dijalankan melalui **Actions → Run workflow**.
5. Setelah sukses, akses `https://NAMA-AKUN.github.io/rama-journal-studio/` (sesuaikan nama repository).

**Tidak perlu** npm install, backend, token API, server, database, build framework, atau environment variable. Deployment Actions menggunakan Node 22 untuk verifikasi dan menyalin aset ke `dist/` sebelum publikasi.

## Tujuh ruang kerja

| Ruang kerja | Dasar materi PPT | Fitur |
|---|---|---|
| Ringkasan | Slide 1–4 | Peta kerja dan indikator kelengkapan internal |
| Fondasi & Gap | Slide 5–8, 12–13 | Pertanyaan, gap, kontribusi, heuristik gap, kerangka berbasis isian |
| Pustaka & Bukti | Slide 6–8, 18 | Pencarian metadata Crossref, pustaka DOI, matriks temuan/metode/keterbatasan |
| Studio IMRaD | Slide 11–17 | Editor Pendahuluan, Metode, Hasil, Pembahasan, Kesimpulan, Abstrak, kata kunci |
| Jurnal & Etika | Slide 9–10, 19, 24 | Kartu jurnal, tautan Scopus Sources, etika dan deklarasi AI |
| Submission & Revisi | Slide 20–22 | Cover letter berpola dengan placeholder, respons reviewer per poin |
| Audit & Laporan | Slide 18, 23–24 | Audit heuristik, Word DOCX asli, cetak PDF A4, Markdown, backup & restore JSON |

## Penggunaan

Isi pertanyaan, masalah, pola literatur, gap dan kontribusi pada Fondasi & Gap. Cari judul atau kata kunci pada Pustaka & Bukti untuk memperoleh metadata Crossref, lalu buka artikel asli dan tulis catatan temuan, desain, serta keterbatasannya. Lanjutkan menulis IMRaD dengan data penelitian yang nyata. Tentukan jurnal, verifikasi kesesuaiannya, catat status sumber berdasarkan Scopus Sources, periksa deklarasi etik dan submission, lalu jalankan audit dan ekspor.

Pencarian Crossref membutuhkan internet dan tergantung status API/kebijakan CORS. Jika API gagal, entri sumber manual tetap dapat digunakan. **Tidak ada** koneksi otomatis ke Scopus atau alat AI generatif; pemeriksaan jurnal tetap manual. Pengambilan informasi Crossref mencakup metadata bibliografis, **bukan validasi hasil** penelitian, kualitas metode, akses isi lengkap, atau indeksasi jurnal.

## Kebijakan data dan privasi

Teks dan referensi disimpan lokal melalui `localStorage` per browser/perangkat, bukan ke server ramalabs. Penyimpanan lokal dapat hilang karena penghapusan cache/browser atau kebijakan organisasi. Buat backup JSON secara rutin; file dapat dipulihkan kembali di modul Audit. Data riset sensitif sebaiknya mengikuti kebijakan institusi dan tidak dimasukkan dalam perangkat publik. Data hanya dikirim ke Crossref sebagai **kata kunci** ketika Anda menekan tombol Cari referensi; teks manuskrip tidak dikirim.

## Ekspor

- **Word** membuat berkas Office Open XML `.docx` asli menggunakan generator ZIP dalam JavaScript lokal, tanpa pustaka eksternal.
- **PDF** menggunakan fitur cetak browser (Ctrl+P / dialog Print → Save as PDF) dengan layout A4. Pengaturan header/footer cetak bergantung pada browser.
- **Markdown** mengekspor laporan sebagai `.md`, dapat ditinjau di editor teks.
- **Backup JSON** menyimpan seluruh isian kerja; gunakan **Pulihkan JSON** untuk memuatnya kembali.

Ekspor Word/PDF berupa **dokumen kerja lengkap** (naskah, matriks bukti, jurnal, cover letter, reviewer, audit), **bukan format submission final** jurnal tertentu. Sesuaikan gaya sitasi, template resmi, panjang, dan blind-review requirement sebelum submit.

## Menjalankan dan mengetes secara lokal

Buka `index.html` langsung di browser. Untuk menjalankan pemeriksaan kode (opsional, hanya pengembang):

```bash
node --check app.js
node --check core.js
node --check docx-export.js
node scripts/check-site.mjs
node --test scripts/test-core.mjs
node scripts/build-pages.mjs
```

Jika menguji via server lokal, jalankan `python -m http.server 8000` dari root proyek lalu buka `http://localhost:8000`.

## Sumber materi dan pranala verifikasi

Materi dasar dari file PPT pengguna: *Menulis Artikel Jurnal Terindeks Scopus Gaya Rama* (25 slide). Referensi yang tercantum pada slide 25:

- Tress, G., Tress, B., & Saunders, D. A. (2014). *How to write a paper for successful publication in an international peer-reviewed journal*. *Pacific Conservation Biology, 20*(1), 17–24. (Sebagaimana tercantum dalam PPT.)
- Elsevier Scopus Sources: https://www.scopus.com/sources
- Elsevier Scopus content: https://www.elsevier.com/en-gb/products/scopus/content
- Elsevier Journal Finder: https://journalfinder.elsevier.com/
- COPE Council, *Authorship and AI tools*: https://doi.org/10.24318/cCVRZBms
- Crossref REST API: https://www.crossref.org/documentation/retrieve-metadata/rest-api/

**Batasan penting:** “Terindeks Scopus” adalah keterangan tentang cakupan sumber dalam basis data, bukan jaminan penerimaan manuskrip. Audit kelengkapan bukan penilaian peer-review, deteksi plagiarisme, maupun verifikasi karya ilmiah. Penulis bertanggung jawab atas ketepatan setiap klaim, data, rujukan, pernyataan kepengarangan, etika, dan kebijakan penerbit.
