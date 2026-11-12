# wedding-invitation-cyber

A single-page cyberpunk-Minang wedding invitation for **Alifa & Daniel**
(#EXActlyforALIFA), built with pure CSS/SVG 3D — no WebGL, no JS frameworks.
One self-contained `index.html` — no build step, no backend, no database.

**Stack:** vanilla HTML/CSS/JS, SVG-based Funko Pop figures with CSS 3D
transforms, scroll-driven story scene, canvas digital-rain background. All
third-party assets (fonts) are vendored under `vendor/`, so the page renders
with no external network access.

> This project is intentionally HTML-only. The fleet `CONSTITUTION.md` stack
> rules (Go + Gin + pgx + PostgreSQL + React/TS/Tailwind) do not apply here.

## Run

```bash
docker compose up -d --force-recreate
# http://localhost:3014
```

Any static file server pointed at this directory works too:

```bash
python3 -m http.server 3014
```

## Edit the content

Everything editable is inline in `index.html`:

- Couple names, date, venue — search for `Alifa`, `Daniel`, `05 · 12 · 2026`,
  `Dharmein Hotel`.
- Love-story chapters — the five `.chap` blocks.
- Gift account — the `[Bank Name]`, `[Account Name]` and `[Account Number]`
  placeholders in the **Wishes & Gift** section. **These are still
  placeholders — fill them in before sharing the invitation.**

## Deploy

```bash
git push origin main
docker compose build --no-cache
docker compose up -d --force-recreate
```

## Files

```
index.html          the whole page (markup + styles + SVG 3D scene)
vendor/             self-hosted fonts (Orbitron, Rajdhani)
nginx.conf          static hosting + cache headers
Dockerfile          nginx:alpine, no build stage
docker-compose.yml  single service on host port 3014
```
