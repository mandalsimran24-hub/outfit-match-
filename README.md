# Atelier Wardrobe — Outfit Match

**Live demo:** https://atelierwardrobe.example.com (GitHub Pages: https://mandalsimran24-hub.github.io/outfit-match-/)

Atelier Wardrobe is a single-file browser app that helps you decide what to wear. Add items to your wardrobe — tops, bottoms, dresses, shoes, bags and accessories — optionally include a photo, pick the occasion, and the app ranks outfit combinations by color pairing, occasion fit and today's weather.

This repo contains a lightweight, dependency-free HTML file (index.html) that runs entirely in the browser — no backend, no build step, and no external dependencies required.

Why this looks like a small clothing site

- The interface is intentionally styled to feel like a boutique clothing landing page so it can be used as a portfolio piece for UI work as well as a practical tool.
- The app demonstrates UI, accessibility-friendly controls, client-side image handling, simple color theory, and a straightforward algorithm for scoring outfits.

What you'll find here

- index.html — the landing page and entry point for demo users.
- app.html — the single-file app users can open to manage a wardrobe and get outfit suggestions.

Design & behavior notes

- Photo uploads are compressed client-side to avoid filling localStorage with full-resolution images (images are resized to a 160px max dimension, saved as JPEG at 70% quality).
- Color matching converts colors to HSL and uses a simplified mix of analogous and complementary scoring; low-saturation / extreme lightness values are treated as neutrals.
- Event fit weights are applied as a pre-filter so the app doesn't suggest outfits that would be obviously inappropriate (e.g., a cocktail dress for the gym).
- Weather uses Open-Meteo (no API key required) when the user grants location permission.

Running locally

Open app.html in any modern browser. The weather feature requests location permission; if denied, the app falls back to neutral weather scoring and still works.

Domain & GitHub Pages

I recommend the domain "atelierwardrobe.app" for a modern, app-focused feel. If you'd like I can add a CNAME file to the repo for that domain — you'll need to add the corresponding DNS records with your registrar to point it to GitHub Pages.

Possible next steps

- Add social meta tags and an og:image for nicer sharing (done in the site).
- Add a tiny assets folder with favicon and social image.
- Create a LICENSE file and a short privacy policy for production readiness.

License

This repository is provided for demonstration and educational purposes. Feel free to fork and adapt.
