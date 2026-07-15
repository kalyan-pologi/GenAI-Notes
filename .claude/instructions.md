# GenAI Notes: Claude Instructions

SPA learning hub for AI and GenAI topics. Live at https://kalyan-pologi.github.io/GenAI-Notes/

## Structure

```
index.html              → App shell and sidebar navigation
assets/style.css       → All styles
assets/app.js          → Router and note caching
notes/*.html           → Topic files (80+)
assets/img/            → SVG diagrams
```

Old Claude doc files consolidated into `claude-code.html`.

## Adding a Note

1. Create `notes/topic-name.html`:
   ```html
   <div class="section-header">
     <div class="tag">Category</div>
     <h1>🔤 Title</h1>
     <p>One-line description</p>
   </div>
   <div class="note-body">
     <h2>1 · Section</h2>
     <p>Content. Use <b>bold</b>, <code>code</code>, .card, .grid2/.grid3 classes.</p>
   </div>
   ```

2. Add to `index.html`: `<div class="nav-item" data-note="topic-name">Title</div>`

3. No em dashes (use "and", "or", colons)

4. Test: `python -m http.server 8000` → `http://localhost:8000/#topic-name`

5. Commit: `Add: Topic name` or `Update: Section title`

## Diagrams

1. Place SVG in `assets/img/diagram-name.svg`
2. Wrap content in `.note-body`; use `.note-figure` for images
3. Hand-drawn style: `feTurbulence` + `feDisplacementMap` filter (scale ~3.5)
4. Font: `'Comic Sans MS', 'Segoe Print', cursive`
5. Colors: green `#5fbf72`, red `#ec6a3c`, grey `#f4f4f4`, dark text `#2b2b2b`
6. Paths relative to root: `assets/img/...`

## CSS Classes

- `.section-header`, `.tag` → Headers
- `.card .c1-.c15` → Colored boxes
- `.grid3 / .grid2` → Layouts
- `.note-body` → Text wrapper
- `.b` → Bullets
- `.note` → Muted text
- `.new` → Beta badge

## Rules

**Writing:** No em dashes. Bold key terms. Keep focused. Link instead of repeat.

**HTML:** Static only. Wrap text in `.note-body`. Semantic HTML5.

**Dev:** One feature per commit. Test locally. Hard refresh after push (`Ctrl+Shift+R`).

**Files:** Kebab-case names. Under 500 lines. Consolidate old files. Delete obsolete notes.
