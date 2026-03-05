# Hyly.ai Brand Voice

Apply Hyly.ai brand voice, tone, and visual identity to any content or UI in this project.

## Brand Personality

**Intelligent · Trustworthy · Modern · Precise**

Hyly.ai is the AI platform for multifamily real estate. The brand speaks like a confident expert — never flashy, never corporate-stiff. Direct sentences, active voice, outcome-focused language.

## Voice Principles

| Principle | Do | Don't |
|-----------|-----|-------|
| **Confident** | "Hayley converts prospects." | "Hayley may help with conversions." |
| **Precise** | "Booking rate up 18% in 30 days." | "Significantly improved results." |
| **Human** | "Your team moves faster." | "Workflow efficiency is optimized." |
| **Outcome-first** | "Leases closed. Costs down." | "A comprehensive AI solution." |

## Tone by Context

- **Dashboard / internal tools:** Crisp labels, no filler words. Let data speak.
- **Team communication:** Peer-to-peer, direct, skip formality.
- **Headings:** Short, declarative. Max 5 words preferred.
- **Goals / north stars:** Metric + outcome. E.g. "Booking rate velocity" not "Improve bookings."

## Visual Identity

### Colors
```
--hyly-cyan:      #26BBED   /* primary accent — CTAs, highlights, links */
--hyly-green:     #2AD08E   /* success, growth, positive signals */
--hyly-navy:      #09152B   /* primary text, card headers, authority */
--hyly-navy-mid:  #1c3a5e   /* secondary headers, hover states */
--hyly-blue-pale: #cfeefb   /* chip backgrounds, subtle highlights */
--hyly-bg:        #f5f8fc   /* page background */
--hyly-white:     #ffffff   /* card backgrounds */
--hyly-border:    #e0eaf3   /* borders, dividers */
--hyly-muted:     #6e7e9a   /* secondary labels, meta text */
```

### Typography
```
Heading font: 'Raleway', sans-serif  (weights: 600, 700, 800)
Body font:    'Inter', sans-serif    (weights: 400, 500, 600)
```

Import in HTML:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Raleway:wght@600;700;800&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

### Spacing & Shape
- Border radius: `12px` (cards), `8px` (chips/pills), `6px` (small elements)
- Card shadow: `0 2px 12px rgba(9,21,43,0.08)`
- Card border: `1px solid #e0eaf3`
- Section gap: `52px`
- Card gap: `20px`

### Card Header Variants
- Tiger Teams: navy `#09152B` with cyan left-border accent `3px solid #26BBED`
- Practice Teams: navy-mid `#1c3a5e`

### Chip Colors
- Core member: `background: #cfeefb; color: #0a7bc4`
- Contributing/partial: `background: #f0f4f8; color: #6e7e9a`
- North star secondary: `background: #e6faf3; color: #1a7f5a; border: 1px solid #a8e6cb`

## Usage

When asked to apply brand voice:
1. Update `<style>` block in `dashboard.html` using the color tokens and typography above
2. Review all label text — strip filler words, make them outcome-focused
3. Ensure Google Fonts import is present in `<head>`
4. Sync `index.html` via: `cp dashboard.html index.html`
