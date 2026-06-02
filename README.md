<div align="center">

<img src="public/echofex-icon-logo.png" alt="Echofex Logo" width="80" height="80" />

# Echofex

### Smart Home Devices & Tech Gadgets — Affiliate Review Platform

[![Live Site](https://img.shields.io/badge/Live%20Site-echofex.me-7c3aed?style=for-the-badge&logo=vercel)](https://www.echofex.me)
[![Deployed on Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-black?style=for-the-badge&logo=vercel)](https://vercel.com/hamzaaitayed-1347s-projects/v0-image-analysis)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=nextdotjs)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=for-the-badge&logo=tailwindcss)](https://tailwindcss.com)
[![Sanity CMS](https://img.shields.io/badge/Sanity-CMS-F03E2F?style=for-the-badge&logo=sanity)](https://www.sanity.io)

</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Live Demo](#-live-demo)
- [Tech Stack](#-tech-stack)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [Sanity CMS Setup](#-sanity-cms-setup)
- [SEO & Performance](#-seo--performance)
- [Deployment](#-deployment)
- [License](#-license)

---

## 🏠 Overview

**Echofex** is a production-ready, SEO-optimized affiliate marketing website for smart home devices and IoT gadgets. It combines an expert review blog with a product catalog, fully powered by a **headless CMS (Sanity.io)** — meaning all content (products, articles, categories) is managed without touching code.

Built as a real monetization platform using the **Amazon Associates** affiliate program, with every technical decision made to maximize organic search traffic and conversion rate.

---

## 🚀 Live Demo

> **[https://www.echofex.me](https://www.echofex.me)**

| Page | URL |
|---|---|
| Homepage | `/` |
| Products | `/products` |
| Articles | `/articles` |
| Product Detail | `/products/[slug]` |
| Article Detail | `/articles/[slug]` |
| Search | `/search?q=...` |
| About | `/about` |

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| **Framework** | [Next.js 15](https://nextjs.org) — App Router |
| **Language** | [TypeScript 5](https://www.typescriptlang.org) |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com) |
| **CMS** | [Sanity.io](https://www.sanity.io) (headless) |
| **UI Components** | [shadcn/ui](https://ui.shadcn.com) + [Radix UI](https://www.radix-ui.com) |
| **Icons** | [Lucide React](https://lucide.dev) |
| **Typography** | Playfair Display + Source Sans 3 (Google Fonts) |
| **Dark Mode** | [next-themes](https://github.com/pacocoursey/next-themes) |
| **Deployment** | [Vercel](https://vercel.com) |
| **Image Optimization** | Next.js `<Image>` + Sanity Image URL builder |
| **Animations** | tailwindcss-animate |
| **Performance** | Web Vitals, critters (critical CSS), lazy loading |

---

## ✨ Features

### 🛍️ Product System
- Filterable product grid — search by name, brand, or description
- Category filter + sort by popularity, price, rating, or newest
- **Grid / List** view toggle
- Smart paginated results
- Product detail pages with image gallery, specifications table, features, and review summary
- Amazon affiliate CTA — **"Check Price on Amazon"** with `nofollow` compliance
- Wishlist toggle (client-side)
- Native **Web Share API** integration on product pages

### 📰 Articles & Blog
- Filterable article listing with search, category, and sort
- **Featured articles** section at the top
- Full article rendering via **Sanity Portable Text**
- Related products embedded inside articles
- Related articles sidebar per article page
- Read time and publish date on every article

### 🔍 SEO — Production Grade
- Full `<meta>` tags: title, description, keywords, canonical
- **Open Graph** and **Twitter Card** support
- **JSON-LD Structured Data**: `WebSite`, `Organization`, `FAQPage`, `BreadcrumbList`, `Product`
- Auto-generated **sitemap.xml** via `app/sitemap.ts` (includes all product and article pages)
- Auto-generated **robots.txt** via `app/robots.ts`
- Google Search Console verification

### ⚡ Performance
- WebP & AVIF image format support via `next/image`
- LQIP (Low Quality Image Placeholder) from Sanity metadata
- Aggressive cache headers (30-day TTL for images, immutable for static assets)
- Critical CSS inlining with **critters**
- Webpack tree-shaking (`usedExports: true`)
- DNS prefetch + preconnect for external fonts
- **Core Web Vitals** monitoring (LCP, CLS, FID)
- Lazy loading for below-the-fold sections

### 🎨 UI / UX
- Light / Dark mode with system preference detection
- Sticky, blurred-backdrop header
- Responsive mobile navigation (Sheet/Drawer component)
- Inline search bar → routes to `/search` page
- Hover animations on cards (scale + border color transition)
- Violet (`#7c3aed`) brand accent throughout

### 🔐 Security Headers
- `Strict-Transport-Security` (HSTS, 1 year)
- `X-Frame-Options: DENY`
- `X-Content-Type-Options: nosniff`
- `X-XSS-Protection`
- `Permissions-Policy` (camera, microphone, geolocation locked)
- `Referrer-Policy: origin-when-cross-origin`

---

## 📁 Project Structure

```
echofex/
├── app/                          # Next.js App Router
│   ├── layout.tsx                # Root layout (fonts, theme, metadata)
│   ├── page.tsx                  # Homepage
│   ├── globals.css               # Global styles + design tokens
│   ├── robots.ts                 # Auto-generated robots.txt
│   ├── sitemap.ts                # Auto-generated XML sitemap
│   ├── products/
│   │   ├── page.tsx              # Products listing page
│   │   └── [slug]/page.tsx       # Product detail page
│   ├── articles/
│   │   ├── page.tsx              # Articles listing page
│   │   └── [slug]/page.tsx       # Article detail page
│   ├── categories/[slug]/        # Category pages
│   ├── search/                   # Full-text search page
│   ├── about/                    # About page
│   ├── privacy/                  # Privacy policy
│   └── affiliate-disclaimer/     # Affiliate disclosure
│
├── components/                   # Reusable UI components
│   ├── header.tsx                # Sticky nav + search + mobile drawer
│   ├── footer.tsx                # Footer with links
│   ├── hero-section.tsx          # Homepage hero with stats
│   ├── featured-products.tsx     # Featured products carousel
│   ├── blog-section.tsx          # Homepage article preview
│   ├── products-listing.tsx      # Filterable/sortable product grid
│   ├── product-detail.tsx        # Full product page with tabs
│   ├── articles-listing.tsx      # Filterable article grid
│   ├── article-detail.tsx        # Article page with portable text
│   ├── related-products.tsx      # Related products widget
│   ├── related-articles.tsx      # Related articles widget
│   ├── optimized-image.tsx       # next/image wrapper
│   ├── structured-data.tsx       # JSON-LD schema injector
│   ├── seo-head.tsx              # Per-page SEO head
│   ├── web-vitals.tsx            # Core Web Vitals reporter
│   ├── performance-monitor.tsx   # Performance metrics monitor
│   ├── theme-provider.tsx        # next-themes provider
│   ├── mode-toggle.tsx           # Dark/light mode toggle
│   ├── lazy-load-section.tsx     # Intersection Observer lazy loader
│   ├── loading-spinner.tsx       # Loading state component
│   └── ui/                       # shadcn/ui component library
│
├── lib/
│   ├── sanity.client.ts          # Sanity client + imageUrlBuilder
│   ├── queries.ts                # All GROQ queries
│   └── utils.ts                  # clsx + tailwind-merge utility
│
├── types/                        # Global TypeScript types
├── hooks/                        # Custom React hooks
├── public/                       # Static assets
├── styles/                       # Additional stylesheets
├── next.config.mjs               # Next.js config (performance + security)
├── tailwind.config.ts            # Tailwind config
└── tsconfig.json                 # TypeScript config
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js `>= 18`
- npm / pnpm
- A [Sanity.io](https://www.sanity.io) account and project

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/echofex.git
cd echofex

# 2. Install dependencies
npm install

# 3. Set up environment variables (see below)
cp .env.local.example .env.local

# 4. Start the development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Available Scripts

| Script | Description |
|---|---|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |

---

## 🔑 Environment Variables

Create a `.env.local` file in the project root:

```env
# Sanity CMS
NEXT_PUBLIC_SANITY_PROJECT_ID=your_sanity_project_id
NEXT_PUBLIC_SANITY_DATASET=production
```

> **Never commit `.env.local` to version control.** It is already in `.gitignore`.

---

## 🗂️ Sanity CMS Setup

This project uses [Sanity.io](https://www.sanity.io) as its headless CMS. The following content types are expected in your Sanity dataset:

### `product` Schema Fields
| Field | Type | Description |
|---|---|---|
| `name` | string | Product name |
| `slug` | slug | URL-friendly identifier |
| `description` | text | Product description |
| `price` | number | Current price |
| `originalPrice` | number | Original / MSRP price |
| `rating` | number | Star rating (0–5) |
| `reviews` | number | Number of reviews |
| `image` | image | Main product image |
| `gallery` | image[] | Additional images |
| `category` | reference → category | Product category |
| `brand` | string | Brand name |
| `model` | string | Model number |
| `features` | string[] | List of key features |
| `specifications` | {key, value}[] | Technical specs table |
| `affiliateUrl` | url | Amazon affiliate link |
| `featured` | boolean | Show on homepage |

### `article` Schema Fields
| Field | Type | Description |
|---|---|---|
| `title` | string | Article title |
| `slug` | slug | URL-friendly identifier |
| `excerpt` | text | Short summary |
| `content` | Portable Text | Rich article body |
| `mainImage` | image | Hero image |
| `category` | reference → category | Article category |
| `publishedAt` | datetime | Publish date |
| `readTime` | string | e.g. "5 min read" |
| `keywords` | string[] | SEO keywords |
| `featured` | boolean | Show in featured section |
| `relatedProducts` | reference[] → product | Linked products |

### `category` Schema Fields
| Field | Type |
|---|---|
| `title` | string |
| `slug` | slug |

---

## 📈 SEO & Performance

### Structured Data (JSON-LD)
The site injects the following schema types automatically:
- **`Organization`** — brand info, social profiles, contact
- **`WebSite`** — site-level with `SearchAction` for sitelinks search box
- **`FAQPage`** — common smart home questions on the homepage
- **`BreadcrumbList`** — on all listing and detail pages
- **`Product`** — on individual product pages (price, rating, availability)

### Sitemap
Auto-generated at `/sitemap.xml` including:
- Static pages (priority 1.0 → 0.4)
- All product pages (priority 0.8, weekly updates)
- All article pages (priority 0.7, uses real `publishedAt` date)

### Core Web Vitals
Web Vitals are tracked client-side via `web-vitals.tsx` and reported using the `PerformanceObserver` API.

---

## 🌐 Deployment

The project is deployed on **Vercel** with automatic deployments from the main branch.

```bash
# Production build
npm run build

# Preview the production build locally
npm run start
```

### Vercel Environment Variables
Set the following in your Vercel project settings:

```
NEXT_PUBLIC_SANITY_PROJECT_ID = your_project_id
NEXT_PUBLIC_SANITY_DATASET    = production
```

---

## 📄 License

This project is for portfolio and educational purposes.  
© 2025 **Echofex** — All rights reserved.

---

<div align="center">

Built with ❤️ using **Next.js**, **Sanity CMS**, and **Tailwind CSS**  
[echofex.me](https://www.echofex.me) · [hello@echofex.com](mailto:hello@echofex.com)

</div>
