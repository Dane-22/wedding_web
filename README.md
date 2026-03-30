# Mariane Joy & Renic - Wedding Invitation Website

A beautiful, editorial-style wedding invitation website featuring minimalist design with veterinary-themed falling animations. Built with pure HTML5, Tailwind CSS, and GSAP.

![Wedding Website](screenshot.png)

## Features

- **Editorial Design**: "Lore Obsessed" inspired aesthetic with Playfair Display & Inter typography
- **Light/Dark Mode**: Toggle between elegant light and dark themes
- **Countdown Timer**: Real-time countdown to the wedding date
- **Veterinary Animations**: Subtle falling medical/pet icons in the Story section
- **Responsive**: Pixel-perfect on mobile and desktop
- **Smooth Animations**: GSAP ScrollTrigger for section reveals and custom cursor

## Tech Stack

- HTML5 (semantic structure)
- Tailwind CSS (CDN)
- GSAP + ScrollTrigger + TextPlugin
- Vanilla JavaScript
- Inline SVG icons

## Project Structure

```
wedding_web/
├── index.html          # Main single-page application
├── netlify.toml        # Deployment configuration
├── .gitignore          # Git ignore rules
├── WORKLOG.md          # Development worklog
├── DOCUMENTATION.md    # Complete documentation
└── README.md           # This file
```

## Quick Start

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/mariane-joy-renic-wedding.git
   cd mariane-joy-renic-wedding
   ```

2. Open `index.html` in your browser or serve locally:
   ```bash
   python -m http.server 5500
   # or
   npx serve
   ```

3. Visit `http://localhost:5500`

## Customization

### Change Couple Names
Edit `index.html`:
- Line ~284: Hero heading
- Line ~389: About section
- Line ~563: Footer

### Change Wedding Date
1. Update visible text in Hero section (line ~295)
2. Update `WEDDING_DATE_ISO` in countdown script (line ~706)

### Change Venue
Edit the Venue section cards (lines ~456-505)

### Change Gallery Images
Replace the placeholder images array in the gallery script (lines ~751-760)

## Deployment

### Deploy to Vercel
1. Push to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your GitHub repository
4. Deploy!

### Deploy to Netlify
1. Push to GitHub
2. Go to [netlify.com](https://netlify.com)
3. Connect your repository
4. Deploy!

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Credits

- Design: "Lore Obsessed" editorial aesthetic
- Fonts: Google Fonts (Playfair Display, Inter)
- Icons: Lucide (inline SVGs)
- Animation: GSAP by GreenSock

## License

Created for personal use - Mariane Joy & Renic Wedding 2026
