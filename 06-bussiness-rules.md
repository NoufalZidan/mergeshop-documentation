# 06. Business Rules

Dokumen ini berisi seluruh aturan bisnis yang menjadi dasar implementasi MergeShop.

Business Rules digunakan sebagai acuan bagi seluruh proses pengembangan backend, frontend, database, API, dan pengujian sistem.

Setiap aturan memiliki identitas unik agar mudah dirujuk selama proses pengembangan.

---

# Authentication

## BR-001 — Email Harus Unik

Setiap akun wajib memiliki alamat email yang unik.

Email yang telah digunakan tidak dapat digunakan kembali untuk registrasi akun lain.

---

## BR-002 — Satu Akun Satu Role

Setiap akun hanya dapat memiliki satu role.

Role yang tersedia:

- Buyer
- Seller
- Admin

Perubahan role hanya dapat dilakukan melalui proses administrasi sistem apabila diperlukan.

---

## BR-003 — Seller Baru Berstatus Pending

Setiap Seller yang baru melakukan registrasi memiliki status awal **Pending**.

Seller tidak dapat membuka toko maupun menjual produk sebelum proses verifikasi selesai.

---

## BR-004 — Email Tidak Dapat Diubah

Alamat email tidak dapat diubah setelah proses registrasi.

---

# Buyer

## BR-005 — Satu Keranjang Satu Seller

Buyer hanya dapat membeli produk dari satu Seller dalam satu transaksi.

Apabila Buyer menambahkan produk dari Seller yang berbeda, sistem harus meminta konfirmasi untuk mengosongkan keranjang sebelumnya.

---

## BR-006 — Produk Habis Tidak Dapat Dibeli

Produk dengan status **Habis** tidak dapat ditambahkan ke keranjang.

---

## BR-007 — Buyer Hanya Memiliki Satu Alamat

Pada versi MVP, Buyer hanya dapat menyimpan satu alamat utama.

Dukungan untuk beberapa alamat dapat ditambahkan pada pengembangan berikutnya.

---

## BR-008 — Produk Favorit Bersifat Personal

Daftar favorit hanya dapat dilihat oleh pemilik akun.

---

# Seller

## BR-009 — Produk Tidak Menggunakan Sistem Stok

MergeShop tidak menggunakan stok numerik.

Seller hanya menentukan status produk:

- Tersedia
- Habis

---

## BR-010 — Satu Seller Memiliki Satu Wallet

Setiap Seller hanya memiliki satu Wallet.

Wallet digunakan sebagai representasi saldo virtual.

---

## BR-011 — Satu Rekening Aktif

Seller hanya dapat memiliki satu rekening aktif untuk withdrawal.

---

## BR-012 — Verifikasi Seller Wajib

Seller wajib melalui proses verifikasi sebelum dapat menjual produk.

---

# Order

## BR-013 — Order Harus Dibayar Terlebih Dahulu

Pesanan tidak dapat diproses sebelum pembayaran berhasil diterima.

---

## BR-014 — Buyer Dapat Membatalkan Sebelum Diproses

Buyer hanya dapat membatalkan pesanan sebelum Seller mulai memproses pesanan.

---

## BR-015 — Seller Dapat Membatalkan Pesanan

Seller dapat membatalkan pesanan apabila pesanan tidak dapat dipenuhi.

Contoh:

- Produk habis
- Kendala operasional

---

## BR-016 — Status Order Bersifat Linear

Status order hanya dapat berubah mengikuti urutan proses yang telah ditentukan.

Status tidak dapat kembali ke status sebelumnya.

---

# Payment

## BR-017 — Midtrans Sebagai Payment Gateway

Seluruh pembayaran online diproses melalui Midtrans.

---

## BR-018 — Pembayaran Offline Tidak Menggunakan Midtrans

Pembayaran offline dilakukan langsung kepada Seller.

---

## BR-019 — Webhook Wajib Diverifikasi

Seluruh webhook dari Midtrans wajib diverifikasi menggunakan Signature Key sebelum diproses.

---

# Wallet

## BR-020 — Wallet Bukan Rekening Bank

Wallet merupakan representasi saldo virtual yang dikelola oleh sistem MergeShop.

---

## BR-021 — Saldo Tidak Boleh Negatif

Saldo Wallet tidak boleh bernilai negatif.

---

## BR-022 — Seluruh Perubahan Saldo Harus Dicatat

Setiap perubahan saldo wajib memiliki riwayat transaksi.

---

# Withdrawal

## BR-023 — Withdrawal Menggunakan Available Balance

Seller hanya dapat melakukan withdrawal menggunakan Available Balance.

---

## BR-024 — Minimum Withdrawal Mengikuti Penyedia Disbursement

Nominal minimum withdrawal mengikuti ketentuan penyedia layanan disbursement.

---

## BR-025 — Withdrawal Diproses Otomatis

Seluruh proses withdrawal dilakukan secara otomatis oleh Backend.

---

## BR-026 — Withdrawal Gagal Mengembalikan Saldo

Apabila transfer gagal dilakukan, saldo harus dikembalikan ke Wallet Seller.

---

## BR-027 — Withdrawal Memerlukan Rekening Aktif

Withdrawal tidak dapat dilakukan apabila Seller belum memiliki rekening aktif.

---

# AI

## BR-028 — Minjan Bersifat Global

Minjan memberikan informasi umum mengenai MergeShop.

---

## BR-029 — Bokul Bersifat Spesifik Toko

Bokul hanya memberikan informasi mengenai toko milik Seller terkait.

---

# Maps

## BR-030 — Lokasi Seller Harus Valid

Setiap Seller wajib memiliki koordinat lokasi yang valid sebelum toko dipublikasikan.

---

# Admin

## BR-031 — Admin Memiliki Hak Akses Penuh

Administrator memiliki hak akses terhadap seluruh modul sistem.

---

## BR-032 — Aktivitas Admin Dicatat

Seluruh aktivitas penting Administrator wajib dicatat pada Audit Log.