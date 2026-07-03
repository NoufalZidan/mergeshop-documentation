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

---

# Payment State Machine

## States

- Pending
- Paid
- Failed
- Expired
- Cancelled

| Current | Event   | Next      |
| ------- | ------- | --------- |
| Pending | Success | Paid      |
| Pending | Failed  | Failed    |
| Pending | Expired | Expired   |
| Pending | Cancel  | Cancelled |

---

# Seller Verification

## States

- Pending
- Approved
- Rejected

| Current  | Action       | Next     |
| -------- | ------------ | -------- |
| Pending  | Approve      | Approved |
| Pending  | Reject       | Rejected |
| Rejected | Submit Again | Pending  |

---

# Withdrawal State Machine

## States

- Processing
- Completed
- Failed

| Current    | Event   | Next      |
| ---------- | ------- | --------- |
| Processing | Success | Completed |
| Processing | Failed  | Failed    |

---

# Product Availability

## States

| Current  | Action | Next     |
| -------- | ------ | -------- |
| Tersedia | Toggle | Habis    |
| Habis    | Toggle | Tersedia |

---

# Notification State Machine

## States

| Current | Action            | Next |
| ------- | ----------------- | ---- |
| Unread  | Open Notification | Read |

---