[index.html](https://github.com/user-attachments/files/35076449/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>FolioEightyOne — puzzle books for quiet hours</title>
  <meta name="description" content="Sudoku and crossword puzzle books by FolioEightyOne. Small, thoughtful books for time away from the screen." />

  <!-- Social preview (replace image path once you have one) -->
  <meta property="og:title" content="FolioEightyOne — puzzle books" />
  <meta property="og:description" content="Sudoku and crossword books for time away from the screen." />
  <meta property="og:image" content="images/og-image.jpg" />

  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,400;0,9..144,600;1,9..144,400&family=DM+Sans:wght@400;500&family=DM+Mono:wght@400&display=swap" rel="stylesheet" />

  <style>
    /* ============================================================
       THEME — change colors and fonts here
       ============================================================ */
    :root {
      --paper: #f7f4ee;
      --paper-2: #fffdf9;
      --ink: #1d1b18;
      --ink-soft: #5b564f;
      --line: #e4ded3;
      --grid: rgba(120, 100, 80, 0.07);
      --accent: #b8321f;        /* buy buttons, highlights */
      --accent-dark: #922515;
      --serif: "Fraunces", Georgia, serif;
      --sans: "DM Sans", system-ui, -apple-system, sans-serif;
      --mono: "DM Mono", ui-monospace, monospace;
      --max: 1120px;
    }

    *, *::before, *::after { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: var(--sans);
      color: var(--ink);
      background-color: var(--paper);
      /* graph-paper background */
      background-image:
        linear-gradient(var(--grid) 1px, transparent 1px),
        linear-gradient(90deg, var(--grid) 1px, transparent 1px);
      background-size: 28px 28px;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }
    img { max-width: 100%; display: block; }
    a { color: inherit; }
    .wrap { max-width: var(--max); margin: 0 auto; padding: 0 24px; }

    /* thin accent strip at the very top */
    body::before {
      content: ""; display: block; height: 4px; background: var(--accent); opacity: .85;
    }

    /* ---------- header ---------- */
    header {
      position: sticky; top: 0; z-index: 10;
      background: rgba(247, 244, 238, 0.9);
      backdrop-filter: blur(8px);
      border-bottom: 1px solid var(--line);
    }
    .nav {
      display: flex; align-items: center; justify-content: space-between;
      height: 64px;
    }
    .logo {
      font-family: var(--serif); font-weight: 600; font-size: 1.15rem;
      text-decoration: none; letter-spacing: -0.01em;
    }
    .logo span { color: var(--accent); }
    .nav ul { list-style: none; display: flex; gap: 28px; margin: 0; padding: 0; }
    .nav a { text-decoration: none; font-size: .9rem; color: var(--ink-soft); }
    .nav a:hover { color: var(--ink); }

    /* ---------- hero ---------- */
    .hero { padding: 88px 0 56px; }
    .eyebrow {
      font-family: var(--mono); font-size: .72rem; letter-spacing: .14em;
      text-transform: uppercase; color: var(--ink-soft); margin: 0 0 18px;
    }
    .hero h1 {
      font-family: var(--serif); font-weight: 600;
      font-size: clamp(2.6rem, 7vw, 5rem);
      line-height: 1.02; letter-spacing: -0.03em; margin: 0 0 24px; max-width: 14ch;
    }
    .hero h1 em { font-weight: 400; color: var(--accent); }
    .hero p { max-width: 54ch; color: var(--ink-soft); font-size: 1.05rem; margin: 0 0 32px; }
    .hero-links { display: flex; flex-wrap: wrap; gap: 10px; }
    .pill {
      display: inline-block; padding: 9px 18px; border-radius: 999px;
      border: 1px solid var(--line); background: var(--paper-2);
      font-size: .88rem; text-decoration: none; transition: border-color .2s, transform .2s;
    }
    .pill:hover { border-color: var(--ink); transform: translateY(-1px); }
    .pill.solid { background: var(--ink); color: var(--paper); border-color: var(--ink); }

    /* ---------- section headings ---------- */
    .section-head {
      display: flex; justify-content: space-between; align-items: baseline;
      border-bottom: 1px solid var(--line); padding-bottom: 12px; margin: 0 0 32px;
      gap: 16px; flex-wrap: wrap;
    }
    .section-head h2 {
      font-family: var(--serif); font-weight: 600; font-size: 2rem;
      letter-spacing: -0.02em; margin: 0;
    }
    .section-head .note { font-family: var(--mono); font-size: .72rem; color: var(--ink-soft); letter-spacing: .06em; }

    /* filter tabs */
    .filters { display: flex; gap: 6px; margin-bottom: 32px; flex-wrap: wrap; }
    .filters button {
      font: inherit; font-size: .85rem; cursor: pointer;
      padding: 7px 16px; border-radius: 999px;
      border: 1px solid var(--line); background: transparent; color: var(--ink-soft);
    }
    .filters button[aria-pressed="true"] { background: var(--ink); color: var(--paper); border-color: var(--ink); }

    /* ---------- book grid ---------- */
    .books { padding-bottom: 96px; }
    .grid {
      display: grid; gap: 48px 32px;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    }
    .book { display: flex; flex-direction: column; }
    .cover-frame {
      aspect-ratio: 1 / 1; background: var(--paper-2);
      border: 1px solid var(--line);
      display: flex; align-items: center; justify-content: center;
      padding: 13%; margin-bottom: 18px; position: relative; overflow: hidden;
    }
    .cover-frame img, .cover-fallback {
      max-height: 100%; width: auto;
      box-shadow: 0 1px 2px rgba(0,0,0,.08), 0 10px 24px rgba(0,0,0,.14);
      transition: transform .35s ease;
    }
    .book:hover .cover-frame img,
    .book:hover .cover-fallback { transform: translateY(-4px) rotate(-1deg); }
    .badge {
      position: absolute; top: 12px; right: 12px;
      font-family: var(--mono); font-size: .64rem; letter-spacing: .1em; text-transform: uppercase;
      padding: 3px 9px; border-radius: 999px; background: var(--accent); color: #fff;
    }

    /* typographic cover shown if an image is missing */
    .cover-fallback {
      height: 100%; aspect-ratio: 5.06 / 7.81;
      display: flex; flex-direction: column; justify-content: space-between;
      padding: 12% 10%; color: #fff; text-align: left;
    }
    .cover-fallback .cf-title { font-family: var(--serif); font-size: 1.5rem; line-height: 1; }
    .cover-fallback .cf-sub { font-family: var(--mono); font-size: .55rem; letter-spacing: .1em; text-transform: uppercase; opacity: .85; }
    .cover-fallback .cf-grid {
      width: 62%; aspect-ratio: 1; align-self: center;
      background-image:
        linear-gradient(rgba(255,255,255,.55) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.55) 1px, transparent 1px);
      background-size: 11.11% 11.11%;
      border: 1.5px solid rgba(255,255,255,.8);
    }

    .book .label {
      font-family: var(--mono); font-size: .66rem; letter-spacing: .14em;
      text-transform: uppercase; color: var(--ink-soft); margin: 0 0 4px;
    }
    .book h3 {
      font-family: var(--serif); font-weight: 600; font-size: 1.45rem;
      letter-spacing: -0.015em; margin: 0 0 8px; line-height: 1.15;
    }
    .book .desc { font-size: .9rem; color: var(--ink-soft); margin: 0 0 12px; }
    .book .meta { font-family: var(--mono); font-size: .72rem; color: var(--ink-soft); margin: 0 0 14px; line-height: 1.7; }

    details { margin: 0 0 18px; font-size: .88rem; }
    summary {
      cursor: pointer; list-style: none; display: inline-block;
      font-size: .82rem; border-bottom: 1px solid var(--ink); line-height: 1.4;
    }
    summary::-webkit-details-marker { display: none; }
    summary::after { content: " +"; }
    details[open] summary::after { content: " –"; }
    details ul { margin: 12px 0 0; padding-left: 18px; color: var(--ink-soft); }

    .buy {
      margin-top: auto; align-self: flex-start;
      display: inline-flex; align-items: center; gap: 8px;
      background: var(--accent); color: #fff; text-decoration: none;
      font-size: .85rem; font-weight: 500;
      padding: 11px 26px; transition: background .2s;
    }
    .buy:hover { background: var(--accent-dark); }
    .buy.soon { background: transparent; color: var(--ink-soft); border: 1px dashed var(--ink-soft); pointer-events: none; }

    /* ---------- about ---------- */
    .about { padding: 96px 0; border-top: 1px solid var(--line); }
    .about-inner { display: grid; grid-template-columns: 300px 1fr; gap: 72px; align-items: center; }
    .polaroid {
      background: #fff; padding: 14px 14px 52px; width: 240px; margin: 0 auto;
      box-shadow: 0 2px 4px rgba(0,0,0,.06), 0 14px 32px rgba(0,0,0,.12);
      transform: rotate(-4deg); position: relative;
    }
    .polaroid .photo {
      aspect-ratio: 1; background: #d8d2c7 center/cover no-repeat;
      display: flex; align-items: center; justify-content: center;
      font-family: var(--mono); font-size: .7rem; color: #8a8278;
    }
    .polaroid .sig {
      position: absolute; bottom: 14px; left: 20px;
      font-family: var(--serif); font-style: italic; font-size: 1.2rem; color: var(--ink-soft);
    }
    .polaroid::before { /* tape */
      content: ""; position: absolute; top: -12px; left: 50%; width: 84px; height: 24px;
      transform: translateX(-50%) rotate(3deg);
      background: rgba(235, 225, 200, .75);
    }
    .about h2 {
      font-family: var(--serif); font-weight: 600; font-size: clamp(2rem, 4vw, 2.8rem);
      letter-spacing: -0.025em; margin: 0 0 20px; line-height: 1.05;
    }
    .about p { color: var(--ink-soft); max-width: 56ch; margin: 0 0 14px; }

    /* ---------- follow / newsletter ---------- */
    .follow { padding: 0 0 96px; }
    .follow-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 14px; }
    .card-link {
      display: flex; align-items: center; gap: 14px; text-decoration: none;
      background: var(--paper-2); border: 1px solid var(--line); padding: 18px 20px;
      transition: border-color .2s;
    }
    .card-link:hover { border-color: var(--ink); }
    .card-link svg { width: 22px; height: 22px; flex-shrink: 0; }
    .card-link strong { display: block; font-weight: 500; font-size: .92rem; }
    .card-link small { color: var(--ink-soft); font-size: .82rem; }
    .card-link .arrow { margin-left: auto; color: var(--ink-soft); }

    /* ---------- footer ---------- */
    footer { border-top: 1px solid var(--line); padding: 28px 0 40px; }
    .foot { display: flex; justify-content: space-between; gap: 16px; flex-wrap: wrap; font-size: .82rem; color: var(--ink-soft); }

    /* ---------- responsive ---------- */
    @media (max-width: 760px) {
      .nav ul { gap: 18px; }
      .hero { padding: 56px 0 40px; }
      .about-inner { grid-template-columns: 1fr; gap: 48px; }
    }
    @media (prefers-reduced-motion: reduce) {
      * { transition: none !important; scroll-behavior: auto !important; }
    }
  </style>
</head>
<body>

  <header>
    <nav class="wrap nav" aria-label="Main">
      <a href="#" class="logo">folio eighty one<span>.</span></a>
      <ul>
        <li><a href="#books">books</a></li>
        <li><a href="#about">about</a></li>
        <li><a href="#follow">follow</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <!-- HERO -->
    <section class="wrap hero">
      <p class="eyebrow">Puzzle books · made by hand, printed on demand</p>
      <h1>a pencil, a puzzle and <em>nowhere to be.</em></h1>
      <p>Sudoku and crossword books for the train, the coffee table and the quiet hour before bed. Every book has its own set of puzzles, with solutions in the back. Pick one, sharpen a pencil and take your time.</p>
      <div class="hero-links">
        <a class="pill solid" href="#books">See the books</a>
        <a class="pill" href="#about">About</a>
      </div>
    </section>

    <!-- BOOKS (cards are generated from the BOOKS list in the script below) -->
    <section class="wrap books" id="books">
      <div class="section-head">
        <h2>The books.</h2>
        <span class="note">All available on Amazon</span>
      </div>
      <div class="filters" role="group" aria-label="Filter books">
        <button type="button" data-filter="all" aria-pressed="true">All</button>
        <button type="button" data-filter="sudoku" aria-pressed="false">Sudoku</button>
        <button type="button" data-filter="crossword" aria-pressed="false">Crossword</button>
      </div>
      <div class="grid" id="book-grid"></div>
    </section>

    <!-- ABOUT -->
    <section class="about" id="about">
      <div class="wrap about-inner">
        <div class="polaroid">
          <!-- Put your photo at images/me.jpg (it loads automatically) -->
          <div class="photo" style="background-image:url('images/me.jpg')">your photo</div>
          <span class="sig">Macey</span>
        </div>
        <div>
          <p class="eyebrow">The person behind the books</p>
          <h2>hi, i'm Macey.</h2>
          <p>I make puzzle books under the name FolioEightyOne. I design every cover and page layout myself, and I care a lot about the small stuff: margins you can write in, clues that make you smile, and grids that feel good to finish.</p>
          <p>These books are for the moments when nothing needs your attention: a commute, a slow morning, a rainy afternoon. If you buy one, thank you. It really does reach me directly.</p>
        </div>
      </div>
    </section>

    <!-- FOLLOW -->
    <section class="wrap follow" id="follow">
      <div class="section-head">
        <h2>Follow along.</h2>
        <span class="note">New books, sneak peeks and sample puzzles</span>
      </div>
      <div class="follow-cards">
        <a class="card-link" href="https://www.instagram.com/YOUR_HANDLE" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><rect x="3" y="3" width="18" height="18" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor"/></svg>
          <span><strong>Instagram</strong><small>@YOUR_HANDLE</small></span>
          <span class="arrow">↗</span>
        </a>
        <a class="card-link" href="https://www.tiktok.com/@YOUR_HANDLE" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16.6 5.8A4.3 4.3 0 0 1 15.5 3h-3.1v12.4a2.6 2.6 0 1 1-2.6-2.6c.3 0 .5 0 .8.1V9.8a5.7 5.7 0 1 0 4.9 5.6V9.1a7.3 7.3 0 0 0 4.3 1.4V7.4a4.3 4.3 0 0 1-3.2-1.6z"/></svg>
          <span><strong>TikTok</strong><small>@YOUR_HANDLE</small></span>
          <span class="arrow">↗</span>
        </a>
        <a class="card-link" href="mailto:hello@example.com">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="m3 7 9 6 9-6"/></svg>
          <span><strong>Email</strong><small>hello@example.com</small></span>
          <span class="arrow">↗</span>
        </a>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap foot">
      <span>© <span id="year"></span> FolioEightyOne</span>
      <span>made for moments away from the screen.</span>
    </div>
  </footer>

  <script>
    /* ============================================================
       YOUR BOOKS — edit this list to add, remove or change books.
       - cover: path to the cover image in your repo (e.g. images/sudoku-01.jpg).
                If the file is missing, a simple placeholder cover is drawn instead.
       - amazon: your Amazon link. Leave as "" to show a "Coming soon" button.
       - category: "sudoku" or "crossword" (used by the filter buttons).
       - color: placeholder cover color (only used when there's no image).
       - badge: optional little tag on the cover, like "New".
       ============================================================ */
    const BOOKS = [
      {
        category: "sudoku",
        label: "Sudoku",
        title: "Sudoku / 01",
        desc: "Our first book of number puzzles, for slow mornings and quiet evenings.",
        meta: ["Easy to hard", "Solutions included", "Paperback"],
        inside: [
          "Puzzles arranged from easy to hard",
          "One large, clear grid per page",
          "Full solutions at the back",
        ],
        cover: "images/sudoku-01.jpg",
        color: "#2f3a33",
        amazon: "https://www.amazon.com/dp/YOUR_ASIN",
        badge: "",
      },
      {
        category: "crossword",
        label: "Crossword",
        title: "Crossword / 01",
        desc: "Witty, wide-ranging clues on everything from history to the internet.",
        meta: ["100 puzzles", "15 × 15 grids", "5.06 × 7.81 in", "Solutions included"],
        inside: [
          "100 newspaper-style 15 × 15 crosswords",
          "Clues on the left page, grid on the right",
          "Topics from history and art to film, food and tech",
          "No repeated answers or clues anywhere in the book",
        ],
        cover: "images/crossword-01.jpg",
        color: "#b8321f",
        amazon: "https://www.amazon.com/dp/YOUR_ASIN",
        badge: "New",
      },
      {
        category: "crossword",
        label: "Crossword",
        title: "Crossword / 02",
        desc: "A brand-new set of 100 puzzles, with nothing repeated from the first book.",
        meta: ["100 puzzles", "15 × 15 grids", "5.06 × 7.81 in", "Solutions included"],
        inside: [
          "100 all-new 15 × 15 crosswords",
          "Same layout and clue style as Volume 01",
          "Full solutions at the back",
        ],
        cover: "images/crossword-02.jpg",
        color: "#2e4a7a",
        amazon: "",          // empty = shows "Coming soon"
        badge: "Soon",
      },
    ];

    /* ---------- rendering (no need to edit below) ---------- */
    const grid = document.getElementById("book-grid");
    const esc = (s) => String(s).replace(/[&<>"']/g, (c) => ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" }[c]));

    function fallbackCover(book) {
      return `<div class="cover-fallback" style="background:${esc(book.color || "#333")}">
          <div class="cf-sub">${esc(book.label)}</div>
          <div class="cf-grid"></div>
          <div class="cf-title">${esc(book.title)}</div>
        </div>`;
    }

    function renderBooks(filter = "all") {
      grid.innerHTML = BOOKS
        .filter((b) => filter === "all" || b.category === filter)
        .map((b, i) => `
          <article class="book">
            <div class="cover-frame">
              ${b.badge ? `<span class="badge">${esc(b.badge)}</span>` : ""}
              <img src="${esc(b.cover)}" alt="Cover of ${esc(b.title)}" loading="lazy"
                   onerror="this.outerHTML = decodeURIComponent('${encodeURIComponent(fallbackCover(b))}')" />
            </div>
            <p class="label">${esc(b.label)}</p>
            <h3>${esc(b.title)}</h3>
            <p class="desc">${esc(b.desc)}</p>
            <p class="meta">${b.meta.map(esc).join(" · ")}</p>
            ${b.inside && b.inside.length ? `
              <details>
                <summary>what's inside</summary>
                <ul>${b.inside.map((x) => `<li>${esc(x)}</li>`).join("")}</ul>
              </details>` : ""}
            ${b.amazon
              ? `<a class="buy" href="${esc(b.amazon)}" target="_blank" rel="noopener">Buy on Amazon ↗</a>`
              : `<span class="buy soon">Coming soon</span>`}
          </article>`)
        .join("");
    }

    document.querySelectorAll(".filters button").forEach((btn) => {
      btn.addEventListener("click", () => {
        document.querySelectorAll(".filters button").forEach((b) => b.setAttribute("aria-pressed", "false"));
        btn.setAttribute("aria-pressed", "true");
        renderBooks(btn.dataset.filter);
      });
    });

    document.getElementById("year").textContent = new Date().getFullYear();
    renderBooks();
  </script>
</body>
</html>
