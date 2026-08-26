# Prasad Sudhir Thorat — Portfolio

A single-page cinematic portfolio (Cybersecurity • AI • Software Engineering) built with React (via CDN + Babel), Tailwind CSS, Three.js, and GSAP. No build step required — it's a static site.

## Structure

```
portfolio/
├── index.html          # the entire site (React app, loaded via CDN scripts)
├── assets/
│   └── prasad-hero.mp4 # background video used in the hero section
└── README.md
```

## Run locally

Just open `index.html` in a browser, or serve the folder so the video path resolves correctly:

```bash
cd portfolio
python3 -m http.server 8000
# visit http://localhost:8000
```

(Opening `index.html` directly via `file://` also works in most browsers, but some browsers block video/module loading over `file://` — a local server avoids that.)

## Upload to GitHub

```bash
cd portfolio
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Deploy free with GitHub Pages

1. Push the repo as above (or rename it to `<your-username>.github.io` for a root domain).
2. In the repo: **Settings → Pages → Source → Deploy from a branch → `main` / root**.
3. Save. Your site will be live at:
   `https://<your-username>.github.io/<repo-name>/`

Notes:
- Video files heavier than a few MB are fine on GitHub Pages, but GitHub itself has a 100MB per-file hard limit and recommends keeping repos under ~1GB — `prasad-hero.mp4` (≈1.9MB) is well within that.
- The "AI Security Lab" chat/forensics tabs and the voice-intro button call the Gemini API directly from the browser with an empty `apiKey` string — they won't work until a real API key is added client-side (not recommended for a public repo) or routed through a backend proxy. Everything else (nav, sections, hero video, certifications, etc.) works with zero configuration.
