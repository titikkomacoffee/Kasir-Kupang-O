KASIRKU v2.0.0 (build 17) - PAKET APLIKASI LENGKAP
==================================================

ISI PAKET
  web/        berkas aplikasi (unggah ke hosting, timpa yang lama)
                index.html     aplikasi utama (semua fitur, tampilan baru)
                sw.js          service worker (offline + pembaruan)
                install.html   halaman pasang aplikasi (harga paket otomatis dari database)
                manifest.json  pengaturan PWA (warna tema merah)
  sql-baru/   SQL perubahan terbaru, jalankan BERURUTAN sesuai nomor
  sql-lama/   salinan SQL yang Anda unggah sebelumnya, TIDAK diubah (untuk arsip/pemasangan ulang)

URUTAN SQL BARU (Supabase > SQL Editor > New query > tempel isi berkas > Run)
  Syarat: SQL lama (supabase, multi-bisnis, update-stok-gaji, stok-cabang-alert, langganan, admin-platform) sudah pernah dijalankan.
  01-update-nota-stok.sql   pembatalan transaksi, stok kembali, selisih terima barang
  02-notifikasi.sql         notifikasi per pengguna
  03-paket.sql              hapus paket, daftar paket publik, harga awal, demo 30 hari
  04-gaji-periode.sql       fee penjualan, lembur, slip gaji otomatis
  05-outlet-pusat.sql       nama outlet pusat bisa diganti
  06-logo-outlet.sql        logo per outlet
  07-pengumuman.sql         pengumuman developer untuk admin bisnis
  08-hapus-sakurupiah.sql   HANYA bila sebelumnya sakurupiah.sql pernah dijalankan
  Semuanya aman dijalankan ulang.

SETELAH MENGUNGGAH
  1. Buka aplikasi dua kali saat online agar versi baru aktif.
  2. Cek Lainnya > Versi aplikasi (harus v2.0.0 build 17).
  3. Lainnya > Mode offline: pastikan semua centang hijau.

YANG TIDAK ADA DI PAKET INI
  - Berkas gambar ikon aplikasi (icon-192.png, icon-512.png, icon-maskable-512.png, apple-touch-icon.png).
    Aplikasi merujuknya; biarkan berkas yang sudah ada di hosting Anda.
  - Integrasi Sakurupiah sudah DIHAPUS. Pembayaran langganan memakai transfer manual + bukti foto.
    Bila fungsi atau kunci Sakurupiah pernah dipasang di Supabase, hapus:
      supabase functions delete sakurupiah-create
      supabase functions delete sakurupiah-callback
      supabase secrets unset SAKURUPIAH_SANDBOX_API_ID SAKURUPIAH_SANDBOX_API_KEY SAKURUPIAH_PROD_API_ID SAKURUPIAH_PROD_API_KEY
    lalu cabut/ganti API Key di dashboard Sakurupiah.

CATATAN PENGUJIAN
  Diuji di lingkungan simulasi (browser dengan Supabase tiruan): semua halaman untuk peran admin, manajer, kasir,
  konsol developer, dan logika inti. BELUM diuji: SQL di database Anda, serta kamera/printer/offline di HP asli.
  Cek di perangkat kasir sebelum dipakai di toko.
