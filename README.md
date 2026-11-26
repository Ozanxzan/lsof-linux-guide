# lsof Linux: Menemukan Proses, File, dan Port

Panduan praktis memakai `lsof` (list open files) di Linux untuk menelusuri proses, file, dan port yang sedang digunakan.

> Artikel lengkap (Bahasa Indonesia): https://nazuaf.com/lsof-linux-menemukan-proses-file-port/
> Blog: https://nazuaf.com — Blog teknologi Indonesia: AI, internet, keamanan digital, dan inovasi teknologi terkini.

## Kenapa lsof?

Port yang dianggap kosong ternyata masih dipakai aplikasi lain, berkas log sudah dihapus tetapi ruang disk belum kembali, atau sebuah file tidak bisa diperbarui karena masih dibuka proses tertentu. `lsof` menampilkan file dan sumber daya yang sedang dibuka proses: direktori, perangkat, pipe, serta koneksi jaringan.

## Yang ditampilkan lsof

Linux memperlakukan banyak sumber daya melalui abstraksi file. Hasil `lsof` mencakup file konfigurasi, direktori kerja, perangkat, socket jaringan, dan file descriptor yang dipakai aplikasi.

Kolom yang umum terlihat:

| Kolom | Arti |
|-------|------|
| `COMMAND` | Nama program |
| `PID` | Identitas proses |
| `USER` | Pemilik proses |
| `FD` | File descriptor |
| `TYPE` | Jenis objek |
| `NAME` | Nama file, alamat, atau socket |

Nilai FD seperti `3u` menunjukkan descriptor bernomor 3 yang dibuka untuk baca-tulis; penanda seperti `cwd` menunjukkan direktori kerja proses.

## Perintah yang sering dipakai

```bash
# Semua file yang dibuka
lsof

# File yang dibuka oleh satu proses
lsof -p <PID>

# Siapa yang memakai port 8080
lsof -i :8080

# Semua koneksi jaringan
lsof -i

# File yang dibuka oleh pengguna tertentu
lsof -u <username>

# File yang dibuka di satu direktori
lsof +D /var/log

# File yang sudah dihapus tapi masih dibuka proses (ruang disk belum kembali)
lsof | grep deleted
```

## Baca selengkapnya

Panduan lengkap dengan contoh kasus dan penjelasan tiap opsi ada di artikel aslinya:

**https://nazuaf.com/lsof-linux-menemukan-proses-file-port/**

Blog teknologi Indonesia — AI, internet, keamanan digital, dan inovasi teknologi terkini: **https://nazuaf.com**
