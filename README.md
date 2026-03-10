# HypnoCards — Multilingual NLP Flash Cards

A hypnotic language pattern practice app. Works offline, no server needed.

## Project Structure

```
hypnocards/
├── index.html          ← The entire app (single file)
├── data/
│   ├── cards_en.csv    ← English cards
│   ├── cards_he.csv    ← Hebrew cards
│   └── cards_fr.csv    ← French cards (add when ready)
└── README.md
```

## Adding a New Language

1. Create your CSV with columns: `ID, Category, Pattern, Theme, Content, Color`
2. Name it `cards_XX.csv` (XX = language code, e.g. `cards_es.csv` for Spanish)
3. Place it in the `/data/` folder
4. Open `index.html` and find `const LANGUAGE_CONFIG = {`
5. Add an entry following the existing pattern (copy `en` block, translate the `ui` strings)
6. Done — the language button appears automatically

## Deploying to GitHub Pages (free)

### First time setup:
1. Create a free account at https://github.com
2. Click **New repository** → name it `hypnocards` → set to **Public**
3. Click **Add file → Upload files**
4. Upload `index.html` and the entire `data/` folder
5. Go to **Settings → Pages**
6. Under **Source**, select `Deploy from a branch` → `main` → `/ (root)`
7. Click **Save**
8. Your site will be live at: `https://YOUR-USERNAME.github.io/hypnocards`

### Updating the site later:
- To update cards: upload a new CSV to `data/`
- To update the app: upload a new `index.html`
- Changes go live within ~1 minute

## How the Language System Works

- Each language stores its card data separately in localStorage
- Switching languages loads that language's saved data instantly
- If no data is saved for a language, the user is prompted to load the CSV
- Favorites and recordings are tracked per-language
- RTL (Hebrew, Arabic) is applied automatically based on language config

## CSV Format

Required columns:
| Column   | Description |
|----------|-------------|
| ID       | Row number (or `CATEGORY_INFO` for metadata rows) |
| Category | Pattern category name |
| Pattern  | The pattern name/title shown on card front |
| Theme    | Emotional theme (Relaxation, Pleasure, etc.) |
| Content  | The card text |
| Color    | Hex color for the category, e.g. `#B3E5FC` |

## Tech Stack
- Vanilla HTML/CSS/JS — zero build step
- TailwindCSS (CDN)
- PapaParse for CSV parsing
- Lucide icons
- Google Fonts (Cormorant Garamond + DM Mono + Heebo)
