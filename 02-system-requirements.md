# 02. System Requirements

## 1. Platform

MergeShop merupakan aplikasi berbasis web (Web Application) yang dirancang menggunakan konsep responsive web design sehingga dapat diakses melalui berbagai perangkat tanpa memerlukan instalasi aplikasi tambahan.

Platform yang didukung meliputi:

- Desktop Browser
- Laptop Browser
- Tablet Browser
- Mobile Browser

---

## 2. Wilayah Operasional

Pada tahap awal pengembangan, MergeShop difokuskan untuk melayani wilayah Purwokerto dan sekitarnya.

Pendekatan hyperlocal ini bertujuan untuk mempermudah masyarakat menemukan UMKM kuliner di sekitar lokasi mereka sekaligus meningkatkan eksposur pelaku usaha lokal.

Ekspansi ke wilayah lain dapat dipertimbangkan pada tahap pengembangan berikutnya.

---

## 3. Kategori Produk

MergeShop berfokus pada penjualan produk kuliner.

Kategori utama yang direncanakan antara lain:

- Makanan
- Minuman
- Camilan

Kategori tambahan dapat ditambahkan sesuai kebutuhan pada pengembangan berikutnya.

---

## 4. Metode Pembayaran

MergeShop mendukung dua metode pembayaran utama.

### Pembayaran Online

Pembayaran online diproses menggunakan Payment Gateway Midtrans dengan metode pembayaran QRIS.

### Pembayaran Langsung

Pembeli juga dapat memilih pembayaran secara langsung kepada penjual (Offline Payment) sesuai kesepakatan antara pembeli dan penjual.

---

## 5. Metode Pengiriman

MergeShop tidak menyediakan layanan logistik sendiri.

Pengiriman pesanan dilakukan menggunakan salah satu metode berikut:

- Diantar langsung oleh penjual.
- Diantar menggunakan kurir yang bekerja sama dengan penjual.
- Diambil langsung oleh pembeli (Pickup).

Kerja sama dengan layanan kurir lokal dapat dipertimbangkan pada pengembangan berikutnya.

---

## 6. Jam Operasional

MergeShop mengikuti jam operasional masing-masing toko.

Setiap seller dapat menentukan sendiri jam buka dan jam tutup tokonya sehingga pelanggan hanya dapat melakukan pemesanan ketika toko sedang beroperasi.

---

## 7. Bahasa

Versi awal MergeShop menggunakan Bahasa Indonesia sebagai bahasa utama antarmuka sistem.

Dukungan terhadap bahasa lain dapat dipertimbangkan pada pengembangan berikutnya.

---

## 8. Autentikasi Pengguna

Pengguna melakukan registrasi menggunakan alamat email.

Pada proses registrasi, pengguna diwajibkan memilih jenis akun yang akan digunakan, yaitu:

- Buyer
- Seller

Jenis akun yang dipilih akan menentukan hak akses dan fitur yang tersedia setelah proses autentikasi berhasil.

---

## 9. Artificial Intelligence

MergeShop memanfaatkan layanan Artificial Intelligence melalui Gemini API.

AI digunakan untuk mendukung dua jenis asisten virtual.

### Minjan

Asisten virtual yang membantu pembeli memperoleh rekomendasi makanan berdasarkan kebutuhan maupun preferensi pengguna.

### Bokul

Asisten virtual yang tersedia pada setiap halaman toko dan dipersonalisasi untuk masing-masing seller guna membantu pelanggan memahami produk serta memperoleh rekomendasi menu.

---

## 10. Sistem Peta

MergeShop memanfaatkan layanan peta digital untuk mendukung fitur geolokasi dan pencarian UMKM di sekitar pengguna.

Implementasi awal direncanakan menggunakan Google Maps Platform.

---

## 11. Sistem Notifikasi

MergeShop menyediakan sistem notifikasi dalam aplikasi (In-App Notification).

Pada versi awal, notifikasi digunakan untuk memberikan informasi mengenai:

- Pesanan baru kepada seller.
- Perubahan status pesanan.
- Status pembayaran.
- Status proses withdrawal.

Jenis notifikasi lainnya dapat ditambahkan pada tahap pengembangan berikutnya.

---

## 12. Verifikasi Seller

Setiap pengguna yang mendaftar sebagai seller wajib melalui proses verifikasi sebelum dapat membuka toko dan menjual produk.

Proses verifikasi bertujuan untuk memastikan validitas identitas seller serta menjaga keamanan dan kepercayaan pengguna terhadap platform MergeShop.

Rincian proses verifikasi dijelaskan pada dokumen Business Rules.