# 703Circuit S4 — Player Tiers & Power Rankings

A single-page web app showing 703Circuit Season 4 players in three views:

- **Tier Board** — League-style 1–5 tiers (Tier 1 reserved for captains)
- **Power Rankings** — Numbered 1–N list by overall rating
- **2K Ratings** — NBA 2K-style OVR + attributes (INS / OUT / PLY / DEF / REB)

## Data

- `data/players.json` — edit this file to update tiers, ratings, teams, notes
- Sources: [703circuit.com](https://703circuit.com), S1–S3 + 571 Cup awards history, S4 Week 1

### Player fields

```json
{
  "name": "John Welsh",
  "team": "Black",
  "tier": 1,
  "ovr": 94,
  "isCaptain": true,
  "attributes": { "inside": 90, "outside": 88, "playmaking": 89, "defense": 92, "rebounding": 91 },
  "awards": ["S1 MVP", "S2 MVP"],
  "s4_week1": "35 PTS, 5 STL",
  "notes": "2x MVP..."
}
```

- `tier`: 1–5 (1 = captains only)
- `ovr`: 60–99 (2K-style overall)
- `attributes`: 60–99 each

## Run locally

```bash
cd 703circuit-rankings
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new repo (e.g. `703circuit-rankings`) under `farhanss3`
2. Push this folder:
```bash
git init
git add .
git commit -m "703Circuit S4 tiers + power rankings + 2K ratings"
git branch -M main
git remote add origin https://github.com/farhanss3/703circuit-rankings.git
git push -u origin main
```
3. In repo Settings → Pages → Deploy from branch → `main` / `/ (root)`

## Updating from 703circuit.com

Re-scrape rosters/stats from https://703circuit.com (Teams / Stats / Rosters pages, Season 4 filter),
then update `data/players.json` and push.
