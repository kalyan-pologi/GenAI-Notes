# GenAI Notes: Claude Instructions

Multi-file single-page application (SPA) learning hub for AI and GenAI topics. Live at https://kalyan-pologi.github.io/GenAI-Notes/

## Project Structure

```
index.html              → Main app shell and sidebar navigation
assets/style.css       → All styles (responsive, dark theme)
assets/app.js          → Client-side router and note caching
notes/*.html           → Individual topic files (consolidated, no em dashes)
assets/img/            → SVG diagrams and hand-drawn visual explanations
.claude/               → Claude Code configuration and settings
```

**Note count:** Approximately 80+ active topic notes. Old Claude documentation files (claude-intro, claude-api, claude-context, etc.) have been consolidated into `claude-code.html`.

## Adding or Updating a Note

1. **Create or edit** `notes/topic-name.html` with proper structure:
   ```html
   <div class="section-header">
     <div class="tag">Category or Badge</div>
     <h1>🔤 Descriptive Title</h1>
     <p>One-sentence overview of this topic</p>
   </div>

   <div class="note-body">
     <h2>1 · Introduction or first section</h2>
     <p>Content here. Use <b>bold</b> for key concepts, <code>/slash-commands</code> or `code`.</p>
     
     <div class="grid2">
       <div class="card c3">
         <h3>Section Title</h3>
         <div class="b">Bullet points with arrow prefix</div>
       </div>
     </div>
   </div>
   ```

2. **Add nav link** to `index.html` in the appropriate sidebar group:
   ```html
   <div class="nav-item" data-note="topic-name">Display Title</div>
   ```

3. **Remove em dashes** (use "and", "or", or colons instead of em dashes for clarity)

4. **Test locally**: `python -m http.server 8000` then visit `http://localhost:8000/#topic-name`

5. **Commit with clear message**: `Add: Claude vision capabilities` or `Update: Expand context window section`

## Diagrams and Visual Explanations

To pair a text explanation with a diagram or flowchart:

1. **Wrap all content in `.note-body`** so typography scales correctly (raw `<h2>`/`<p>` inherit oversized browser defaults):
   ```html
   <div class="note-body">
     <h2>Section title</h2>
     <p>Explain the concept. Use <b>bold</b> for key terms, <code>/commands</code>, or key phrases.</p>

     <figure class="note-figure">
       <img src="assets/img/diagram-name.svg" alt="Detailed description for screen readers">
       <figcaption>Concise caption (max one line)</figcaption>
     </figure>

     <p>Resume explanation after the diagram.</p>
   </div>
   ```

2. **Create hand-drawn-style SVG diagrams** in `assets/img/`. Examples: `agentic-loop.svg`, `sub-agent-vs-team.svg`
   - Use `viewBox` sized to actual content dimensions
   - Apply hand-drawn filter: `feTurbulence` + `feDisplacementMap` with scale ~3.5
   - Font: `'Comic Sans MS', 'Segoe Print', cursive` for casual look
   - Colors: green `#5fbf72` (success), red `#ec6a3c` (alert), grey `#f4f4f4` (background), dark `#2b2b2b` (strokes/text)
   - Include arrowhead markers for flow diagrams
   - Validate XML: `python -c "import xml.dom.minidom as m; m.parse('assets/img/NAME.svg')"`

3. **Image paths are always relative to root** (`assets/img/...`), never `../assets/...`

4. **Styling is built-in**: `.note-figure img` in CSS caps width at 520px and centers automatically. Don't override.

5. **File format**: SVG is preferred (crisp zoom, tiny file size). PNG exports work if provided by user.

## CSS Classes and Styling

**Headers and structure:**
- `.section-header` → Top heading area with tag, title, description
- `.tag` → Small badge (e.g., "Claude Code", "Foundations")

**Content containers:**
- `.card .c1` through `.c15` → Colored info boxes (each has unique background and title color)
- `.grid3` → 3-column layout for cards
- `.grid2` → 2-column layout for cards
- `.note-body` → Wrapper for all text/content (fixes typography scaling)
- `.note-figure` → Diagram or image container

**Text formatting:**
- `.b` → Styled bullet points (adds arrow prefix via CSS)
- `.note` → Muted gray explanatory text
- `.sl` → Section label (uppercase, monospace)
- `.row` / `.k` / `.v` → Key-value pair display
- `.sep` → Horizontal divider
- `.new` → Experimental/beta badge (green)

**Interaction:**
- `.coming-soon` → Placeholder for unfinished topics

See existing notes (claude-code.html, agents.html, etc.) for working examples.

## Standards and Rules

**Writing:**
- No em dashes. Use conjunctions ("and", "or") or colons instead for clarity
- Bold key terms and commands with `<b>` or `<code>`
- Keep paragraphs concise and scannable
- Link to related topics instead of repeating content
- Use numbered sections (1 · Title) for long notes

**HTML:**
- Static HTML only. No inline `<script>` or inline `<style>` in notes
- Always wrap content in `<div class="note-body">` if it contains text
- Use semantic HTML5 when possible
- Validate HTML before commit

**Development:**
- One feature or fix per commit with clear message
- Test locally before pushing: `python -m http.server 8000` → `http://localhost:8000/#topic`
- Hard refresh browser after pushing (`Ctrl+Shift+R`) to clear cache
- Update this instructions file when adding new conventions

**File management:**
- Topic filenames use kebab-case: `topic-name.html`
- Keep notes focused and under ~500 lines
- Consolidate related topics (e.g., old claude-* files → claude-code.html)
- Delete or archive obsolete note files

---

**For architecture and design patterns, see REFACTOR.md**
