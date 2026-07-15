# GenAI Notes — Claude Instructions

Multi-file SPA learning hub for AI/GenAI topics at https://kalyan-pologi.github.io/GenAI-Notes/

## Structure

```
index.html              → App shell
assets/style.css       → All CSS
assets/app.js          → Router + note caching
notes/*.html           → Individual topic files (91 total)
```

## Adding a New Note

1. Create `notes/topic-name.html` with content:
   ```html
   <div class="section-header">
     <div class="tag">Category</div>
     <h1>🔤 Title</h1>
     <p>Description</p>
   </div>
   <!-- Content here -->
   ```

2. Add nav link to `index.html`:
   ```html
   <div class="nav-item" data-note="topic-name">Title</div>
   ```

3. Test: `python -m http.server 8000` → `http://localhost:8000/#topic-name`

4. Commit with clear message: `Add: Claude vision capabilities`

## CSS Classes

- `.section-header`, `.tag` → Headers
- `.coming-soon` → Placeholders
- `.card .c1-.c15` → Colored content boxes
- `.grid3 / .grid2` → Layouts
- `.b` → Bullets
- `.note` → Gray text

See existing notes for examples.

## Rules

- Static HTML only (no inline scripts/styles in notes)
- One feature per commit
- Test locally before pushing
- Keep notes focused—link to related topics instead of repeating

---

**See REFACTOR.md for architecture details.**
