# KIYAAAA di Vercel (harga dimuat otomatis dari server)

Dashboard memanggil `/api/chart` (fungsi server Vercel) yang mengambil data Yahoo Finance
dari sisi server, tanpa proxy gratis. Hasil disimpan di cache Vercel 15 menit, jadi buka
berikutnya cepat dan Yahoo jarang dipanggil. Tidak perlu token atau environment variable.

Isi: `index.html` (menu), `breakout.html`, `rsi.html`, `api/chart.js`, `vercel.json`

## Pasang lewat GitHub (disarankan)
1. Buat akun GitHub, buat repository baru, upload semua isi folder ini
   (folder `api` dan file `vercel.json` harus ikut, tetap di lokasi aslinya).
2. Buka vercel.com > Sign Up > **Continue with GitHub**.
3. **Add New > Project** > pilih repository tadi > **Deploy** (tanpa mengubah setting apa pun).
4. Tunggu sekitar 1 menit, lalu buka alamat `https://NAMA-PROYEK.vercel.app`.
5. Tes fungsi server: buka `https://NAMA-PROYEK.vercel.app/api/chart?s=BBCA`.
   Kalau muncul deretan angka (d, o, h, l, c, v), fungsi bekerja.
   Kalau muncul `{"error":"HTTP 429"}` atau sejenisnya, Yahoo sedang menolak server Vercel (lihat catatan).

## Alternatif lewat komputer (tanpa GitHub)
Pasang Node.js, lalu di folder ini jalankan `npm i -g vercel`, kemudian `vercel`
(login lewat browser) dan `vercel --prod`. Token tidak perlu disalin manual.

## Catatan
- Yahoo kadang membatasi alamat server cloud. Dashboard otomatis mengulang, memakai proxy
  lama sebagai cadangan, dan mengisi simbol gagal dari cache. Cek kartu Status Data.
- Saat bursa buka, candle hari ini belum final. Sinyal strategi baru valid setelah bursa tutup.
- Tab yang terbuka memuat ulang harga tiap 30 menit.
- Untuk edukasi dan simulasi, bukan rekomendasi investasi.
