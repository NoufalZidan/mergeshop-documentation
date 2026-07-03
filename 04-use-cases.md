# 04. Use Cases

## Tujuan

Dokumen ini mendeskripsikan seluruh interaksi antara aktor dengan sistem MergeShop.

Use case digunakan sebagai acuan dalam proses analisis kebutuhan, perancangan sistem, implementasi backend, frontend, API, database, serta pengujian sistem.

---

# Actors

| Actor | Deskripsi |
|--------|-----------|
| Buyer | Pengguna yang membeli makanan melalui MergeShop. |
| Seller | UMKM yang menjual makanan melalui MergeShop. |
| Admin | Administrator yang mengelola seluruh platform MergeShop. |

---

# Buyer Use Cases

## UC-B-001 — Register Account

### Goal

Buyer membuat akun baru pada platform MergeShop.

### Primary Actor

Buyer

### Trigger

Buyer memilih menu **Daftar**.

### Preconditions

- Buyer belum memiliki akun.
- Buyer berada pada halaman Register.

### Main Flow

1. Buyer membuka halaman Register.
2. Buyer memilih role sebagai Buyer.
3. Buyer mengisi nama lengkap.
4. Buyer mengisi alamat email.
5. Buyer mengisi password.
6. Buyer menekan tombol **Daftar**.
7. Sistem memvalidasi seluruh data.
8. Sistem membuat akun Buyer.
9. Sistem mengarahkan Buyer ke halaman Login.

### Alternative Flow

#### A1. Email sudah digunakan

- Sistem menolak registrasi.
- Sistem menampilkan pesan bahwa email telah digunakan.

#### A2. Data tidak valid

- Sistem menampilkan kesalahan validasi.
- Buyer diminta memperbaiki data.

### Postconditions

- Akun Buyer berhasil dibuat.
- Buyer dapat melakukan login.

---

## UC-B-002 — Login

### Goal

Buyer masuk ke dalam sistem.

### Primary Actor

Buyer

### Trigger

Buyer membuka halaman Login.

### Preconditions

- Akun Buyer telah terdaftar.

### Main Flow

1. Buyer memasukkan email.
2. Buyer memasukkan password.
3. Buyer menekan tombol Login.
4. Sistem memverifikasi kredensial.
5. Sistem membuat session login.
6. Buyer diarahkan ke halaman Home.

### Alternative Flow

#### A1. Password salah

- Sistem menampilkan pesan kesalahan.

#### A2. Email tidak ditemukan

- Sistem menampilkan informasi bahwa akun belum terdaftar.

### Postconditions

- Session login aktif.

---

## UC-B-003 — Mencari Produk

### Goal

Buyer mencari makanan berdasarkan nama produk atau nama toko.

### Primary Actor

Buyer

### Trigger

Buyer menggunakan kolom pencarian.

### Preconditions

- Buyer berada pada halaman Home.

### Main Flow

1. Buyer mengetik kata kunci.
2. Sistem melakukan pencarian.
3. Sistem menampilkan daftar hasil.
4. Buyer memilih salah satu produk.

### Alternative Flow

#### A1. Produk tidak ditemukan

- Sistem menampilkan pesan bahwa tidak ada hasil yang sesuai.

### Postconditions

- Daftar produk berhasil ditampilkan.

---

## UC-B-004 — Melihat Detail Produk

### Goal

Buyer melihat informasi lengkap suatu produk.

### Primary Actor

Buyer

### Trigger

Buyer memilih salah satu produk.

### Preconditions

- Produk tersedia.

### Main Flow

1. Buyer membuka halaman detail produk.
2. Sistem menampilkan:
   - Foto Produk
   - Nama Produk
   - Harga
   - Deskripsi
   - Rating
   - Review
   - Nama Toko
   - Lokasi Toko
   - AI Bokul
3. Buyer dapat melihat seluruh informasi produk.

### Alternative Flow

#### A1. Produk sudah dihapus

- Sistem menampilkan halaman tidak ditemukan.

### Postconditions

- Detail produk berhasil ditampilkan.

---

## UC-B-005 — Menambahkan Produk ke Keranjang

### Goal

Buyer menambahkan produk ke dalam keranjang.

### Primary Actor

Buyer

### Trigger

Buyer menekan tombol **Tambah ke Keranjang**.

### Preconditions

- Buyer telah login.
- Produk masih tersedia.
- Keranjang hanya berisi produk dari Seller yang sama.

### Main Flow

1. Buyer memilih jumlah produk.
2. Buyer menekan tombol Tambah ke Keranjang.
3. Sistem memvalidasi Seller.
4. Sistem menambahkan produk ke keranjang.
5. Sistem memperbarui jumlah item pada keranjang.

### Alternative Flow

#### A1. Produk berasal dari Seller lain

- Sistem meminta konfirmasi untuk mengosongkan keranjang sebelumnya.

#### A2. Produk habis

- Sistem menolak penambahan produk.

### Postconditions

- Produk berhasil masuk ke keranjang.

---

## UC-B-006 — Checkout

### Goal

Buyer membuat pesanan baru.

### Primary Actor

Buyer

### Supporting Actors

- Seller
- Midtrans (untuk pembayaran online)

### Trigger

Buyer menekan tombol **Checkout**.

### Preconditions

- Buyer telah login.
- Keranjang tidak kosong.
- Seluruh produk berasal dari Seller yang sama.

### Main Flow

1. Buyer membuka halaman Checkout.
2. Sistem menampilkan ringkasan pesanan.
3. Buyer memilih metode pengiriman.
4. Buyer memilih metode pembayaran.
5. Buyer menambahkan catatan apabila diperlukan.
6. Buyer menekan tombol Buat Pesanan.
7. Sistem membuat Order.
8. Sistem membuat Payment.
9. Buyer diarahkan menuju proses pembayaran.

### Alternative Flow

#### A1. Produk habis

- Checkout dibatalkan.

#### A2. Keranjang kosong

- Sistem menolak checkout.

### Postconditions

- Order berhasil dibuat.
- Payment berhasil dibuat.

---

## UC-B-007 — Melakukan Pembayaran

### Goal

Buyer menyelesaikan pembayaran atas pesanan yang telah dibuat.

### Primary Actor

Buyer

### Supporting Actors

- Midtrans

### Trigger

Buyer menekan tombol **Bayar Sekarang**.

### Preconditions

- Order telah berhasil dibuat.
- Status pembayaran masih **Pending**.

### Main Flow

1. Buyer memilih metode pembayaran.
2. Sistem menghubungi Midtrans untuk membuat transaksi pembayaran.
3. Midtrans mengembalikan informasi pembayaran.
4. Sistem menampilkan halaman pembayaran.
5. Buyer menyelesaikan pembayaran.
6. Midtrans mengirimkan webhook ke Backend.
7. Backend memverifikasi webhook.
8. Status pembayaran diperbarui menjadi **Paid**.
9. Status Order diperbarui menjadi **Paid**.

### Alternative Flow

#### A1. Pembayaran gagal

- Status pembayaran menjadi **Failed**.

#### A2. Pembayaran kedaluwarsa

- Status pembayaran menjadi **Expired**.

#### A3. Buyer membatalkan pembayaran

- Status pembayaran menjadi **Cancelled**.

### Postconditions

- Pembayaran berhasil diproses atau status pembayaran diperbarui sesuai hasil transaksi.

---

## UC-B-008 — Membatalkan Pesanan

### Goal

Buyer membatalkan pesanan sebelum Seller mulai memproses pesanan.

### Primary Actor

Buyer

### Trigger

Buyer menekan tombol **Batalkan Pesanan**.

### Preconditions

- Order masih dapat dibatalkan sesuai aturan bisnis.

### Main Flow

1. Buyer membuka detail pesanan.
2. Buyer menekan tombol Batalkan Pesanan.
3. Sistem meminta konfirmasi.
4. Buyer menyetujui pembatalan.
5. Sistem memperbarui status pesanan menjadi **Cancelled**.
6. Sistem menjalankan proses refund apabila diperlukan.

### Alternative Flow

#### A1. Pesanan sudah diproses

- Sistem menolak pembatalan.

### Postconditions

- Order berhasil dibatalkan.

---

## UC-B-009 — Memberikan Rating dan Review

### Goal

Buyer memberikan penilaian terhadap pesanan yang telah selesai.

### Primary Actor

Buyer

### Trigger

Buyer membuka riwayat pesanan.

### Preconditions

- Order telah berstatus **Completed**.

### Main Flow

1. Buyer membuka detail pesanan.
2. Buyer memilih jumlah bintang.
3. Buyer menulis ulasan.
4. Buyer menekan tombol Kirim.
5. Sistem menyimpan rating dan review.
6. Rating toko diperbarui.

### Alternative Flow

#### A1. Buyer sudah pernah memberikan review

- Sistem mengizinkan Buyer mengubah review yang sudah ada.

### Postconditions

- Review berhasil disimpan.

---

## UC-B-010 — Menggunakan AI Minjan

### Goal

Buyer memperoleh rekomendasi makanan atau informasi mengenai MergeShop melalui AI Minjan.

### Primary Actor

Buyer

### Supporting Actors

- Gemini API

### Trigger

Buyer membuka halaman AI Minjan.

### Preconditions

- Layanan AI tersedia.

### Main Flow

1. Buyer membuka AI Minjan.
2. Buyer mengetik pertanyaan.
3. Sistem mengirim pertanyaan ke AI.
4. AI memproses permintaan.
5. Sistem menampilkan jawaban AI.

### Alternative Flow

#### A1. AI tidak tersedia

- Sistem menampilkan pesan bahwa layanan AI sedang mengalami gangguan.

### Postconditions

- Buyer menerima jawaban AI.

---

## UC-B-011 — Menggunakan AI Bokul

### Goal

Buyer memperoleh informasi mengenai toko tertentu melalui AI Bokul.

### Primary Actor

Buyer

### Supporting Actors

- Gemini API

### Trigger

Buyer membuka halaman toko.

### Preconditions

- Seller telah mengaktifkan AI Bokul.

### Main Flow

1. Buyer membuka halaman toko.
2. Buyer membuka AI Bokul.
3. Buyer mengirim pertanyaan.
4. Sistem mengirim konteks toko ke AI.
5. AI memberikan jawaban sesuai informasi toko.
6. Sistem menampilkan jawaban kepada Buyer.

### Alternative Flow

#### A1. AI Bokul belum dikonfigurasi

- Sistem menampilkan informasi bahwa AI belum tersedia.

### Postconditions

- Buyer memperoleh informasi mengenai toko.

---

## UC-B-012 — Melihat Peta UMKM

### Goal

Buyer melihat lokasi UMKM makanan di Purwokerto.

### Primary Actor

Buyer

### Supporting Actors

- Google Maps

### Trigger

Buyer membuka halaman Maps.

### Preconditions

- Buyer memberikan izin lokasi (opsional).

### Main Flow

1. Buyer membuka halaman Maps.
2. Sistem memuat Google Maps.
3. Sistem menampilkan marker seluruh Seller aktif.
4. Buyer memilih salah satu marker.
5. Sistem menampilkan informasi toko.
6. Buyer dapat membuka navigasi menuju toko.

### Alternative Flow

#### A1. Lokasi perangkat tidak tersedia

- Sistem tetap menampilkan seluruh toko tanpa lokasi Buyer.

### Postconditions

- Lokasi Seller berhasil ditampilkan.

---

## UC-B-013 — Mengelola Profil

### Goal

Buyer memperbarui informasi profil akun.

### Primary Actor

Buyer

### Trigger

Buyer membuka halaman Profil.

### Preconditions

- Buyer telah login.

### Main Flow

1. Buyer membuka halaman Profil.
2. Buyer mengubah nama, foto profil, password, atau alamat.
3. Buyer menekan tombol Simpan.
4. Sistem memvalidasi data.
5. Sistem menyimpan perubahan.
6. Sistem menampilkan pesan berhasil.

### Alternative Flow

#### A1. Password lama salah

- Sistem menolak perubahan password.

#### A2. Data tidak valid

- Sistem menampilkan pesan validasi.

### Postconditions

- Profil berhasil diperbarui.

---

## UC-B-014 — Logout

### Goal

Buyer mengakhiri sesi penggunaan aplikasi.

### Primary Actor

Buyer

### Trigger

Buyer menekan tombol **Logout**.

### Preconditions

- Buyer sedang login.

### Main Flow

1. Buyer menekan tombol Logout.
2. Sistem menghapus session login.
3. Sistem menghapus token autentikasi.
4. Buyer diarahkan ke halaman Login.

### Alternative Flow

Tidak ada.

### Postconditions

- Session login berakhir.

---

# Seller Use Cases

## UC-S-001 — Register Seller Account

### Goal

Calon Seller membuat akun baru sebagai penjual pada MergeShop.

### Primary Actor

Seller

### Trigger

Pengguna memilih role **Seller** pada halaman Register.

### Preconditions

- Seller belum memiliki akun.

### Main Flow

1. Seller membuka halaman Register.
2. Seller memilih role sebagai Seller.
3. Seller mengisi nama lengkap.
4. Seller mengisi email.
5. Seller mengisi password.
6. Seller menekan tombol Daftar.
7. Sistem memvalidasi data.
8. Sistem membuat akun Seller.
9. Status akun diatur menjadi **Pending Verification**.
10. Seller diarahkan ke halaman Login.

### Alternative Flow

#### A1. Email sudah digunakan

- Sistem menolak registrasi.

#### A2. Data tidak valid

- Sistem menampilkan pesan validasi.

### Postconditions

- Akun Seller berhasil dibuat.
- Status Seller adalah **Pending Verification**.

---

## UC-S-002 — Login

### Goal

Seller masuk ke Dashboard Seller.

### Primary Actor

Seller

### Trigger

Seller membuka halaman Login.

### Preconditions

- Akun telah terdaftar.

### Main Flow

1. Seller memasukkan email.
2. Seller memasukkan password.
3. Sistem melakukan autentikasi.
4. Sistem membuat session login.
5. Seller diarahkan ke Dashboard.

### Alternative Flow

#### A1. Password salah

- Sistem menolak login.

#### A2. Akun tidak ditemukan

- Sistem menampilkan pesan kesalahan.

### Postconditions

- Session login aktif.

---

## UC-S-003 — Melengkapi Profil Toko

### Goal

Seller melengkapi informasi toko sebelum mulai berjualan.

### Primary Actor

Seller

### Trigger

Seller membuka menu **Profil Toko**.

### Preconditions

- Seller telah login.

### Main Flow

1. Seller membuka halaman Profil Toko.
2. Seller mengisi nama toko.
3. Seller mengisi alamat toko.
4. Seller menentukan lokasi pada Maps.
5. Seller mengisi nomor telepon.
6. Seller mengisi deskripsi toko.
7. Seller mengunggah logo atau foto toko.
8. Seller menyimpan perubahan.
9. Sistem menyimpan seluruh data.

### Alternative Flow

#### A1. Data belum lengkap

- Sistem meminta Seller melengkapi data.

### Postconditions

- Profil toko berhasil diperbarui.

---

## UC-S-004 — Mengelola Produk

### Goal

Seller mengelola daftar produk yang dijual.

### Primary Actor

Seller

### Trigger

Seller membuka menu **Produk**.

### Preconditions

- Seller telah login.
- Akun Seller telah diverifikasi.

### Main Flow

1. Seller membuka halaman Produk.
2. Seller menambahkan produk baru atau memilih produk yang sudah ada.
3. Seller mengisi atau mengubah:
   - Nama Produk
   - Harga
   - Deskripsi
   - Kategori
   - Foto Produk
4. Seller menyimpan perubahan.
5. Sistem memvalidasi data.
6. Sistem menyimpan produk.

### Alternative Flow

#### A1. Data tidak valid

- Sistem menampilkan pesan validasi.

### Postconditions

- Data produk berhasil diperbarui.

---

## UC-S-005 — Mengubah Status Ketersediaan Produk

### Goal

Seller mengubah status ketersediaan produk.

### Primary Actor

Seller

### Trigger

Seller mengubah toggle **Tersedia/Habis**.

### Preconditions

- Produk telah dibuat.

### Main Flow

1. Seller membuka daftar produk.
2. Seller mengubah status produk.
3. Sistem memperbarui status produk.
4. Status langsung terlihat oleh Buyer.

### Alternative Flow

Tidak ada.

### Postconditions

- Status produk berhasil diperbarui.

---

## UC-S-006 — Menerima Pesanan

### Goal

Seller menerima pesanan baru dari Buyer.

### Primary Actor

Seller

### Trigger

Terdapat pesanan baru.

### Preconditions

- Order berstatus **Paid**.

### Main Flow

1. Seller membuka detail pesanan.
2. Seller memeriksa isi pesanan.
3. Seller menekan tombol **Terima Pesanan**.
4. Sistem mengubah status order menjadi **Waiting Seller Confirmation**.

### Alternative Flow

#### A1. Produk habis

- Seller membatalkan pesanan.

### Postconditions

- Order berhasil diterima.

---

## UC-S-007 — Menentukan Estimasi Waktu

### Goal

Seller memberikan estimasi waktu penyelesaian pesanan kepada Buyer.

### Primary Actor

Seller

### Trigger

Seller telah menerima pesanan.

### Preconditions

- Order berstatus **Waiting Seller Confirmation**.

### Main Flow

1. Seller membuka detail pesanan.
2. Seller memasukkan estimasi waktu penyelesaian.
3. Seller menyimpan estimasi.
4. Sistem menyimpan estimasi.
5. Buyer dapat melihat estimasi pada detail pesanan.

### Alternative Flow

#### A1. Estimasi tidak diisi

- Sistem menggunakan estimasi default apabila tersedia.

### Postconditions

- Estimasi waktu tersimpan.

---

## UC-S-008 — Mengubah Status Pesanan

### Goal

Seller memperbarui status pesanan sesuai proses yang sedang berlangsung.

### Primary Actor

Seller

### Trigger

Seller menekan tombol perubahan status.

### Preconditions

- Order telah diterima.

### Main Flow

1. Seller membuka detail pesanan.
2. Seller memilih status berikutnya.
3. Sistem memvalidasi transisi status.
4. Sistem memperbarui status order.
5. Buyer menerima informasi status terbaru.

### Alternative Flow

#### A1. Transisi status tidak valid

- Sistem menolak perubahan status.

### Postconditions

- Status order berhasil diperbarui.

---

## UC-S-009 — Mengelola AI Bokul

### Goal

Seller mengatur AI Bokul agar dapat menjawab pertanyaan Buyer mengenai toko.

### Primary Actor

Seller

### Supporting Actors

- Gemini API

### Trigger

Seller membuka menu **AI Bokul**.

### Preconditions

- Seller telah login.

### Main Flow

1. Seller membuka halaman AI Bokul.
2. Seller mengisi informasi mengenai toko.
3. Seller mengatur prompt atau instruksi AI.
4. Seller menyimpan konfigurasi.
5. Sistem menyimpan konfigurasi AI.

### Alternative Flow

#### A1. Konfigurasi tidak valid

- Sistem menampilkan pesan kesalahan.

### Postconditions

- AI Bokul berhasil diperbarui.

---

## UC-S-010 — Mengelola Rekening Withdrawal

### Goal

Seller mengelola rekening tujuan pencairan dana.

### Primary Actor

Seller

### Trigger

Seller membuka menu **Rekening Withdrawal**.

### Preconditions

- Seller telah login.

### Main Flow

1. Seller memilih tambah atau ubah rekening.
2. Seller memilih nama bank.
3. Seller memasukkan nomor rekening.
4. Sistem melakukan validasi rekening.
5. Seller menyimpan data.
6. Sistem menyimpan rekening sebagai rekening aktif.

### Alternative Flow

#### A1. Nomor rekening tidak valid

- Sistem menolak penyimpanan.

#### A2. Validasi rekening gagal

- Sistem meminta Seller mencoba kembali.

### Postconditions

- Rekening aktif berhasil diperbarui.

---

## UC-S-011 — Melakukan Withdrawal

### Goal

Seller mencairkan saldo yang tersedia ke rekening bank.

### Primary Actor

Seller

### Supporting Actors

- Penyedia Disbursement (misalnya Jack)

### Trigger

Seller menekan tombol **Withdraw**.

### Preconditions

- Seller memiliki rekening aktif.
- Available Balance mencukupi.
- Nominal memenuhi minimum withdrawal.

### Main Flow

1. Seller membuka halaman Wallet.
2. Seller menekan tombol Withdraw.
3. Seller memasukkan nominal withdrawal.
4. Sistem memvalidasi nominal.
5. Sistem membuat permintaan withdrawal.
6. Backend mengirim permintaan ke penyedia disbursement.
7. Sistem menampilkan status **Processing**.
8. Setelah transfer berhasil, status berubah menjadi **Completed**.
9. Saldo Wallet dikurangi sesuai nominal withdrawal.

### Alternative Flow

#### A1. Saldo tidak mencukupi

- Sistem menolak withdrawal.

#### A2. Nominal di bawah minimum

- Sistem menolak withdrawal.

#### A3. Transfer gagal

- Status menjadi **Failed**.
- Saldo dikembalikan ke Wallet.

### Postconditions

- Withdrawal berhasil diproses atau gagal dengan rollback saldo.

---

## UC-S-012 — Melihat Wallet

### Goal

Seller melihat informasi saldo dan riwayat transaksi wallet.

### Primary Actor

Seller

### Trigger

Seller membuka halaman **Wallet**.

### Preconditions

- Seller telah login.

### Main Flow

1. Seller membuka halaman Wallet.
2. Sistem menampilkan:
   - Available Balance
   - Pending Balance
   - Total Withdrawal
   - Riwayat Withdrawal
   - Riwayat Perubahan Saldo
3. Seller dapat melihat detail setiap transaksi.

### Alternative Flow

Tidak ada.

### Postconditions

- Informasi Wallet berhasil ditampilkan.

---

## UC-S-013 — Logout

### Goal

Seller mengakhiri sesi penggunaan aplikasi.

### Primary Actor

Seller

### Trigger

Seller menekan tombol **Logout**.

### Preconditions

- Seller sedang login.

### Main Flow

1. Seller menekan tombol Logout.
2. Sistem menghapus session login.
3. Sistem menghapus token autentikasi.
4. Seller diarahkan ke halaman Login.

### Alternative Flow

Tidak ada.

### Postconditions

- Session login berakhir.

---

# Admin Use Cases

## UC-A-001 — Login

### Goal

Administrator masuk ke Dashboard Admin untuk mengelola platform MergeShop.

### Primary Actor

Admin

### Trigger

Admin membuka halaman Login.

### Preconditions

- Akun Admin telah terdaftar.

### Main Flow

1. Admin memasukkan email.
2. Admin memasukkan password.
3. Sistem memverifikasi kredensial.
4. Sistem membuat session login.
5. Admin diarahkan ke Dashboard Admin.

### Alternative Flow

#### A1. Email atau password salah

- Sistem menampilkan pesan kesalahan.

### Postconditions

- Session login berhasil dibuat.

---

## UC-A-002 — Melihat Dashboard

### Goal

Administrator melihat ringkasan kondisi platform.

### Primary Actor

Admin

### Trigger

Admin membuka Dashboard.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka Dashboard.
2. Sistem menampilkan:
   - Total Buyer
   - Total Seller
   - Seller Pending Verification
   - Total Order
   - Total Pendapatan Platform
   - Total Withdrawal
   - Statistik Penjualan
3. Admin dapat melihat ringkasan aktivitas platform.

### Alternative Flow

Tidak ada.

### Postconditions

- Dashboard berhasil ditampilkan.

---

## UC-A-003 — Verifikasi Seller

### Goal

Administrator memverifikasi akun Seller sebelum dapat mulai berjualan.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Seller Verification**.

### Preconditions

- Terdapat Seller dengan status **Pending**.

### Main Flow

1. Admin membuka daftar Seller Pending.
2. Admin memilih salah satu Seller.
3. Sistem menampilkan informasi Seller.
4. Admin memilih:
   - Approve
   - Reject
5. Sistem memperbarui status Seller.

### Alternative Flow

#### A1. Data Seller belum lengkap

- Admin menolak verifikasi.
- Admin dapat memberikan alasan penolakan.

### Postconditions

- Status Seller berhasil diperbarui.

---

## UC-A-004 — Mengelola Buyer

### Goal

Administrator mengelola akun Buyer.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Buyer Management**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka daftar Buyer.
2. Sistem menampilkan seluruh akun Buyer.
3. Admin melihat detail akun.
4. Admin dapat menonaktifkan akun apabila diperlukan.

### Alternative Flow

Tidak ada.

### Postconditions

- Data Buyer berhasil diperbarui apabila terdapat perubahan.

---

## UC-A-005 — Mengelola Seller

### Goal

Administrator mengelola seluruh akun Seller.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Seller Management**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka daftar Seller.
2. Sistem menampilkan seluruh Seller.
3. Admin melihat detail toko.
4. Admin dapat memperbarui status Seller apabila diperlukan.

### Alternative Flow

Tidak ada.

### Postconditions

- Informasi Seller berhasil diperbarui.

---

## UC-A-006 — Monitoring Order

### Goal

Administrator memantau seluruh transaksi pesanan.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Orders**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka daftar Order.
2. Sistem menampilkan seluruh Order.
3. Admin melihat detail Order.
4. Admin memantau status Order.

### Alternative Flow

Tidak ada.

### Postconditions

- Informasi Order berhasil ditampilkan.

---

## UC-A-007 — Monitoring Payment

### Goal

Administrator memantau seluruh transaksi pembayaran.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Payments**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka daftar pembayaran.
2. Sistem menampilkan seluruh transaksi pembayaran.
3. Admin melihat detail pembayaran.

### Alternative Flow

Tidak ada.

### Postconditions

- Informasi pembayaran berhasil ditampilkan.

---

## UC-A-008 — Monitoring Withdrawal

### Goal

Administrator memantau seluruh proses withdrawal Seller.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Withdrawals**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka daftar withdrawal.
2. Sistem menampilkan seluruh riwayat withdrawal.
3. Admin melihat detail setiap withdrawal.
4. Admin memantau status withdrawal.

### Alternative Flow

Tidak ada.

### Postconditions

- Informasi withdrawal berhasil ditampilkan.

---

## UC-A-009 — Mengelola Kategori Produk

### Goal

Administrator mengelola kategori produk pada MergeShop.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Categories**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin melihat daftar kategori.
2. Admin menambahkan kategori baru.
3. Admin mengubah kategori.
4. Admin menghapus kategori apabila diperlukan.

### Alternative Flow

#### A1. Kategori masih digunakan oleh produk

- Sistem menolak penghapusan kategori.

### Postconditions

- Data kategori berhasil diperbarui.

---

## UC-A-010 — Melihat Analytics

### Goal

Administrator melihat statistik performa platform.

### Primary Actor

Admin

### Trigger

Admin membuka menu **Analytics**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka halaman Analytics.
2. Sistem menampilkan:
   - Grafik penjualan
   - Jumlah transaksi
   - Pendapatan platform
   - Seller aktif
   - Buyer aktif
   - Produk terlaris
3. Admin dapat memilih periode statistik.

### Alternative Flow

Tidak ada.

### Postconditions

- Statistik platform berhasil ditampilkan.

---

## UC-A-011 — Mengubah Konfigurasi Sistem

### Goal

Administrator mengubah konfigurasi umum platform.

### Primary Actor

Admin

### Trigger

Admin membuka menu **System Configuration**.

### Preconditions

- Admin telah login.

### Main Flow

1. Admin membuka halaman konfigurasi.
2. Admin mengubah parameter sistem, seperti:
   - Biaya layanan
   - Pengaturan AI
   - Pengaturan Payment Gateway
   - Pengaturan Withdrawal
3. Admin menekan tombol Simpan.
4. Sistem memvalidasi konfigurasi.
5. Sistem menyimpan perubahan.

### Alternative Flow

#### A1. Konfigurasi tidak valid

- Sistem menolak penyimpanan.

### Postconditions

- Konfigurasi sistem berhasil diperbarui.

---

## UC-A-012 — Logout

### Goal

Administrator mengakhiri sesi penggunaan sistem.

### Primary Actor

Admin

### Trigger

Admin menekan tombol **Logout**.

### Preconditions

- Admin sedang login.

### Main Flow

1. Admin menekan tombol Logout.
2. Sistem menghapus session login.
3. Sistem menghapus token autentikasi.
4. Admin diarahkan ke halaman Login.

### Alternative Flow

Tidak ada.

### Postconditions

- Session login berakhir.