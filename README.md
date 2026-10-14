# Astra

Aplikasi latihan bahasa Inggris dan Mandarin: dengar, tirukan, umpan balik per kata. React + Vite + Tailwind, dibungkus Android dengan Capacitor 8.

Panduan menerbitkan ke Google Play ada di [PUBLISH.md](PUBLISH.md).

## Fitur di versi 1.0
Home (target harian, streak, kalimat harian), Learning Hub (5 modul), Listen & Echo (TTS, pengenalan suara, skor per kata, saran), Tone Master (mode Dengar dan Ucap), Profil (statistik, badge, roadmap), data lokal tanpa akun. Scanner dan Roleplay belum ada.

## Pengembangan

```bash
npm install
npm run dev        # http://localhost:5173 (pengenalan suara jalan di Chrome)
npm test           # unit test logika inti
npm run build      # build web ke dist/
```

## Android

```bash
npm run build && npx cap sync android
npx cap open android      # buka di Android Studio (JDK 21)
```

Build rilis otomatis lewat `.github/workflows/android-release.yml`.

## Struktur

- `src/lib/` logika murni: `score.js` (skor ucapan), `tones.js` dan `pitch.js` (nada), `progress.js` (streak, poin, badge), `content.js` (kalimat), `speech.js` (TTS/STT)
- `src/screens/` layar, `src/components/` komponen UI
- `tools/make_assets.py` membuat ikon, splash, dan aset Play Store
- `store/` listing dan aset Play Store, `privacy-policy.md`

## Batasan yang perlu diketahui
- Skor ucapan berbasis hasil pengenalan suara: menunjukkan kata yang terkenali, bukan penilaian fonem.
- Di Android, pengenal suara dan pembaca nada tidak bisa memakai mikrofon bersamaan, sehingga kurva nada pengguna hanya ada di Tone Master mode Ucap.
- Perilaku di perangkat Android asli belum diuji; lihat daftar uji di PUBLISH.md.
