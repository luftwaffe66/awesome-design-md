---
version: alpha
name: IONOS-design-analysis
description: A hosting-provider brand canvas built on a deep navy hero band (#001b41), a signature bright cyan (#11c7e6) used on primary CTAs and interactive pills, and a dark navy footer (#0b2a63). The system pairs Overpass (Semi Bold) for display headings with Open Sans (Regular/Semi Bold/Bold) for body and UI. Cards live on white surfaces with generous border-radii (24px), and a purple accent (#e480f8) marks AI-powered features. The palette is anchored in blue—navy backgrounds, cyan actions, light blue tints—with Trustpilot social proof integrated as a pattern.

colors:
  primary: "#11c7e6"
  primary-press: "#095bb1"
  primary-soft: "#3196d6"
  primary-deep: "#0b2a63"
  brand-dark: "#001b41"
  ink: "#2e4360"
  ink-heading: "#001b41"
  ink-muted: "#465a75"
  ink-subtle: "#757575"
  on-primary: "#001b41"
  on-brand: "#ffffff"
  canvas: "#ffffff"
  canvas-soft: "#f4f7fa"
  canvas-blue-light: "#dbedf8"
  hairline: "#e5e7eb"
  hairline-muted: "#dbe2e8"
  hairline-subtle: "#bcc8d4"
  accent-purple: "#e480f8"
  overlay-hero: "linear-gradient(rgba(0,0,0,0.3), rgba(0,61,143,0.4))"
  gradient-light: "linear-gradient(to right bottom, #f7fcff, #bfdbeb)"
  gradient-dark: "linear-gradient(to right bottom, #063d7c, #0a5cb2)"

typography:
  display-xl:
    fontFamily: "Overpass Semi Bold, system-ui, sans-serif"
    fontSize: 52px
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: normal
  display-lg:
    fontFamily: "Overpass Semi Bold, system-ui, sans-serif"
    fontSize: 48px
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: normal
  display-md:
    fontFamily: "Overpass Regular, system-ui, sans-serif"
    fontSize: 40px
    fontWeight: 400
    lineHeight: 1.2
    letterSpacing: normal
  heading-lg:
    fontFamily: "Overpass Semi Bold, system-ui, sans-serif"
    fontSize: 32px
    fontWeight: 600
    lineHeight: 1.25
    letterSpacing: normal
  heading-md:
    fontFamily: "Open Sans Bold, system-ui, sans-serif"
    fontSize: 28px
    fontWeight: 700
    lineHeight: 1.15
    letterSpacing: normal
  heading-sm:
    fontFamily: "Overpass Semi Bold, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 600
    lineHeight: 1.33
    letterSpacing: normal
  subhead:
    fontFamily: "Open Sans Regular, system-ui, sans-serif"
    fontSize: 20px
    fontWeight: 400
    lineHeight: 1.4
    letterSpacing: normal
  body-lg:
    fontFamily: "Open Sans Regular, system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.44
    letterSpacing: normal
  body:
    fontFamily: "Open Sans Regular, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: normal
  body-sm:
    fontFamily: "Open Sans Semi Bold, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 600
    lineHeight: 1.3
    letterSpacing: normal
  caption:
    fontFamily: "Open Sans Semi Bold, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 600
    lineHeight: 1.33
    letterSpacing: normal

shadows:
  card: "0 2px 12px rgba(0,0,0,0)"
  elevated: "0 10px 15px -3px rgba(107,114,128,0.1), 0 4px 6px -4px rgba(107,114,128,0.1)"

rounded:
  pill: 9999px
  cta: 40px
  card: 24px
  section: 16px
  button: 6px
  input: 6px
  tag: 2px
---

## Overview

IONOS deploys a **trust-and-scale** design language built on a blue-centric palette. The hero section uses a dark navy (`#001b41`) full-width band as a dramatic entry point, with bright cyan (`#11c7e6`) CTAs as the primary interactive mechanism. The system reads as **approachable infrastructure**: bold headlines in Overpass Semi Bold, generous rounded containers (24px card radii), and a social-proof layer built around Trustpilot ratings.

The brand positions AI as a core differentiator—a purple accent (`#e480f8`) appears on Momentum AI badges, distinguishing AI-powered features from traditional hosting products.

## Colors

The palette centers on a navy-to-cyan axis with cool gray text and white/alabaster canvases.

- **Brand Dark** (`#001b41`): The hero curtain and primary dark surface. Used as a full-width backdrop for the top-of-page experience. Also serves as ink for headings and dark-on-light elements.
- **Primary Cyan** (`#11c7e6`): The single interactive bright color. Used on the domain search CTA, pricing call-to-action pills, and hover/active states. Text on cyan reads in brand dark (`#001b41`).
- **Deep Navy** (`#0b2a63`): The footer background and secondary brand surface. Deeper than hero navy, used at page bottom.
- **Ink** (`#2e4360`): Primary body text on light canvases.
- **Canvas Soft** (`#f4f7fa`): Near-white background for alternating sections and card grids.
- **Canvas Blue Light** (`#dbedf8`): Tinted blue background used sparingly for highlighted sections.
- **Accent Purple** (`#e480f8`): Marks AI/Momentum-branded features, badges, and pills.
- **Secondary Blues** (`#095bb1`, `#3196d6`): Press states and secondary button alternatives.

## Typography

IONOS uses a **dual-type-family** hierarchy: **Overpass** for display and headings, **Open Sans** for body and UI.

Overpass Semi Bold (52px–24px) drives headlines with a geometric, slightly condensed character—it avoids the rigid utility feel common in hosting brands. Open Sans takes over for body copy (20px–12px), providing readability at scale.

- **Display XL** (52px/600): Used for hero headlines on the dark navy stage. Large but not aggressive.
- **Display LG** (48px/600): Section anchor headlines.
- **Heading SM** (24px/600): Card titles and testimonial names.
- **Body** (16px/400): The workhorse size, used across descriptions, navigation, and paragraph copy.
- **Caption** (12px/600): Legal, footnotes, small print.

Line heights are tight for display (1.0–1.2) and generous for body (1.4–1.5). Letter spacing stays at normal—no negative tracking.

## Layout

The page follows a standard marketing SaaS layout:
- **Full-bleed hero** with a navy backdrop, centered content, and a domain search form as the primary interaction.
- **Product grid** of 9 icon tiles (Domain, Email, Website, etc.) in a responsive 3×3 grid.
- **AI feature section** splitting into a two-column content card layout (text left, image right).
- **4-column card grid** for product categories (Domains, Email, Website, eCommerce, etc.), each with a pill CTA.
- **Partner logo carousel** with brand logos.
- **Footer** in deep navy with 4-column link layout.

Max content width is approximately 1280px, with generous section padding (80px+ vertical).

## Elevation & Depth

The system uses minimal elevation:
- **Card shadow**: `0 2px 12px rgba(0,0,0,0)` — a very subtle, nearly flat hover indicator.
- **Elevated shadow**: `0 10px 15px -3px rgba(107,114,128,0.1)` — used sparingly for floating elements.
- The hero section uses a **gradient overlay** (`rgba(0,0,0,0.3)` → `rgba(0,61,143,0.4)`) over background imagery for text legibility.

Depth is understated—IONOS favors clean separation through alternating background colors rather than shadows.

## Shapes

Border radius is expressive and generous:
- **Pill/CTA buttons**: 40px / 9999px — the signature button shape.
- **Card containers**: 24px — the defining radius of the product card system.
- **Feature blocks**: 16px — for section-level containers.
- **UI buttons/inputs**: 6px — standard form and navigation radius.
- **Tags**: 2px — minimal technical badges.

The 24px card radius is a distinctive design marker, making product cards feel friendly and non-corporate.

## Components

### Navigation

A single-tier sticky navigation bar on a dark navy (`#001b41`) background with white text:

- **Logo**: The IONOS wordmark logo on the left side of the bar, served as a standalone SVG asset.
- **Product links**: New Momentum AI (with purple AI badge), Domains & SSL, Email & Office, Websites, eCommerce, WordPress, Hosting, Servers, Cloud — rendered in Open Sans Semi Bold 14px, positioned to the left of the logo.
- **Icon tray** (right-aligned): Language selector (globe icon + "EN"), phone icon, and sign-in (user silhouette) icon. No dividers between icons. Icons are slightly muted white at 0.8 opacity with a 34px hit area and 6px border-radius on hover.

The bar is 64px tall with 32px horizontal padding. On mobile (<768px), the link list collapses behind a hamburger toggle positioned between the links and the logo.

### Buttons

- **Primary CTA** (Check): Background `#11c7e6`, text `#001b41`, Open Sans Semi Bold 16px, pill shape (40px radius), padding 14px 24px. No icon—just text.
- **Card CTA pills** ("Start searching", "Get your email", etc.): Background `#11c7e6`, text `#0b2a63`, radius 24px, with `0 2px 12px` shadow. Text reads "View plans and pricing" or the specific action.
- **Secondary/Link buttons**: Transparent background, text in brand dark or ink, no border.

### Cards

Product cards use a white background, 24px border radius, and a flat shadow. Each card contains:
- An image/illustration (above or beside)
- A category label (uppercase, small)
- A heading (24px Overpass Semi Bold)
- A price line ("Starting at $X/month")
- A pill CTA button in cyan

### Domain Search

The primary interaction is a domain search form with:
- A text input (rounded 6px, white background)
- A .com logo badge
- "$1 /year" pricing callout
- A cyan pill "Check" button

### AI Badge

AI-powered features carry a distinct **purple** (`#e480f8`) badge/tag, marking Momentum AI products from traditional hosting. This is the sole chromatic accent outside the blue family.

### Footer

Deep navy (`#0b2a63`) full-width footer with white text, organized in 4 columns:
- Company, Knowledge, Partner Programs, Support
- Social media link row: 5 inline SVG icons (Instagram, Facebook, YouTube, LinkedIn, TikTok) rendered in solid white (`fill="currentColor"`, color inherited from parent white text). Each icon uses an 18×18 viewBox and a standard platform-specific path. No background, no label text — icon-only. Links are spaced evenly and wrapped in `<a>` tags with `aria-label` for accessibility.
- Country selector
- Tax notice and Terms link

### Trustpilot Section

A dedicated review carousel with Trustpilot branding. Shows 4.6/5 stars, 43K+ reviews, and 3 testimonial cards with avatar, name, date, and quote heading.

## Do's and Don'ts

- **Do** use the cyan pill for all primary actions—it's the single interactive color.
- **Do** pair Overpass for headlines with Open Sans for body—don't swap.
- **Do** use the 24px card radius as the container default.
- **Don't** add shadows deeper than `0 2px 12px`—the system is intentionally flat.
- **Don't** use purple outside AI/Momentum contexts.
- **Don't** use negative letter-spacing—IONOS typography is set at normal tracking.
- **Don't** deviate from the navy primary palette—blue is the brand anchor.

## Responsive Behavior

- **Desktop (>1024px)**: Full hero, 3×3 icon grid, 4-column card grid, side-by-side AI section.
- **Tablet (768–1024px)**: Grids collapse to 2-column layouts. Hero text scales down.
- **Mobile (<768px)**: Single-column stack. Navigation collapses behind a hamburger menu. Hero heading reduces to 32px. Cards stack vertically. Domain search form stacks input and button.

## Known Gaps

This analysis is based on the public marketing homepage (ionos.com) and does not include:
- The My IONOS dashboard / admin interface design system
- Cloud console (cloud.ionos.com) UI components
- Email and communication templates
- Mobile app design language
- The full Momentum AI conversational interface
- Any design token values not exposed in CSS custom properties (the site uses Tailwind utility classes rather than a semantic token system)
