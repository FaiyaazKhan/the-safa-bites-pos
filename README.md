# 🍽️ The Safa Bites (TSB) — Commercial Offline POS & Cloud Invoice System

![Vercel Status](https://img.shields.io/badge/Vercel-Deployed-black?logo=vercel)
![Electron](https://img.shields.io/badge/Electron-Desktop%20App-47848F?logo=electron)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react)
![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?logo=nodedotjs)
![SQLite](https://img.shields.io/badge/SQLite-Local%20Database-003B57?logo=sqlite)
![Redis](https://img.shields.io/badge/Upstash%20Redis-Serverless%20Cloud-FF4438?logo=redis)
![Platform](https://img.shields.io/badge/Platform-Windows%20x64-0078D6?logo=windows)

A commercial, production-grade Point-of-Sale (POS) and floor management desktop system built for **The Safa Bites (TSB)** restaurant. Features a 100% offline-first billing counter, real-time dining table state management, automated customer WhatsApp billing, and 24/7 permanent cloud receipt delivery via Vercel serverless edge functions.

---

## 🌐 Live Cloud Digital Invoice Demo

Experience the customer receipt interface live on mobile or desktop:  
👉 **[View Live Production Digital Invoice](https://thesafabites.vercel.app/invoice/TEST-ORD-888)**

*(Renders in under 50ms with Indian Standard Time formatting, itemized breakdown, and responsive mobile layout).*

---

## 🏗️ System Architecture

```
                       COUNTER LAPTOP (100% Offline-First)
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │  • React 19 + Tailwind CSS Frontend                                         │
 │  • Electron 40 Desktop Container (Windows .exe)                            │
 │  • Embedded Node.js Express API + Local SQLite 3 Database                   │
 │  • Instant zero-latency bill punching & KOT printing                        │
 │  • WhatsApp Web socket integration for silent background customer messaging │
 └──────────────────────────────────────┬──────────────────────────────────────┘
                                        │ Non-blocking background sync 
                                        │ on order finalization (Print & EBill)
                                        ▼
                      GLOBAL CLOUD EDGE (Vercel + Upstash Redis)
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │  • Permanent 24/7 Public URL: https://thesafabites.vercel.app               │
 │  • Serverless Node.js API Functions                                         │
 │  • Global In-Memory Redis Database (Mumbai AWS Region)                      │
 │  • Automatic 90-day retention & LRU eviction                                │
 └──────────────────────────────────────┬──────────────────────────────────────┘
                                        │ Customer taps WhatsApp receipt link
                                        ▼
                               CUSTOMER MOBILE PHONE
 ┌─────────────────────────────────────────────────────────────────────────────┐
 │  • Clean branded digital invoice                                            │
 │  • Works 24/7 even if restaurant counter laptop is powered OFF              │
 └─────────────────────────────────────────────────────────────────────────────┘
```

---

## ✨ Key Features & Engineering Highlights

### 1. 100% Offline-First Counter Operations
- The restaurant's billing never stops even during complete internet outages.
- Local SQLite database handles transactions, daily revenues, dish categories, and floor table memory directly on disk.

### 2. Dining Floor & Table Memory
- Interactive 12-table floor layout showing **Available**, **Occupied**, and **Saved** statuses in real-time.
- **Save (F1):** Cashier can lock items to a table draft without logging sales history or sending bills.
- **Accidental Switch Protection:** Unsaved table drafts are automatically wiped if the cashier navigates away, eliminating ghost orders.

### 3. Double-Click Order Finalization (F2 Protection)
- Cashier presses **Print & EBill (F2)** once to trigger a confirmation state: `⚠️ Confirm & Bill (F2)`.
- Prevents accidental bill closure during peak rush hours.
- Second press writes the completed sale into history, frees the table, and dispatches the customer WhatsApp message.

### 4. Automated WhatsApp Web Delivery
- Integrated directly with WhatsApp Web sockets.
- When an order is completed, the receipt text and permanent cloud link are sent automatically in the background without opening browser tabs.

### 5. Instant Analytics & Sales Intelligence
- Daily, Weekly, and Monthly revenue breakdowns.
- Cash vs. UPI split, average ticket size, and Top-selling dishes reports.
- One-click CSV / Excel export and printable summary reports.

---

## 🔒 Commercial Notice & IP Protection

> **Proprietary Commercial Software**  
> The core source code, desktop application binaries, and proprietary business logic are maintained in a private commercial repository.  
> Architecture walkthroughs and technical system design discussions are available upon request for interview and verification purposes.

---

## 👨‍💻 Author

**Faiyaaz Khan**  
- GitHub: [@FaiyaazKhan](https://github.com/FaiyaazKhan)  
- Production Deployment: [thesafabites.vercel.app](https://thesafabites.vercel.app)

