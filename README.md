# My Enggris — Gemini AI Tutor Edition

Website belajar bahasa Inggris A1–C1 untuk penutur Indonesia, dengan kamus anatomi dan gambar, percakapan keseharian, grammar, latihan acak, dan IELTS Academic / TOEFL iBT preparation.

## AI Tutor berbasis Gemini

Lima mode yang tetap tersedia:
- **Conversation** — dialog dengan koreksi dan pertanyaan lanjutan.
- **Grammar** — koreksi kalimat dan penjelasan dalam bahasa Indonesia.
- **Writing** — umpan balik dan saran revisi tulisan (bukan band IELTS resmi).
- **Speaking** — transkripsi mikrofon berbasis dukungan browser, lalu penilaian grammar/vocabulary/isi teks. **Bukan penilaian aksen atau kualitas pronunciation.**
- **Adaptive Quiz** — satu soal baru per permintaan yang memprioritaskan kelemahan yang tercatat. Soal bisa saja mirip atau berulang.

Antarmuka AI Tutor tetap memanggil `/api/tutor`, tetapi kini Netlify Function `netlify/functions/tutor.mjs` terhubung ke **Gemini generateContent REST API**. Tanpa dependency npm tambahan.

## Cara deploy ke Netlify

1. Extract ZIP, lalu unggah seluruh isi folder ke repository GitHub (atau repository Git lain).
2. Di Netlify, pilih **Add new project > Import an existing project** dan hubungkan repository tersebut.
3. Konfigurasi publish directory `.` dan functions directory `netlify/functions` (sudah diset di `netlify.toml`). Build command boleh dikosongkan.
4. Di Netlify > **Project configuration > Environment variables**, tambahkan:
   - `GEMINI_API_KEY` = API key **baru** dari https://aistudio.google.com/api-keys (scope harus mencakup **Functions**).
   - `GEMINI_MODEL` = `gemini-2.5-flash-lite` (opsional; default demikian). Alternatif dalam kode: `gemini-2.5-flash`.
5. Lakukan deploy/redeploy, kemudian buka My Enggris > **AI English Tutor**.
6. Pilih mode Grammar, masukkan `She go to school every day.` dan tekan **Kirim ke AI Tutor**.

**Jangan simpan API key di dalam ZIP, HTML, JavaScript frontend, `netlify.toml`, atau Git.** Key yang pernah diposting ke percakapan atau tempat publik sebaiknya dicabut dan diganti sebelum digunakan.

### Bila sebelumnya situs diunggah dengan Netlify Drop

Mengunggah folder statis tidak otomatis menjamin bundling Netlify Functions. Gunakan deploy berbasis Git atau Netlify CLI agar fungsi backend turut terpasang. Ini penting karena AI Tutor tidak bisa aktif hanya dengan `index.html` dan `GEMINI_API_KEY`.

## Cara kerja dan batasannya

- Website mengirim data tutor ke Netlify Function, lalu function menghubungi Gemini menggunakan secret key server-side.
- Progres, chat, dan kategori kesalahan tersimpan secara lokal di browser; belum otomatis sinkron antardevice.
- Gemini API menyediakan kuota gratis pada sejumlah model/project, tetapi **kuota dan kelayakan dapat berubah**. Bila free tier habis, AI Tutor akan menampilkan informasi kuota dan fitur non-AI masih berfungsi.
- Belum tersedia autentikasi dan pembatasan kuota server-side. **Jangan publikasikan endpoint untuk penggunaan luas tanpa kontrol akses dan rate limit.**
- Teks yang dikirim diproses Google dan tunduk pada ketentuan data Gemini Free Tier. Jangan mengirim informasi pribadi/sensitif.
- Hasil AI bukan skor sertifikasi atau penilaian pronunciation resmi.

## Struktur penting

- `index.html`, `app.js`, `style.css` — tampilan situs.
- `ai-tutor.js`, `ai-tutor.css` — antarmuka dan logika AI Tutor yang sudah kompatibel.
- `netlify/functions/tutor.mjs` — **Gemini API backend** (pengganti integrasi OpenAI).
- `netlify.toml` — konfigurasi Netlify.
- `lessons-a1.js`, `advanced.js`, `my-enggris-data.js`, `anatomy.webp` — materi, latihan, dan gambar.

Sumber resmi:
- Gemini API: https://ai.google.dev/gemini-api/docs/text-generation
- Google AI Studio: https://aistudio.google.com/api-keys
- Netlify Functions: https://docs.netlify.com/build/functions/get-started/
- Netlify environment variables: https://docs.netlify.com/build/functions/environment-variables/
