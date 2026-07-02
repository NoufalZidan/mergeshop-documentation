# 00. Glossary

Dokumen ini berisi daftar istilah yang digunakan selama proses perancangan, pengembangan, dan dokumentasi MergeShop.

## Daftar Istilah

| Istilah | Definisi |
|----------|----------|
| MergeShop | Platform e-commerce hyperlocal yang berfokus pada digitalisasi UMKM kuliner di wilayah Purwokerto. |
| Hyperlocal | Konsep layanan yang beroperasi pada wilayah geografis tertentu, dalam hal ini wilayah Purwokerto dan sekitarnya. |
| Buyer | Pengguna yang melakukan pembelian produk melalui MergeShop. |
| Seller | Pelaku UMKM yang menjual produk melalui MergeShop. |
| Admin | Pengguna yang bertugas mengelola operasional marketplace, termasuk verifikasi data, transaksi, dan aktivitas pengguna. |
| Super Admin | Tim pengembang MergeShop yang memiliki hak akses penuh terhadap konfigurasi dan pengelolaan sistem. |
| Product | Produk makanan yang dijual oleh seller. |
| Order | Pesanan yang dibuat oleh buyer terhadap satu atau lebih produk. |
| Checkout | Proses sebelum pembayaran dilakukan, meliputi konfirmasi pesanan, alamat, metode pembayaran, dan informasi lainnya. |
| Payment Gateway | Layanan pihak ketiga yang digunakan untuk memproses pembayaran online. Pada MergeShop menggunakan Midtrans. |
| Midtrans | Payment Gateway yang digunakan untuk memproses pembayaran online pada MergeShop. |
| Jack | Layanan Business Banking dan Disbursement API yang digunakan untuk proses pencairan dana (withdraw) seller. |
| Settlement | Proses pencairan dana hasil transaksi dari Payment Gateway ke rekening merchant sesuai jadwal settlement. |
| Merchant | Akun bisnis milik MergeShop yang menerima dana hasil transaksi dari Payment Gateway. |
| Wallet | Saldo virtual milik seller yang dikelola oleh sistem MergeShop. |
| Pending Balance | Saldo seller yang berasal dari transaksi namun belum dapat dicairkan karena masih menunggu penyelesaian pesanan atau proses bisnis lainnya. |
| Available Balance | Saldo seller yang telah dapat digunakan untuk proses penarikan dana. |
| Withdrawal | Proses pencairan saldo seller dari Wallet menuju rekening bank atau metode pembayaran lainnya. |
| Disbursement | Proses pengiriman dana dari rekening perusahaan kepada seller menggunakan layanan pihak ketiga. |
| Webhook | Mekanisme komunikasi di mana sistem pihak ketiga secara otomatis mengirimkan notifikasi ke backend MergeShop ketika suatu event terjadi, misalnya pembayaran berhasil atau proses payout selesai. |
| API | Application Programming Interface, yaitu mekanisme komunikasi antar sistem atau aplikasi. |
| REST API | Arsitektur API yang digunakan oleh backend MergeShop untuk komunikasi antara frontend, backend, dan layanan pihak ketiga. |
| JWT | JSON Web Token yang digunakan sebagai mekanisme autentikasi pengguna. |
| Authentication | Proses untuk memverifikasi identitas pengguna. |
| Authorization | Proses untuk menentukan hak akses pengguna setelah berhasil melakukan autentikasi. |
| Geolocation | Informasi lokasi geografis pengguna atau seller yang digunakan untuk menampilkan UMKM di sekitar pengguna. |
| AI Assistant | Fitur chatbot berbasis Artificial Intelligence yang membantu pengguna selama menggunakan MergeShop. |
| Minjan | AI Assistant yang membantu buyer menemukan rekomendasi makanan sesuai kebutuhan dan preferensi mereka. |
| Bokul | AI Assistant yang dipersonalisasi pada setiap halaman seller untuk membantu pelanggan memahami produk, menjawab pertanyaan, dan memberikan rekomendasi menu. |
| Dashboard Seller | Halaman yang digunakan seller untuk mengelola toko, produk, pesanan, wallet, dan proses withdrawal. |
| Dashboard Admin | Halaman yang digunakan administrator untuk mengelola seluruh aktivitas marketplace. |
| Dashboard Buyer | Halaman yang digunakan buyer untuk melihat pesanan, profil, dan aktivitas akun. |
| MVP (Minimum Viable Product) | Versi awal aplikasi yang memiliki fitur inti dan siap digunakan untuk validasi kebutuhan pengguna. |