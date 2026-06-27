> **Public Notice**
> This repository contains the *public framework* for the Perpetual Résumé system.
> It includes schemas, documentation, and structural components only.
> It does **not** contain any personal, private, or proprietary career data.
> All real résumé content is maintained in a **separate private repository**.

# Perpetual Résumé — Public Framework

The Perpetual Résumé is a structured, long-term career system designed to replace the traditional résumé with something more powerful, more flexible, and more accurate over time. Instead of rewriting your résumé for every job, the Perp acts as a single source of truth for your entire career — roles, skills, outcomes, projects, STAR stories, and narrative elements — all stored in a clean, queryable structure.

---

## 🚀 Quick Start (GitHub Pages)

This repo is designed to run as a static site on GitHub Pages — no server, no backend, no cost.

**Enable GitHub Pages:**
1. Go to your repo → **Settings** → **Pages**
2. Set Source to `main` branch, `/ (root)` folder
3. Save — your site will be live at `https://yourusername.github.io/perp`

**Run locally:**
```bash
# Python 3
python3 -m http.server 8080

# Node
npx serve .
```
Then open `http://localhost:8080`

---

## 📁 Repository Structure

```
perp/
├── index.html          ← Main app: viewer + free-tier entry form
├── data/
│   ├── person.json     ← Your profile (name, location, education, certs)
│   ├── experiences.json← Your complete career history
│   └── *-sample.json   ← Example data matching each schema
├── schema/
│   ├── perp-schema.md  ← Full schema documentation
│   ├── experience.json ← JSON Schema: experience entries
│   ├── achievement.json← JSON Schema: achievements
│   ├── bullet.json     ← JSON Schema: resume bullets
│   ├── narratives.json ← JSON Schema: STAR stories & narratives
│   ├── skills.json     ← JSON Schema: skills inventory
│   ├── metrics.json    ← JSON Schema: quantified metrics
│   └── themes.json     ← JSON Schema: cross-cutting themes
└── README.md
```

---

## 🗂️ How to Use

### The Free Tier (live now)

The app has three sections:

**View Perp** — Renders `data/experiences.json` and `data/person.json` as a formatted reverse-chronological résumé with collapsible detail sections and STAR story cards.

**Add Entry** — A form to capture a new role: company, title, dates, employment type, role summary, responsibilities, achievements, and STAR stories. Exports as a JSON file you can add to `data/experiences.json`.

**About** — Explains the three tiers and the philosophy behind the Perp.

### Adding your own data

1. Edit `data/person.json` with your name, location, education, and certifications.
2. Replace `data/experiences.json` with your career history, or use the **Add Entry** form to generate individual entries.
3. Push to GitHub — your Perp is live.

---

## 🧠 What the Perpetual Résumé Solves

Traditional résumés are static, brittle, and constantly rewritten from memory. The Perp solves that by:

- Maintaining a living archive of your entire career
- Capturing STAR stories while memories are fresh
- Separating data from presentation
- Making achievements and outcomes searchable and reusable
- Eliminating the blank-page problem — forever

It's not a résumé generator. It's a career operating system.

---

## 🛤️ Roadmap

| Tier | Status | Description |
|------|--------|-------------|
| **Free** | ✅ Live | Entry form, local JSON export, viewer |
| **Subscription** | 🔜 Planned | AI-tailored résumé generation from job description |
| **Book** | 🔜 Planned | One-year subscription included with book purchase |

---

## 📄 License

Apache 2.0 — see [LICENSE](LICENSE)
