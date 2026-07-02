# 03. Functional Requirements

Dokumen ini menjelaskan seluruh kebutuhan fungsional (Functional Requirements) yang harus dipenuhi oleh sistem MergeShop.

Setiap requirement memiliki identitas unik agar mudah ditelusuri selama proses pengembangan, pengujian, maupun pemeliharaan sistem.

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