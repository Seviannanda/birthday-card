# Kartu Ucapan Ulang Tahun 🌸

Website kartu ucapan interaktif — statis (HTML/CSS/JS biasa), tidak butuh database atau backend. Jauh lebih simpel dibanding project Next.js kamu sebelumnya, jadi deploy-nya juga nggak akan ada drama migrasi.

## 1. Struktur folder

```
kartu-ucapan/
├─ index.html      ← semua kode ada di sini
└─ assets/         ← taruh foto & musik kamu di sini
```

## 2. Edit isi kartu

Buka `index.html` pakai text editor (VS Code, dsb), cari bagian:

```js
const CONFIG = { ... }
```

Semua teks, nama, foto, dan musik diatur dari situ. Tidak perlu ubah bagian lain.

## 3. Menambahkan foto sendiri

1. Taruh file foto (misal `foto1.jpg`) ke dalam folder `assets/`.
2. Di `CONFIG.photos`, ganti url picsum dengan path lokal:
   ```js
   { url:"assets/foto1.jpg", caption:"awal cerita kita" },
   ```

## 4. Menambahkan musik

1. Taruh file mp3 (misal `musik-latar.mp3`) ke folder `assets/`.
2. Isi `CONFIG.musicSrc`:
   ```js
   musicSrc: "assets/musik-latar.mp3"
   ```
3. Pastikan file mp3 milikmu sendiri / bebas lisensi — jangan pakai lagu berhak cipta kalau situsnya akan dibagikan publik.

Cek dulu hasilnya dengan buka `index.html` langsung di browser sebelum deploy.

## 5. Deploy ke Vercel (tanpa GitHub, paling cepat)

Karena ini situs statis, kamu tidak perlu setup project/database seperti sebelumnya.

1. Install Vercel CLI (sekali saja):
   ```
   npm i -g vercel
   ```
2. Buka terminal di dalam folder `kartu-ucapan/`, lalu jalankan:
   ```
   vercel
   ```
3. Ikuti pertanyaannya:
   - Login/daftar kalau diminta.
   - "Set up and deploy?" → Yes
   - "Link to existing project?" → No
   - Framework preset → pilih **Other**
   - Biarkan default untuk sisanya (tidak ada build command, output directory `./`)
4. Setelah selesai, Vercel akan kasih link (misal `kartu-ucapan.vercel.app`). Untuk deploy versi final/production, jalankan:
   ```
   vercel --prod
   ```

## 6. Deploy ke Vercel lewat GitHub (kalau mau lebih rapi / kolaborasi)

1. Push folder ini ke repo GitHub baru.
2. Buka [vercel.com/new](https://vercel.com/new), import repo tersebut.
3. Framework preset → **Other**, build command dikosongkan, output directory `./`.
4. Klik Deploy.

Catatan: karena tidak ada Prisma/database/API di project ini, tidak akan ada masalah migrasi seperti project top-up game kamu kemarin — situs ini murni file statis.
