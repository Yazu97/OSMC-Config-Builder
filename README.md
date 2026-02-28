# OSMC Config Builder

A visual web editor for managing OSMC skill configuration JSON files. Built for Zenith server staff.

## 🚀 Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `osmc-config-builder`)
2. Upload `index.html` to the root of the repo
3. Go to **Settings → Pages → Source → Deploy from branch → main → / (root)**
4. Your editor will be live at `https://<your-username>.github.io/osmc-config-builder/`

No build step. No dependencies to install. Pure HTML/JS.

## ✨ Features

- **Multi-skill management** — create, edit, and delete any number of OSMC skills in one place
- **Visual XP source editor** — add/remove block targets per tier, change XP values, switch event types
- **Skill effects editor** — configure drop multipliers, chance formulas, and target blocks visually
- **Level curve visualiser** — live Chart.js graph with 4 modes:
  - XP Required per level
  - Cumulative total XP
  - XP gained per level (delta)
  - Compare XP sources (blocks needed to reach each level)
- **Milestone reference table** — key levels with XP required, cumulative XP, and drop bonus %
- **Formula editor** — tweak the `floor(A × level^B)` parameters and see the curve update live
- **JSON output** — live JSON preview, format button, apply-to-editor sync
- **Import** — paste JSON or open a `.json` file to import a skill (merges if ID already exists)
- **Export** — download individual skill as `osmc_skillname.json`, or export all skills as an array
- **Browser persistence** — all changes auto-saved to `localStorage`

## 📁 File Structure (GitHub Pages)

```
/
└── index.html    ← entire app, single file
```

## 📦 Usage

### Importing your existing configs
Click **⬆ Import JSON** in the top bar and either paste or open your existing skill `.json` file.
The app will detect if the skill ID already exists and update it in place.

### Creating a new skill
Click **+ New Skill** in the sidebar or home page. Set the ID (e.g. `osmc:woodcutting`), display name, color, and formula parameters.

### Exporting
- **⬇ Export Skill** — downloads the currently selected skill as a correctly formatted `.json` file ready to drop into your mod's data folder
- **⬇ Export All** — downloads all skills as a JSON array (useful for backup or bulk review)

## 🎨 Skill Color

The `color` field is used by the mod to color the skill name in chat and UI. Use a hex color that fits your skill's theme.

## 📐 Formula

Level XP requirements follow: `floor(A × level^B)`

- Default: `A = 50`, `B = 2.5`
- Higher B = steeper exponential curve (harder end game)
- Higher A = more XP required at all levels
- OSRS uses approximately `B = 2.5` which makes level 92 roughly the halfway point to 99 by total XP
