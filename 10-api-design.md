# 10. API Design

# Tujuan

Dokumen ini menjelaskan desain REST API yang digunakan oleh MergeShop.

Dokumen ini menjadi acuan implementasi Backend (NestJS) dan integrasi Frontend (Next.js).

Seluruh endpoint menggunakan format JSON dan mengikuti prinsip RESTful API.

---

# Base URL

Development

```
http://localhost:3000/api/v1
```

Production

```
https://api.mergeshop.id/api/v1
```

---

# Authentication

MergeShop menggunakan JWT Authentication.

Endpoint yang memerlukan autentikasi wajib mengirimkan:

Authorization

```
Bearer <access_token>
```

---

# Standard Response

## Success

```json
{
  "success": true,
  "message": "Success",
  "data": {}
}
```

---

## Error

```json
{
  "success": false,
  "message": "Validation Error",
  "errors": []
}
```

---

# HTTP Status Code

| Status | Keterangan |
|---------|------------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 422 | Validation Error |
| 500 | Internal Server Error |

---

# API Modules

- Authentication
- User
- Seller
- Buyer
- Category
- Product
- Favorite
- Cart
- Order
- Payment
- Wallet
- Withdrawal
- Review
- AI
- Notification
- Admin

---

# Authentication API

## Register

POST

```
/auth/register
```

Body

```json
{
  "fullName": "",
  "email": "",
  "password": "",
  "role": "BUYER"
}
```

---

## Login

POST

```
/auth/login
```

Body

```json
{
  "email": "",
  "password": ""
}
```

Response

```json
{
  "accessToken": "",
  "user": {}
}
```

---

## Forgot Password

POST

```
/auth/forgot-password
```

---

## Reset Password

POST

```
/auth/reset-password
```

---

## Logout

POST

```
/auth/logout
```

---

# User API

## Get Profile

GET

```
/users/me
```

---

## Update Profile

PUT

```
/users/me
```

---

## Change Password

PATCH

```
/users/change-password
```

---

# Seller API

## Get Store Profile

GET

```
/seller/profile
```

---

## Update Store Profile

PUT

```
/seller/profile
```

---

## Upload Store Logo

POST

```
/seller/logo
```

---

## Get Dashboard

GET

```
/seller/dashboard
```

---

# Category API

## Get Categories

GET

```
/categories
```

---

## Create Category

POST

```
/categories
```

Admin Only

---

## Update Category

PUT

```
/categories/{id}
```

---

## Delete Category

DELETE

```
/categories/{id}
```

---

# Product API

## Get Products

GET

```
/products
```

Query

- page
- limit
- search
- category
- seller
- radius

---

## Get Product Detail

GET

```
/products/{id}
```

---

## Create Product

POST

```
/products
```

---

## Update Product

PUT

```
/products/{id}
```

---

## Delete Product

DELETE

```
/products/{id}
```

---

## Toggle Availability

PATCH

```
/products/{id}/availability
```

---

# Favorite API

## Add Favorite

POST

```
/favorites
```

---

## Remove Favorite

DELETE

```
/favorites/{productId}
```

---

## Get Favorites

GET

```
/favorites
```

---

# Cart API

## Get Cart

GET

```
/cart
```

---

## Add Item

POST

```
/cart/items
```

---

## Update Quantity

PATCH

```
/cart/items/{id}
```

---

## Remove Item

DELETE

```
/cart/items/{id}
```

---

## Clear Cart

DELETE

```
/cart
```

---

# Order API

## Checkout

POST

```
/orders/checkout
```

---

## Get Orders

GET

```
/orders
```

---

## Get Order Detail

GET

```
/orders/{id}
```

---

## Cancel Order

PATCH

```
/orders/{id}/cancel
```

---

## Update Status

PATCH

```
/orders/{id}/status
```

Seller Only

---

# Payment API

## Create Payment

POST

```
/payments
```

---

## Payment Webhook

POST

```
/payments/webhook
```

Midtrans Only

---

## Payment Detail

GET

```
/payments/{id}
```

---

# Wallet API

## Get Wallet

GET

```
/wallet
```

---

## Wallet History

GET

```
/wallet/transactions
```

---

# Withdrawal API

## Create Withdrawal

POST

```
/withdrawals
```

---

## Get Withdrawals

GET

```
/withdrawals
```

---

## Get Withdrawal Detail

GET

```
/withdrawals/{id}
```

---

## Get Bank Accounts

GET

```
/withdrawals/bank-accounts
```

---

## Add Bank Account

POST

```
/withdrawals/bank-accounts
```

---

## Update Bank Account

PUT

```
/withdrawals/bank-accounts/{id}
```

---

## Delete Bank Account

DELETE

```
/withdrawals/bank-accounts/{id}
```

---

# Review API

## Create Review

POST

```
/reviews
```

---

## Update Review

PUT

```
/reviews/{id}
```

---

## Delete Review

DELETE

```
/reviews/{id}
```

---

# AI API

## Minjan

POST

```
/ai/minjan
```

---

## Bokul

POST

```
/ai/bokul/{sellerId}
```

---

## Update Bokul Prompt

PUT

```
/ai/bokul/settings
```

Seller Only

---

# Notification API

## Get Notifications

GET

```
/notifications
```

---

## Read Notification

PATCH

```
/notifications/{id}/read
```

---

## Read All

PATCH

```
/notifications/read-all
```

---

# Admin API

## Dashboard

GET

```
/admin/dashboard
```

---

## Verify Seller

PATCH

```
/admin/sellers/{id}/verify
```

---

## Reject Seller

PATCH

```
/admin/sellers/{id}/reject
```

---

## Get Users

GET

```
/admin/users
```

---

## Get Orders

GET

```
/admin/orders
```

---

## Get Withdrawals

GET

```
/admin/withdrawals
```

---

## Analytics

GET

```
/admin/analytics
```

---

# Pagination

Endpoint yang mengembalikan daftar data menggunakan format berikut.

Response

```json
{
  "success": true,
  "data": [],
  "pagination": {
    "page": 1,
    "limit": 20,
    "totalItems": 150,
    "totalPages": 8
  }
}
```

---

# Filtering

Contoh

```
GET /products?page=1&limit=20&search=ayam&category=1
```

---

# Sorting

Contoh

```
GET /products?sort=price&order=asc
```

---

# Error Handling

Seluruh endpoint menggunakan format error yang konsisten.

```json
{
  "success": false,
  "message": "Validation Error",
  "errors": [
    {
      "field": "email",
      "message": "Email sudah digunakan"
    }
  ]
}
```

---

# API Versioning

Seluruh endpoint menggunakan versioning.

Contoh

```
/api/v1/products
```

Apabila terjadi breaking changes, versi baru akan dibuat.

Contoh

```
/api/v2/products
```

---

# Security

Seluruh endpoint menerapkan:

- JWT Authentication
- Role-Based Access Control (RBAC)
- Input Validation
- Rate Limiting
- CORS
- HTTPS
- Request Validation
- Webhook Signature Verification