# EliteSelf OS — Landing Page

## What This Is
A single-page marketing/sales site for **EliteSelf OS** — a 60-day performance coaching program for founders, traders, and executives. The page sells discovery calls via Calendly. No backend, no build step.

## File Structure
```
elite-self/
  index.html      — the main landing page (HTML + CSS + JS, ~1700 lines, all in one file)
  blueprint.html  — the free abs guide / fat-loss lead magnet (self-contained page)
  _redirects      — Netlify rewrite: /abs → /blueprint.html (200), so the guide lives at a clean URL
  CLAUDE.md       — this file
```

## Abs Guide (Free Fat Loss Guide)
- Lives in `blueprint.html`, served live at **https://elite-self.com/abs** (Netlify `_redirects` rewrite, not a real folder)
- Canonical + og:url point to `/abs`; nav "Free Abs Guide" links (in both index.html and blueprint.html) point to `/abs`
- Ends with a testimonials carousel (`.ttrack`) of before/after transformation cards (`.tcard`)
- Card order (left→right): Prince 37, Trevor 39, Nitin 43, Jonathan 35, Michael 41, Daniel 37, Darius 32, Andrew 32
- Cards show first name + age only (no last names); role text `.tcard-role` is 0.8rem
- First/last card inset uses `scroll-padding` on `.ttrack` (mandatory scroll-snap eats plain padding/margin — must use scroll-padding)

## Tech Stack
- Pure HTML/CSS/JS — no framework, no build tool, no dependencies
- Google Fonts: Bebas Neue, DM Sans, JetBrains Mono (loaded via CDN)
- No package.json, no npm, no bundler
- Open `index.html` directly in a browser to preview (or use `python3 -m http.server`)

## Design System
- `--black: #080808` (body bg)
- `--dark: #0f0f0f` (section bg alternate)
- `--card: #141414`
- `--border: #1e1e1e`
- `--green-accent: #7ed957` (primary accent — same as client-dashboard)
- `--green-light: #9be872`
- `--white: #f5f5f0`
- `--gray: #888880`
- Fonts: Bebas Neue (headings), DM Sans (body), JetBrains Mono (tags/labels)

## Page Sections (in order)
1. **Nav** — logo + "Book Discovery Call" CTA → Calendly
2. **Hero** — headline, sub, two CTAs (primary: Calendly, secondary: #offer anchor), 3 stats
3. **Problem** — "You're Running The Wrong OS" — 3 problem items
4. **Quote Break** — full-width pull quote
5. **Who It's For** — Founders, Traders, Executives
6. **Dashboard** — feature grid + screenshot showcase (full-width)
7. **How It Works** — 3 steps: Identify Gap → Build Protocol → Execute & Track
8. **Truth** — "Showing Up Exhausted Isn't Noble" callout
9. **Testimonials** — horizontal drag-to-scroll carousel (3 cards: Jonathan Billiot, Trevor, Daniel)
10. **Offer** (`#offer`) — $497 (regular $997), feature list, guarantee, Calendly CTA
11. **Final CTA** — "You Already Know Something Needs To Change"
12. **Footer** — logo + copyright

## Key Links
- **Primary CTA**: `https://calendly.com/eliteselfcoaching/performance-os`
- All CTAs point to that same Calendly URL

## JavaScript (inline, bottom of file)
- **Scroll reveal** — IntersectionObserver animates `.reveal` elements in on scroll
- **Testimonial drag-to-scroll** — mousedown/mousemove/touchstart drag on `#testimonialsTrack`

## Editing Notes
- All CSS is in `<style>` in `<head>` (~1300 lines)
- All HTML content starts at line ~1296 (`<!-- NAV -->`)
- Responsive breakpoints: `@media (max-width: 768px)` and `@media (max-width: 480px)`

## Deploying Live (one shot)
GitHub repo: `https://github.com/eliteself13/elite-self`
Netlify auto-deploys from `main` branch.

```bash
git -C ~/Developer/elite-self add -A && git -C ~/Developer/elite-self commit -m "your message" && git -C ~/Developer/elite-self push origin main
```

That's it — Netlify picks it up automatically within ~30 seconds.
