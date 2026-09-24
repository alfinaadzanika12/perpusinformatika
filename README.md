# 📚 Sistem Peminjaman Perpustakaan

Aplikasi web berbasis **PHP dan MySQL** untuk mengelola data buku, anggota, serta transaksi peminjaman dan pengembalian secara digital. Sistem ini menggantikan pencatatan manual agar proses di perpustakaan lebih cepat, rapi, dan minim kesalahan.

## ✨ Fitur Utama

- **Autentikasi** — login dan logout dengan pemisahan halaman sesuai role.
- **Manajemen Anggota** — tambah, edit, dan hapus data anggota (Admin).
- **Manajemen Buku** — tambah, edit, dan hapus data buku beserta foto sampul (Admin).
- **Peminjaman Buku** — pencatatan transaksi pinjam.
- **Pengembalian Buku** — pencatatan pengembalian beserta perhitungan denda keterlambatan otomatis.
- **Katalog, Rating & Ulasan** — anggota dapat melihat katalog dan memberi ulasan buku.
- **Dashboard per Role** — tampilan dan menu disesuaikan dengan kebutuhan tiap pengguna.

## 👥 Hak Akses

| Role | Kemampuan |
|---|---|
| **Admin** | Mengelola seluruh data master (anggota dan buku) |
| **Petugas** | Memproses peminjaman dan pengembalian harian |
| **User (Anggota)** | Melihat katalog, meminjam, memantau status pinjaman, dan melihat denda |

Setiap halaman dilindungi oleh `includes/cek_session.php` yang memeriksa status login dan role sebelum halaman ditampilkan.

## 🗂️ Struktur Proyek

```
peminjamanperpustakaan/
│
├── index.php                # Halaman awal / redirect ke login
├── login.php
├── logout.php
├── koneksi.php              # Koneksi database (dipakai semua modul)
│
├── proses/                  # File pemrosesan (proses_*.php)
│   ├── proses_login.php
│   ├── proses_pinjam.php
│   └── proses_kembali.php
│
├── admin/
│   ├── dashboard_admin.php
│   ├── tambah_anggota.php
│   ├── edit_anggota.php
│   ├── hapus_anggota.php
│   ├── tambah_buku.php
│   ├── edit_buku.php
│   └── hapus_buku.php
│
├── petugas/
│   └── dashboard_petugas.php
│
├── user/
│   └── dashboard_user.php
│
├── includes/                # Komponen yang dipakai berulang
│   ├── header.php
│   ├── footer.php
│   ├── navbar.php
│   └── cek_session.php      # Cek role & login sebelum akses halaman
│
├── assets/
│   ├── gambar/              # Foto buku, anggota, dll.
│   ├── video/
│   │   └── video.mp4
│   ├── css/
│   └── js/
│
└── config/
    └── settings.php         # Konfigurasi terpisah dari koneksi.php (opsional)
```

## 🛠️ Teknologi

- **Bahasa:** PHP (mysqli)
- **Database:** MySQL
- **Frontend:** HTML, CSS, JavaScript
- **Server lokal:** XAMPP

## 🚀 Cara Instalasi (Localhost)

1. **Clone repositori** ke folder `htdocs` XAMPP:
   ```bash
   cd C:/xampp/htdocs
   git clone https://github.com/USERNAME/peminjamanperpustakaan.git
   ```
2. **Jalankan Apache dan MySQL** melalui XAMPP Control Panel.
3. **Buat database** baru di phpMyAdmin (`http://localhost/phpmyadmin`), lalu **import** file `.sql` dari repositori ini.
4. **Sesuaikan koneksi database** di `koneksi.php`:
   ```php
   <?php
   $host = "localhost";
   $user = "root";
   $pass = "";
   $db   = "nama_database_anda";

   $koneksi = mysqli_connect($host, $user, $pass, $db);
   ```
5. **Buka aplikasi** di browser:
   ```
   http://localhost/peminjamanperpustakaan
   ```

## 🎯 Tujuan Proyek

- Mempermudah pengelolaan data buku dan anggota.
- Mempercepat proses peminjaman dan pengembalian.
- Menghitung denda keterlambatan secara otomatis.
- Memberikan akses yang aman sesuai peran pengguna.

## 📄 Lisensi

Proyek ini dibuat untuk keperluan pembelajaran. Silakan gunakan dan kembangkan sesuai kebutuhan.
