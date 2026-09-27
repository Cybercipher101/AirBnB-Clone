# UI Specification Contract (UI-SPEC.md)
## Airbnb Property Listing Clone (HTML5 & CSS3 Only)

**Design System:** Airbnb Luxury / Design Language System (DLS)  
**Lead Designer Persona:** Senior UI/UX Designer (15+ Years MNC Experience)  
**Design Frameworks Applied:** Atomic Design, Gestalt Psychology, F-Pattern Scanning, Hick's Law, WCAG 2.1 AA  
**Constraint Mandate:** **100% Pure HTML5 & CSS3** (0% JavaScript, Zero External Frameworks, Zero Build Tools)

---

## 1. Design Philosophy & Cognitive Psychology

### 1.1 Gestalt Principles
* **Law of Common Region:** The sticky booking widget and sleeping arrangement cards are enclosed within dedicated hairline borders (`1px solid var(--color-border-light)`) and soft ambient shadows to immediately signal discrete interactive zones.
* **Law of Proximity:** Form inputs, date pickers, and price calculation rows are spaced tightly (8px-12px) to communicate direct functional interdependence, while distinct sections are separated by 32px-48px with subtle hairline dividers.
* **Law of Similarity:** All interactive action pills (search segments, share/save buttons, "Show all" buttons) share uniform pill radii (`9999px`), neutral hover tints (`#F7F7F7`), and identical transition timings (`0.2s cubic-bezier(0.2, 0, 0, 1)`).

### 1.2 F-Pattern Visual Hierarchy
1. **Top Bar (Horizontal Scan):** Instantly anchors identity (Airbnb logo), search affordance (central pill), and profile utility.
2. **Hero Header & Media (Impact Zone):** Prominent `<h1>` title immediately followed by the asymmetric 5-photo grid (50% visual weight on primary hero photo, 50% split across 4 lifestyle quadrant photos).
3. **Core Split (Two-Column Scan):** 
   - Left column (`65%` width) drives **Desire & Evaluation** (Host credibility, property narrative, bedroom comfort, amenities, reviews).
   - Right column (`35%` width) drives **Action & Conversion** (Sticky reservation widget anchored at eye-level throughout scrolling).

---

## 2. Design Tokens & Styling Primitives

All tokens are defined in `:root` inside `listing-style.css`:

```css
:root {
  /* Brand & Theme Colors */
  --color-canvas: #FFFFFF;
  --color-surface-subtle: #F7F7F7;
  --color-surface-card: #FFFFFF;
  --color-text-primary: #222222;
  --color-text-secondary: #717171;
  --color-text-dark: #000000;
  
  /* Borders & Dividers */
  --color-border-hairline: #DDDDDD;
  --color-border-subtle: #EBEBEB;
  --color-border-focus: #222222;
  
  /* Airbnb Coral Brand Accents */
  --color-brand-coral: #FF385C;
  --color-brand-gradient: linear-gradient(to right, #E61E4D 0%, #E31C5F 50%, #D70466 100%);
  --color-brand-hover: #E00B41;
  
  /* Status & Accents */
  --color-star-gold: #FF385C;
  --color-badge-bg: #F0EFE9;
  --color-success: #008A05;

  /* Typography Scale */
  --font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --font-size-xs: 0.75rem;    /* 12px */
  --font-size-sm: 0.875rem;   /* 14px */
  --font-size-base: 1rem;     /* 16px */
  --font-size-md: 1.125rem;   /* 18px */
  --font-size-lg: 1.375rem;   /* 22px */
  --font-size-xl: 1.625rem;   /* 26px */
  --font-size-2xl: 2rem;      /* 32px */
  
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Spacing Scale (8pt Grid) */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
  --space-20: 80px;

  /* Elevation & Layered Shadows */
  --shadow-subtle: 0 1px 2px rgba(0, 0, 0, 0.08);
  --shadow-card: 0 6px 16px rgba(0, 0, 0, 0.12);
  --shadow-hover: 0 6px 20px rgba(0, 0, 0, 0.15);
  --shadow-header: 0 1px 0 rgba(0, 0, 0, 0.08);
  --shadow-modal: 0 16px 40px rgba(0, 0, 0, 0.25);

  /* Border Radii */
  --radius-xs: 4px;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-pill: 9999px;

  /* Motion & Transitions */
  --transition-fast: 0.15s ease;
  --transition-smooth: 0.25s cubic-bezier(0.2, 0, 0, 1);
  --transition-bounce: 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

---

## 3. Atomic Design Architecture

### 3.1 Atoms
* **Typography:** Headers (`h1`, `h2`, `h3`), paragraph body text, inline metadata links, rating labels.
* **Badges:** "Guest favorite" award ribbon, "Superhost" medal, rare find indicator.
* **Buttons:** 
  * Primary conversion button ("Reserve" gradient button with micro-sheen).
  * Ghost/Pill buttons ("Show all photos", "Show all 45 amenities", "Report listing").
  * Icon buttons (Heart Save, Share, Language Globe, Navigation search).
* **Inputs & Controls:** Native `<input type="date">`, native `<select>` guest count, `<input type="checkbox">` toggles.
* **Rating Progress Bars:** High-contrast meter track (`#EBEBEB`) and filled score bar (`#222222`).

### 3.2 Molecules
* **Search Pill:** 3 interactive segments (`Anywhere` | `Any week` | `Add guests`) + circular coral search trigger.
* **User Profile Pill:** Rounded capsule with hamburger icon and circular user avatar.
* **Metadata Bar:** Star rating + review count + Superhost badge + breadcrumb location + Share & Save buttons.
* **Sleeping Room Card:** Card with stylized bed SVG icon, room title, and bed configuration text.
* **Amenity Item:** Inline SVG icon paired with title and description.
* **Review Item:** Reviewer avatar + name + rating date + testimonial text.
* **Price Line Item:** Calculation description (e.g. `$450 × 5 nights`) and formatted amount.

### 3.3 Organisms
* **Global Navigation Header (`<header class="site-header">`):** Fixed top navigation bar.
* **Asymmetric 5-Photo Grid Gallery (`<section class="photo-gallery">`):** 2fr / 1fr / 1fr grid with 1 master photo and 4 quadrant photos.
* **Property Detail Section (`<article class="listing-details">`):** Host banner, property highlights, description with CSS expander, bedroom cards, amenities list, availability calendar, rating breakdown, reviews, and neighborhood map.
* **Sticky Booking Sidebar (`<aside class="booking-sidebar">`):** `position: sticky; top: 90px;` booking card with live calculation table.
* **Pure CSS Modals:** Full photo lightbox modal (`#gallery-modal`) and amenities modal (`#amenities-modal`) operated via `:target`.
* **Global Footer (`<footer class="site-footer">`):** 4-column sitemap and copyright bar.

---

## 4. Pure HTML & CSS Functional Innovations (0% JavaScript)

| Interaction | Traditional JS Method | Pure HTML5 & CSS3 Implementation |
|---|---|---|
| **Wishlist Save Toggle** | React `useState` / JS click handler | Hidden `<input type="checkbox" id="wishlist-toggle">` + `<label for="wishlist-toggle">` with CSS `:checked` selector that fills the heart SVG with `#FF385C` and triggers a pop/scale animation (`transform: scale(1.2)`). |
| **Sticky Booking Widget** | Scroll event listener / intersection observer | Native `position: sticky; top: 90px; align-self: start;` inside a Flex/Grid container. |
| **Full Photo Lightbox Modal** | JS Modal component / React Portal | CSS `:target` pseudo-class. Link `<a href="#gallery-modal">` opens modal; `<a href="#close">` dismisses modal with smooth opacity fade. |
| **Amenities Lightbox Modal** | JS Modal / Popup library | CSS `:target` pseudo-class on `#amenities-modal`. |
| **Guest Picker Dropdown** | JS Dropdown library | Native `<details class="guest-selector-details">` with `<summary>` styled as an Airbnb input card, opening an interactive guest allocation panel. |
| **"Read More" Text Expander** | JS toggle height / clamp | CSS `<details>` / `<summary>` or checkbox fold technique for smooth content expansion. |
| **Category Rating Progress** | JS Chart library | Pure CSS Flexbox tracks with inline style width percentages (`width: 98%`) and smooth CSS transitions. |

---

## 5. Responsive Viewport Strategy

1. **Desktop Large (`>= 1128px`):**
   - Max content container: `1120px; margin: 0 auto;`.
   - Photo gallery: Full 5-photo asymmetric grid (480px height).
   - Main content: 2 columns (`65%` left details, `35%` sticky sidebar) with `80px` gap.
2. **Tablet (`744px - 1127px`):**
   - Container padding: `24px` horizontal.
   - Main content: 2 columns (`60%` / `40%`) with `32px` gap.
   - Sidebar maintains sticky behavior.
3. **Mobile (`< 744px`):**
   - Gallery collapses to a single full-width hero photo with a floating photo counter badge.
   - Main content transitions to a single linear vertical stack (`100%` width).
   - Sidebar converts to a standard card inline, and an elegant **Sticky Mobile Booking Bar** appears at the bottom (`position: fixed; bottom: 0; left: 0; width: 100%; z-index: 100;`).
