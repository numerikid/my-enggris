# My Enggris — belajar English from A1 to C1

Website belajar bahasa Inggris dalam Bahasa Indonesia, dapat di-hosting di Netlify tanpa server. Cocok sebagai platform belajar mandiri dan persiapan IELTS Academic / TOEFL iBT untuk studi lanjut.

## Yang tersedia

- 60 modul A1–C1 (12 setiap level) dengan penjelasan dan kuis.
- Setiap percobaan modul memakai paket latihan 6 soal (atau sebanyak ketersediaan bank), dengan pengacakan opsi dan pilihan jenis soal berbasis grammar, contoh, dan terjemahan. Pertanyaan dapat terulang jika bank terbatas; ini bukan AI yang membuat pertanyaan tanpa batas.
- Body Anatomy: **120 entri** tubuh dari kepala hingga ujung kaki dan beberapa organ internal, terjemahan Bahasa Indonesia, tombol audio pronunciation sintetis, notasi IPA untuk sebagian kata, gambar depan/belakang dengan 25 titik interaktif.
- Daily Conversation: **18 situasi**, 72 kalimat dialog berbahasa Inggris beserta terjemahan dan audio, dari bangun hingga tidur malam, menu checklist untuk yang sudah dilatih.
- Reading, Listening, Speaking, Writing, flashcards, learning planner, jurnal, mini mock dan tautan latihan tes resmi.
- Ekspor/impor backup JSON, penyimpanan lokal browser. Otomatis mengimpor progres dari `ruang-english-s2-v1` di browser yang sama ketika My Enggris pertama kali dipakai.

## Instalasi Netlify

1. Ekstrak ZIP ini.
2. Buka https://app.netlify.com/drop
3. Seret folder `my-enggris-netlify` yang memuat `index.html`, atau unggah ZIP melalui proses deploy manual yang mendukungnya.
4. Website dapat langsung dipakai tanpa instalasi database atau `npm`.

## Keterbatasan

- Data progres hanya disimpan di browser, bukan sinkron antarperangkat. Backup berkala lewat Data & Pengaturan.
- Tombol pronunciation menggunakan Web Speech API (speechSynthesis), memerlukan browser/suara perangkat yang mendukung. Kualitas aksen bergantung perangkat. IPA tidak tersedia untuk setiap entri.
- Ilustrasi tubuh merupakan gambar edukasi, bukan diagram anatomi klinis dan tidak memperlihatkan organ internal.
- Soal latihan bervariasi dari bank lokal tetapi tidak tak terbatas. Beberapa soal pemahaman berjenis penerjemahan, tidak selalu menguji tata bahasa sesuai modul secara mendalam.
- Mini mock bukan simulasi penuh resmi atau prediksi skor IELTS/TOEFL. Tidak memberikan koreksi speaking/writing tervalidasi. Silakan gunakan sumber resmi tes untuk simulasi.

## Struktur

- `index.html`: halaman utama dan navigasi.
- `style.css`: tata letak responsif.
- `app.js`: mesin aplikasi, kuis, pembelajaran dan progres.
- `my-enggris-data.js`: anatomi dan aktivitas harian.
- `anatomy.webp`: ilustrasi tubuh tampak depan dan belakang.
- `lessons-a1.js` / `advanced.js`: modul dan bank soal asli.

My Enggris adalah produk latihan belajar mandiri independen dan tidak berafiliasi dengan IELTS atau ETS.
