# Product Requirements Document (PRD): Airbnb Property Listing Clone (HTML & CSS Only)

**Project Name:** Airbnb Property Listing Clone MVP  
**Author:** Shrut Dev Malviya (Full-Stack Developer / CS Student)  
**Status:** Approved / Ready for Implementation  
**Constraint Rule:** **STRICTLY HTML5 and CSS3 ONLY** (No JavaScript, No Frameworks, No Preprocessors, No Backend)  

---

## 1. Executive Summary & Purpose

The purpose of this project is to construct a production-grade, pixel-accurate, and fully responsive clone of Airbnb's property details page using only foundational web standards: **Semantic HTML5** and **Modern CSS3**.

This project establishes deep mastery of:
1. **Semantic HTML5 Document Flow:** Leveraging meaningful document hierarchy, accessibility milestones, and native input elements.
2. **Advanced CSS Layout Engines:** Mastering two-dimensional layout with **CSS Grid** and one-dimensional linear flow with **CSS Flexbox**.
3. **Advanced Positioning Mechanics:** Implementing persistent user conversion widgets via `position: sticky` and layered interactive badges via `position: absolute`/`relative`.
4. **CSS-Only Micro-Interactions:** Creating a tactile, polished feel utilizing CSS pseudo-classes (`:hover`, `:active`, `:focus-visible`, `:focus-within`) without a single line of JavaScript.

---

## 2. Technical Stack & Invariants

| Layer | Technology | Justification & Strict Boundary |
|---|---|---|
| **Structure** | Semantic HTML5 | Clean DOM tree utilizing `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<figure>`, `<figcaption>`, `<time>`, and `<address>`. Generic `<div>` elements are restricted solely to layout wrapper roles. |
| **Styling** | External CSS3 (`listing-style.css`) | External stylesheet utilizing standard CSS Custom Properties (CSS variables) for tokens. Zero inline styles. |
| **Tooling & Build** | Native Browser | Zero bundlers (no Webpack, Vite, Parcel). Zero preprocessors (no SASS/LESS). Zero UI frameworks (no Tailwind, Bootstrap). Runs directly by opening `index.html`. |
| **Scripting** | **STRICTLY NONE (0 JS)** | No `.js` files, no `<script>` tags, no event handlers (`onclick`), no external script CDNs. |
| **Backend & DB** | None | Purely static client presentation. Forms use native GET/POST structure without submission target or action placeholder. |

---

## 3. Design System & Style Guide

All styles will be anchored by CSS custom properties in the `:root` pseudo-class.

### 3.1 Color Palette
* `--color-bg-canvas`: `#FFFFFF` (Pure White)
* `--color-bg-subtle`: `#F7F7F7` (Light Gray surface for badges and cards)
* `--color-text-primary`: `#222222` (High-contrast charcoal, avoids harsh pure black)
* `--color-text-secondary`: `#717171` (Muted gray for subtitles, ratings, metadata)
* `--color-border-light`: `#DDDDDD` (Standard 1px hairline border)
* `--color-border-divider`: `#EBEBEB` (Section separator lines)
* `--color-brand-primary`: `#FF385C` (Airbnb signature coral)
* `--color-brand-gradient`: `radial-gradient(circle, rgba(255,56,92,1) 0%, rgba(230,30,77,1) 100%)`
* `--color-star`: `#FF385C` / `#222222`
* `--color-card-shadow`: `rgba(0, 0, 0, 0.12) 0px 6px 16px`

### 3.2 Typography Stack
* **Font Family:** `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`
* **Hierarchy:**
  * Property Title (`h1`): `26px / 1.25`, font-weight `600`
  * Section Headers (`h2`): `22px / 1.3`, font-weight `600`
  * Card Subtitles (`h3`): `16px / 1.35`, font-weight `600`
  * Body Text (`p`, `span`): `16px / 1.5`, font-weight `400`
  * Captions & Fine Print: `12px - 14px / 1.4`, font-weight `400`
  * Pricing Emphasis: `22px`, font-weight `600`

### 3.3 Spacing Scale
* Based on an 8px grid:
  * `--space-xs`: `4px`
  * `--space-sm`: `8px`
  * `--space-md`: `16px`
  * `--space-lg`: `24px`
  * `--space-xl`: `32px`
  * `--space-2xl`: `48px`
  * `--space-3xl`: `80px`

### 3.4 Elevation & Border Radii
* Card Radius: `12px`
* Pill Radius: `9999px` (Search pill, badges, buttons)
* Image Gallery Outer Radius: `16px`
* Hairline borders: `1px solid var(--color-border-light)`

---

## 4. Component-by-Component Functional Specifications

### 4.1 Global Navigation Header (`<header class="site-header">`)
* **Layout:** Full-width sticky/fixed header with maximum content width matching listing container (1120px). Uses Flexbox with `justify-content: space-between; align-items: center;`.
* **Elements:**
  1. **Brand Identity:** Airbnb icon (inline SVG) + brand typography.
  2. **Search Pill:** Compact three-segment pill:
     * Segment 1: "Anywhere" (Bold)
     * Vertical divider (`1px solid #DDDDDD; height: 24px;`)
     * Segment 2: "Any week" (Bold)
     * Vertical divider
     * Segment 3: "Add guests" (Light) + circular red search icon button (`#FF385C`).
     * Hover effect: `box-shadow: 0 2px 4px rgba(0,0,0,0.18); transition: box-shadow 0.2s ease;`.
  3. **User Action Bar:**
     * "Airbnb your home" text button (hover background: `#F7F7F7`, border-radius: 9999px)
     * Language / Globe icon button
     * User profile pill button containing: hamburger menu icon + circular default avatar icon with a 1px border.

### 4.2 Listing Title & Action Bar (`<section class="listing-header">`)
* **Property Title:** Descriptive title (`<h1>`) formatted with bold weighting (e.g., *"Luxury Modern Eco-Villa with Infinity Pool & Ocean View"*).
* **Metadata Row:** Uses Flexbox `justify-content: space-between; align-items: center;`.
  * **Left Metadata:**
    * Star icon + Rating (e.g., `★ 4.98`)
    * Review count link (e.g., `124 reviews`)
    * Badge pill: "Guest favorite" or "Superhost"
    * Location link (e.g., `Malibu, California, United States`)
  * **Right Actions (Interactive):**
    * "Share" button with share icon (hover transition)
    * "Save" button with heart icon (hover stroke/fill transition)

### 4.3 Asymmetric Photo Gallery (`<section class="photo-gallery">`)
* **Layout Mechanism:** 2-dimensional **CSS Grid**:
  * Grid definition: 2 columns (or 4 columns in 2fr 1fr 1fr ratio) spanning 2 rows with a fixed aspect ratio or height (approx. 420px - 480px).
  * Gap: `8px`.
  * Container has `border-radius: 16px; overflow: hidden; position: relative;`.
* **Tile Distribution (5 Images Total):**
  * `Image 1` (Hero): Left side, spans row 1 to 3 and column 1 to 2 (`grid-row: span 2; grid-column: span 1` in a 2-column or 3-column split). Takes ~50% of total width.
  * `Image 2`: Top-middle
  * `Image 3`: Top-right (top-right border radius)
  * `Image 4`: Bottom-middle
  * `Image 5`: Bottom-right (bottom-right border radius)
* **Hover Interaction:** Images dim slightly (`filter: brightness(0.92)`) or zoom smoothly (`transform: scale(1.02); transition: transform 0.3s ease;`).
* **Floating Badge Button:** "Show all 32 photos" anchored to bottom-right corner using `position: absolute; bottom: 20px; right: 20px;`.
  * Styled with white background, black border, 8px radius, photo grid icon, and subtle shadow.

### 4.4 Two-Column Main Content Container (`<div class="listing-body">`)
A two-column responsive layout:
* Maximum width: `1120px; margin: 0 auto; padding: 32px 0;`.
* CSS Grid or Flexbox: Left column takes `65%` (`~650px`), Right column takes `35%` (`~380px`), with a `80px` gap (`gap: 80px`).

---

### 4.5 Left Column: Detailed Information Architecture (`<article class="listing-details">`)

1. **Host Summary Section:**
   * Headline: "Entire villa hosted by Alexandra" (`h2`).
   * Sub-details: "8 guests · 4 bedrooms · 4 beds · 3.5 baths".
   * Host avatar image (circular, 56px × 56px, with optional superhost badge badge overlay).
   * Bottom divider line (`border-bottom: 1px solid var(--color-border-divider)`).

2. **Listing Highlights / Badges:**
   * List of 3 key USPs with SVGs:
     * **Dedicated workspace:** A private room with wifi well-suited for working.
     * **Self check-in:** Check yourself in with the smart lock.
     * **Free cancellation for 48 hours:** Full refund before check-in date.

3. **Description Section:**
   * Clean typography paragraphs detailing the architectural philosophy, living areas, outdoor patio, and amenities.
   * "Show more >" link with chevron.

4. **Sleeping Arrangements Section:**
   * Header: "Where you'll sleep"
   * Flexbox card row (horizontal scroll or wrap):
     * Bedroom 1: Bed icon, "Bedroom 1", "1 king bed"
     * Bedroom 2: Bed icon, "Bedroom 2", "1 queen bed"
     * Bedroom 3: Bed icon, "Bedroom 3", "2 single beds"
   * Cards have `1px solid var(--color-border-light)`, `12px` border radius, and padding.

5. **Amenities Section:**
   * Header: "What this place offers"
   * CSS Grid: 2 columns of amenity items.
   * Each item has an SVG icon and title:
     * Scenic mountain / ocean view
     * Private outdoor infinity pool
     * Fast Wifi (500 Mbps)
     * Dedicated workspace
     * Free parking on premises
     * Kitchen with chef equipment
     * Carbon monoxide alarm & Smoke alarm
   * "Show all 45 amenities" button (outlined style, 8px radius).

6. **Availability & Calendar Section:**
   * Visual calendar grid preview created using pure CSS Grid (7 columns for days of the week, numbered day cells).
   * Visual styling for selected range (Check-in to Check-out).

7. **Reviews & Rating Breakdown:**
   * Summary: Star rating `★ 4.98 · 124 reviews`.
   * 2-column grid of rating progress meters (Cleanliness, Accuracy, Communication, Location, Check-in, Value):
     * Left label
     * CSS progress bar (`background: #DDDDDD; height: 4px; border-radius: 2px;` with inner filled span `background: #222222; width: 98%;`)
     * Score number (`4.9` / `5.0`).
   * 2 representative review cards with reviewer avatar, name, date, and feedback paragraph.

8. **Location Section:**
   * Header: "Where you'll be"
   * Static styled map card (clean mockup image or SVG-based map styling with pin).
   * Location description paragraph.

---

### 4.6 Right Column: Sticky Reservation Sidebar (`<aside class="booking-sidebar">`)

* **Sticky Positioning Mechanics:**
  * Must specify `position: sticky; top: 100px;` (accounts for fixed header height).
  * Container height self-contained; floats alongside left column as user scrolls through description, amenities, and reviews.
* **Card Container:**
  * `border: 1px solid var(--color-border-light);`
  * `border-radius: 16px;`
  * `padding: 24px;`
  * `box-shadow: 0 6px 16px rgba(0,0,0,0.12);`
* **Card Header:**
  * Price per night: `<span class="price">$450</span> <span class="unit">night</span>`
  * Rating snippet: `★ 4.98 · 124 reviews`.
* **Reservation Form (`<form>`):**
  * Segmented Input Box: Outer wrapper with `border: 1px solid #B0B0B0; border-radius: 8px; overflow: hidden;`.
    * **Top Split (2 Columns via Flexbox/Grid):**
      * Check-in box: Label `<label>CHECK-IN</label>` + `<input type="date" value="2026-10-15" required>`
      * Checkout box: Label `<label>CHECKOUT</label>` + `<input type="date" value="2026-10-20" required>`
    * **Bottom Row:**
      * Guests dropdown: Label `<label>GUESTS</label>` + `<select><option>1 guest</option><option selected>2 guests</option><option>3 guests</option><option>4+ guests</option></select>`
  * **Primary CTA Button:**
    * Label: "Reserve"
    * Background: Vibrant coral gradient (`var(--color-brand-gradient)`).
    * Styling: `width: 100%; padding: 14px; border: none; border-radius: 8px; color: #FFFFFF; font-size: 16px; font-weight: 600; cursor: pointer; margin-top: 16px;`.
    * Interactive hover/active states with subtle brightness or scale transform.
  * **Sub-notice:** "You won't be charged yet" centered below CTA.
* **Cost Calculation Table:**
  * Clean two-column table / flex layout:
    * `$450 × 5 nights`: `$2,250`
    * `Cleaning fee`: `$150`
    * `Airbnb service fee`: `$338`
  * Divider line (`1px solid var(--color-border-divider)`).
  * **Total Before Taxes:** `$2,738` (Bolded `16px`).
* **Reporting Link:**
  * Centered link: Flag icon + "Report this listing" (`#717171`).

---

### 4.7 Global Footer (`<footer class="site-footer">`)
* **Background:** `#F7F7F7` with top border `1px solid var(--color-border-divider)`.
* **Columns (CSS Grid 4 Columns):**
  * Column 1: **Support** (Help Center, AirCover, Anti-discrimination, Disability support)
  * Column 2: **Hosting** (Airbnb your home, AirCover for Hosts, Hosting resources, Community forum)
  * Column 3: **Airbnb** (Newsroom, New features, Careers, Investors, Gift cards)
* **Bottom Bar (Flexbox):**
  * Left: `© 2026 Airbnb, Inc. · Privacy · Terms · Sitemap · Company details`
  * Right: English (US) · $ USD · Social media icons

---

## 5. Responsive Design Specifications

| Viewport | Width Range | Layout Adjustments |
|---|---|---|
| **Desktop** | `>= 1128px` | Full 2-column layout (Left details 65%, Right sticky sidebar 35%). 5-image asymmetric photo grid. Complete navigation pill. |
| **Tablet** | `744px - 1127px` | Listing content scales down with 24px side padding. Photo gallery scales gracefully. Right sidebar remains sticky or converts to fluid column if width drops below 950px. |
| **Mobile** | `< 744px` | Single-column linear layout. Photo gallery converts to a single hero image or horizontal swipe carousel preview. Sticky booking card converts to a sticky bottom reservation bar (`position: fixed; bottom: 0; left: 0; width: 100%;`). |

---

## 6. Accessibility & Semantic Compliance Matrix

* **Semantic Landmarks:** `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`.
* **Headings:** Proper hierarchical nesting (`h1` -> `h2` -> `h3`). No skipped heading levels.
* **Form Accessibility:** Every `<input>` and `<select>` has an associated `<label>` (explicit `for` attribute matching input `id`).
* **Images:** Every `<img>` tag has meaningful, descriptive `alt` text.
* **Contrast:** All text satisfies WCAG 2.1 AA minimum contrast ratio (4.5:1 for normal text, 3:1 for large text).
* **Keyboard Focus:** Clear `:focus-visible` outlines on all interactive elements (buttons, inputs, links).

---

## 7. Quality Gates & Verification Checklist

- [ ] **Zero JavaScript Gate:** Verification confirms no `.js` files, `<script>` tags, or inline JS event attributes exist anywhere in the codebase.
- [ ] **External Stylesheet Gate:** All presentation rules reside in `listing-style.css`.
- [ ] **CSS Grid Photo Gallery Gate:** Gallery correctly displays 5 images in asymmetric layout (1 large hero, 4 smaller quadrant images) with clean borders and hover effects.
- [ ] **Sticky Sidebar Gate:** Reservation card sticks dynamically below the header when scrolling and does not clip or overflow.
- [ ] **Form Completeness Gate:** Form contains native date inputs, guest selector, and styled submit button.
- [ ] **Semantic Tree Gate:** Page passes HTML5 validator without semantic structure errors.
