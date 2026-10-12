# Web Music Player

Web music player ringan dan gratis, tanpa API key, tanpa akun, dan tanpa database.

## Fitur
- Cari lagu dari katalog publik Audius (artis independen)
- Player lengkap: play/pause, seek, volume, next/previous, shuffle, repeat, antrean
- Like, playlist (buat, ubah nama, tambah/hapus lagu, urutkan), dan riwayat putar
- Library tersimpan di browser (localStorage), hanya metadata, tanpa stream URL
- Tampilan responsif dengan MiniPlayer dan FullPlayer untuk HP
- Provider musik terpisah dari UI, jadi mudah diganti

## Teknologi
Next.js, React, TypeScript (strict), Tailwind CSS, Zustand

## Catatan
- Katalog hanya dari Audius, bukan Spotify atau SoundCloud
- Bergantung pada API publik pihak ketiga yang bisa berubah atau down
- Gratis dan tidak untuk dijual. Credit wajib dipertahankan (lihat LICENSE)

#CARA DEPLOY LOCALHOST, TINGGAL SALIN TEMPEL DI TERMUX.
** pkg update -y && pkg upgrade -y
pkg install -y nodejs-lts unzip
node -v **

**_termux-setup-storage_**
**_cp ~/storage/downloads/music.zip ~
mkdir -p ~/music
unzip -o ~/music.zip -d ~/music
cd ~/music_**
#SESUAIKAN DENGAN FOLDER ZIP↑↑↑

**cp .env.example .env.local**
**npm install**
**sed -i 's/"dev": "next dev"/"dev": "next dev --webpack"/; s/"build": "next build"/"build": "next build --webpack"/' package.json**

**termux-wake-lock
npm run build
npm start**

#DONE UDAH BISA DI PAKAI


## Deploy ke Vercel (siap produksi)

1. Ekstrak ZIP ini, lalu upload folder `source-music-player-website-main` ke repository GitHub.
2. Di Vercel pilih **Add New → Project**, import repository tersebut.
3. Biarkan **Framework Preset: Next.js**, **Root Directory** pada folder yang berisi `package.json`, dan Build Command `npm run build`.
4. Klik **Deploy**. Tidak perlu API key atau database.
5. Jika ingin mengatur provider secara eksplisit, buka **Project → Settings → Environment Variables**, tambahkan `MUSIC_PROVIDER` dengan nilai `audius`, lalu redeploy. Tanpa variabel itu, aplikasi otomatis menggunakan Audius.

### Catatan
- Pencarian dan stream bergantung pada layanan publik Audius; gangguan/limit dari Audius di luar kendali Vercel.
- Playlist, lagu favorit, dan riwayat disimpan di browser pengguna, bukan di server.
- Gunakan Node.js 20.9 atau lebih baru untuk menjalankan/build lokal.
