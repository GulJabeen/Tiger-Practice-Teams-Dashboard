# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file HTML dashboard for HayleyAAI Tiger Teams + Practice Teams. Hosted on GitHub Pages at https://guljabeen.github.io/Tiger-Practice-Teams-Dashboard/

## Deploy to GitHub Pages

```bash
cp dashboard.html index.html && git add index.html && git commit -m "Update teams" && git push
```

`dashboard.html` is the working file (untracked by git). `index.html` is the GitHub Pages entry point (tracked).

## Architecture

`dashboard.html` is split into three clearly labeled zones — only the first zone needs editing:

1. **DATA TABLE** (top `<script>` block) — all team data lives here, nothing else needs touching
2. **STYLES** (`<style>` block) — visual design, rarely touched
3. **RENDERER** (bottom `<script>` block) — `renderTigerCard()` and `renderPracticeCard()` functions

### Data Arrays

**TIGER_TEAMS** schema:
```js
{
  name, productOwner, enterpriseArchitect, businessWhisperer, technicalExpert,
  members: [{ name, role, contrib }],
  goal,
  northStar: { primary, secondary: [] },
  executionHorizon
}
```
- `technicalExpert: "-"` renders in red as "Not assigned"

**PRACTICE_TEAMS** schema:
```js
{
  name, subtitle,       // subtitle is optional
  productOwner, techLead,
  goal,                 // optional
  members: [{ name, role, contrib }],
  owns: []
}
```

### Member chips
- `contrib: false` → blue chip (core member)
- `contrib: true` → grey chip (contributing/partial)

## Current Teams

**Tiger Teams:** Voice/SMS · Agentic Solutions · Unification of MA and AAI · Prompt Quality

**Practice Teams:** ML Eng · API · QA · DevOps · FE · Dsc
