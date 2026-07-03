# MergeShop

> Dokumentasi teknis dan arsitektur sistem **MergeShop**, sebuah platform e-commerce hyperlocal yang berfokus pada digitalisasi UMKM kuliner di Purwokerto.

## Tentang Proyek

MergeShop adalah platform e-commerce hyperlocal yang dirancang untuk menghubungkan masyarakat dengan berbagai UMKM kuliner di wilayah Purwokerto. Platform ini memungkinkan pengguna menemukan, memesan, dan membayar makanan secara online dengan pengalaman yang cepat, mudah, dan terintegrasi.

Berbeda dengan marketplace pada umumnya, MergeShop mengutamakan ekosistem kuliner lokal melalui berbagai fitur yang dirancang khusus untuk kebutuhan UMKM, termasuk dashboard penjual, sistem wallet, penarikan dana (withdraw), integrasi payment gateway, hingga pemanfaatan Artificial Intelligence (AI) sebagai asisten pelanggan.

Repository ini berisi seluruh dokumentasi teknis, perancangan sistem, keputusan arsitektur, serta proses pengembangan MergeShop.

---

## Status Proyek

**Sedang dalam tahap pengembangan (Development)**

Seluruh fitur utama sedang dirancang dan dikembangkan secara bertahap.

---

## Target Pengguna

### Pembeli

Seluruh masyarakat yang ingin membeli makanan dari UMKM kuliner di wilayah Purwokerto.

### Penjual

UMKM kuliner di Purwokerto yang ingin memasarkan produknya secara digital.

### Administrator

Mengelola keseluruhan operasional platform, data pengguna, transaksi, dan aktivitas marketplace.

---

## Fitur Utama

- Multi-vendor marketplace
- Sistem transaksi online
- Dashboard Penjual
- Dashboard Admin
- Wallet & Seller Withdrawal
- Integrasi Midtrans Payment Gateway & Disbursement API
- Geolocation & Maps
- Manajemen Produk
- Manajemen Pesanan
- AI Chatbot

---

## AI Assistant

MergeShop memiliki dua AI Assistant yang dirancang untuk membantu pengalaman pengguna.

### Minjan (Mimin Jajan)

Asisten AI pada halaman utama yang membantu pengguna menemukan rekomendasi makanan berdasarkan preferensi dan kebutuhan mereka.

---

### Bokul (Bot Bakul)

Asisten AI yang tersedia pada setiap halaman toko penjual.

Bokul dipersonalisasi untuk masing-masing UMKM sehingga mampu membantu pelanggan menjawab pertanyaan mengenai produk, memberikan rekomendasi menu, serta meningkatkan interaksi antara penjual dan pembeli.

---

## Tech Stack

### Frontend

- Next.js
- TypeScript

### Backend

- NestJS
- TypeScript

### Database

- MySQL

---

## Third Party Services

- Midtrans (Payment Gateway & Disbursement API)

---

## Isi Dokumentasi

Repository ini berisi dokumentasi mengenai:

- Project Overview
- Requirement Analysis
- System Architecture
- Database Design
- Business Rules
- Payment System
- Wallet System
- Withdrawal System
- API Design
- Security
- Deployment
- Architecture Decision Records (ADR)
- Diagrams
- Future Improvements

---

## Tujuan Dokumentasi

Repository ini dibuat sebagai dokumentasi teknis selama proses pengembangan MergeShop sehingga setiap keputusan arsitektur, desain sistem, dan implementasi dapat terdokumentasi dengan baik serta mudah dipahami oleh anggota tim maupun developer lain di masa mendatang.
