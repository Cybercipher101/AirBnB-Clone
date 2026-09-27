# Product Requirements Document (PRD)
## Airbnb Property Listing Clone (HTML5 & CSS3 Only)

**Document Version:** 1.0.0  
**Target Platform:** Modern Web Browsers (Chrome, Edge, Firefox, Safari)  
**Author:** Shrut Dev Malviya (Full-Stack Developer / Computer Science Student)  
**Strict Constraint:** **Pure Semantic HTML5 and External CSS3 ONLY** (0% JavaScript, No Frameworks, No Preprocessors, No Backend)  

---

## 1. Executive Summary & Vision

The objective of this project is to craft a pixel-accurate, visually engaging, and accessible web document cloning the user interface of an Airbnb property listing page. 

By deliberately constraining the project to **Pure HTML5 and CSS3**, the project serves as a showcase of core web fundamentals:
* Semantic document hierarchy without `div`-soup.
* Precise layout modeling using modern **CSS Grid** and **CSS Flexbox**.
* Advanced positioning mechanisms including `position: sticky` and layered overlays.
* Interactive, tactile feedback and micro-animations created purely with CSS pseudo-classes (`:hover`, `:active`, `:focus-within`).

---

## 2. Scope Boundaries & Constraints

### In-Scope (The Core Product)
* **Global Navigation Bar:** Logo, brand identity, 3-segment search pill, and user profile menu pill.
* **Listing Header:** Property title (`<h1>`), rating score, review count, location link, and interactive Share & Save actions.
* **Asymmetric Photo Gallery:** 5-image asymmetric CSS Grid layout (1 large hero image taking 2fr, 4 quadrant images taking 1fr each) with hover effects and a floating "Show all photos" button.
* **Two-Column Main Layout:** 65% / 35% desktop split container.
* **Left Content Column:** Host summary card, highlight features, property description, bedroom cards, amenities grid, visual availability calendar, rating breakdown progress meters, and location card.
* **Right Sticky Sidebar:** Sticky reservation widget (`position: sticky`), nightly price header, segmented date input box, guests dropdown, coral gradient "Reserve" button, price breakdown table, and reassurance text.
* **Global Footer:** Categorized sitemap links, copyright, and language/currency selectors.
* **Responsive Breakpoints:** Smooth degradation across Desktop (>=1128px), Tablet (744px–1127px), and Mobile (<744px) with a mobile sticky bottom reservation bar.

### Out-of-Scope (Strict Exclusions)
* **Zero JavaScript:** No `.js` files, `<script>` tags, inline scripts, or client-side runtime logic.
* **Zero External Frameworks / Libraries:** No Bootstrap, Tailwind, jQuery, or React.
* **Zero Preprocessors or Bundlers:** No Sass, Less, Webpack, Vite, or PostCSS. Runs natively in any browser.
* **Zero Backend Database:** Form submission is simulated with native HTML `<form>` markup.

---

## 3. Design System & CSS Token Specifications

The external stylesheet `listing-style.css` will declare CSS custom properties in `:root`:

```css
:root {
  /* Color Tokens */
  --color-canvas: #FFFFFF;
  --color-surface-subtle: #F7F7F7;
  --color-text-primary: #222222;
  --color-text-secondary: #717171;
  --color-border-light: #DDDDDD;
  --color-border-divider: #EBEBEB;
  --color-accent-coral: #FF385C;
  --color-accent-gradient: radial-gradient(circle, #FF385C 0%, #E61E4D 100%);
  --color-accent-dark: #D70466;

  /* Typography Stack */
  --font-family-base: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  
  /* 8px Spacing Grid */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 16px;
  --space-4: 24px;
  --space-5: 32px;
  --space-6: 48px;
  --space-8: 64px;

  /* Border Radii */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-pill: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.08);
  --shadow-md: 0 2px 4px rgba(0, 0, 0, 0.12);
  --shadow-lg: 0 6px 16px rgba(0, 0, 0, 0.12);
  --shadow-hover: 0 4px 12px rgba(0, 0, 0, 0.18);
}
```

---

## 4. Detailed Component Architecture

### 4.1 Global Header (`<header class="site-header">`)
* **Semantic Structure:** `<header>` containing `<nav class="header-nav">`.
* **Sub-components:**
  * **Brand Identity:** Left-aligned SVG logo with Airbnb wordmark.
  * **Search Pill:** Centered rounded pill (`--radius-pill`) with subtle box-shadow. Contains three text segments ("Anywhere", "Any week", "Add guests") separated by 1px vertical rules, and a circular coral search button.
  * **User Profile Controls:** Right-aligned group featuring "Airbnb your home" anchor, globe language icon, and an interactive pill containing a hamburger icon and profile avatar.

### 4.2 Listing Header & Action Strip (`<section class="listing-header">`)
* **Semantic Structure:** `<section>` with an `<h1>` heading.
* **Content:**
  * Primary title: *"Luxury Cliffside Villa with Panoramic Pacific Ocean Views"*
  * Sub-bar (Flexbox): Left group with star rating badge (`★ 4.98`), review link (`124 reviews`), Superhost status badge, and location link (`Malibu, California`).
  * Right group: Interactive "Share" and "Save" buttons with SVG icons and hover background transitions.

### 4.3 Asymmetric 5-Photo Grid Gallery (`<section class="gallery-section">`)
* **Semantic Structure:** `<section>` wrapping a `<div class="photo-grid">` with 5 `<figure>` elements.
* **CSS Grid Blueprint:**
  ```css
  .photo-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    grid-template-rows: repeat(2, 220px);
    gap: var(--space-2);
    border-radius: var(--radius-lg);
    overflow: hidden;
    position: relative;
  }
  .photo-item:nth-child(1) {
    grid-column: 1 / 2;
    grid-row: 1 / 3; /* Spans both rows */
  }
  ```
* **Visual States:**
  * Hovering over any photo slightly alters brightness or scales the image smoothly (`transition: transform 0.3s ease`).
  * Floating "Show all photos" pill button positioned with `position: absolute; bottom: 20px; right: 20px;` with camera icon and white background.

### 4.4 Left-Column Content Flow (`<article class="listing-details">`)
* **Host Card:** Avatar, host name ("Hosted by Alexandra"), co-host status, and hosting tenure.
* **Key Highlights:** 3 stacked rows with SVG icons:
  * *Dedicated workspace*
  * *Self check-in with keypad*
  * *Free cancellation for 48 hours*
* **Listing Description:** Formatted narrative detailing architecture, views, and layout.
* **Sleeping Arrangements:** Horizontal Flexbox cards displaying bedroom names and bed counts with bed icons.
* **Amenities Section:** 2-column CSS Grid showcasing 10+ essential amenities (Wifi, Chef Kitchen, Pool, Free Parking, Workspace, EV Charger, Ocean View, etc.) with clean inline SVGs.
* **Calendar Preview:** Pure CSS visual calendar grid displaying current booking window.
* **Reviews & Ratings Breakdown:** Overall score display (`4.98`) followed by a 2-column grid of category ratings with visual progress bars (`Cleanliness`, `Accuracy`, `Communication`, `Location`, `Check-in`, `Value`).
* **Location & Map Card:** Visual map placeholder card with pin and neighborhood summary.

### 4.5 Right-Column Sticky Reservation Card (`<aside class="booking-sidebar">`)
* **Positioning:**
  ```css
  .booking-sidebar {
    position: sticky;
    top: 100px;
    align-self: start;
  }
  ```
* **Card Container:** Elevated card with `1px solid var(--color-border-light)`, `16px` border-radius, and `--shadow-lg`.
* **Card Header:** Nightly price (`$450 / night`) and compact rating summary (`★ 4.98 · 124 reviews`).
* **Native Form Components (`<form class="booking-form">`):**
  * Segmented Date Box:
    * Check-in `<label>` and native `<input type="date">`
    * Checkout `<label>` and native `<input type="date">`
  * Guest Selector:
    * `<label>` and native `<select>` dropdown (1 guest, 2 guests, 3 guests, 4+ guests)
  * Primary Action:
    * `<button type="submit" class="btn-reserve">Reserve</button>` with coral gradient and hover transition.
* **Reassurance Notice:** "You won't be charged yet" centered below the CTA.
* **Calculation Table:** Detailed pricing calculation table breakdown:
  * `$450 × 5 nights` -> `$2,250`
  * `Cleaning fee` -> `$150`
  * `Airbnb service fee` -> `$338`
  * **Total before taxes** -> `$2,738` (Bolded)
* **Report Link:** Subtle flag icon and "Report this listing".

### 4.6 Global Footer (`<footer class="site-footer">`)
* **Multi-Column Sitemap:** CSS Grid with 4 columns: *Support*, *Community*, *Hosting*, and *Airbnb*.
* **Bottom Legal Strip:** Flexbox container containing copyright notice, privacy & terms links, and language/currency selector badges.

---

## 5. Responsive Behavior Matrix

| Feature | Desktop (`>= 1128px`) | Tablet (`744px - 1127px`) | Mobile (`< 744px`) |
|---|---|---|---|
| **Header** | Full 3-segment search pill + user menu | Condensed search pill | Simplified search bar with filter icon |
| **Gallery** | 5-image asymmetric grid (2fr / 1fr / 1fr) | 5-image grid scaled down | Single hero image with swipe pill |
| **Main Content** | 2-column split (65% details / 35% sidebar) | 2-column split (60% / 40%) | 1-column linear stack |
| **Reservation Widget** | Sticky floating card on the right | Sticky floating card | Fixed bottom booking bar with "Reserve" button |
| **Amenities** | 2-column grid | 2-column grid | 1-column list |

---

## 6. Verification & Quality Acceptance Criteria

1. **Zero JavaScript Verification:** Codebase contains strictly 0 `<script>` tags, 0 `.js` files, and 0 inline JavaScript event handlers.
2. **HTML5 Semantic Conformance:** Standard landmarks (`<header>`, `<nav>`, `<main>`, `<article>`, `<aside>`, `<footer>`) are used properly with no invalid nesting.
3. **CSS Grid Fidelity:** The photo gallery maintains its 2fr/1fr/1fr asymmetric ratio without warping or overflow.
4. **Sticky Behavior Verification:** The reservation card remains smoothly fixed in the viewport as the user scrolls past the long description and amenities, stopping before overflowing into the footer.
5. **Native Form Validity:** Date inputs and select dropdowns render native controls and respect keyboard navigation.
