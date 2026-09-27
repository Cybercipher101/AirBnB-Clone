# 🏡 The Glass House Malibu — Pure HTML5 & CSS3 Airbnb Clone

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript Free](https://img.shields.io/badge/JavaScript-0%25%20(Pure%20CSS)-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](#zero-javascript-invariants)
[![Responsive Design](https://img.shields.io/badge/Responsive-Mobile%20%7C%20Tablet%20%7C%20Desktop-222222?style=for-the-badge)](#responsive-design)
[![WCAG 2.1 AA](https://img.shields.io/badge/Accessibility-WCAG%202.1%20AA-008A05?style=for-the-badge)](#accessibility)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

A high-fidelity, pixel-accurate, and accessible single-page clone of an Airbnb luxury property listing page. Built entirely with **Semantic HTML5** and **Modern CSS3**, demonstrating mastery of raw DOM architecture, CSS Grid, Flexbox, positioning mechanisms, and pure CSS micro-interactions with **strictly 0% JavaScript**.

---

## 📸 Overview & Features

| Feature | Implementation | Highlight |
|---|---|---|
| **Global Navigation Header** | Sticky Flexbox Header | Logo wordmark, interactive 3-segment search pill (`Anywhere` \| `Any week` \| `Add guests`), and user profile menu capsule. |
| **Photo Gallery** | 2D Asymmetric CSS Grid | 5-photo grid (`2fr 1fr 1fr`) spanning 2 rows, hover zoom transitions, and a floating *"Show all 32 photos"* trigger button. |
| **Wishlist Save Toggle** | Pure CSS Checkbox Hack | Hidden `<input type="checkbox">` toggles heart icon fill to `#FF385C` with a pulse animation and dynamic *"Saved"* label without JavaScript. |
| **Two-Column Split Layout** | CSS Grid Layout | 65% / 35% desktop division between property details and conversion sidebar with an 80px visual breathing gap. |
| **Sticky Booking Widget** | `position: sticky; top: 100px;` | Elevated reservation card tracking viewport scroll alongside listing details, featuring live price breakdown and date selectors. |
| **Guest Selector Dropdown** | Semantic `<details>` / `<summary>` | Native popover displaying interactive adult/children stepper counters. |
| **Pure CSS Lightbox Modals** | CSS `:target` Pseudo-Class | `#gallery-modal` (32 photos) and `#amenities-modal` open with smooth backdrop blur and dismiss via anchor links. |
| **Reviews & Rating Breakdown** | CSS Progress Bars | 6-category rating meters (Cleanliness, Accuracy, Communication, Location, Check-in, Value) rendered with pure CSS tracks. |
| **Mobile Bottom Booking Bar** | `position: fixed; bottom: 0;` | Persistent conversion bar displaying price and *"Reserve"* button on mobile viewports (< 744px). |

---

## 🎨 Design System & Tokens

Architected following Airbnb's Design Language System (DLS) and MNC-tier UI/UX standards:

* **Color Palette:**
  * **Canvas:** Pure White (`#FFFFFF`)
  * **Surfaces:** Light Gray (`#F7F7F7`)
  * **Text Primary:** Off-Black (`#222222`, satisfies WCAG AA contrast)
  * **Text Secondary:** Muted Slate (`#717171`)
  * **Brand Accent:** Airbnb Coral (`#FF385C` to `#E61E4D` radial/linear gradient)
  * **Hairline Borders:** `#DDDDDD` / `#EBEBEB`
* **Typography:** System font stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`) with strict hierarchical scale (`26px` title, `22px` section headings, `16px` body, `14px` metadata).
* **Spacing:** 8pt modular grid (`8px`, `16px`, `24px`, `32px`, `48px`, `64px`, `80px`).
* **Elevation:** Layered ambient shadows for cards (`0 6px 16px rgba(0,0,0,0.12)`), search pill (`0 1px 2px ...`), and modals.

---

## ⚡ Zero-JavaScript Invariants

This project adheres to a strict architectural rule: **No JavaScript runtime dependencies**.

All dynamic behaviors are achieved through browser-native HTML5 and CSS3 capabilities:
1. **Interactive Modal Lightboxes:** Driven by URL fragment identifiers and the CSS `:target` pseudo-class:
   ```html
   <a href="#gallery-modal" class="btn-show-photos">Show all photos</a>
   <div id="gallery-modal" class="modal-overlay">...</div>
   ```
   ```css
   .modal-overlay { display: none; opacity: 0; }
   .modal-overlay:target { display: flex; opacity: 1; }
   ```
2. **Wishlist Heart Toggle:** Driven by CSS `:checked` pseudo-class:
   ```html
   <input type="checkbox" id="wishlist-toggle" class="wishlist-checkbox">
   <label for="wishlist-toggle" class="wishlist-label">...</label>
   ```
3. **Interactive Dropdowns & Collapsibles:** Powered by semantic `<details>` and `<summary>` elements with styled animated chevron indicators.

---

## 📱 Responsive Breakpoints

| Viewport | Range | Layout Characteristics |
|---|---|---|
| **Desktop** | `>= 1128px` | Full 2-column layout (65% details / 35% sticky sidebar), full 5-photo asymmetric grid, 3-segment search pill. |
| **Tablet** | `744px - 1127px` | Fluid 2-column container with 24px side padding, 4-photo grid scale-down. |
| **Mobile** | `< 744px` | Single-column linear flow, single hero image, inline reservation card, and sticky mobile bottom booking bar (`position: fixed; bottom: 0;`). |

---

## 📂 Project Directory Structure

```text
AirBnB Clone/
├── .planning/               # GSD Project Specifications & Memory
│   ├── config.json          # Workflow configuration
│   ├── PROJECT.md           # High-level project context & invariants
│   ├── REQUIREMENTS.md      # Detailed functional & non-functional requirements
│   ├── ROADMAP.md           # 6-phase completed roadmap & verification log
│   ├── STATE.md             # Project state & architectural audit
│   └── UI-SPEC.md           # MNC Senior UI/UX Design System Specification
├── index.html               # Main semantic HTML5 web document
├── listing-style.css        # External CSS3 stylesheet with design tokens
├── PRD.md                   # Product Requirements Document
├── Requirements.md          # Original MVP blueprint & guidelines
└── README.md                # Project documentation & maintenance guide
```

---

## 🚀 Quick Start (Running Locally)

Because this project relies strictly on foundational web standards, **no build steps, Node.js installations, or bundlers are required**.

### Option 1: Direct File Access
Simply double-click `index.html` or open it with your browser:
* **Windows:** Right click `index.html` → *Open with* → *Google Chrome / Microsoft Edge / Firefox*
* **macOS:** `open index.html`
* **Linux:** `xdg-open index.html`

### Option 2: Lightweight HTTP Server
If testing with a local server:

**Using Python (Pre-installed on most systems):**
```bash
# Python 3
python -m http.server 8080
```
Then visit `http://localhost:8080` in your web browser.

**Using VS Code Live Server Extension:**
Right-click `index.html` and select **"Open with Live Server"**.

---

## 🛠️ Maintenance & Contribution Guidelines

To preserve code quality and the project's educational integrity, please follow these guidelines:

1. **Maintain the 0% JavaScript Invariant:**
   * Do not introduce `.js` files, `<script>` tags, or inline `onclick`/`onload` attributes.
   * If adding new interactive features (e.g., accordions, tabs, tooltips), implement them using native semantic HTML elements (`<details>`, `<dialog>`) or CSS selectors (`:target`, `:checked`, `:hover`, `:focus-within`).
2. **Preserve External CSS Architecture:**
   * All styles must be defined inside `listing-style.css`. Avoid inline `style=""` attributes.
   * Utilize existing custom properties (`var(--color-...)`, `var(--space-...)`) instead of hardcoded hex values or pixel counts.
3. **Semantic HTML5 Integrity:**
   * Always prefer semantic container elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`) over generic `<div>` tags.
   * Ensure all images have descriptive `alt` text and form inputs have matching `<label>` elements.
4. **Git Workflow:**
   * Keep commits concise and meaningful (e.g., `feat: add mobile bottom booking bar`, `style: refine 8pt spacing grid`).

---

## 👤 Author & Acknowledgments

* **Developer:** **Shrut Dev Malviya** — Full-Stack Developer & Computer Science Student
* **GitHub:** [@Cybercipher101](https://github.com/Cybercipher101)
* **Inspiration:** [Airbnb](https://www.airbnb.com) Design Language System (DLS)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
