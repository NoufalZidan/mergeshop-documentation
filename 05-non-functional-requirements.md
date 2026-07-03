# 05. Non-Functional Requirements

## Tujuan

Dokumen ini mendefinisikan kebutuhan non-fungsional pada MergeShop.

Kebutuhan non-fungsional menjelaskan standar kualitas sistem yang harus dipenuhi selama proses pengembangan maupun operasional aplikasi.

---

# Kategori

- Performance
- Availability
- Reliability
- Security
- Scalability
- Maintainability
- Usability
- Accessibility
- Compatibility
- Logging
- Backup & Recovery

---

# Performance

## NFR-001 — Waktu Respons Halaman

Sebagian besar halaman harus dapat dimuat dalam waktu kurang dari **3 detik** pada koneksi internet normal.

Priority:
High

---

## NFR-002 — Waktu Respons API

Sebagian besar endpoint API harus memberikan respons dalam waktu kurang dari **500 ms** untuk request normal.

Priority:
High

---

## NFR-003 — Pagination

Seluruh data yang berpotensi memiliki jumlah besar wajib menggunakan pagination.

Contoh:

- Produk
- Order
- Seller
- Buyer
- Review
- Withdrawal

Priority:
High

---

## NFR-004 — Lazy Loading

Gambar dan komponen berat sebaiknya menggunakan lazy loading.

Priority:
Medium

---

## NFR-005 — Optimasi Query Database

Query database harus dioptimalkan untuk menghindari proses yang tidak efisien.

Priority:
High

---

# Availability

## NFR-006 — Ketersediaan Sistem

Target ketersediaan sistem minimal **99%** selama periode operasional.

Priority:
Medium

---

## NFR-007 — Graceful Error

Apabila terjadi kegagalan layanan eksternal (Midtrans, Jack, Gemini API), sistem tetap dapat berjalan untuk fitur yang tidak bergantung pada layanan tersebut.

Priority:
High

---

# Reliability

## NFR-008 — Konsistensi Data

Seluruh transaksi penting harus menggunakan database transaction untuk menjaga konsistensi data.

Contoh:

- Checkout
- Payment
- Withdrawal

Priority:
High

---

## NFR-009 — Idempotent Webhook

Webhook dari Midtrans hanya boleh diproses satu kali meskipun dikirim ulang.

Priority:
High

---

# Security

## NFR-010 — Password Hashing

Password wajib disimpan menggunakan algoritma hashing yang aman (misalnya Argon2 atau bcrypt).

Priority:
Critical

---

## NFR-011 — HTTPS

Seluruh komunikasi antara client dan server harus menggunakan HTTPS.

Priority:
Critical

---

## NFR-012 — JWT Authentication

Endpoint yang memerlukan autentikasi wajib menggunakan JWT.

Priority:
High

---

## NFR-013 — Role Based Access Control

Hak akses harus dibatasi berdasarkan role:

- Buyer
- Seller
- Admin

Priority:
Critical

---

## NFR-014 — Validasi Input

Seluruh input pengguna wajib divalidasi di Backend.

Priority:
Critical

---

## NFR-015 — SQL Injection Protection

Sistem harus terlindungi dari SQL Injection.

Priority:
Critical

---

## NFR-016 — XSS Protection

Sistem harus meminimalkan risiko Cross Site Scripting (XSS).

Priority:
High

---

## NFR-017 — CSRF Protection

Endpoint yang rentan terhadap CSRF harus memiliki mekanisme perlindungan yang sesuai.

Priority:
High

---

## NFR-018 — Secret Management

API Key, JWT Secret, Database Password, dan kredensial lainnya tidak boleh disimpan di source code.

Priority:
Critical

---

## NFR-019 — Audit Log

Aktivitas Administrator harus dicatat.

Priority:
Medium

---

# Scalability

## NFR-020 — Stateless Backend

Backend dirancang agar dapat dijalankan pada beberapa instance tanpa bergantung pada session lokal.

Priority:
Medium

---

## NFR-021 — Modular Architecture

Backend harus menggunakan arsitektur modular agar mudah dikembangkan.

Priority:
High

---

## NFR-022 — External Service Isolation

Integrasi dengan Midtrans, Jack, Gemini API, dan Google Maps dipisahkan ke dalam service/module tersendiri.

Priority:
High

---

# Maintainability

## NFR-023 — Clean Code

Kode program harus mengikuti standar clean code.

---

## NFR-024 — Type Safety

Seluruh project menggunakan TypeScript.

---

## NFR-025 — Documentation

API, database, dan arsitektur sistem harus terdokumentasi.

---

## NFR-026 — Consistent Naming

Penamaan file, variabel, tabel, endpoint, dan module harus konsisten.

---

# Usability

## NFR-027 — Responsive Design

Website harus dapat digunakan pada desktop, tablet, maupun smartphone.

---

## NFR-028 — Simple UI

Antarmuka dirancang sederhana agar mudah digunakan oleh seluruh kalangan masyarakat.

---

## NFR-029 — Consistent Design System

Seluruh halaman menggunakan design system yang konsisten.

---

# Accessibility

## NFR-030 — Keyboard Navigation

Seluruh fitur utama dapat diakses menggunakan keyboard.

---

## NFR-031 — Semantic HTML

Komponen harus menggunakan elemen HTML yang semantik.

---

## NFR-032 — Color Contrast

Kontras warna harus cukup agar mudah dibaca.

---

# Compatibility

## NFR-033 — Browser Support

Aplikasi mendukung versi terbaru browser modern seperti:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Safari

---

## NFR-034 — Responsive Device

Website dapat berjalan pada berbagai ukuran layar.

---

# Logging

## NFR-035 — Application Log

Backend harus mencatat error penting.

---

## NFR-036 — API Log

Request penting dapat dicatat untuk kebutuhan debugging.

---

## NFR-037 — Error Monitoring

Error yang bersifat kritis harus mudah dilacak melalui sistem logging.

---

# Backup & Recovery

## NFR-038 — Database Backup

Database harus dibackup secara berkala.

---

## NFR-039 — Recovery

Database harus dapat dipulihkan dari backup apabila terjadi kegagalan.

---

## NFR-040 — Backup Verification

Backup harus diuji secara berkala untuk memastikan dapat digunakan saat proses pemulihan.