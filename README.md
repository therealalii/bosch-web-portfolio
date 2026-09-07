# BoschWeb — Production Full-Stack E-Commerce Platform

![BoschWeb Homepage](screenshots/homepage.png)

Modern e-commerce platform for Bosch home appliances, built end-to-end — from database schema to SEO to production deployment. Live at **bosch-web.ir**.

> **Note:** BoschWeb is an independent retail platform for Bosch-branded appliances and is not affiliated with or endorsed by Robert Bosch GmbH.

---

## Project Overview

BoschWeb is a full-stack e-commerce platform for selling Bosch home appliances (washing machines, vacuums, and related products) online. It covers the full customer journey — browsing, search, cart, checkout, order tracking, reviews — alongside an admin panel and a companion mobile app for store management.

## My Role

I built and manage this project **end-to-end**, independently:

- Designed the database schema and API layer (Prisma + custom Node server)
- Built the entire frontend (Next.js/React) and backend (API routes, auth, cart/order logic)
- Implemented SEO from the ground up (structured data, sitemaps, meta/OG tags)
- Handled deployment, domain setup, and ongoing production maintenance
- Built the companion admin/mobile app for non-technical store management

This wasn't a "front-end only" or "template customization" job — architecture, backend logic, SEO strategy, and deployment were all my responsibility.

## Problem / Purpose

The client needed a modern, fast, SEO-friendly storefront to replace an outdated setup, with:
- A shopping experience competitive with major e-commerce platforms
- Strong Google visibility for appliance-related search terms
- A way for non-technical staff to manage products/orders without touching code
- Reliable order handling, including manual payment verification via uploaded receipts

## Features

**Storefront**
- Product catalog with categories, best-sellers, new arrivals, and special offers
- Product detail pages with image galleries, stock status, and customer reviews
- Full-text product search with search analytics/logging
- Cart with persistent sync (add/remove/clear/load) via `CartContext`
- Checkout flow with discount code support
- Order creation, order history, and delivery status tracking
- Payment receipt upload for order verification
- SMS-based registration, login, and password recovery (OTP verification)
- User profile and address management
- Company blog with category-based content and blog-specific SEO

**Admin & Management**
- Admin panel for managing products, images, and orders
- Companion mobile app (see [Product Management App](../product-management-app)) for remote store management

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js (Pages Router), React |
| Styling | Tailwind CSS |
| Backend | Node.js, custom Express-style server (`server.js`), middleware auth |
| Database / ORM | PostgreSQL (or MySQL) via Prisma |
| Auth | Custom SMS OTP verification, session-based login |
| SEO | Custom structured data, dynamic sitemaps, Google Search Console |
| Deployment | [HOSTING PROVIDER — e.g. Vercel / VPS] |
| Companion App | React Native, Expo, EAS |

## Development Work

A sample of what's under the hood:

- **Auth system**: custom SMS OTP flow (`RegistrationFormWithSMS`, `SMSVerification`, `useAuth`) instead of relying on a third-party auth provider
- **Cart architecture**: context-based cart state (`CartContext`) synced to the backend so carts persist across devices/sessions
- **Order pipeline**: order creation, delivery-status checks, and receipt-based payment verification for markets without full card-payment infrastructure
- **Blog engine**: dedicated blog service layer, SEO component, and category pages, separate from the product catalog
- **Database**: schema and migrations managed with Prisma, including an initial migration and ongoing schema evolution
- **Cleanup tooling**: scheduled script (`cleanup-orphaned-receipts.js`) to remove unused uploaded files

## SEO & Google Results

![SEO & Analytics](screenshots/seo-analytics.jpg)

- Verified in Google Search Console (site verification file served directly from the app)
- Dynamic `sitemap.xml` and a dedicated `sitemap-images.xml` for image search visibility
- Custom `robots.txt` generation
- Structured data (JSON-LD `Product` schema) on product pages for rich results
- Dedicated SEO components per content type (`ProductSEO`, `CategorySEO`, `BlogSEO`)

## Performance & Optimization

*(PageSpeed results shown in the screenshot above)*

- **Google PageSpeed Insights: 99/100** performance score
- **First Contentful Paint: 0.3s**
- **Largest Contentful Paint: 0.6s**
- Perfect/near-perfect Accessibility, Best Practices, and SEO scores
- Optimized image delivery and lazy loading across product and blog pages

## Deployment & Domain Migration

- Deployed to production at **bosch-web.ir**
- [HOSTING PROVIDER / infra details — e.g. Vercel, custom VPS, CI/CD setup]
- [DOMAIN MIGRATION DETAILS — if the site moved from a previous domain/platform, describe the migration and any redirect/SEO-preservation work here]
- Environment-based configuration (`.env` / `.env.production`) for separating local and production settings

## Architecture

```
Next.js (Pages Router)
   ├── Frontend: React components, Tailwind CSS
   ├── API routes: auth, cart, orders, products, reviews, search, blog
   ├── Middleware: request/auth handling
   ├── Prisma ORM → PostgreSQL/MySQL database
   └── Custom Node server (server.js)

Companion: React Native / Expo mobile app
   └── Talks to the same backend API for remote product/order management
```

*(Add a visual diagram to `architecture/architecture.png` once available.)*

## Screenshots

| Homepage | Product Page | SEO & Performance Dashboard |
|---|---|---|
| ![Homepage](screenshots/homepage.png) | ![Product Page](screenshots/product-detail.png) | ![SEO & Performance](screenshots/seo-analytics.jpg) |

## Results

- 99/100 Google PageSpeed performance score
- Sub-second load times (FCP 0.3s, LCP 0.6s)
- [Add concrete business results if available — e.g. organic traffic growth, indexed pages, order volume]

## Live Website

🔗 **[bosch-web.ir](https://bosch-web.ir)**

---

### Related Projects
- [Product Management App](../product-management-app) — React Native/Expo companion app for managing this store
