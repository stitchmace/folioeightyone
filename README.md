# FolioEightyOne — puzzle book site

A one-page website for my sudoku and crossword books. Plain HTML/CSS/JS, so there's nothing to build or install.

## Files

```
index.html      ← the whole site
images/         ← book covers + your photo go here
  sudoku-01.jpg
  crossword-01.jpg
  crossword-02.jpg
  me.jpg
```

If a cover image is missing, the site draws a simple placeholder cover so nothing looks broken.

## Editing

- **Books:** open `index.html`, find `const BOOKS = [` near the bottom, and edit the list. Copy one `{ ... },` block to add a new book. Set `amazon: ""` to show "Coming soon".
- **Colors and fonts:** change the variables at the top of the `<style>` block (`--accent`, `--paper` and so on).
- **Socials and email:** search for `YOUR_HANDLE` and `hello@example.com`.
- **About text:** find the `<!-- ABOUT -->` section.

## Publishing with GitHub Pages

1. Create a new repo and upload `index.html`, `README.md` and the `images` folder.
2. Go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. After a minute your site is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

To use your own domain, add it under **Settings → Pages → Custom domain**.
