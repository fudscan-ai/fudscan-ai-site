# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Fudscan** is a static marketing website for the Fudscan AI project - an AI-powered crypto/web3 project scanner bot that performs instant due diligence on crypto projects, whitepapers, smart contracts, and teams. The site is built using the "Ashley" HTML template (by Nazar Miller/millerDigitalDesign).

This is a client-side only static website with no build process or server-side components.

## Project Structure

```
Ashley html template/ashley/
├── css/
│   ├── plugins/          # Third-party CSS (Bootstrap Grid, Font Awesome, Swiper, Fancybox)
│   └── style.css         # Main stylesheet
├── js/
│   ├── plugins/          # jQuery, GSAP, ScrollTrigger, Swiper, Swup, etc.
│   └── main.js           # Main JavaScript file with animations and interactions
├── img/                  # Image assets
├── scss/                 # SCSS source files (if using Prepros for compilation)
├── *.html                # Individual page templates
└── prepros.config        # Prepros configuration for SCSS compilation

PROJECT_DESCRIPTION.md    # Detailed project information and tokenomics
```

## Technology Stack

- **Frontend Framework**: Pure HTML/CSS/JavaScript (no framework)
- **CSS Framework**: Bootstrap Grid (minimal, grid-only)
- **JavaScript Libraries**:
  - jQuery
  - GSAP (animations) with ScrollTrigger and ScrollToPlugin
  - Swiper.js (sliders/carousels)
  - Swup (page transitions)
  - Fancybox (lightbox)
  - Tilt.js (3D tilt effects)
- **Icons**: Font Awesome
- **CSS Preprocessor**: SCSS (compiled with Prepros)

## Development Workflow

### Serving the Site Locally

Since this is a static site, use any simple HTTP server:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (if http-server is installed globally)
npx http-server -p 8000

# Then navigate to http://localhost:8000/Ashley html template/ashley/
```

### Working with Styles

The template uses SCSS. If you need to modify styles:

1. Edit SCSS files in `Ashley html template/ashley/scss/`
2. Compile using Prepros (desktop app) or another SCSS compiler
3. The compiled output goes to `Ashley html template/ashley/css/style.css`

For quick changes, you can edit `style.css` directly, but this is not recommended for maintainability.

### Page Structure

All HTML pages follow the same structural pattern:

```html
<div class="mil-wrapper" id="top">
  <div class="mil-ball"><!-- Custom cursor --></div>
  <div class="mil-preloader"><!-- Preloader animation --></div>
  <div class="mil-progress-track"><!-- Scroll progress --></div>
  <div class="mil-menu-frame"><!-- Navigation menu --></div>

  <!-- Page content wrapped in swup containers -->
  <div id="swupMain">
    <!-- Actual page content -->
  </div>

  <footer><!-- Footer --></footer>
</div>
```

## Key Features & Components

### Page Transitions (Swup)
- Handles smooth SPA-like page transitions
- Containers: `#swupMain` and `#swupMenu`
- Animation selector: `.mil-main-transition`

### Custom Cursor
- Implemented via `.mil-ball` element
- Changes state on hover over interactive elements (`.mil-drag`, `.mil-more`, `.mil-choose`)

### Animations (GSAP)
- Scroll-triggered animations using ScrollTrigger
- Elements with `.mil-up` class fade in on scroll
- Parallax effects on `.mil-parallax` elements
- Rotation animations on `.mil-rotate` elements
- Scale animations on `.mil-scale` elements

### Sliders (Swiper)
- Reviews slider (`.mil-reviews-slider`)
- Infinite slider (`.mil-infinite-show`)
- Portfolio slider (`.mil-portfolio-slider`)
- 1-item and 2-item sliders (`.mil-1-slider`, `.mil-2-slider`)

### Accordions
- Custom accordion implementation using GSAP animations
- Selector: `.mil-accordion-group`

### Available Pages
- `home-1.html` - Main landing page
- `home-2.html` - Personal variant
- `portfolio-1.html`, `portfolio-2.html`, `portfolio-3.html` - Portfolio grids and slider
- `project-1.html` through `project-6.html` - Individual project pages
- `services.html`, `service.html` - Services pages
- `team.html` - Team page
- `blog.html`, `blog-inner.html` - Blog pages
- `publication.html` - Publications
- `contact.html` - Contact page
- `404.html` - Error page

## Customization for Fudscan

When adapting this template for Fudscan:

1. **Branding**: Update logo (currently "A."), colors (accent color set in `main.js` line 41: `var accent = 'rgba(255, 152, 0, 1)'`)
2. **Content**: Replace placeholder text with Fudscan content from `PROJECT_DESCRIPTION.md`
3. **Preloader**: Update preloader text (currently shows "Pioneering / Creative / Excellence" and "ashley.com")
4. **Navigation**: Update menu structure in `.mil-main-menu`
5. **Social Links**: Update social media links in footer
6. **Meta Tags**: Update title, description, and Open Graph tags in each HTML file

## Notes

- The template is designed for creative agencies/portfolios, so significant content adaptation is needed for crypto/AI focus
- All JavaScript is in a single `main.js` file with reinit logic for Swup page transitions
- The site is fully responsive with mobile breakpoints
- Custom cursor only appears on desktop (pointer devices)
- GSAP animations are performance-optimized with hardware acceleration
