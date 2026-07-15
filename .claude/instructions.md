# GenAI Notes — Claude Instructions

You are helping maintain and expand a GenAI learning notes site. This document guides your behavior when working in this repo.

## Project Overview

**What:** Comprehensive learning hub for AI, GenAI, Claude, and LLM-related topics  
**Where:** https://kalyan-pologi.github.io/GenAI-Notes/  
**Tech:** Multi-file SPA (Single Page Application) with hash routing, no build step  
**Structure:**
```
index.html              → App shell (minimal)
assets/style.css       → All styling
assets/app.js          → Router + caching
notes/*.html           → Individual topic files (~91 currently)
CLAUDE.md              → Project docs
```

## When Adding New Content

### Creating a New Note

1. **Check if it exists**: Search `notes/` folder for the topic
2. **Create file**: `notes/my-topic.html` with this structure:
   ```html
   <div class="section-header">
     <div class="tag">Category Name</div>
     <h1>🔤 Topic Title</h1>
     <p>One-line description of what this covers.</p>
   </div>
   
   <!-- Content here - use the utility classes below -->
   <div class="coming-soon">
     <div class="cs-icon">🚧</div>
     <h3>Coming Soon</h3>
     <p>Brief placeholder text.</p>
   </div>
   ```

3. **Add nav link** to `index.html`:
   ```html
   <div class="nav-item" data-note="my-topic">My Topic Title</div>
   ```

4. **Test locally**: `python -m http.server 8000` then visit `http://localhost:8000/#my-topic`

5. **Commit**: One commit per feature, clear message

### Utility Classes for Content

Use these CSS classes to format content consistently:

- **`.section-header`** — Top of note (tag, h1, description)
- **`.tag`** — Category label (e.g., "Foundations", "Claude & Anthropic")
- **`.coming-soon`** — Placeholder for incomplete sections
- **`.card` + `.c1` through `.c15`** — Colored content cards
- **`.grid3` / `.grid2`** — 3-column or 2-column layouts
- **`.cs-section-label`** — Section divider with line
- **`.b`** — Bullet point (auto-adds arrow)
- **`.row` + `.k` + `.v`** — Key-value pairs
- **`.note`** — Subtle gray note text
- **`.new`** — Green "new" badge

Examples already in `notes/home.html` if you need reference.

## Code Style

- **HTML**: Keep it minimal, no inline scripts or styles in notes
- **CSS**: Already in `assets/style.css` — don't duplicate
- **JS**: Only in `assets/app.js` — notes are static HTML fragments
- **Formatting**: Use semantic HTML, keep lines under 100 chars where reasonable

## Content Standards

### For Each Note:

1. **Clear structure**: header → concept → examples → resources
2. **Visual breaks**: Use `.coming-soon`, `.card`, or `.cs-section-label` to separate ideas
3. **No duplication**: Link to related topics instead of repeating
4. **Practical examples**: Prefer code snippets and real-world patterns
5. **Progressive disclosure**: Start simple, build to advanced topics

### For Categories:

- **Claude & Anthropic** — API, models, capabilities specific to Claude
- **Foundations** — Core LLM concepts (tokens, context, prompting, etc.)
- **Embeddings & Vector Search** — Vector ops, similarity, chunking
- **RAG** — Retrieval-augmented generation patterns and techniques
- **Agents & Orchestration** — Agent loops, tool use, multi-agent systems
- **Frameworks & Tooling** — LangChain, LlamaIndex, Anthropic SDK, etc.
- **Fine-Tuning & Alignment** — LoRA, RLHF, instruction tuning
- **Multimodal & Diffusion** — Vision, image generation, multi-modal models
- **Production & Reliability** — Latency, caching, evals, security, observability
- **Patterns** — Architecture patterns (fan-out, memory, streaming, etc.)
- **Question Breakdowns** — Design interview-style system design questions

## Git Workflow

1. **Branch**: Work on `main` (small repo, no complex branching needed)
2. **Commit message**: Clear, present tense, reference the change type:
   - `Add: <what>` — New content/file
   - `Update: <what>` — Enhanced existing content
   - `Fix: <what>` — Bug or broken link
   - `Refactor: <what>` — Restructured code/content
3. **One commit per logical change** — Don't batch unrelated updates
4. **Push immediately** — Keep GitHub in sync

Example:
```
Add: Claude vision capabilities note

Document how to use Claude's vision API with images and multimodal inputs.
Includes examples of image analysis and screenshot understanding.
```

## When Responding to Prompts

- **Read CLAUDE.md first** for context on goals and structure
- **Check existing notes** before suggesting new content (avoid duplicates)
- **Suggest organization** if content feels scattered
- **Test locally** before declaring victory on link changes
- **Explain trade-offs** when refactoring — why this way is better
- **Keep it focused** — one feature/note per conversation turn

## Known Limitations & Quirks

- **No build step** — Everything is vanilla HTML/CSS/JS, no bundlers
- **Fetch over HTTP only** — Local testing needs `python -m http.server`, not `file://`
- **Static hosting** — GitHub Pages only, no backend APIs
- **Single file per note** — Don't split one topic across multiple files

## Next Priority Tasks

1. Fill in "Coming Soon" sections with real content (start with Claude & Anthropic)
2. Add code examples to production/reliability topics
3. Create comparison tables for model capabilities
4. Link related topics to each other
5. Add visual diagrams (ASCII or SVG) for architecture patterns

## Questions?

Refer to:
- **Project structure**: See REFACTOR.md
- **Live site**: https://kalyan-pologi.github.io/GenAI-Notes/
- **Git history**: `git log --oneline` to see past changes

---

**Last updated:** 2026-07-14  
**Maintained by:** Kalyan Pologi + Claude Code
