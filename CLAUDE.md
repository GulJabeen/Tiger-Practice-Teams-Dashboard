# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file HTML dashboard for Hyly Tiger Teams + Practice Teams. Hosted on Netlify at https://voluble-banoffee-875bf0.netlify.app

## File Structure

```
dashboard.html              ← source file — edit this one
index.html                  ← redirects to Netlify (GitHub Pages fallback)
netlify.toml                ← Netlify build config (functions dir)
netlify/
  functions/
    teams.js                ← Netlify Function: fetches from Notion API
scripts/
  setup-notion.js           ← one-time script: creates Notion DBs + populates rows
images/
  hyly-logo.png             ← Hyly wordmark used in navbar
teams.md                    ← Tiger/Practice Teams concept document
CLAUDE.md                   ← this file
.claude/
  commands/
    brand-voice.md          ← /brand-voice skill (colors, fonts, tone)
.gitignore                  ← excludes .env, .DS_Store
```

## Deploy to Netlify

```bash
netlify deploy --prod --dir .
```

Netlify must have these env vars set (printed by setup-notion.js after first run):
- `NOTION_API_KEY`
- `NOTION_TIGER_DB_ID`
- `NOTION_PRACTICE_DB_ID`

## Notion Setup (one-time)

1. Share the Tiger-Practice-Teams page in Notion with the **"Hyly.AI ML Team"** integration
2. `node scripts/setup-notion.js` — creates both databases + populates all rows
3. Copy the printed DB IDs → set as Netlify env vars (netlify.com > Site > Environment Variables)
4. `netlify deploy --prod --dir .`

## Architecture

`dashboard.html` has three clearly labeled zones — only the first needs editing:

1. **DATA TABLE** (top `<script>`) — all team data, nothing else needs touching
2. **STYLES** (`<style>`) — Hyly brand design system
3. **RENDERER** (bottom `<script>`) — `renderTigerCard()` and `renderPracticeCard()`

### TIGER_TEAMS schema
```js
{
  product,                  // "Hayley" | "Halo" | "Helix"
  type,                     // "Client Impact" | "Strategic Impact"
  name, productOwner, enterpriseArchitect, businessWhisperer,
  technicalExpert,          // null shows as red "Not assigned"
  members: [{ name, role, contrib }],
  goal,
  northStar: { primary, secondary: [] },
  milestones: { threeMonth, sixMonth }
}
```

### PRACTICE_TEAMS schema
```js
{
  name, subtitle,           // subtitle optional
  productOwner, techLead,
  goal,                     // optional
  members: [{ name, role, contrib }],
  owns: []
}
```

### Member chips
- `contrib: false` → blue chip (core member)
- `contrib: true` → grey chip (partial / contributing)

## Brand Tokens

```css
--cyan: #26BBED   --green: #2AD08E   --navy: #09152B
```

Fonts: `Raleway` (headings, weight 700–800) · `Inter` (body, weight 400–600)
