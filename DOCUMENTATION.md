# Wedding Invitation Website - Documentation

## Overview

A "Lore Obsessed" inspired wedding invitation website featuring minimalist, editorial design with veterinary-themed background animations. Built for **Mariane Joy & Renic**.

---

## Tech Stack

- **HTML5** - Semantic structure
- **Tailwind CSS (CDN)** - Utility-first styling
- **GSAP** - Advanced animations (ScrollTrigger, TextPlugin)
- **Vanilla JavaScript** - Interactive functionality
- **Lucide Icons (Inline SVG)** - Veterinary/medical themed icons

---

## Project Structure

```
wedding_web/
├── index.html          # Main single-page application
├── WORKLOG.md          # Development worklog
└── DOCUMENTATION.md    # This file
```

---

## Design System

### Typography
- **Headings**: Playfair Display (serif) - Elegant, editorial feel
- **Body**: Inter (sans-serif) - Clean, readable

### Color Palette

#### Light Mode
| Element | Color |
|---------|-------|
| Background | `#F9F9F9` (Paper-white) |
| Text | `#1A1A1A` (Ink-black) |
| Accents | `#B89B5E` (Gold) |
| Borders | `rgba(26, 26, 26, 0.12)` |
| Cards | `rgba(255, 255, 255, 0.65)` |

#### Dark Mode
| Element | Color |
|---------|-------|
| Background | `#0A0A0A` (Obsidian) |
| Text | `#E5E5E5` (Silver-white) |
| Accents | `#9A8452` (Muted Gold) |
| Borders | `rgba(229, 229, 229, 0.14)` |
| Cards | `rgba(10, 10, 10, 0.55)` |

---

## Sections

### 1. Navigation
- **Sticky header** with blur effect on scroll
- Transparent initially, solid blur background when scrolled
- Theme toggle (Light/Dark)
- Mobile responsive menu

### 2. Hero (Home)
- Cinematic letter-by-letter text reveal (GSAP)
- Couple names in massive serif font
- "Save the Date" countdown timer
- Dress code information
- **Floating veterinary icons** (subtle drift animation)

### 3. About
- Editorial card layout
- Couple introduction
- Vibe description

### 4. Story
- Vertical timeline with scroll reveals
- Key relationship milestones
- **Falling veterinary icons** (rain effect from top)

### 5. Venue
- Editorial cards with hover-reveal details
- Location information
- Arrival instructions

### 6. Program
- Clean schedule cards
- Timeline of events
- Hover interactions

### 7. Gallery
- Masonry layout (Pinterest-style)
- Lightbox functionality
- Click to expand images

### 8. Footer
- Thank you message
- Quick notes

---

## Features

### Theme Toggle
- Light/Dark mode switch
- Persists via localStorage (when served over HTTP)
- Graceful degradation for file:// protocol
- No flash on load (class applied in `<head>`)

### Custom Cursor
- Minimalist circle cursor
- Follows mouse with smooth interpolation
- Expands on hover over interactive elements
- `mix-blend-mode: difference` for visibility
- Respects `prefers-reduced-motion`

### Smooth Scrolling
- Anchor links scroll smoothly
- GSAP ScrollTrigger for section animations

### Countdown Timer
- Real-time countdown to wedding date
- Displays Days, Hours, Minutes, Seconds
- Configurable via `WEDDING_DATE_ISO` variable

### Veterinary Background Animations

#### Floating Elements (Home Section)
- **Icons**: Syringe, Stethoscope, Paw, Cat, Heart
- **Count**: 18 icons
- **Animation**: Gentle drift (X, Y, rotation, scale)
- **Duration**: 10-20 seconds per cycle
- **Opacity**: 22% (light), 14% (dark)
- **Size**: 40px

#### Falling Elements (Story Section)
- **Icons**: Pill, Syringe, Stethoscope, Heart, Activity
- **Count**: 15 icons
- **Animation**: Continuous fall from top to bottom
- **Duration**: 12-22 seconds per fall
- **Opacity**: 18% (light), 12% (dark)
- **Size**: 32px

Both animations:
- Use inline SVGs (no external dependencies)
- Trigger only on their respective sections
- Respect `prefers-reduced-motion`
- Non-blocking (`pointer-events: none`)

---

## Customization Guide

### Changing Couple Names
Edit these locations in `index.html`:
1. Hero heading (`<h1 id="heroNames">`)
2. About section - "The Couple" card
3. Footer name

### Changing Wedding Date
1. Update visible text in Hero section
2. Update `WEDDING_DATE_ISO` in the countdown script:
   ```javascript
   var WEDDING_DATE_ISO = '2026-12-14T15:30:00+08:00';
   ```

### Changing Venue
Edit the Venue section cards with:
- Venue name
- Address
- Parking/notes

### Changing Gallery Images
Replace the placeholder images array in the gallery script:
```javascript
var images = [
  'https://your-domain.com/photo1.jpg',
  'https://your-domain.com/photo2.jpg',
  // ...
];
```

### Modifying Background Icons
Edit the `icons` object in each animation script:
- Floating icons (Home): Line ~875
- Falling icons (Story): Line ~955

Available Lucide icons: https://lucide.dev/icons/

### Adjusting Animation Opacity
Edit CSS variables:
```css
.floating-icon { opacity: 0.22; }
.dark .floating-icon { opacity: 0.14; }

.falling-icon { opacity: 0.18; }
.dark .falling-icon { opacity: 0.12; }
```

---

## Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

**Requirements:**
- JavaScript enabled
- CSS Grid support
- ES6 support

---

## Performance Notes

- All animations use `transform` (GPU-accelerated)
- `will-change` applied to animated elements
- Icons use inline SVGs (no HTTP requests)
- Images lazy-loaded in gallery
- Respects `prefers-reduced-motion` for accessibility

---

## Known Limitations

1. **File Protocol (`file://`)**:
   - localStorage won't persist (browser security)
   - Some console warnings may appear
   - Solution: Serve via local HTTP server

2. **Tailwind CDN**:
   - Console warning about production use
   - Acceptable for this use case
   - For production: consider building Tailwind locally

---

## Development Commands

### Local Development Server

**Python 3:**
```bash
python -m http.server 5500
```

**Node.js (http-server):**
```bash
npx http-server -p 5500
```

**PHP:**
```bash
php -S localhost:5500
```

Then open: `http://localhost:5500`

---

## File Size

- `index.html`: ~35KB (self-contained)
- No external assets required (CDN-loaded)
- Total load: ~150KB with all CDNs

---

## Credits

- Design Inspiration: "Lore Obsessed" editorial aesthetic
- Icons: Lucide (inline SVGs)
- Animation: GSAP by GreenSock
- Typography: Google Fonts (Playfair Display, Inter)

---

## License

Created for personal use - Mariane Joy & Renic Wedding 2026
