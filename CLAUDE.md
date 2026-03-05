# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file HTML dashboard for Hyly Tiger Teams + Practice Teams. Hosted on GitHub Pages at https://guljabeen.github.io/Tiger-Practice-Teams-Dashboard/

## File Structure

```
dashboard.html          ← source file — edit this one
index.html              ← GitHub Pages entry (copy of dashboard.html)
images/
  hyly-logo.png         ← Hyly wordmark used in navbar
teams.md                ← Tiger/Practice Teams concept document
CLAUDE.md               ← this file
.claude/
  commands/
    brand-voice.md      ← /brand-voice skill (colors, fonts, tone)
.gitignore              ← excludes .env, .DS_Store
```

## Deploy to GitHub Pages

```bash
cp dashboard.html index.html && git add -A && git commit -m "Update" && git push
```

`dashboard.html` is the working source. `index.html` is the GitHub Pages entry point — always kept in sync.

## Architecture

`dashboard.html` has three clearly labeled zones — only the first needs editing:

1. **DATA TABLE** (top `<script>`) — all team data, nothing else needs touching
2. **STYLES** (`<style>`) — Hyly brand design system
3. **RENDERER** (bottom `<script>`) — `renderTigerCard()` and `renderPracticeCard()`

### TIGER_TEAMS schema
```js
{
  name, productOwner, enterpriseArchitect, businessWhisperer,
  technicalExpert,          // "-" shows as red "Not assigned"
  members: [{ name, role, contrib }],
  goal,
  northStar: { primary, secondary: [] },
  executionHorizon
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
