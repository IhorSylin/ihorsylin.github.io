# ihorsylin.github.io

Personal portfolio. Plain HTML and CSS — no build step, no dependencies, no framework.

**Live at:** https://ihorsylin.github.io

## How it works

GitHub Pages serves this repo's `main` branch directly. Push a change and it's live in
30–60 seconds. There is nothing to compile.

```
index.html   all the content — edit the text right here
style.css    all the styling — colours live in :root at the top
images/      your pictures go here
```

## Layout

One breakpoint, at **920px**:

- **below 920px** — single column, everything stacked. Phones and small tablets.
- **920px and up** — two columns: the name/links/intro become a sticky sidebar on the left
  that stays put while the right column scrolls. Content grids (skills, cards, gallery)
  add columns as the window widens, up to a 1240px cap so lines don't get unreadably long.

To change where it switches, edit the two `@media (min-width: 920px)` blocks in `style.css`.
Sidebar width and the outer cap are `--sidebar` and `--maxw` in `:root`.

## ⚠️ After changing style.css, bump the version

The stylesheet is linked as `style.css?v=2`. Browsers cache CSS aggressively — without
bumping that number, people who have visited before keep seeing the old styling even after
you push. So when you edit `style.css`, also change the link in `index.html`:

```html
<link rel="stylesheet" href="style.css?v=3">
```

## Editing it

**Text:** open `index.html` and change the words. That's it.

**Colours:** `style.css`, the `:root` block at the top. Change `--accent` to recolour every
link and highlight at once. Light mode is handled automatically from the visitor's OS
setting — you don't need to maintain two themes.

**Adding a 3D piece:** drop the image in `images/`, then find a `<figure>` block in the
gallery section and replace the placeholder:

```html
<!-- before -->
<div class="placeholder">images/piece-1.jpg<br>final render</div>

<!-- after -->
<img src="images/piece-1.jpg" alt="Stone archway, 4.2k tris">
```

The grid reflows on its own — add as many `<figure>` blocks as you like.

**Embedding a Sketchfab model** — paste their iframe in place of a `<figure>`:

```html
<iframe title="Model" src="https://sketchfab.com/models/YOUR_ID/embed"
        frameborder="0" allowfullscreen style="width:100%;aspect-ratio:4/3;border-radius:10px">
</iframe>
```

**Embedding a YouTube clip** — same idea, with the `/embed/VIDEO_ID` URL.

## Previewing locally

```bash
cd ~/git/ihorsylin.github.io
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just double-click `index.html` — it works straight from the filesystem.

## Publishing a change

```bash
git add -A && git commit -m "Add archway renders" && git push
```

## Still to do

- [ ] Replace the six gallery placeholders with real work — render, **wireframe** and **UV
      layout** for each piece. The breakdowns prove craft; renders alone only prove taste.
- [ ] Add a gameplay video (unlisted YouTube is fine).
- [ ] Decide which email address to publish.
- [ ] Consider a custom domain — Settings → Pages → Custom domain.
