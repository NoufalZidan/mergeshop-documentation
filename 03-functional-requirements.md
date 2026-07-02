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

---

# Module: Product

## FR-070 — Menampilkan Daftar Produk

### Deskripsi

Sistem harus menampilkan seluruh produk yang dimiliki oleh Seller pada halaman toko.

Produk ditampilkan dalam bentuk daftar maupun grid yang responsif sesuai ukuran perangkat.

### Acceptance Criteria

- Daftar produk berhasil dimuat.
- Produk hanya berasal dari seller yang sedang dibuka.
- Produk ditampilkan secara responsif.

### Priority

High

---

## FR-071 — Menampilkan Detail Produk

### Deskripsi

Sistem harus menampilkan informasi lengkap mengenai suatu produk.

Informasi yang ditampilkan meliputi:

- Foto Produk
- Nama Produk
- Harga
- Deskripsi
- Status Ketersediaan
- Rating
- Review
- Informasi Seller
- Lokasi Seller
- AI Bokul

### Acceptance Criteria

- Seluruh informasi berhasil dimuat.
- Produk yang tidak tersedia tetap dapat dilihat namun tidak dapat dipesan.

### Priority

High

---

## FR-072 — Menambahkan Produk

### Deskripsi

Seller harus dapat menambahkan produk baru ke dalam tokonya.

Informasi produk meliputi:

- Nama Produk
- Harga
- Deskripsi
- Kategori
- Foto Produk
- Status Ketersediaan

### Acceptance Criteria

- Produk berhasil dibuat.
- Produk langsung muncul pada halaman toko.

### Priority

High

---

## FR-073 — Mengubah Produk

### Deskripsi

Seller dapat memperbarui informasi produk yang telah dibuat.

### Acceptance Criteria

- Seluruh informasi produk dapat diperbarui.
- Perubahan langsung terlihat oleh Buyer.

### Priority

High

---

## FR-074 — Menghapus Produk

### Deskripsi

Seller dapat menghapus produk dari tokonya.

### Acceptance Criteria

- Produk berhasil dihapus.
- Produk tidak lagi muncul pada halaman Buyer.

### Priority

Medium

---

## FR-075 — Mengelompokkan Produk Berdasarkan Kategori

### Deskripsi

Produk dapat dikelompokkan berdasarkan kategori makanan.

Kategori awal meliputi:

- Makanan
- Minuman
- Cemilan

Kategori lain dapat ditambahkan pada pengembangan selanjutnya.

### Acceptance Criteria

- Produk tampil sesuai kategori.
- Buyer dapat melihat daftar kategori.

### Priority

Medium

---

## FR-076 — Menampilkan Status Ketersediaan Produk

### Deskripsi

Sistem harus menampilkan status ketersediaan setiap produk.

Status yang tersedia:

- Tersedia
- Habis

Produk dengan status "Habis" tidak dapat dipesan.

### Acceptance Criteria

- Status tampil pada halaman produk.
- Tombol pembelian dinonaktifkan apabila status produk "Habis".

### Priority

High

---

## FR-077 — Menampilkan Rating Produk

### Deskripsi

Sistem harus menampilkan rating rata-rata yang diperoleh suatu produk.

### Acceptance Criteria

- Rating dihitung secara otomatis.
- Rating diperbarui ketika terdapat review baru.

### Priority

Medium

---

## FR-078 — Menampilkan Review Produk

### Deskripsi

Buyer dapat melihat seluruh review yang diberikan oleh pengguna lain terhadap suatu produk.

### Acceptance Criteria

- Daftar review berhasil dimuat.
- Review ditampilkan berdasarkan urutan terbaru.

### Priority

Medium

---

## FR-079 — Produk Favorit

### Deskripsi

Buyer dapat menambahkan maupun menghapus produk dari daftar favorit.

### Acceptance Criteria

- Produk berhasil ditambahkan ke favorit.
- Produk berhasil dihapus dari favorit.
- Daftar favorit dapat diakses melalui halaman profil Buyer.

### Priority

Medium

---

# Module: Order

## FR-080 — Membuat Pesanan

### Deskripsi

Buyer harus dapat membuat pesanan dari produk yang terdapat pada satu seller.

Sistem hanya memperbolehkan satu seller dalam satu transaksi.

### Acceptance Criteria

- Keranjang tidak kosong.
- Seluruh produk berasal dari seller yang sama.
- Pesanan berhasil dibuat.

### Priority

High

---

## FR-081 — Checkout

### Deskripsi

Buyer dapat melakukan checkout terhadap produk yang berada di dalam keranjang.

Informasi checkout meliputi:

- Catatan Pesanan
- Metode Pembayaran
- Metode Pengiriman

### Acceptance Criteria

- Buyer berhasil mengisi seluruh informasi.
- Sistem membuat ringkasan pesanan.
- Total pembayaran dihitung otomatis.

### Priority

High

---

## FR-082 — Status Pesanan

### Deskripsi

Setiap pesanan memiliki status yang menggambarkan proses transaksi.

Status yang digunakan:

- Pending Payment
- Paid
- Waiting Seller Confirmation
- Processing
- Ready for Pickup
- Out for Delivery
- Completed
- Cancelled

### Acceptance Criteria

- Status berubah sesuai alur bisnis.
- Riwayat perubahan status tersimpan.

### Priority

High

---

## FR-083 — Pembatalan Pesanan oleh Buyer

### Deskripsi

Buyer dapat membatalkan pesanan sebelum seller mulai memproses pesanan.

### Acceptance Criteria

- Status pesanan belum memasuki Processing.
- Sistem mengubah status menjadi Cancelled.
- Pembatalan tercatat pada riwayat pesanan.

### Priority

High

---

## FR-084 — Pembatalan Pesanan oleh Seller

### Deskripsi

Seller dapat membatalkan pesanan apabila pesanan tidak dapat dipenuhi.

Contoh:

- Produk habis.
- Toko tutup mendadak.
- Kendala operasional.

### Acceptance Criteria

- Alasan pembatalan wajib diisi.
- Buyer menerima notifikasi.
- Status berubah menjadi Cancelled.

### Priority

High

---

## FR-085 — Riwayat Pesanan Buyer

### Deskripsi

Buyer dapat melihat seluruh riwayat pesanan yang pernah dilakukan.

### Acceptance Criteria

- Riwayat berhasil dimuat.
- Pesanan diurutkan dari yang terbaru.

### Priority

Medium

---

## FR-086 — Detail Pesanan

### Deskripsi

Buyer dan Seller dapat melihat detail lengkap suatu pesanan.

Informasi yang ditampilkan meliputi:

- Nomor Pesanan
- Daftar Produk
- Total Pembayaran
- Metode Pembayaran
- Metode Pengiriman
- Catatan
- Status Pesanan
- Waktu Pemesanan

### Acceptance Criteria

- Detail berhasil dimuat.
- Informasi sesuai data transaksi.

### Priority

High

---

## FR-087 — Perubahan Status Pesanan oleh Seller

### Deskripsi

Seller dapat memperbarui status pesanan sesuai progres pengerjaan.

### Acceptance Criteria

- Status mengikuti alur yang valid.
- Buyer menerima pembaruan status.
- Riwayat status tersimpan.

### Priority

High

---

## FR-088 — Menentukan Estimasi Waktu Penyelesaian

### Deskripsi

Seller harus dapat menentukan estimasi waktu penyelesaian pesanan setelah menerima pesanan.

Estimasi waktu digunakan untuk memberikan informasi kepada Buyer mengenai perkiraan kapan pesanan akan siap diambil atau dikirim.

### Acceptance Criteria

- Seller dapat memilih estimasi waktu.
- Estimasi tersimpan pada data pesanan.
- Estimasi dapat diperbarui selama pesanan belum selesai.
- Buyer menerima pembaruan estimasi waktu apabila terjadi perubahan.

### Priority

Medium

---

## FR-089 — Menampilkan Estimasi Waktu kepada Buyer

### Deskripsi

Sistem harus menampilkan estimasi waktu penyelesaian pesanan yang diberikan oleh Seller.

Estimasi ditampilkan pada halaman detail pesanan sehingga Buyer dapat mengetahui perkiraan waktu pesanan selesai diproses.

### Acceptance Criteria

- Estimasi waktu ditampilkan pada halaman detail pesanan.
- Estimasi diperbarui secara otomatis apabila Seller mengubahnya.
- Buyer dapat melihat estimasi hingga pesanan berstatus Completed atau Cancelled.

### Priority

Medium

---

# Module: Payment

## FR-090 — Membuat Transaksi Pembayaran

### Deskripsi

Sistem harus membuat transaksi pembayaran setelah Buyer berhasil melakukan checkout.

### Acceptance Criteria

- Checkout berhasil dilakukan.
- Sistem menghasilkan transaksi baru.
- Nomor transaksi bersifat unik.

### Priority

High

---

## FR-091 — Menampilkan Ringkasan Pembayaran

### Deskripsi

Sistem harus menampilkan ringkasan pembayaran sebelum Buyer melakukan pembayaran.

Informasi yang ditampilkan meliputi:

- Daftar Produk
- Total Harga Produk
- Biaya Layanan
- Total Pembayaran
- Metode Pembayaran

### Acceptance Criteria

- Informasi sesuai dengan isi keranjang.
- Total pembayaran dihitung secara otomatis.

### Priority

High

---

## FR-092 — Pembayaran Menggunakan QRIS

### Deskripsi

Buyer dapat melakukan pembayaran menggunakan QRIS melalui Midtrans.

### Acceptance Criteria

- QRIS berhasil dibuat.
- Buyer dapat melakukan pembayaran.
- Status pembayaran diperbarui secara otomatis.

### Priority

High

---

## FR-093 — Pembayaran Langsung (Offline)

### Deskripsi

Buyer dapat memilih pembayaran langsung kepada Seller.

### Acceptance Criteria

- Sistem mencatat metode pembayaran Offline.
- Seller mengetahui bahwa pembayaran dilakukan secara langsung.

### Priority

High

---

## FR-094 — Menerima Webhook Pembayaran

### Deskripsi

Backend harus menerima webhook dari Midtrans untuk memperbarui status pembayaran.

### Acceptance Criteria

- Signature webhook berhasil diverifikasi.
- Status pembayaran diperbarui.
- Status order ikut diperbarui.

### Priority

High

---

## FR-095 — Memperbarui Status Pembayaran

### Deskripsi

Sistem harus memperbarui status pembayaran berdasarkan hasil yang diterima dari Midtrans.

Status pembayaran meliputi:

- Pending
- Paid
- Failed
- Expired
- Cancelled

### Acceptance Criteria

- Status berubah sesuai webhook.
- Riwayat status tersimpan.

### Priority

High

---

## FR-096 — Menangani Pembayaran Gagal

### Deskripsi

Sistem harus menangani transaksi yang gagal dibayar.

### Acceptance Criteria

- Status menjadi Failed.
- Order tidak diproses.
- Buyer dapat mencoba pembayaran kembali apabila masih diperbolehkan.

### Priority

High

---

## FR-097 — Menampilkan Riwayat Pembayaran

### Deskripsi

Buyer dapat melihat riwayat pembayaran dari seluruh transaksi.

### Acceptance Criteria

- Riwayat berhasil dimuat.
- Informasi pembayaran lengkap ditampilkan.

### Priority

Medium

---

## FR-098 — Menghitung Biaya Layanan

### Deskripsi

Sistem harus menghitung biaya layanan sesuai aturan bisnis yang berlaku.

### Acceptance Criteria

- Biaya layanan dihitung otomatis.
- Total pembayaran diperbarui.

### Priority

High

---

## FR-099 — Retry Pembayaran

### Deskripsi

Buyer dapat melakukan pembayaran ulang terhadap transaksi yang masih berstatus Pending atau Failed sesuai kebijakan sistem.

### Acceptance Criteria

- Retry hanya tersedia pada status yang valid.
- Sistem membuat sesi pembayaran baru apabila diperlukan.

### Priority

Medium

---

# Module: Wallet

## FR-100 — Menampilkan Wallet Seller

### Deskripsi

Sistem harus menyediakan halaman Wallet yang menampilkan informasi saldo milik Seller.

### Acceptance Criteria

- Seller dapat membuka halaman Wallet.
- Informasi saldo berhasil dimuat.
- Data yang ditampilkan sesuai dengan akun Seller yang sedang login.

### Priority

High

---

## FR-101 — Menampilkan Saldo Tersedia

### Deskripsi

Sistem harus menampilkan saldo yang telah memenuhi syarat untuk dilakukan penarikan dana (Available Balance).

### Acceptance Criteria

- Saldo dihitung secara otomatis.
- Nilai saldo sesuai dengan transaksi yang telah memenuhi aturan bisnis.

### Priority

High

---

## FR-102 — Menampilkan Saldo Pending

### Deskripsi

Sistem harus menampilkan saldo yang masih dalam proses penyelesaian (Pending Balance).

Saldo pending belum dapat ditarik oleh Seller.

### Acceptance Criteria

- Saldo pending ditampilkan secara terpisah.
- Nilai diperbarui sesuai status transaksi.

### Priority

High

---

## FR-103 — Menampilkan Total Pendapatan

### Deskripsi

Sistem harus menampilkan total pendapatan Seller berdasarkan seluruh transaksi yang berhasil.

### Acceptance Criteria

- Total pendapatan dihitung otomatis.
- Data sesuai dengan riwayat transaksi.

### Priority

Medium

---

## FR-104 — Menampilkan Riwayat Wallet

### Deskripsi

Seller dapat melihat seluruh riwayat perubahan saldo Wallet.

Riwayat meliputi:

- Dana masuk
- Dana keluar
- Withdrawal
- Penyesuaian saldo (jika ada)

### Acceptance Criteria

- Riwayat ditampilkan secara kronologis.
- Setiap transaksi memiliki informasi yang lengkap.

### Priority

High

---

## FR-105 — Menambahkan Saldo Secara Otomatis

### Deskripsi

Sistem harus menambahkan saldo ke Wallet Seller secara otomatis ketika transaksi telah memenuhi aturan bisnis.

### Acceptance Criteria

- Saldo bertambah secara otomatis.
- Tidak terjadi penambahan saldo ganda.
- Seluruh perubahan tercatat pada riwayat Wallet.

### Priority

High

---

## FR-106 — Mengurangi Saldo Setelah Withdrawal

### Deskripsi

Sistem harus mengurangi Available Balance setelah proses withdrawal berhasil dilakukan.

### Acceptance Criteria

- Saldo berkurang sesuai nominal withdrawal.
- Riwayat Wallet diperbarui.
- Saldo tidak dapat bernilai negatif.

### Priority

High

---

## FR-107 — Detail Transaksi Wallet

### Deskripsi

Seller dapat melihat informasi lengkap dari setiap transaksi Wallet.

Informasi yang ditampilkan meliputi:

- Nomor Referensi
- Jenis Transaksi
- Nominal
- Waktu
- Status
- Keterangan

### Acceptance Criteria

- Detail transaksi berhasil dimuat.
- Informasi sesuai dengan data transaksi.

### Priority

Medium

---

## FR-108 — Refresh Saldo Wallet

### Deskripsi

Sistem harus memperbarui informasi saldo Wallet ketika terjadi perubahan transaksi.

### Acceptance Criteria

- Saldo diperbarui setelah transaksi berhasil.
- Informasi Wallet tetap konsisten dengan database.

### Priority

Medium