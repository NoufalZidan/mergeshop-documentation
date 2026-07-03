# 09. Database Design

# Tujuan

Dokumen ini menjelaskan desain database MergeShop.

Dokumen ini menjadi acuan dalam pembuatan schema database, Prisma ORM, migrasi database, implementasi backend, serta pengembangan fitur baru.

Database yang digunakan adalah **MySQL** dengan **Prisma ORM** sebagai Object Relational Mapping (ORM).

---

# Design Principles

Database MergeShop dirancang dengan prinsip berikut:

- Normalisasi hingga minimal Third Normal Form (3NF)
- Menggunakan Primary Key berupa UUID
- Foreign Key untuk menjaga integritas relasi
- Soft Delete untuk data penting
- Timestamp pada seluruh tabel utama
- Auditability untuk data kritikal
- Konsistensi penamaan

---

# Naming Convention

## Table

Menggunakan bentuk jamak.

Contoh:

- users
- products
- orders
- reviews

---

## Primary Key

Seluruh tabel menggunakan:

id

bertipe UUID.

---

## Foreign Key

Menggunakan format:

entityId

Contoh:

sellerId

buyerId

productId

orderId

---

## Timestamp

Seluruh tabel utama memiliki:

createdAt

updatedAt

Beberapa tabel juga memiliki:

deletedAt

---

# Database Modules

Database dibagi menjadi beberapa kelompok utama.

- Authentication
- User
- Seller
- Product
- Category
- Cart
- Order
- Payment
- Wallet
- Withdrawal
- Review
- AI
- Maps
- Notification

---

# Authentication Module

## users

Menyimpan seluruh akun sistem.

Kolom:

- id
- fullName
- email
- passwordHash
- role
- profilePicture
- createdAt
- updatedAt

Relasi:

- One-to-One → buyer_profiles
- One-to-One → seller_profiles

---

# Buyer Module

## buyer_profiles

Menyimpan informasi Buyer.

Kolom:

- id
- userId
- address
- latitude
- longitude
- createdAt
- updatedAt

Relasi:

- Belongs to users

---

# Seller Module

## seller_profiles

Kolom:

- id
- userId
- storeName
- description
- phoneNumber
- address
- latitude
- longitude
- logoUrl
- verificationStatus
- createdAt
- updatedAt

Relasi:

- Belongs to users

---

## seller_bank_accounts

Kolom:

- id
- sellerId
- bankCode
- accountNumber
- accountHolder
- isActive
- createdAt

Relasi:

- Belongs to seller_profiles

Catatan:

Satu Seller hanya boleh memiliki satu rekening aktif.

---

# Category Module

## categories

Kolom:

- id
- name
- icon
- createdAt

---

# Product Module

## products

Kolom:

- id
- sellerId
- categoryId
- name
- description
- price
- imageUrl
- availability
- ratingAverage
- reviewCount
- createdAt
- updatedAt

Relasi:

- Belongs to seller_profiles
- Belongs to categories

---

## favorite_products

Kolom:

- buyerId
- productId
- createdAt

Relasi:

Many-to-Many

Buyer ↔ Product

---

# Cart Module

## carts

Kolom:

- id
- buyerId
- sellerId
- createdAt

---

## cart_items

Kolom:

- id
- cartId
- productId
- quantity
- note

---

# Order Module

## orders

Kolom:

- id
- buyerId
- sellerId
- paymentId
- subtotal
- serviceFee
- totalPrice
- deliveryMethod
- paymentMethod
- note
- status
- estimatedTime
- createdAt
- updatedAt

---

## order_items

Kolom:

- id
- orderId
- productId
- productName
- price
- quantity
- note

Catatan:

Nama produk dan harga disalin agar histori tetap konsisten meskipun Seller mengubah produk.

---

# Payment Module

## payments

Kolom:

- id
- orderId
- provider
- providerTransactionId
- amount
- status
- paidAt
- createdAt

---

## payment_logs

Kolom:

- id
- paymentId
- rawWebhook
- createdAt

Digunakan untuk audit webhook Midtrans.

---

# Wallet Module

## wallets

Kolom:

- id
- sellerId
- pendingBalance
- availableBalance
- totalWithdrawn
- updatedAt

---

## wallet_transactions

Kolom:

- id
- walletId
- type
- amount
- referenceId
- description
- createdAt

Type:

- CREDIT
- DEBIT

---

# Withdrawal Module

## withdrawals

Kolom:

- id
- walletId
- bankAccountId
- amount
- provider
- providerReference
- status
- createdAt
- completedAt

Status:

- Processing
- Completed
- Failed

---

# Review Module

## reviews

Kolom:

- id
- orderId
- buyerId
- sellerId
- productId
- rating
- review
- createdAt

---

# AI Module

## seller_ai_settings

Kolom:

- id
- sellerId
- prompt
- updatedAt

---

# Notification Module

## notifications

Kolom:

- id
- userId
- title
- message
- isRead
- createdAt

---

# Audit Module

## audit_logs

Kolom:

- id
- userId
- action
- entity
- entityId
- ipAddress
- createdAt

---

# Relationship Summary

users

↓

buyer_profiles

↓

orders

↓

order_items

↓

products

↓

categories

---

users

↓

seller_profiles

↓

products

↓

reviews

↓

wallets

↓

withdrawals

---

# Index Recommendation

Index yang direkomendasikan:

users

- email

products

- sellerId
- categoryId
- name

orders

- buyerId
- sellerId
- status

payments

- orderId
- status

wallet_transactions

- walletId

notifications

- userId
- isRead

---

# Soft Delete

Soft Delete digunakan pada:

- users
- seller_profiles
- products
- categories

Kolom:

deletedAt

---

# Data Integrity Rules

- Email harus unik.
- Satu Seller hanya memiliki satu Wallet.
- Satu Wallet hanya dimiliki satu Seller.
- Satu Seller hanya memiliki satu rekening aktif.
- Order wajib memiliki minimal satu Order Item.
- Review hanya dapat dibuat setelah Order selesai.
- Wallet tidak boleh memiliki saldo negatif.
- Semua Foreign Key wajib tervalidasi.
- Semua transaksi penting menggunakan Database Transaction.

---

# Future Database Expansion

Database dirancang agar mudah dikembangkan untuk fitur berikut:

- Promo
- Voucher
- Diskon
- Multi Address Buyer
- Multi Cabang Seller
- Multi Kurir
- E-Wallet Withdrawal
- Seller Analytics
- AI Conversation History
- Push Notification
- Recommendation Engine

---