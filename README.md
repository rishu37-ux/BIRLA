# UltraTech Cement Ltd. - Unit Birla White ERP
### Sales & Distribution Enterprise Resource Planning System

![Birla White Logo](frontend/src/assets/birlaabg.svg)

A complete, production-ready full-stack **Sales & Distribution ERP System** built for **UltraTech Cement Ltd. (Unit: Birla White)**, Aditya Birla Group.

---

## 🏛️ Executive Summary & Key Highlights

This ERP system manages the end-to-end sales, distribution, order booking, blind drop-shipping dual-receipt generation, partial dispatch fulfillment, and live credit ageing for Birla White's regional operations in **Himachal Pradesh** (Mandi, Sundernagar, Joginder Nagar, Balh, and surrounding commercial belts).

### Default Territory Executive Profile (Pre-filled & Printed on All Invoices)
- **Officer Name & ID:** `Suraj (PZ7550)`
- **Mobile Number:** `8219796922`
- **Official Email:** `suraj-v@adityabirla.com`
- **Operating Unit:** `UltraTech Cement Ltd. - Unit Birla White`

---

## 🚀 Tech Stack Architecture

| Layer | Technologies Used |
| :--- | :--- |
| **Frontend** | React 18, Vite 6, Tailwind CSS 3, Lucide Icons, Recharts (BI Analytics) |
| **Backend** | Node.js (v24), Express.js (v4), REST API architecture |
| **Database & ORM** | PostgreSQL 18, Prisma ORM 6 (Active Connection: `birla_white_erp`) |
| **Receipts & PDFs** | PDFKit Vector Engine (Dual Receipts, Split Challans, Money Receipts) |
| **Branding & Assets** | Official Aditya Birla & Birla White SVG vector brand marks (`birlaabg.svg`) |

---

## 📦 Core Modules & System Workflows

### 1. Master Management (Separate Lists for Stockists & Retailers)
- **Two Independent Registries:** Completely separated tabs and database tables for **Stockists** (Distributors/Depots) and **Retailers** (Hardware Stores/Painters/Dealers).
- **Mandatory Structured Address Fields:**
  - District (e.g., Mandi, Kangra, Shimla)
  - Tehsil (e.g., Sundernagar, Mandi Sadar, Joginder Nagar)
  - Sub-Tehsil (e.g., Nihri, Kotli, Baldwara)
  - Locality / Market Area (e.g., Cinema Chowk, Bhojpur Bazaar, NH-21 Depot)
  - PIN Code (e.g., 175002, 175019)
- **Firm Details:** Firm Name, GSTIN, Proprietor/Owner Name, Contact Mobile, Credit Limits, and Credit Days.
- **Stockist-to-Retailer Mapping:** Retailers can have an assigned primary stockist for rapid order dispatch.
- **Global Actions:** Full **Edit / Modify / Delete** actions with interactive confirmation modals.

### 2. Product Catalogue & Dynamic Unit Master
- **Supported Packaging Unit Types:**
  - `Bag` (e.g. WallCare Putty 40kg, White Cement 50kg, Levelplast 30kg)
  - `Bucket` (e.g. Extocare Primer 20L, PrimaCoat 20L, Bio-Shield Putty 10L)
  - `Box` (e.g. Grout Master 5kg Box, Wall Seal 4L Box)
  - `PCS` (e.g. Texture Roller Kit)
  - `Manual` (Custom user-defined text input, e.g. *Metric Ton (MT)* for pneumatic bulk road tankers)
- **Unit Weights:** Weight specified in `Kg` or `Ltr`.
- **Pricing:** Reference Unit Price (Catalogue base price) with individual GST rates (18% / 28%).
- **Full CRUD:** Real-time adding, editing, and deleting of products with confirmation dialogs.

### 3. Order Creation & Dynamic Rate Override
- **Stockist-to-Retailer Mapping:** Select any Stockist and assign any Retailer to fulfill the order.
- **Custom Selectable Dates:** Order date defaults to today with an option to select any custom date.
- **Site Delivery Information:** Location of Delivery (Site Address), Contact Person Name, and Mobile Number.
- **Pre-filled Confirmed By:** Default pre-filled with `Suraj (PZ7550)`, phone `8219796922`, email `suraj-v@adityabirla.com`.
- **Line Items & Manual Rate Entry:**
  - Displays the product's **Catalogue Reference Price** on screen for transparent comparison.
  - Allows salesperson to enter the **actual negotiated Unit Rate** per retailer.
  - Automatically calculates subtotal, GST per line item, and grand total.

### 4. Dual-Receipt Generation (Blind Drop-Shipping Logic)
Upon confirming an order, two distinct printable and downloadable PDF receipts are generated:
1. **Retailer Order Confirmation Receipt:**
   - **STRICTLY HIDES** all Stockist details (no stockist name, firm, contact, or address).
   - Features official UltraTech / Birla White corporate header, retailer billing details, negotiated rates, delivery site information, and `Suraj (PZ7550)` credentials.
2. **Stockist Order Confirmation Receipt:**
   - Displays **complete Retailer details** (Firm Name, GST, Owner Name, Mobile, full District/Tehsil/Locality/PIN address) so the warehouse knows exactly who to dispatch to, along with dispatch verification checkboxes.

### 5. Order History, Order Status & Partial Fulfillment Engine
- **Two Status Layers:**
  - **State:** `Active` / `Inactive`
  - **Fulfillment Status:** `Full` / `Partial` / `Out of Stock`
- **Delivery Tracking:** Delivery Date field and a one-click **"Mark as Delivered Successfully"** button.
- **Partial Dispatch Workflow:**
  - If status is `Partial`, requires a mandatory **Reason** text field (e.g. Transporter vehicle load exceeded, Plant stock lot inspection).
  - Item-by-item entry of **Dispatched Quantity** vs. **Pending Quantity**.
  - Auto-calculates two separate financial totals with GST:
    1. **Dispatched Bill Amount** (value of goods going out).
    2. **Pending Bill Amount** (value of goods remaining).
- **Stage-Specific Split Receipts:**
  - **Stage 1: Dispatched Delivery Challan** (downloadable PDF showing dispatched items and billing value).
  - **Stage 2: Pending Backorder & Balance Slip** (downloadable PDF showing remaining items, pending amount, and reason).

### 6. Payment & Receipt Section + Retailer Ledger
- **Payment Entry:**
  - Linked to specific Retailers and Orders (or general running accounts).
  - Payment Modes: `Cash`, `UPI`, `Cheque`, `Online`.
  - **Mandatory Cheque Date:** If `Cheque` is selected, requires a mandatory Cheque Date field.
  - Generates downloadable official **Payment Receipts** with receipt number, UTR/Cheque ref, and remaining balance.
- **Retailer Ledger & Live Ageing / Overdue Tracker:**
  - Full Paid vs. Unpaid summary per Retailer.
  - **Live Overdue Counter:** Calculates exact `Due Days` (e.g., *15 Days Due*, *27 Days Due*) past the credit limit and highlights overdue balances in red.
  - **Grouped by Created By:** Tracks total order portfolio value grouped by Territory Sales Officer.

### 7. Command Center Dashboard & BI Performance Tracker
- **Main Command Center:** High-level KPI cards for Total Sales, Dispatched Value, Pending Value, Total Collected, and Overdue Amount.
- **BI Performance Tracker:**
  - Timeframe Filters: **Monthly**, **Quarterly**, **Half-Yearly**, and **Annually**.
  - **Payment-wise Breakdown:** Realized vs. Due amount bar chart, and Payment Mode distribution pie chart.
  - **Product-wise Breakdown:** Top-selling products by revenue bar chart, and volume distribution by packaging unit (Bag, Bucket, Box, PCS, Manual).
- **PJP (Permanent Journey Plan):**
  - Beat schedule by date, retailer, and location (Tehsil/Locality).
  - Visit status tracking (`Scheduled`, `Completed`, `Order Booked`, `Payment Collected`).
  - Logs discussion notes, booked order amount, and collected payments during field visits.

---

## 🛠️ Installation & Setup Instructions

### Prerequisites
- Node.js v18+ (tested on Node v24)
- PostgreSQL 14+ (installed and running locally on port 5432)

### 1. Database Setup
Ensure PostgreSQL is running and create the database `birla_white_erp`:
```bash
# Using psql
psql -U postgres -c "CREATE DATABASE birla_white_erp;"
```

### 2. Backend Setup
```bash
cd backend

# Create .env file with your database connection string
# Example:
PORT=5000
DATABASE_URL="postgresql://postgres@localhost:5432/birla_white_erp"
NODE_ENV=development

# Install dependencies
npm install

# Push Prisma schema to PostgreSQL
npm run prisma:push

# Seed Himachal Pradesh (Mandi, Sundernagar, Joginder Nagar) sample data
npm run prisma:seed

# Start backend server
npm start
# or development with auto-reload:
npm run dev
```

### 3. Frontend Setup
```bash
cd frontend

# Install dependencies
npm install

# Start Vite development server
npm run dev
# Running on http://localhost:5173
```

---

## 📜 API Route Endpoints Reference

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/health` | Service health and default user metadata |
| `GET` | `/api/stockists` | List all stockists with search and filters |
| `POST` | `/api/stockists` | Create stockist with structured address |
| `PUT` | `/api/stockists/:id` | Update stockist details |
| `DELETE` | `/api/stockists/:id` | Delete stockist (with active order check) |
| `GET` | `/api/retailers` | List all retailers with mapped stockists |
| `POST` | `/api/retailers` | Create retailer with structured address |
| `PUT` | `/api/retailers/:id` | Update retailer details |
| `DELETE` | `/api/retailers/:id` | Delete retailer (with active order check) |
| `GET` | `/api/products` | List catalogue products with category/unit filters |
| `POST` | `/api/products` | Create product (Bag/Bucket/Box/PCS/Manual) |
| `PUT` | `/api/products/:id` | Update product details |
| `DELETE` | `/api/products/:id` | Delete product |
| `GET` | `/api/orders` | List sales orders with status and date filters |
| `POST` | `/api/orders` | Book order (manual rates, line items, auto GST) |
| `PUT` | `/api/orders/:id/deliver` | One-click mark as delivered successfully |
| `GET` | `/api/orders/:id/receipt/retailer` | Stream Retailer PDF receipt (Hides Stockist) |
| `GET` | `/api/orders/:id/receipt/stockist` | Stream Stockist PDF receipt (Shows Retailer) |
| `POST` | `/api/dispatches/orders/:id/dispatch` | Process Full / Partial / OOS dispatch with reason |
| `GET` | `/api/dispatches/:id/receipt/dispatched` | Stream Dispatched Goods Challan PDF |
| `GET` | `/api/dispatches/:id/receipt/pending` | Stream Pending Backorder Slip PDF |
| `GET` | `/api/payments/ledger/summary` | Retailer ledger & live ageing due days tracker |
| `POST` | `/api/payments` | Record payment (requires Cheque Date if Cheque) |
| `GET` | `/api/payments/:id/receipt` | Stream Payment Money Receipt PDF |
| `GET` | `/api/analytics/dashboard` | Main Command Center KPI metrics |
| `GET` | `/api/analytics/bi?timeframe=...` | Timeframe BI analytics (Monthly/Quarterly/Annual) |
| `GET` | `/api/pjp` | List PJP beat visits with date and tehsil filters |
| `POST` | `/api/pjp` | Schedule retailer beat visit |
| `PUT` | `/api/pjp/:id` | Complete visit with booked orders & collected payment |

---

## 🔒 License & Copyright
Developed for **UltraTech Cement Ltd. - Unit: Birla White**, Aditya Birla Group.
Confidential & Proprietary. All rights reserved.
