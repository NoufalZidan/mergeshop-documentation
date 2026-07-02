# 03. Functional Requirements

Dokumen ini menjelaskan seluruh kebutuhan fungsional (Functional Requirements) yang harus dipenuhi oleh sistem MergeShop.

Setiap requirement memiliki identitas unik agar mudah ditelusuri selama proses pengembangan, pengujian, maupun pemeliharaan sistem.


## Daftar Modul

1. Authentication
2. Buyer
3. Seller
4. Product
5. Order
6. Payment
7. Wallet
8. Withdrawal
9. AI Assistant
10. Maps
11. Notification
12. Admin

---

# Module: Authentication

## FR-001 — Registrasi Pengguna

### Deskripsi

Sistem harus memungkinkan pengguna membuat akun baru menggunakan alamat email.

Pada proses registrasi, pengguna wajib memilih jenis akun yang akan digunakan, yaitu:

- Buyer
- Seller

### Data Registrasi

Field yang wajib diisi:

- Nama Lengkap
- Email
- Password
- Role (Buyer / Seller)

### Acceptance Criteria

- Nama lengkap wajib diisi.
- Email harus unik dan belum pernah digunakan.
- Password memenuhi aturan keamanan minimum.
- Role berhasil tersimpan sesuai pilihan pengguna.
- Sistem berhasil membuat akun baru.

### Priority

High

---

## FR-002 — Login Pengguna

### Deskripsi

Sistem harus memungkinkan pengguna masuk menggunakan email dan password yang telah terdaftar.

### Acceptance Criteria

- Email terdaftar.
- Password benar.
- Sistem membuat sesi login.
- Pengguna diarahkan menuju dashboard sesuai role.

### Priority

High

---

## FR-003 — Lupa Password

### Deskripsi

Sistem harus menyediakan mekanisme bagi pengguna yang lupa password.

### Acceptance Criteria

- Pengguna dapat memasukkan email yang terdaftar.
- Sistem mengirimkan email reset password.
- Link reset memiliki masa berlaku tertentu.
- Link hanya dapat digunakan satu kali.

### Priority

High

---

## FR-004 — Reset Password

### Deskripsi

Pengguna harus dapat membuat password baru melalui tautan yang dikirimkan melalui email.

### Acceptance Criteria

- Link reset masih valid.
- Password baru memenuhi aturan keamanan.
- Password lama diganti dengan password baru.
- Link reset tidak dapat digunakan kembali.

### Priority

High

---

## FR-005 — Logout

### Deskripsi

Pengguna dapat mengakhiri sesi login.

### Acceptance Criteria

- Session dihapus.
- Token tidak lagi dapat digunakan.
- Pengguna diarahkan ke halaman login.

### Priority

Medium

---

## FR-006 — Kelola Profil

### Deskripsi

Pengguna dapat mengubah informasi profil.

Data yang dapat diperbarui:

- Nama Lengkap
- Foto Profil
- Password

Alamat email tidak dapat diubah setelah proses registrasi.

### Acceptance Criteria

- Data berhasil diperbarui.
- Email tetap tidak berubah.
- Password lama harus diverifikasi sebelum diganti.

### Priority

Medium

---

## FR-007 — Status Akun Seller

### Deskripsi

Setiap akun Seller yang baru dibuat memiliki status **Pending**.

Seller belum dapat membuka toko maupun menjual produk sebelum proses verifikasi selesai.

Status yang tersedia:

- Pending
- Approved
- Rejected

### Acceptance Criteria

- Seller baru memiliki status Pending.
- Seller tidak dapat mengakses fitur penjualan sebelum Approved.
- Admin dapat mengubah status menjadi Approved atau Rejected.

### Priority

High

---

## FR-008 — Verifikasi Seller

### Deskripsi

Administrator bertanggung jawab melakukan proses verifikasi akun Seller.

Seller yang ditolak dapat memperbaiki data dan mengajukan verifikasi ulang.

### Acceptance Criteria

- Admin dapat melihat data seller.
- Admin dapat menyetujui atau menolak verifikasi.
- Alasan penolakan dapat dicatat.
- Seller dapat mengirim ulang data setelah melakukan perbaikan.

### Priority

High

---

## FR-009 — Verifikasi Email (Future Development)

### Deskripsi

Pada versi production, sistem akan mendukung verifikasi email sebelum akun dapat digunakan.

### Acceptance Criteria

- Sistem mengirim email verifikasi.
- Pengguna mengklik tautan verifikasi.
- Status email berubah menjadi Verified.

### Priority

Low

---

# Module: Buyer

## FR-020 — Menampilkan Halaman Beranda

### Deskripsi

Sistem harus menampilkan halaman utama bagi Buyer setelah berhasil login.

Halaman utama menampilkan informasi yang membantu pengguna menemukan makanan dan toko dengan cepat.

Komponen utama meliputi:

- Search Bar
- Banner
- Daftar Kategori
- Rekomendasi Produk
- Rekomendasi Toko
- AI Assistant (Minjan)

### Acceptance Criteria

- Buyer berhasil masuk ke halaman utama.
- Seluruh komponen utama berhasil ditampilkan.
- Data dimuat sesuai kondisi terbaru.

### Priority

High

---

## FR-021 — Pencarian Produk

### Deskripsi

Sistem harus memungkinkan Buyer mencari produk berdasarkan nama makanan.

### Acceptance Criteria

- Buyer dapat memasukkan kata kunci.
- Sistem menampilkan produk yang sesuai.
- Pencarian bersifat tidak sensitif terhadap huruf besar dan kecil.

### Priority

High

---

## FR-022 — Pencarian Toko

### Deskripsi

Sistem harus memungkinkan Buyer mencari toko berdasarkan nama toko.

### Acceptance Criteria

- Buyer dapat mencari toko.
- Sistem menampilkan daftar toko yang sesuai.

### Priority

High

---

## FR-023 — Filter Pencarian (Future Development)

### Deskripsi

Sistem akan menyediakan fitur penyaringan hasil pencarian.

Filter yang direncanakan:

- Harga
- Rating
- Jarak
- Kategori

### Priority

Medium

---

## FR-024 — Melihat Detail Produk

### Deskripsi

Sistem harus menampilkan informasi lengkap mengenai produk.

Informasi yang ditampilkan:

- Foto Produk
- Nama Produk
- Harga
- Deskripsi
- Rating
- Review
- Informasi Seller
- Lokasi Seller
- AI Bokul

### Acceptance Criteria

- Informasi produk berhasil dimuat.
- Informasi seller ditampilkan.
- AI Bokul tersedia pada halaman toko.

### Priority

High

---

## FR-025 — Menambahkan Produk ke Keranjang

### Deskripsi

Buyer dapat menambahkan produk ke keranjang belanja.

Keranjang hanya dapat berisi produk dari satu seller.

### Acceptance Criteria

- Produk berhasil ditambahkan.
- Jumlah produk dapat diubah.
- Keranjang hanya berisi produk dari satu seller.

### Priority

High

---

## FR-026 — Validasi Seller pada Keranjang

### Deskripsi

Apabila Buyer menambahkan produk dari seller yang berbeda, sistem harus meminta konfirmasi untuk menghapus isi keranjang sebelumnya sebelum produk baru dapat ditambahkan.

### Acceptance Criteria

- Sistem mendeteksi seller berbeda.
- Dialog konfirmasi ditampilkan.
- Buyer dapat membatalkan atau melanjutkan proses.

### Priority

High

---

# Module: Seller

## FR-060 — Menampilkan Dashboard Seller

### Deskripsi

Sistem harus menyediakan dashboard utama bagi Seller setelah berhasil login.

Dashboard digunakan sebagai pusat informasi mengenai aktivitas toko.

Informasi yang ditampilkan meliputi:

- Total Pendapatan
- Saldo Tersedia
- Saldo Pending
- Total Pesanan Hari Ini
- Produk Terjual
- Grafik Penjualan
- Notifikasi
- Quick Actions

### Acceptance Criteria

- Dashboard berhasil dimuat.
- Data ditampilkan berdasarkan seller yang sedang login.
- Informasi diperbarui secara berkala.

### Priority

High

---

## FR-061 — Mengelola Produk

### Deskripsi

Seller harus dapat mengelola daftar produk yang dijual.

Fitur yang tersedia:

- Menambah Produk
- Mengubah Produk
- Menghapus Produk

### Acceptance Criteria

- Produk baru berhasil dibuat.
- Produk dapat diperbarui.
- Produk dapat dihapus.
- Perubahan langsung tercermin pada halaman toko.

### Priority

High

---

## FR-062 — Mengubah Status Ketersediaan Produk

### Deskripsi

Seller harus dapat mengubah status ketersediaan produk menggunakan mekanisme toggle.

Status yang tersedia:

- Tersedia
- Habis

Sistem tidak menggunakan manajemen stok numerik karena produk yang dijual merupakan makanan dengan ketersediaan yang bersifat dinamis.

### Acceptance Criteria

- Seller dapat mengubah status produk.
- Produk berstatus Habis tidak dapat dipesan.
- Perubahan status langsung terlihat oleh Buyer.

### Priority

High

---

## FR-063 — Mengelola Pesanan

### Deskripsi

Seller harus dapat mengelola seluruh pesanan yang masuk.

Status pesanan yang dapat diberikan oleh Seller:

- Diproses
- Siap Diambil
- Sedang Diantar
- Selesai
- Dibatalkan

### Acceptance Criteria

- Seller dapat mengubah status pesanan.
- Buyer menerima perubahan status.
- Riwayat status tersimpan.

### Priority

High

---

## FR-064 — Wallet Seller

### Deskripsi

Sistem harus menyediakan Wallet sebagai tempat penyimpanan saldo virtual milik Seller.

Wallet menampilkan:

- Saldo Tersedia
- Saldo Pending
- Total Pendapatan
- Riwayat Transaksi

### Acceptance Criteria

- Informasi saldo sesuai transaksi.
- Riwayat transaksi dapat dilihat.
- Nilai saldo dihitung secara otomatis.

### Priority

High

---

## FR-065 — Withdrawal

### Deskripsi

Seller dapat mengajukan pencairan saldo yang tersedia.

Sistem mendukung:

- Menambah rekening
- Mengubah rekening
- Pengajuan withdrawal

Dukungan terhadap e-wallet dapat ditambahkan apabila didukung oleh penyedia layanan disbursement.

### Acceptance Criteria

- Seller hanya dapat menarik Saldo Tersedia.
- Nominal memenuhi batas minimum.
- Permintaan withdrawal tercatat.
- Status withdrawal dapat dipantau.

### Priority

High

---

## FR-066 — AI Bokul

### Deskripsi

Seller dapat melakukan konfigurasi AI Bokul yang digunakan pada halaman toko.

Konfigurasi meliputi:

- Informasi toko
- FAQ
- Prompt AI
- Personality AI

### Acceptance Criteria

- Konfigurasi berhasil disimpan.
- AI menggunakan konfigurasi terbaru.
- Perubahan berlaku pada halaman toko.

### Priority

Medium

---

## FR-067 — Mengelola Profil Toko

### Deskripsi

Seller dapat memperbarui informasi toko.

Data yang dapat diperbarui meliputi:

- Nama Toko
- Logo
- Banner
- Deskripsi
- Jam Operasional
- Lokasi
- Nomor Telepon

### Acceptance Criteria

- Perubahan berhasil disimpan.
- Informasi toko diperbarui pada halaman Buyer.

### Priority

High

---

## FR-068 — Melihat Statistik Penjualan

### Deskripsi

Seller dapat melihat statistik performa toko.

Informasi yang tersedia meliputi:

- Pendapatan Hari Ini
- Pendapatan Minggu Ini
- Pendapatan Bulan Ini
- Produk Terlaris
- Total Pesanan
- Total Pembatalan

### Acceptance Criteria

- Statistik dihitung otomatis.
- Data ditampilkan sesuai periode.

### Priority

Medium

---

## FR-069 — Notifikasi Seller

### Deskripsi

Seller menerima notifikasi terkait aktivitas toko.

Jenis notifikasi meliputi:

- Pesanan Baru
- Status Withdrawal
- Verifikasi Akun
- Pembatalan Pesanan

### Acceptance Criteria

- Notifikasi muncul secara real-time atau setelah data diperbarui.
- Seller dapat melihat riwayat notifikasi.

### Priority

Medium