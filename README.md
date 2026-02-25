# Perpustakaan
# Dokumentasi Belajar Database Perpustakaan (XAMPP/MariaDB)

Repository ini berisi catatan perintah SQL lengkap untuk membuat sistem database perpustakaan sederhana, mulai dari pembuatan struktur hingga manipulasi data.

## 🛠️ Cara Masuk ke MariaDB (XAMPP)
1. Buka XAMPP Control Panel, jalankan **MySQL**.
2. Buka Command Prompt (CMD), lalu ketik:
   ```bash
   cd c:\xampp\mysql\bin
   mysql -u root
-- Buat Database
CREATE DATABASE perpustakaan;
USE perpustakaan;

-- Buat Tabel Anggota
CREATE TABLE anggota (
    id_anggota INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    kelas VARCHAR(20) NOT NULL,
    alamat TEXT,
    tanggal_daftar DATE
);

-- Buat Tabel Buku
CREATE TABLE buku (
    id_buku INT AUTO_INCREMENT PRIMARY KEY,
    judul VARCHAR(100) NOT NULL,
    pengarang VARCHAR(100),
    penerbit VARCHAR(100),
    tahun_terbit YEAR,
    stok INT DEFAULT 0
);

-- Buat Tabel Peminjaman (Relasi)
CREATE TABLE peminjaman (
    id_peminjaman INT AUTO_INCREMENT PRIMARY KEY,
    id_anggota INT,
    id_buku INT,
    tanggal_pinjam DATE,
    tanggal_kembali DATE,
    status VARCHAR(20),
    FOREIGN KEY (id_anggota) REFERENCES anggota(id_anggota),
    FOREIGN KEY (id_buku) REFERENCES buku(id_buku)
);
