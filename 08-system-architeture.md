# 08. System Architecture

# Tujuan

Dokumen ini menjelaskan arsitektur sistem MergeShop secara keseluruhan.

Dokumen ini menjadi acuan dalam proses pengembangan frontend, backend, database, integrasi layanan pihak ketiga, serta deployment aplikasi.

---

# Arsitektur Sistem

MergeShop menggunakan arsitektur berbasis client-server dengan pemisahan yang jelas antara Frontend, Backend, Database, dan layanan pihak ketiga (Third-Party Services).

Sistem dikembangkan menggunakan pendekatan modular sehingga setiap fitur dapat dikembangkan secara independen tanpa mempengaruhi modul lainnya.

---

# Technology Stack

## Frontend

- Next.js
- TypeScript
- Tailwind CSS

---

## Backend

- NestJS
- TypeScript
- JWT Authentication
- Prisma ORM

---

## Database

- MySQL

---

## Third Party Services

- Midtrans
- Gemini API
- Google Maps API

---

# Frontend Architecture

Frontend menggunakan Next.js dengan pendekatan component-based architecture.

Struktur utama terdiri dari:

- Pages / App Router
- Components
- Features
- Hooks
- Services
- Types
- Utils

Seluruh komunikasi dengan Backend dilakukan menggunakan REST API.

Frontend tidak melakukan akses langsung ke database.

---

# Backend Architecture

Backend dikembangkan menggunakan NestJS dengan pendekatan Modular Architecture.

Setiap fitur utama memiliki module tersendiri.

Contoh:

- Auth Module
- User Module
- Seller Module
- Buyer Module
- Product Module
- Category Module
- Cart Module
- Order Module
- Payment Module
- Wallet Module
- Withdrawal Module
- Review Module
- AI Module
- Maps Module
- Notification Module
- Admin Module

Setiap module terdiri dari:

- Controller
- Service
- Repository (melalui Prisma)
- DTO
- Entity/Model
- Guards
- Interceptors
- Validators

---

# Authentication Flow

Autentikasi menggunakan JWT.

Alur autentikasi:

1. User melakukan login.
2. Backend memverifikasi email dan password.
3. Password dibandingkan menggunakan hash.
4. JWT Access Token dibuat.
5. Token dikirim ke Frontend.
6. Frontend menyimpan token.
7. Setiap request berikutnya membawa Authorization Header.
8. Backend melakukan verifikasi token sebelum memproses request.

---

# Authorization

MergeShop menggunakan Role-Based Access Control (RBAC).

Role yang tersedia:

- Buyer
- Seller
- Admin

Setiap endpoint memiliki guard yang menentukan role yang diizinkan mengakses endpoint tersebut.

---

# Database Layer

Backend menggunakan Prisma ORM sebagai penghubung antara aplikasi dan database MySQL.

Keuntungan penggunaan Prisma:

- Type-safe query
- Migration
- Relasi database lebih mudah dikelola
- Auto-generated TypeScript Client

Seluruh akses database dilakukan melalui Prisma.

Frontend tidak pernah berkomunikasi langsung dengan database.

---

# Payment Architecture

Pembayaran online diproses menggunakan Midtrans.

Alur pembayaran:

1. Buyer membuat Order.
2. Backend membuat transaksi Midtrans.
3. Midtrans mengembalikan Snap Token atau Payment URL.
4. Buyer melakukan pembayaran.
5. Midtrans mengirim Webhook ke Backend.
6. Backend memverifikasi Signature Key.
7. Status Payment diperbarui.
8. Status Order diperbarui.

---

# Wallet Architecture

MergeShop menggunakan Virtual Wallet.

Wallet bukan rekening bank.

Wallet merupakan representasi saldo Seller di dalam sistem.

Wallet memiliki dua jenis saldo:

- Pending Balance
- Available Balance

Pending Balance akan dipindahkan ke Available Balance apabila seluruh syarat bisnis telah terpenuhi.

---

# Withdrawal Architecture

Withdrawal diproses menggunakan layanan disbursement.

Alur:

1. Seller membuat Withdrawal Request.
2. Backend memvalidasi saldo.
3. Backend membuat Withdrawal Transaction.
4. Backend mengirim request ke Jack.
5. Jack mengirim hasil transfer.
6. Backend memperbarui status Withdrawal.
7. Wallet diperbarui.

---

# AI Architecture

MergeShop menggunakan Gemini API.

AI dibagi menjadi dua layanan.

## Minjan

Memberikan informasi umum mengenai:

- MergeShop
- Rekomendasi makanan
- Bantuan penggunaan aplikasi

## Bokul

Memberikan informasi khusus mengenai toko tertentu.

Prompt AI dibentuk menggunakan informasi toko milik Seller.

---

# Maps Architecture

Google Maps digunakan untuk:

- Menampilkan lokasi toko
- Menampilkan marker seluruh Seller
- Navigasi menuju toko
- Menampilkan toko terdekat

Lokasi toko disimpan menggunakan koordinat Latitude dan Longitude.

---

# Error Handling

Seluruh exception ditangani menggunakan Global Exception Filter.

Response error memiliki format yang konsisten.

Contoh:

- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 409 Conflict
- 500 Internal Server Error

---

# Logging

Backend mencatat aktivitas penting seperti:

- Login
- Register
- Payment
- Withdrawal
- Error
- Seller Verification

Logging digunakan untuk kebutuhan debugging dan audit.

---

# Security

Beberapa mekanisme keamanan yang diterapkan:

- HTTPS
- JWT Authentication
- Password Hashing
- Role Based Access Control
- Input Validation
- SQL Injection Protection
- XSS Protection
- Secret Management
- Webhook Signature Verification

---

# Scalability

Arsitektur dirancang agar mudah dikembangkan.

Strategi yang digunakan:

- Modular Backend
- Stateless API
- Service Layer
- Repository Pattern melalui Prisma
- Pemisahan Third-Party Service
- REST API

Pendekatan ini memungkinkan MergeShop dikembangkan menjadi platform yang lebih besar tanpa perlu melakukan perubahan arsitektur secara menyeluruh.

---

# Architecture Principles

MergeShop dikembangkan dengan prinsip-prinsip berikut:

- Separation of Concerns
- Modular Design
- Single Responsibility Principle
- DRY (Don't Repeat Yourself)
- Clean Architecture Principles
- Type Safety
- API First
- Security by Default
- Maintainability
- Scalability

---