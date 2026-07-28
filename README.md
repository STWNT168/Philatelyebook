# State Level Philately Exhibition — eBook

A two-page, single-file-per-page HTML experience:

- **`index.html`** — the animated cover (stamp mosaic background, gold
  glassmorphism "Open eBook" button, cinematic page-turn on tap).
- **`ebook.html`** — the eBook itself: a hanging-lamp reading room with a
  swinging brass lamp, illuminated parchment pages, chapter navigation,
  and a Table of Contents drawer.

No build step, no dependencies beyond Google Fonts (loaded via CDN) —
just static HTML/CSS/JS.

## 1. Add your audio files (optional but recommended)

Both pages reference sound effects by filename, expected in the **same
folder** as the HTML files:

| File                | Used by              | Purpose                          |
|---------------------|-----------------------|-----------------------------------|
| `page-turn.mp3`     | `index.html`, `ebook.html` | Page-turn sound effect      |
| `paper-rustle.mp3`  | `index.html`, `ebook.html` | Paper rustle accompanying turns |
| `whoosh.mp3`        | `index.html`          | Cinematic whoosh on cover open   |
| `lamp-flicker.mp3`  | `ebook.html`           | Looping ambient flame sound (starts on first tap, per browser autoplay rules) |

If a file is missing, the site still works perfectly — playback just
fails silently. Add your own royalty-free `.mp3` files with these exact
names at the repo root to enable sound.

## 2. Push to GitHub

```bash
git init
git add .
git commit -m "Philately exhibition eBook"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

## 3. Turn on GitHub Pages

1. On GitHub, open your repo → **Settings** → **Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Save.
4. GitHub gives you a URL like:
   `https://<your-username>.github.io/<your-repo>/`
   That URL loads `index.html` automatically — the cover page.

Changes pushed to `main` redeploy automatically within a minute or two.

## File structure

```
your-repo/
├── index.html          (the cover — loads first on GitHub Pages)
├── ebook.html           (the reading-room eBook)
├── .nojekyll             (tells GitHub Pages to skip Jekyll processing)
├── page-turn.mp3         (add your own)
├── paper-rustle.mp3      (add your own)
├── whoosh.mp3            (add your own)
├── lamp-flicker.mp3      (add your own)
└── README.md
```

## Notes

- Everything is mobile-first and responsive; test on a phone by opening
  the GitHub Pages URL directly.
- The cover checks that `ebook.html` is reachable before navigating to
  it (via a `HEAD` request), so it degrades gracefully if that file is
  ever removed.
- All background artwork (stamps, postmarks, motifs) is generated
  procedurally in CSS/JS — no external images, no copyrighted material.
