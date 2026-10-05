# Tam Custom Tailor — website

Single-page static site (Next.js 16, App Router, Tailwind v4, GSAP + Lenis).

## Run

```bash
npm install
npm run dev                 # http://localhost:3000
npm run dev -- -H 0.0.0.0   # test on a phone/tablet via http://<your-LAN-IP>:3000
npm run build               # static export -> out/  (upload that folder to any host)
```

Set `NEXT_PUBLIC_SITE_URL` (e.g. `https://www.example.com`) before building once the
final domain is known; it is used for canonical, Open Graph, robots and sitemap URLs.

## Content & images

- All copy lives in `src/data/content.ts` (taken from the old Weebly site).
- Photos: `assets/photos/` holds the source images (not deployed). They are currently
  **free CC0 sample photos** (see `assets/photos/CREDITS.md`) standing in for the client's
  own photography. To replace one, overwrite the file with the same name and run
  `npm run images`; it regenerates AVIF/WebP/JPEG sizes and `src/data/images.generated.json`.
  The `photo` / `alt` / `position` fields per slot live in `src/data/content.ts`; remove
  `photo` to fall back to a labelled placeholder frame.
- `public/logo.png` is used unmodified. `npm run images` also writes proportional
  downscales of it plus the OG image and icons (logo on ivory).

## Structure

- `src/components/sections/` — page sections in scroll order
- `src/components/ui/` — RevealText, RevealImage, Preloader, Navbar, MenuOverlay,
  Cursor, MagneticButton, Marquee, Logo, Picture, PlaceholderFrame
- `src/lib/motion.ts` — shared easing, durations, breakpoints (gsap.matchMedia)
- `src/lib/gsap.ts` — plugin registration; `src/components/providers/SmoothScroll.tsx` — Lenis ↔ GSAP
