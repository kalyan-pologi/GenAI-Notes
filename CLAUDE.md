# GenAI-Notes Project

A comprehensive learning hub for AI, GenAI, Claude, and related technologies. Hosted on GitHub Pages at https://kalyan-pologi.github.io/GenAI-Notes/

## Project Goals

Learn and document:
- Large Language Models (LLMs) — foundations, how they work
- GenAI concepts — embeddings, RAG, agents, fine-tuning
- Claude and Anthropic — models, APIs, SDKs
- Production patterns — caching, streaming, evals, guardrails
- Industry tools — LangChain, LangGraph, LlamaIndex, vector DBs
- Real-world architectures — ChatGPT, Copilot, Perplexity, agents

## Project Structure

```
GenAI-Notes/
├── index.html              # Main single-page application
├── CLAUDE.md               # This file
├── README.md               # GitHub repo info
├── claude/                 # Claude & Anthropic notes
│   ├── claude-api.md
│   ├── prompt-engineering.md
│   ├── tool-use.md
│   └── ...
├── patterns/               # GenAI patterns & architectures
│   ├── rag-pattern.md
│   ├── agent-loop.md
│   └── ...
├── technologies/           # Framework & tool documentation
│   ├── langchain.md
│   ├── vector-dbs.md
│   └── ...
└── assets/                 # Images, diagrams (if needed)
```

## Technical Stack

- **Frontend:** Single-page HTML/CSS/JS app
- **Hosting:** GitHub Pages (static)
- **Navigation:** Sidebar + dynamic section switching
- **Design:** Dark theme with colorful cards and icons

## Content Strategy

Each topic should include:
1. **Core Concept** — What it is, why it matters
2. **Key Points** — Bullets, code snippets, diagrams
3. **Real-world Use Cases** — Practical examples
4. **Tools & Resources** — Links to docs, libraries, papers
5. **Common Mistakes** — Pitfalls to avoid

## Next Steps

1. Create `/claude` folder with initial notes on Claude APIs
2. Modularize components in `index.html` for reusability
3. Add navigation links between markdown files and the main app
4. Populate each section with content as you learn

## Collaboration with Claude Code

- Ask Claude to help fill content, explain concepts, or review your notes
- Use `/code-review` for checking quality before commits
- Push frequently to GitHub — each commit documents your learning progress
