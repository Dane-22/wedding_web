# Wedding Invitation Website — Worklog & Documentation

## Project
- **Style**: "Lore Obsessed" inspired (editorial, high-fashion, minimalist)
- **Stack**: HTML5 + Tailwind CSS (CDN) + GSAP (ScrollTrigger, TextPlugin) + Vanilla JS
- **Key Features**:
  - Light/Dark mode toggle (persisted via LocalStorage)
  - Scroll-driven section transitions (GSAP ScrollTrigger)
  - Hero text reveal (letter-by-letter)
  - Custom cursor (hover expand/invert)
  - Smooth scrolling
  - Countdown timer
  - Masonry gallery + lightbox

## Goals / Requirements
- **Typography**:
  - Headings: Playfair Display
  - Body: Inter
- **Palette**:
  - Light: Paper-white `#F9F9F9`, Ink-black `#1A1A1A`, subtle gold accents
  - Dark: Obsidian `#0A0A0A`, Silver-white `#E5E5E5`, muted gold accents
- **Layout**:
  - High contrast
  - Generous whitespace
  - Asymmetric grids
- **Sections**:
  - Sticky nav (transparent -> solid blur on scroll): Home, About, Story, Venue, Program, Gallery
  - Hero (cinematic intro with massive serif names)
  - Story timeline (scroll reveals)
  - Venue/Program editorial cards (hover reveal)
  - Gallery masonry + lightbox
- **Responsiveness**:
  - Pixel-perfect mobile layout

## Project Structure (planned)
- `index.html`
- `assets/` (optional)
  - `images/` (optional: local images)

## Running Locally
- Open `index.html` directly in the browser, or serve the folder with a local static server.

## Content Inputs (fill these in)
- **Couple Names**: 
- **Wedding Date & Time**: 
- **Timezone (for countdown)**: 
- **Venue Name & Address**: 
- **Program Items**: 
- **Gallery Images**:
  - Option A: Local files in `assets/images/`
  - Option B: Hosted image URLs

## Worklog

### 2026-03-30
- **Created**: `WORKLOG.md`
- **Planned**: Build single-page invitation site with Tailwind CDN + GSAP interactions.

## QA Checklist
- **Theme**:
  - Toggle works
  - Persists after refresh
  - No flashing wrong theme on load
- **Animations**:
  - Hero text reveal runs once
  - Each section has ScrollTrigger transition
  - Timeline items reveal smoothly
- **Gallery**:
  - Masonry layout responsive
  - Lightbox opens/closes and supports keyboard escape
- **Cursor**:
  - Follows smoothly
  - Hover state applies to buttons/links/images
- **Performance**:
  - Avoid heavy DOM work in scroll handlers
  - No memory leaks (remove listeners where appropriate)

## Notes
- Keep everything minimal and editorial.
- Avoid changing visual design unless requested.
