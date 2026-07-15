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

## Diagrams & Text-with-Images in Notes

To explain a concept with a diagram next to the text (Excalidraw-style flowcharts, etc.):

1. **Wrap prose in `.note-body`** so text uses the correct scoped sizes (raw `<h2>`/`<p>` inherit oversized browser defaults):
   ```html
   <div class="note-body">
     <h2>Section title</h2>
     <p>Explain the concept. Use <b>bold</b> for key terms and <code>/commands</code>.</p>

     <figure class="note-figure">
       <img src="assets/img/diagram-name.svg" alt="Describe the diagram for accessibility">
       <figcaption>Short caption</figcaption>
     </figure>

     <p>Continue the explanation after the image.</p>
   </div>
   ```

2. **Create diagrams as hand-drawn-style SVG** in `assets/img/` (not real Excalidraw files — code-generated SVGs that mimic the look):
   - `viewBox` sized to content; `font-family:'Comic Sans MS','Segoe Print',cursive`
   - A `feTurbulence` + `feDisplacementMap` filter (`scale≈3.5`) for the hand-drawn wobble
   - Green `#5fbf72` / red `#ec6a3c` / grey `#f4f4f4` boxes, dark `#2b2b2b` strokes, arrowhead markers
   - Validate it parses: `python -c "import xml.dom.minidom as m; m.parse('assets/img/NAME.svg')"`

3. **Paths are relative to `index.html` (root)** — always `assets/img/...`, never `../assets/...`.

4. Image styling is already in `style.css`: `.note-figure img` caps width at **520px** and centers — don't let diagrams fill the page.

5. SVG is preferred (crisp at any zoom, tiny files). Exported PNG works too if the user provides one.

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
