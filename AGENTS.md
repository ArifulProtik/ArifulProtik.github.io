# AGENTS.md — ai-engineer notes book

Greenfield repo (empty, no git, no files as of 2026-09-29). Goal: detailed, researched Markdown notes for **every node of https://roadmap.sh/ai-engineer**, published chapter-by-chapter as a free book on GitHub Pages.

## Non-negotiable source of truth

- Roadmap mirror: `roadmap.sh/ai-engineer` (2026). If roadmap.sh conflicts with this file on chapter order, follow roadmap.sh and update this file.
- Book stack: **mdBook + GitHub Pages** (user-chosen). No MkDocs/Jekyll unless user explicitly switches.
- Language for examples: **Python** (mdBook code blocks; JS only when the roadmap node requires it, e.g. Transformers.js).
- Depth: **detailed research** per note — concept, how-it-works, Python example, pitfalls, free resources. No concise summaries.

## mdBook layout (do not invent another)

```
book.toml
src/SUMMARY.md          # chapter/subchapter index = single source of truth
src/preface.md          # unnumbered first page, before ch00
src/ch00-prereqs.md
src/ch01-intro/...
src/ch02-how-llms-work/...
...
PROGRESS.md             # - [ ] per Node/Leaf, updated on every completion
.github/workflows/mdbook.yml  # build + deploy to gh-pages
```

- `src/SUMMARY.md` must exactly match the Chapter Index below. Add a new subchapter only if roadmap.sh added a node; update this file in the same commit.
- Per-note template (keep order):
  1. `# Title` + 3–5 learning goals (bullets)
  2. `## Detailed notes` (researched, no speculation)
  3. `## How it works` (mechanism, tokens/cost/limits where relevant)
  4. `## Example (Python)` (runnable, pinned lib versions in comment)
  5. `## Pitfalls / Gotchas`
  6. `## Free resources` (links only; format `[title](url) — 1-line why`)
  7. `## Done checklist` (`- [ ]` items; all checked = done)
- Free-resources rule: free only. If no free alternative exists, mark `[paid]` and justify in one line. Never invent URLs — only links you fetched/verified.

## Writing style (no AI slop — read as human-written)

- Concrete and direct; zero filler. Start each section with the key fact or definition, never a generic intro.
- Banned: `delve`, `tapestry`, `landscape`, `game-changer`, `in today's fast-paced world`, `it is important to note`, `as an AI`, emojis, hype adjectives without numbers.
- Active voice, short sentences and paragraphs; define jargon on first use.
- Show via mechanism + runnable code + real numbers (latency, cost, limits), not adjectives.
- Cut any sentence that doesn't help the reader build something or make a decision.

## Chapter / Subchapter Index (mirrors roadmap.sh/ai-engineer visual nesting)

Notation: `Main chapter` > `Group box` > `Node` > `Leaf`. One mdBook file per Main chapter dir; Groups become `##` sections inside it. `PROGRESS.md` tracks every Node/Leaf as `- [ ] chXX-group-node`. Work in visual order (top-to-bottom); one Node per session unless asked otherwise.
Side boxes (`Scrimba`, `Related Roadmaps`) are resources, not chapters — log them under ch13.
Index rule: one bullet per node — never join nodes with `|`; each is its own sub-chapter note.

- **Preface (unnumbered, first page of SUMMARY.md — write before ch00)** — `src/preface.md`: what this book is + node-for-node mapping to roadmap.sh/ai-engineer; how to use (goals → notes → example → pitfalls → resources → checklist); conventions (Python, free-only links, pinned versions). Not a roadmap node — no PROGRESS.md checkbox. Wherever the author is named, write it as [MD Ariful Islam Protik](https://github.com/arifulprotik) (linked).
- **ch00 Pre-requisites (One of these)** — `src/ch00-prereqs.md`
  - Frontend
  - Backend
  - Full-Stack (pick one track)
- **ch01 Introduction** — `src/ch01-intro/`
  - What is an AI Engineer?
  - Roles and Responsibilities
  - Impact on Product Development
  - AI Engineer vs ML Engineer
- **ch02 How LLMs Work** — `src/ch02-how-llms-work/`
  - Group `Common Terminology`
    - AI vs AGI
    - Large Language Model (LLM)
    - Embeddings
    - Training
    - Inference
    - Vector DBs
    - AI Agents
    - RAGs
    - Context Window
    - Fine-tuning
    - Prompt Engineering
    - Context Engineering
  - Group `Core LLM Elements`
    - Tokens
    - Context
    - Sampling Parameters
    - Temperature
    - Top-K
    - Top-P
    - Repetition Penalties
- **ch03 OpenAI API** — `src/ch03-openai-api/`
  - Chat Completions API
  - Writing Prompts
  - OpenAI Playground
  - Group `Managing Tokens`
    - Maximum Tokens
    - Token Counting
    - Pricing Considerations
  - Fine-tuning (intro; deep dive in ch09)
- **ch04 Prompt Engineering** — `src/ch04-prompt-eng/` (follows Prompt Engineering roadmap link)
  - Zero-Shot Prompting
  - Few-Shot Prompting
  - Chain-of-Thought
  - System Prompting
  - Roles and Behaviours
  - Context and Constraints
  - Structured Outputs
  - Streaming Responses
- **ch05 Safety & Ethics** — `src/ch05-safety/`
  - Understanding AI Safety Issues
  - Prompt Injection Attacks
  - Bias and Fairness
  - Security and Privacy Concerns
  - Conducting Adversarial Testing
  - OpenAI Moderation API
  - Adding End-User IDs in Prompts
  - Robust Prompt Engineering
  - Know Your Customers / Usecases
  - Constraining Outputs and Inputs
  - Safety Best Practices
- **ch06 Open-Source AI** — `src/ch06-opensource/`
  - Open vs Closed Source Models
  - Popular Open Source Models
  - Group `Hugging Face`
    - Hugging Face Hub
    - Hugging Face Tasks
    - Finding Open Source Models
    - Using Open Source Models
    - Inference SDK
  - Transformers.js
  - Group `Ollama`
    - Ollama Models
    - Ollama SDK
- **ch07 Embeddings** — `src/ch07-embeddings/`
  - What are Embeddings
  - Group `Use Cases for Embeddings`
    - Semantic Search
    - Recommendation Systems
    - Anomaly Detection
    - Data Classification
  - Group `OpenAI Embeddings`
    - OpenAI Embeddings API
    - OpenAI Embedding Models
    - Pricing Considerations
  - Group `Open-Source Embeddings`
    - Sentence Transformers
    - Models on Hugging Face
- **ch08 Vector Databases** — `src/ch08-vector-dbs/`
  - Purpose and Functionality
  - Group `Popular Vector DBs (pick one deep: Chroma)`
    - Chroma
    - Pinecone
    - Weaviate
    - FAISS
    - LanceDB
    - Qdrant
    - Supabase
    - MongoDB Atlas
  - Indexing Embeddings
  - Performing Similarity Search
  - Implementing Vector Search
- **ch09 RAG & Implementation** — `src/ch09-rag/`
  - RAG Usecases
  - RAG vs Fine-tuning
  - Chunking
  - Embedding
  - Vector Database
  - Retrieval Process
  - Generation
  - Implementing RAG
  - Group `Ways of Implementing RAG`
    - Using SDKs Directly
    - LangChain
    - LlamaIndex
    - OpenAI Assistant API
    - Replicate
- **ch10 AI Agents** — `src/ch10-agents/`
  - RAG Alternative
  - Agents Usecases
  - Prompt Engineering (agent prompts)
  - ReAct Prompting
  - Manual Implementation
  - OpenAI Functions / Tools
  - OpenAI Assistant API
  - Building AI Agents
- **ch11 MCP** — `src/ch11-mcp/` (2026 node; verify against latest visual)
  - What is MCP
  - Building MCP Servers
  - Building MCP Clients
- **ch12 Multimodal AI** — `src/ch12-multimodal/`
  - Multimodal AI Usecases
  - Image Understanding
  - Image Generation
  - Video Understanding
  - Audio Processing
  - Text-to-Speech
  - Speech-to-Text
  - Multimodal AI Tasks
  - OpenAI Vision API
  - DALL-E API
  - Whisper API
  - Hugging Face Models
  - LangChain for Multimodal Apps
  - LlamaIndex for Multimodal Apps
  - Implementing Multimodal AI
- **ch13 Ship It & Keep Learning** — `src/ch13-ship-it/`
  - Group `Development Tools`
    - AI Code Editors
    - Code Completion Tools
  - Group `Related Roadmaps`
    - AI and Data Scientist Roadmap
    - Prompt Engineering
    - Data Analyst Roadmap
    - Vibe Coding
    - Claude Code
    - Forward Deployed Engineer Roadmap
  - Scrimba – AI Engineer Path (resource link, `[paid]` with discount note)

## Commands (exact)

```bash
cargo install mdbook                  # one-time
mdbook init --title "AI Engineer Notes" .
mdbook serve --open                   # local preview :3000
mdbook build                          # output in book/
```

- Deploy: `book.toml` must set `output.html.git-repository-icon` off if it breaks Pages; workflow `.github/workflows/mdbook.yml` builds on `main` push and publishes `./book` via `peaceiris/actions-gh-pages@v4` to `gh-pages` branch. Never commit `book/` output.
- No `npm`/`pip` book deps. Python examples use stdlib + `openai`, `sentence-transformers`, `chromadb`, `langchain` pinned per-file; note install line in code comment, do not add root requirements file unless user asks.

## Session workflow (every future session)

1. Read `PROGRESS.md` + `src/SUMMARY.md`, pick the first `- [ ]` subchapter in index order.
2. Research (webfetch/websearch) then write the single note file per template.
3. Verify: `mdbook build` must pass; fix broken links/`SUMMARY.md` paths before claiming done.
4. Flip that item to `- [x]` in `PROGRESS.md` and check all boxes in the note's Done checklist. Commit per chapter.

## Exclude

Generic advice, paywalled courses as primary sources, unverified URLs, committing `book/`, restructuring `src/` outside mdBook conventions.
