# CLAUDE.md — lateeflaw.info

## Project Overview

Personal portfolio and resume website for **Lateef Law**, a dual CCIE-certified Network Architect and Cloud Engineer with 15+ years of experience in DoD infrastructure, multi-cloud architecture, and enterprise networking. The site targets DoD agencies, enterprise clients, and consulting opportunities.

**Live site:** lateeflaw.com
**Contact email:** contact@lateeflaw.com
**Copyright year:** 2026

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 (semantic) |
| Styling | CSS3 (embedded, CSS variables, Grid, keyframe animations) |
| Behavior | Vanilla JavaScript (no frameworks or libraries) |
| Fonts | Google Fonts — Barlow Condensed, Barlow, Share Tech Mono |
| Build | None — single static file, deploy as-is |
| Form handling | `mailto:` (opens email client — no backend) |

**Zero external JS dependencies.** All code is embedded in one file.

## Folder Structure

```
lateeflaw.info/
└── index.html   # Entire site — HTML + embedded CSS + embedded JavaScript (1,808 lines, ~64KB)
```

This is intentionally a single-file project. Keep it that way unless given an explicit reason to split.

## Key File: index.html

Structure inside the file:

```
<head>
  Google Fonts preconnect + stylesheet
  <style> ... </style>   ← All CSS (~900 lines)
</head>
<body>
  <nav>              Sticky navbar + mobile hamburger menu
  <section#hero>     Full-screen intro, typewriter, badges, CTAs
  <div.stats-bar>    4 animated counters (15+ yrs, 2× CCIE, 40K+ users, TS clearance)
  <section#about>    Bio, education (BBA Baruch / MS Kaplan), credentials grid
  <section#skills>   6 specialization cards with 3D tilt effect
  <section#experience>  Timeline of 7 career roles (2001–present)
  <section#projects> 6 project showcases
  <section#certs>    9 certification tiles (2 gold CCIE)
  <section#testimonials>  2 placeholder testimonial cards
  <section#contact>  Contact form + clearance badge
  <footer>           Copyright + social links (LinkedIn/GitHub — links empty)
  <script> ... </script>  ← All JavaScript (~200 lines)
</body>
```

## Design System

CSS variables defined in `:root`:

| Variable | Value | Usage |
|----------|-------|-------|
| `--bg0` | `#080d1a` | Darkest background |
| `--bg1` | `#0d1425` | Medium dark |
| `--bg2` | `#111c30` | Section backgrounds |
| `--accent` | `#00d4ff` | Primary cyan/electric blue |
| `--accent-dim` | `rgba(0,212,255,0.1)` | Subtle accents |
| `--accent-glow` | `rgba(0,212,255,0.3)` | Glow effects |
| `--gold` | `#f0b429` | CCIE certs, awards |
| `--green` | `#22c55e` | Active status, clearance |
| `--text` | `#c8d8e8` | Primary text |
| `--muted` | `#7a90a8` | Secondary text |
| `--border` | `rgba(0,212,255,0.12)` | Borders |

**Aesthetic:** Dark futuristic tech — think enterprise network ops center.

## JavaScript Features

All vanilla, no libraries:

- **Sticky navbar** — adds `.scrolled` class after 30px scroll
- **Mobile hamburger menu** — toggle with overlay, closes on nav link click
- **Scroll reveal animations** — IntersectionObserver on `.reveal`, `.reveal-left`, `.reveal-right`
- **Typewriter effect** — cycles 5 phrases in the hero (60ms type / 35ms delete)
- **Animated stat counters** — requestAnimationFrame, 1200ms duration, triggers at 50% visibility
- **3D card tilt** — mousemove parallax on `.skill-card` using CSS perspective transforms

## Content — Key Personal Details

| Field | Value |
|-------|-------|
| Current employer | General Dynamics (Defense Logistics Agency) |
| Title | Cloud Network Engineer / Enterprise Architect |
| Tenure | Dec 2018 – Present |
| Certifications | CCIE Enterprise, CCIE SP, AZ-104, AZ-700, OCI Foundations, CCSA, CASP+, CAP, Network+ |
| Award | BEYA 2023 Modern-Day Technology Leader |
| Security clearance | Active Top Secret |
| Military | USMC Veteran (MOS 2542, Honorable Discharge) |
| Education | BBA — Baruch College; MS Information Technology — Kaplan University |

### Career Timeline (reverse chrono)

1. Cloud Network Engineer / Enterprise Architect — General Dynamics (Dec 2018–present)
2. Senior Systems Engineer — NES Associates (Aug–Dec 2018)
3. Senior Network Engineer — Phoenix House Foundation (Jul 2013–Jul 2018)
4. Field Network Engineer — GOS Technical Services (Feb 2012–Jul 2013)
5. Network Administrator / Consultant — Tate LLC (Jun 2011–Mar 2012)
6. Field Technician — Verizon Communications (Jan 2005–Dec 2009)
7. Communications Center Operator — USMC (–2001)

### Projects Showcased

1. **EVE-NG Network Automation Lab** — Cisco ISE, Ansible, RADIUS/TACACS+, AD/DNS
2. **AI Second Brain** — PostgreSQL/pgvector (Supabase), Voyage AI, MCP Server, Claude Desktop
3. **Multi-Agent AI Operating System** — Obsidian, Python, Flask, email/calendar automation
4. **STIG PowerShell Automation Engine** — 100+ DoD CKL files, DLA production
5. **Custom Web Builds** — PepTek (Shopify), JBExclusive Studios (WIX), Divine Assisted Care (HIPAA)
6. **Python Network Automation Framework** — Netmiko, Ansible, REST APIs

## Deployment

**Hosting:** Static file — no build step required.

Compatible with:
- GitHub Pages
- Netlify (consider enabling Netlify Forms to replace `mailto:`)
- Vercel
- AWS S3 + CloudFront
- Any traditional web host

**Form note:** Current contact form uses `action="mailto:contact@lateeflaw.com"` which opens the user's email client. For a proper form submission experience, swap in Netlify Forms, Formspree, or a backend endpoint.

**Social links:** LinkedIn and GitHub `<a>` tags in the footer currently have empty `href` attributes — fill these in when accounts are ready.

## Responsive Breakpoints

| Breakpoint | Target |
|-----------|--------|
| `768px` | Tablet — grid collapses, hamburger activates |
| `600px` | Large mobile — further layout adjustments |
| `480px` | Small mobile — typography/spacing tweaks |

## CSS Animations

| Name | Purpose |
|------|---------|
| `scan-sweep` | Horizontal scan line across hero section |
| `blink-cursor` | Typewriter cursor blink |
| `pulse-green` | Green badge pulse (clearance status) |
| `pulse-dot` | Dot pulsing animation |
| `blink-green` | Slower clearance indicator blink |

## Important Notes for Future Sessions

- **Do not split into multiple files** unless explicitly asked. The single-file approach is intentional.
- **Do not introduce frameworks** (React, Vue, etc.) unless asked. This is a deliberate vanilla stack.
- **Preserve the CSS variable system** — all color changes should go through `:root` variables.
- **Animation performance** — stick to CSS transforms and opacity for animations (GPU-accelerated). Avoid animating layout properties.
- **The testimonials section** has placeholder content — Lateef may want to replace these with real quotes.
- **Footer social links** (`href=""`) are intentionally left blank pending account setup.
- **No git history** — this project is not currently a git repository.
- **The `#projects` section** includes real personal projects (AI Second Brain, STIG automation) that are actual active work, not just showcase items.
