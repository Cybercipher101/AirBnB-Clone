# Project Roadmap: Airbnb Property Listing Clone (HTML & CSS Only)

## Overview
This roadmap decomposes the development of the pure HTML & CSS property listing clone into six focused, milestone-driven phases. Each phase establishes a verified layer of the application.

---

### Phase 1: Project Scaffolding & Design System Foundation
* **Goal:** Initialize file structure, define CSS custom properties (design tokens), normalize browser defaults, and establish the main container layout.
* **Deliverables:**
  - `index.html` structure with `<head>` metadata, viewport configuration, and semantic skeleton (`<header>`, `<main>`, `<footer>`).
  - `listing-style.css` containing:
    * CSS Reset (box-sizing, margin/padding clears, media defaults)
    * `:root` tokens for colors, typography, spacing, shadows, and radii
    * Base typography and container constraints (`max-width: 1120px; margin: 0 auto;`)
* **Verification Gate:** Browser renders clean canvas, loads stylesheet, and demonstrates token styling.

---

### Phase 2: Navigation Header & Listing Hero Metadata
* **Goal:** Construct the persistent top navigation and listing metadata section.
* **Deliverables:**
  - `<header class="site-header">` with Flexbox:
    * Airbnb SVG logo and brand wordmark
    * Interactive 3-segment search pill with divider lines and search button
    * User menu pill with hamburger and avatar icons
  - `<section class="listing-header">`:
    * Listing `<h1>` title
    * Metadata line (rating, review count, superhost badge, location)
    * Interactive Share and Save buttons with SVG icons
* **Verification Gate:** Header and metadata layout match specifications with active hover micro-interactions.

---

### Phase 3: Asymmetric CSS Grid Photo Gallery
* **Goal:** Implement the flagship 5-image asymmetric photo gallery with pure CSS Grid and hover states.
* **Deliverables:**
  - `<section class="photo-gallery">` container with 16px border-radius and overflow clipping.
  - CSS Grid rules: 1 primary hero photo (2fr) + 4 secondary photos (organized in a 2x2 quadrant).
  - Pure CSS hover transitions (subtle brightness adjustment and scale).
  - Floating pill button: "Show all photos" positioned with `position: absolute; bottom: 20px; right: 20px;`.
* **Verification Gate:** Gallery renders 5 images in correct proportions without grid blowouts across desktop resolutions.

---

### Phase 4: Left-Column Information Architecture
* **Goal:** Build the detailed property narrative, host summary, amenities, sleeping arrangements, and review breakdown.
* **Deliverables:**
  - `<article class="listing-details">`:
    * Host summary card with avatar and duration badge
    * Highlights list with icons (Self check-in, Great location, Free cancellation)
    * Property description with expandable visual styling
    * "Where you'll sleep" bedroom card cards with bed icons
    * "What this place offers" 2-column amenities grid with SVG icons
    * Availability visual calendar preview
    * Reviews rating summary with CSS-based category score progress bars
    * Location & neighborhood static map card
* **Verification Gate:** All content blocks render cleanly with consistent 8px-based spacing and border dividers.

---

### Phase 5: Sticky Reservation Card & Native Form Mechanics
* **Goal:** Implement the high-converting sticky sidebar booking widget and native HTML form controls.
* **Deliverables:**
  - `<aside class="booking-sidebar">` styled with `position: sticky; top: 100px;`.
  - Elevation card container with border and box-shadow.
  - Pricing header with nightly rate and review score.
  - `<form class="reservation-form">`:
    * Segmented input container with border
    * Native `<input type="date">` for check-in and checkout
    * Native `<select>` for guest count
    * Primary CTA button ("Reserve") with signature coral gradient
    * "You won't be charged yet" reassurance notice
  - Cost calculation breakdown table (nights calculation, fees, total before taxes).
* **Verification Gate:** Sidebar remains sticky while scrolling through left column content; native date pickers and dropdowns function seamlessly.

---

### Phase 6: Responsive Layout Optimization & Visual QA
* **Goal:** Optimize layout for tablet and mobile viewports, including the mobile bottom booking bar.
* **Deliverables:**
  - Media queries for Tablet (`max-width: 1127px`) and Mobile (`max-width: 743px`):
    * Fluid column wrapping for main container
    * Photo gallery responsive collapse (single hero image on mobile)
    * Mobile sticky bottom booking bar (`position: fixed; bottom: 0; left: 0; width: 100%;`)
    * Global footer multi-column grid responsiveness
  - Cross-browser QA and accessibility audit.
* **Verification Gate:** Page functions seamlessly from 375px mobile screens up to 4K displays with 0 console errors and 0 JavaScript.
