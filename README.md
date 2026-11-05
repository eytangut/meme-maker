# Meme maker
- `index.html` – the meme maker. `editor.html` – hidden helper (not linked): open `/editor.html`.
- `templates/` – drop `name.jpg` + optional `name.json` here (no json = classic top/bottom boxes).
- Config: `{"boxes":[{"x":0.03,"y":0.02,"w":0.94,"h":0.22,"color":"#fff"}]}` (fractions of the image; color `#fff` or `#000`).
- Batch workflow: open `editor.html`, drop all images, adjust boxes (or "copy layout to ALL"), Export zip, unzip into the repo root, push.
- Deploy: repo Settings → Pages → Source: **GitHub Actions**. The workflow regenerates `templates/manifest.json` on every push.
- Local test: `python -m http.server`, since `fetch` doesn't work on `file://`. Without Actions, write `templates/manifest.json` by hand: `["a.jpg","b.png"]`.
- Output: memes are saved as JPEG via MozJPEG (WASM, loaded from jsDelivr; falls back to the browser's encoder offline). Fonts: Anton (Latin) + Secular One (Hebrew).
