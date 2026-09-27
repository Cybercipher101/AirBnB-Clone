# Full Project Blueprint & Requirements: Listing Clone MVP

**Prepared for:** Shrut Dev Malviya
**Role:** Full-Stack Developer / Computer Science Student
**Project:** Pure HTML & CSS Property Listing Clone

---

## 1. Product Requirements Document (PRD)

**Project Overview:**
This project is a static, single-page clone of a modern property rental platform. The goal is to translate a high-fidelity visual design into a structured, accessible, and responsive web document using only foundational web technologies. 

**Business & Learning Objectives:**
*   **What:** Build a visual clone of a listing layout.
*   **Need:** To demonstrate mastery of HTML document flow, CSS layout mechanics (Flexbox and Grid), and form construction without relying on external libraries.
*   **Why:** Understanding the raw DOM (Document Object Model) and pure CSS is a mandatory prerequisite. Mastering these pure DOM fundamentals now is exactly what will make your component architectures bulletproof when you are building full-stack applications with React, Next.js, or Node.
*   **How:** By creating a strict separation of concerns—HTML for structure and an external CSS file for presentation.

---

## 2. Minimum Viable Product (MVP) Scope

**What is Included (The MVP):**
*   A global navigation header with a search pill and profile menu.
*   A listing title section with semantic metadata (ratings, location).
*   An asymmetric CSS Grid photo gallery (1 hero image, 4 sub-images).
*   A two-column layout separating the property details from the booking form.
*   A sticky reservation form capturing dates and guest counts.

**What is Excluded (To keep this focused on layout basics):**
*   **JavaScript:** No dynamic price updates or functioning image carousels. *Why?* To maintain focus purely on structure and styling.
*   **Backend Databases:** The form will not submit data anywhere. *Why?* The scope is strictly front-end presentation.
*   **Complex Tooling:** No build steps, bundlers, or CSS preprocessors. *Why?* A standard `.html` and `.css` file setup eliminates configuration fatigue and keeps the environment lightweight.

---

## 3. Tech Stack Definition

*   **HTML5 (HyperText Markup Language)**
    *   **Need:** It provides the skeleton of the application.
    *   **Why:** Browsers need semantic meaning to understand what a button is versus a paragraph.
    *   **How:** We will use semantic tags like `<main>`, `<section>`, `<aside>`, and `<header>` rather than generic `<div>` containers wherever possible.
*   **CSS3 (Cascading Style Sheets - External)**
    *   **Need:** It provides the visual styling, positioning, and responsive behavior.
    *   **Why:** Using an *external* stylesheet keeps the HTML clean and allows you to cache styles for faster page loads.
    *   **How:** We will utilize **CSS Flexbox** for linear alignments (like the navigation bar) and **CSS Grid** for two-dimensional layouts (like the photo gallery).

---

## 4. Application / User Flow

Even without JavaScript, the user experiences a "flow" as they scan the page visually.

1.  **Identity & Search (Header):** The user lands and instantly recognizes the brand and search utilities. *How:* Fixed top navigation.
2.  **Desire & Validation (Hero & Gallery):** The user reads the high-contrast property title and is drawn into the CSS Grid photo gallery. *Why:* High-quality imagery builds trust and emotional connection.
3.  **Evaluation (Left Column):** The user scrolls down to read the host details, text descriptions, and amenity chips. *Need:* This provides the logical justification for the booking.
4.  **Conversion (Right Column):** As the user scrolls, the booking form "sticks" to the screen. *Why:* Keeping the form permanently in the viewport drastically increases conversion rates. *How:* `position: sticky` in CSS.

---

## 5. UI Base & Design System

*   **Typography:** System fonts (`-apple-system, sans-serif`). 
    *   *Why:* Zero load time and perfectly optimized for whatever OS the user is on.
*   **Color Palette:** 
    *   **Canvas:** Pure White (`#FFFFFF`). *Need:* Clean, breathable background.
    *   **Text:** Off-Black (`#222222`). *Why:* Pure black causes eye strain on digital screens; off-black is softer.
    *   **Accent/CTA:** Vibrant Coral (`#FF385C`). *How:* Used *only* on the "Reserve" button to draw the eye immediately to the conversion point.
*   **Spacing System:** Multiples of 8px (8, 16, 24, 32). 
    *   *Need:* Consistent spacing creates a subconscious feeling of quality and order.

---

## 6. `memory.md` (Project Tracker)

Create a file named `memory.md` in your project folder. This acts as your external brain, tracking what has been built and what remains in the pipeline.

```markdown
# Project Memory & Progress Log

- [ ] **Step 1: Environment Setup**
  - [ ] Create `index.html`.
  - [ ] Create `listing-style.css`.
  - [ ] Link the CSS file inside the HTML `<head>`. (Why: Separates structure from design).

- [ ] **Step 2: HTML Scaffolding**
  - [ ] Build `<header>` navigation.
  - [ ] Build `<main>` container.
  - [ ] Add `<section>` for title and metadata.
  - [ ] Add `<section>` for the 5-image gallery.
  - [ ] Build the two-column split (`<div class="left">`, `<aside class="right">`).

- [ ] **Step 3: Form Construction (The Sticky Sidebar)**
  - [ ] Add `<form>` tag.
  - [ ] Add `<input type="date">` for check-in/out. (Need: Native browser calendar UI).
  - [ ] Add `<select>` for guest count.
  - [ ] Add `<button type="submit">` for reservation.

- [ ] **Step 4: CSS Styling & Layout**
  - [ ] Apply CSS Flexbox to the header.
  - [ ] Apply CSS Grid to the photo gallery. (How: `grid-template-columns: 2fr 1fr 1fr`).
  - [ ] Apply `position: sticky` to the sidebar.