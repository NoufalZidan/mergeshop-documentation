# 07. State Machines

Dokumen ini mendefinisikan seluruh state machine yang digunakan pada MergeShop.

State machine digunakan untuk memastikan setiap perubahan status pada sistem mengikuti aturan bisnis yang telah ditetapkan.

---

# Order State Machine

## States

- Pending Payment
- Paid
- Waiting Seller Confirmation
- Processing
- Ready for Pickup
- Out for Delivery
- Completed
- Cancelled

Pending Payment
        │
        ├───────────── Payment Failed ─────────────┐
        │                                          │
        ▼                                          ▼
Paid                                      Cancelled
        │
        ▼
Waiting Seller Confirmation
        │
        ├──────── Seller Cancel ───────────────┐
        │                                      │
        ▼                                      ▼
Processing                              Cancelled
   │
   ├──────────────┐
   ▼              ▼
Ready for     Out for
Pickup        Delivery
   │              │
   └───────┬──────┘
           ▼
Completed

| Current State               | Action           | Next State                  |
| --------------------------- | ---------------- | --------------------------- |
| Pending Payment             | Payment Success  | Paid                        |
| Pending Payment             | Payment Failed   | Cancelled                   |
| Paid                        | Seller Accept    | Waiting Seller Confirmation |
| Waiting Seller Confirmation | Start Processing | Processing                  |
| Waiting Seller Confirmation | Seller Cancel    | Cancelled                   |
| Processing                  | Pickup           | Ready for Pickup            |
| Processing                  | Delivery         | Out for Delivery            |
| Ready for Pickup            | Buyer Pickup     | Completed                   |
| Out for Delivery            | Delivered        | Completed                   |