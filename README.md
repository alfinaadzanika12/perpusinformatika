Deskripsi Proyek: Sistem Peminjaman Perpustakaan

Sistem Peminjaman Perpustakaan adalah aplikasi web berbasis PHP dan MySQL yang digunakan untuk mengelola data buku, anggota, serta transaksi peminjaman dan pengembalian secara digital. Aplikasi ini menggantikan pencatatan manual agar proses di perpustakaan lebih cepat, rapi, dan minim kesalahan.
Fitur Utama
Autentikasi: login dan logout dengan pemisahan halaman sesuai role.
Manajemen Anggota: tambah, edit, dan hapus data anggota (Admin).
Manajemen Buku: tambah, edit, dan hapus data buku beserta foto sampul (Admin).
Peminjaman Buku: pencatatan transaksi pinjam melalui proses_pinjam.php.
Pengembalian Buku: pencatatan pengembalian melalui proses_kembali.php, termasuk perhitungan denda keterlambatan.
Dashboard Per Role: tampilan dan menu yang disesuaikan dengan kebutuhan masing-masing pengguna.

peminjamanperpustakaan/
│
├── index.php                  # halaman awal / redirect ke login
├── login.php
├── logout.php
├── koneksi.php                # koneksi database (tetap di root, dipakai semua)
│
├── proses/                    # semua file "proses_*.php"
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
├── includes/                  # bagian yang dipakai berulang
│   ├── header.php
│   ├── footer.php
│   ├── navbar.php
│   └── cek_session.php        # cek role & login sebelum akses halaman
│
├── assets/
│   ├── gambar/                # foto buku, anggota, dll
│   ├── video/
│   │   └── video.mp4
│   ├── css/
│   └── js/
│
└── config/
    └── settings.php           # kalau nanti butuh konfigurasi terpisah dari koneksi.php
    1. Keterangan Akses Pengguna (Role)
Role	Login lewat	Akses
Admin	login.php → dashboard_admin.php	Kelola semua data: tambah/edit/hapus anggota, tambah/edit/hapus buku, lihat semua transaksi peminjaman & denda, kelola akun petugas
Petugas	login.php → dashboard_petugas.php	Proses peminjaman (proses_pinjam.php) & pengembalian (proses_kembali.php), input pembayaran denda, tidak bisa hapus data master (buku/anggota)
User/Anggota	login.php → dashboard_user.php	Lihat katalog buku, riwayat pinjam sendiri, status denda sendiri, kasih rating & ulasan buku.
Database
Koneksi database dikonfigurasi pada file koneksi.php. Tabel utama yang digunakan antara lain:

users — akun admin & petugas
anggota — akun/data siswa
buku — data koleksi buku
transaksi — data peminjaman & pengembalian buku
rating — rating & ulasan buku dari user
