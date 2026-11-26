# GODE GODE SONG CARD — PROYEK BARU

Isi: `index.html`, `firestore.rules`, dan panduan ini.

## 1. Buat Firebase baru
- Buka https://console.firebase.google.com/ lalu Add project.
- Buat proyek baru (contoh: `gode-gode-song-card-live`).
- Project settings > General > Your apps > Add app (Web `</>`).
- Salin konfigurasi Web: apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId.

## 2. Isi konfigurasi
Buka `index.html`, cari `const firebaseConfig` lalu ganti keenam nilai `ISI_...` dengan nilai dari Firebase baru. Jangan gunakan konfigurasi proyek lama.

## 3. Aktifkan login
Firebase > Authentication > Get started > Sign-in method > Email/Password > Enable > Save.

## 4. Buat database
Firestore Database > Create database > Production mode. Pilih lokasi dengan cermat karena lokasi database tidak bisa diganti setelah dibuat.
Buka tab Rules, tempel seluruh isi `firestore.rules`, lalu Publish.

## 5. Buat admin pertama
- Authentication > Users > Add user. Buat email dan sandi admin.
- Salin UID akun.
- Firestore > Data > Start collection: `admins`.
- Document ID harus persis UID tadi. Tidak perlu field.
Aplikasi sengaja tidak menyediakan pendaftaran admin publik.

## 6. Deploy
- Buat repository GitHub baru.
- Upload `index.html` ke root repository.
- Import repository ke Vercel. Framework: Other; build command dan output directory kosong.
- Setelah deploy, tambahkan domain Vercel ke Authentication > Settings > Authorized domains.

## 7. Uji
Login admin, buat sesi 5 pemain, isi skor enam pertandingan, simpan, lalu buka situs di perangkat lain untuk memeriksa sinkronisasi.

## Catatan versi awal
- Setiap sesi berisi 5 pemain dan 6 pasangan pertandingan.
- Skor masing-masing pemain dijumlahkan untuk klasemen lintas sesi.
- Sistem gugur versi awal menyimpan daftar pemain cadangan, tetapi belum membuat bracket eliminasi/promosi otomatis.
- Firebase SDK dimuat melalui CDN. Tidak perlu `npm install firebase`.
