# TravelSphere Pro 🌍✨
### Commercial-Grade Full-Stack Luxury Travel Booking Management System

TravelSphere Pro is a production-level, turnkey luxury travel platform engineered for seamless deployment on **Vercel** with a single-stack Next.js 15 App Router architecture, PostgreSQL (Neon-compatible) with Prisma ORM, NextAuth.js authentication with Role-Based Access Control (RBAC), and high-resolution media management.

---

## 🌟 Key Features

### 👤 Customer Experience
- **Luxury Home Page**: Full-screen cinematic hero, animated multi-parameter search engine (destinations, dates, guest parties, themes), popular destinations grid, featured itineraries, 4 value pillars, verified customer reviews, and newsletter journal.
- **Voyage Catalog & Discovery**: Interactive package browsing with live search, price slider, duration filters, and sorting.
- **Destination Showcase**: Explore worldwide countries and private sanctuaries with related package breakdowns.
- **Rich Package Details**: High-resolution image gallery, interactive day-by-day itinerary timeline with meal plans & activities, included/excluded services breakdown, and customer reflections.
- **5-Step Booking Workflow**:
  1. *Select Package*: Live pricing calculator.
  2. *Choose Date & Travellers*: Departure calendar and party size selector with remaining capacity enforcement.
  3. *Guest Details*: Primary passenger passport name, email, phone, and dietary/special requests.
  4. *Payment Confirmation*: Credit/Debit card payment simulator, Bank Wire transfer with IBAN/SWIFT instructions, or Cash on Arrival.
  5. *Booking Success Celebration*: Confetti animation, reservation reference number, instant confirmation summary, and PDF invoice download.
- **Booking Management**: View reservations with status badges (`PENDING`, `CONFIRMED`, `COMPLETED`, `CANCELLED`), cancellation capability, and official branded PDF invoice generator.
- **Personal Wishlist**: Save favorite luxury packages with real-time heart toggles.
- **Account Profile**: Manage passenger name, telephone, avatar, and billing address.

### 🛡️ Admin Command Portal
- **Dashboard Telemetry**: Real-time KPI metric cards (Gross Revenue, Total Bookings, Registered Voyagers, Active Packages), Recharts financial area graphs, and monthly booking bar charts.
- **Booking Management**: Comprehensive reservation table with status moderation modal (`PENDING` ➔ `CONFIRMED` ➔ `COMPLETED` ➔ `CANCELLED`).
- **Package Management**: Complete CRUD operations for luxury packages (title, slug, destination association, descriptions, duration, pricing, discount percentage, seat availability, inclusions, exclusions, and featured flag).
- **Destination Management**: Complete CRUD operations for worldwide destinations (name, country, category, image URL, rating, and promotional status).
- **Payment & Treasury Ledger**: Transaction monitoring across Cards, Bank Wires, and Cash with one-click CSV export.
- **User Management**: Member roster with role elevation (`CUSTOMER` ⇄ `ADMIN`).
- **Review Moderation**: Star rating inspection with one-click approval or removal.
- **Intelligence Reports & CSV Exports**: Instant download of audit-ready CSV datasets for Bookings and Payments.

---

## 🔑 Demo Accounts (Pre-Seeded)

The application comes pre-configured with two demo accounts for testing both user perspectives:

| Role | Email | Password |
| :--- | :--- | :--- |
| **Super Admin** | `admin@travelsphere.com` | `Admin@123` |
| **VIP Customer** | `customer@travelsphere.com` | `Customer@123` |

> *Tip: The Login page also features **1-Click Demo Buttons** to log into either account instantly!*

---

## 🛠️ Technology Stack

- **Framework**: Next.js 15 (App Router) + TypeScript
- **Styling**: Tailwind CSS + Luxury CSS Custom Properties
- **Icons**: Lucide React
- **Animations**: Canvas Confetti + Tailwind Keyframes
- **Charts**: Recharts
- **Database**: PostgreSQL (Neon Serverless compatible)
- **ORM**: Prisma ORM v6
- **Authentication**: NextAuth.js v4 (JWT + Credentials + RBAC)
- **PDF Generation**: jsPDF + jsPDF-AutoTable (client-side branded invoice generation)
- **Image Storage**: Cloudinary (with built-in high-res Unsplash fallbacks)
- **Validation**: Zod runtime schema validation

---

## 🚀 Quick Start & Installation

### 1. Clone & Install Dependencies

```bash
git clone https://github.com/your-username/travelsphere-pro.git
cd travelsphere-pro
npm install
```

### 2. Configure Environment Variables

Create a `.env` file in the root directory:

```env
# PostgreSQL Database (Neon / Supabase / Local PostgreSQL)
DATABASE_URL="postgresql://user:password@ep-sample-neon-pooler.us-east-2.aws.neon.tech/travelsphere?sslmode=require"

# NextAuth Authentication
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="travelsphere_pro_super_secret_jwt_key_2025_luxury_travel"

# Cloudinary Storage (Optional - Fallbacks provided)
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME="demo"
CLOUDINARY_KEY="123456789012345"
CLOUDINARY_SECRET="demo_secret_key"
CLOUDINARY_UPLOAD_PRESET="travelsphere"

# App Public URL
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

### 3. Database Setup & Prisma Migration

Push the schema to your Neon PostgreSQL database and seed demo data:

```bash
# Push database schema
npx prisma db push

# Seed luxury destinations, packages, admin, and demo bookings
npm run prisma:seed
```

> **Note**: Even if you do not connect a live PostgreSQL database immediately, TravelSphere Pro includes a graceful built-in mock fallback service, allowing you to run, build, and explore the entire application locally with zero errors!

### 4. Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## ☁️ Vercel 1-Click Deployment Guide

TravelSphere Pro is optimized for deployment on Vercel without external build servers or Docker:

1. **Push to GitHub**:
   ```bash
   git add .
   git commit -m "feat: initial commit of TravelSphere Pro"
   git push origin main
   ```

2. **Import to Vercel**:
   - Go to [vercel.com](https://vercel.com) and log in.
   - Click **"Add New..."** ➔ **"Project"**.
   - Select your `travelsphere-pro` repository and click **Import**.

3. **Configure Environment Variables in Vercel**:
   Add the following environment variables in the Vercel dashboard under **Project Settings ➔ Environment Variables**:

   | Key | Value |
   | :--- | :--- |
   | `DATABASE_URL` | Your Neon PostgreSQL connection string (`postgresql://...`) |
   | `NEXTAUTH_SECRET` | A secure random 32-character string (e.g. `openssl rand -base64 32`) |
   | `NEXTAUTH_URL` | Your Vercel deployment URL (e.g. `https://travelsphere-pro.vercel.app`) |
   | `NEXT_PUBLIC_APP_URL` | Your Vercel deployment URL |
   | `CLOUDINARY_KEY` | *(Optional)* Cloudinary API Key |
   | `CLOUDINARY_SECRET` | *(Optional)* Cloudinary API Secret |
   | `NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME` | *(Optional)* Cloudinary Cloud Name |

4. **Deploy**:
   - Click **Deploy**.
   - The `postinstall: "prisma generate"` script will automatically generate the Prisma client during Vercel's build pipeline.

5. **Initialize Database from Vercel**:
   After deployment, run the database push and seed commands against your Neon database from your local machine:
   ```bash
   DATABASE_URL="your-neon-database-url" npx prisma db push
   DATABASE_URL="your-neon-database-url" npm run prisma:seed
   ```

---

## 📁 Project Architecture

```
travelsphere-pro/
├── actions/                   # Next.js Server Actions (CRUD, Auth, Reservations)
│   ├── booking-actions.ts
│   ├── destination-actions.ts
│   ├── favourite-actions.ts
│   ├── package-actions.ts
│   ├── review-actions.ts
│   └── user-actions.ts
├── app/                       # Next.js 15 App Router
│   ├── (auth)/                # Customer & Admin Auth (Login & Registration)
│   ├── (customer)/            # Customer Website (Home, Packages, Bookings, Profile)
│   ├── admin/                 # Protected Admin Command Portal & Telemetry
│   ├── api/                   # REST Route Handlers (Auth, Register, Upload, CSV Exports)
│   ├── globals.css            # Luxury Design System & Tailwind Styling
│   ├── layout.tsx             # Root Layout with SEO OpenGraph & Providers
│   ├── robots.ts              # Search Engine Robots Protocol
│   └── sitemap.ts             # Dynamic XML Sitemap Generator
├── components/                # Reusable React & Radix Components
│   ├── ui/                    # Buttons, Inputs, Cards, Badges, Modals
│   ├── admin-charts.tsx       # Recharts Analytics Area & Bar Graphs
│   ├── admin-header.tsx       # Admin Navigation Header
│   ├── admin-sidebar.tsx      # Admin Fixed Navigation Sidebar
│   ├── booking-stepper.tsx    # 5-Step Checkout Stepper Workflow
│   ├── destination-card.tsx   # Curated Destination Card
│   ├── footer.tsx             # Luxury Travel Footer & VIP Newsletter
│   ├── hero-search.tsx        # Multi-parameter Search Component
│   ├── invoice-pdf.tsx        # Client-side jsPDF Invoice Generator
│   ├── navbar.tsx             # Sticky Glassmorphism Header
│   ├── package-card.tsx       # Luxury Travel Itinerary Card
│   ├── providers.tsx          # SessionProvider & HotToast Provider
│   └── review-card.tsx        # Testimonial & Review Component
├── lib/                       # Core Utilities, Types, and Services
│   ├── auth.ts                # NextAuth Configuration & RBAC Callbacks
│   ├── cloudinary.ts          # Cloudinary File Storage Helper
│   ├── db-service.ts          # Resilient Database Query Service
│   ├── demo-data.ts           # Pre-populated Luxury Seed Dataset
│   ├── prisma.ts              # Singleton Prisma Client Instance
│   ├── types.ts               # Application TypeScript Interfaces
│   └── utils.ts               # Currency & Date Formatters
├── prisma/
│   ├── schema.prisma          # PostgreSQL Relational Schema
│   └── seed.ts                # Database Seeding Script
└── README.md
```

---

## 📄 License

This project is licensed under the MIT License. Built with passion for luxury travel worldwide.
