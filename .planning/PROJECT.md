# Project Blueprint: Pure HTML & CSS Property Listing Clone

## Executive Summary
This project is a high-fidelity, single-page web clone of a modern property rental listing (modeled after Airbnb's flagship property page). The core mission of this project is to build an industry-grade, accessible, and responsive web document strictly using foundational web technologies: **semantic HTML5** and **external CSS3**.

## Developer & Persona
* **Developer:** Shrut Dev Malviya (Full-Stack Developer / Computer Science Student)
* **Goal:** Master the raw DOM, layout engines (Flexbox & CSS Grid), positioning mechanisms (`position: sticky`), and native form controls to build an unbreakable foundation before transitioning to full-stack frameworks (React, Next.js, Node).

## Architectural Principles & Strict Scope Boundaries
* **Strict Technology Scope:** Pure HTML5 and CSS3 **only**.
* **Zero JavaScript:** All layout states, sticky behavior, form styling, and micro-interactions are driven purely by native HTML elements and CSS pseudo-classes (`:hover`, `:active`, `:focus-within`, `:target`).
* **Zero External CSS Frameworks:** No Tailwind, Bootstrap, or preprocessors (SASS/LESS). All styling resides in an external, highly organized `listing-style.css` stylesheet using CSS Custom Properties (CSS variables).
* **Zero Bundlers or Build Steps:** Clean, standard browser-native files (`index.html` and `listing-style.css`) eliminating configuration overhead.
* **Semantic First:** Strict usage of semantic tags (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<figure>`, `<time>`, etc.) rather than generic `<div>` soup.

## Core Features & Layout Architecture
1. **Global Header (`<header>`):**
   - Brand logo and name
   - Centralized search pill with segmented destination, dates, and guest indicators
   - Right-side utilities: "Airbnb your home" CTA, language/globe toggle, and user profile pill with avatar
2. **Listing Header & Metadata (`<section class="listing-header">`):**
   - Property title (`<h1>`)
   - Metadata line: Superhost badge, guest favorite pill, star rating, reviews count, and location link
   - Action controls: Share and Save (Wishlist) interactive buttons
3. **Asymmetric Photo Gallery (`<section class="gallery">`):**
   - 5-image asymmetric CSS Grid (1 large primary hero image taking 2fr, 4 sub-images organized in a 2x2 grid taking 1fr each)
   - Border radius treatment, hover dimming/scaling effects
   - Floating "Show all photos" button anchored to the bottom-right corner
4. **Main Two-Column Split (`<div class="content-container">`):**
   - **Left Column (`<article class="listing-details">`):**
     * Host profile header with avatar and co-host details
     * Highlights list (Self check-in, Great location, Free cancellation)
     * Sleeping arrangements card grid (bedroom layouts, bed icons)
     * Detailed property description & house rules
     * Comprehensive Amenities grid with icons (Kitchen, Wifi, Dedicated workspace, Pool, Air conditioning, etc.)
     * Availability & Calendar visual display
     * Rating category breakdown bars (Cleanliness, Accuracy, Communication, Location, Value)
     * Static Map & Neighborhood guide
   - **Right Column (`<aside class="booking-sidebar">`):**
     * Sticky booking card (`position: sticky; top: 100px;`)
     * Price header (price per night + rating summary)
     * Segmented reservation form (Check-in date, Checkout date, Guests dropdown)
     * High-conversion gradient CTA button ("Reserve")
     * Pricing calculation summary table (Nightly rate × nights, Cleaning fee, Service fee, Taxes, Total)
     * "You won't be charged yet" reassurance copy
5. **Global Footer (`<footer>`):**
   - Categorized footer links (Support, Community, Hosting, Airbnb)
   - Copyright, privacy, terms, and currency/language selectors

## Design Tokens & Foundations
* **Typography:** System font stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif`)
* **Color Palette:**
  * Background / Canvas: `#FFFFFF`
  * Primary Text: `#222222` (Off-black for reduced eye strain)
  * Secondary / Muted Text: `#717171`
  * Border & Dividers: `#DDDDDD` / `#EBEBEB`
  * Accent / Primary CTA: `#FF385C` (Airbnb Coral) with gradient `#E61E4D`
  * Star Rating: `#222222` / `#FF385C`
* **Spacing:** 8px modular scale (`--space-1: 8px`, `--space-2: 16px`, `--space-3: 24px`, `--space-4: 32px`, `--space-6: 48px`, `--space-8: 64px`)
* **Radii:** `--radius-sm: 8px`, `--radius-md: 12px`, `--radius-lg: 16px`, `--radius-pill: 9999px`
* **Shadows:** Elevation tokens for cards, header, and floating elements.
