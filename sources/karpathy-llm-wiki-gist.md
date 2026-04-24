# llm-wiki — Karpathy Gist 原文

> 来源：https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
> 作者：Andrej Karpathy
> 日期：2026-04-04
> 本文件为不可变原始来源，LLM 读取但不修改

---

# LLM Wiki

A pattern for building personal knowledge with LLMs.

## Core idea

Most people's experience of LLMs + documents is something like RAG: you upload a set of files, the LLM retrieves relevant snippets at query time, and generates an answer. This works, but the LLM is re-discovering the knowledge from scratch every time you ask a question. Nothing accumulates. Ask a nuanced question that requires synthesizing five documents, and the LLM has to find and piece together the relevant snippets every single time. Nothing is built up.

The idea here is different. Instead of the LLM retrieving from raw docs at query time, it incrementally builds and maintains a persistent wiki — a structured, interlinked collection of markdown files — between you and the raw sources.

When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key info, and integrates it into the existing wiki — updating entity pages, modifying topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis.

The knowledge is compiled once, and then kept up to date, instead of re-derived at every query.

## Key distinction

> The wiki is a persistent, compound artifact. The cross-references are already there. The contradictions are already flagged. The synthesis already reflects everything you've read. The wiki gets richer with every source you add and every question you ask.

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sources, exploration, and asking the right questions. The LLM does all the grunt work — summarizing, cross-referencing, filing, and bookkeeping to make the knowledge base actually useful over time.

In practice, you're recommended to have the LLM agent and Obsidian side by side. The LLM edits based on the conversation, and you browse the result in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.

## Applications

- **Personal**: Track your own goals, health, psychology, self-improvement — archiving journal entries, articles, podcast notes, and building up a structured picture over time.
- **Research**: Go deep on a topic for weeks or months — reading papers, articles, reports, and progressively building a wiki that holds an evolving thesis.
- **Reading**: Archive each chapter as you read, building up pages for characters, themes, plot threads, and the connections between them.
- **Business/team**: Internal wiki maintained by an LLM, fed by Slack threads, meeting notes, project docs, customer calls.
- **Competitive analysis, due diligence, travel planning, course notes, hobby deep-dives** — anywhere you want knowledge to accumulate over time and be organized instead of scattered.

## Architecture

There are three layers:

1. **Raw sources** — Your curated collection of source documents. Articles, papers, images, data files. These are immutable — the LLM reads them but never modifies them. This is your ground truth.

2. **The wiki** — A directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, overviews, syntheses. The LLM fully owns this layer. It creates pages, updates them as new sources arrive, maintains cross-references, and keeps everything consistent. You read it; the LLM writes it.

3. **The schema** — A document (like Claude Code's CLAUDE.md or Codex's AGENTS.md) that tells the LLM what the wiki's structure is, what the conventions are, and what workflows to follow when ingesting sources, answering questions, or maintaining the wiki. This is the key config file — it's what turns the LLM into a disciplined wiki maintainer instead of a general-purpose chatbot. You and the LLM co-evolve this as you learn about your domain.

## Operations

**Ingest**: You put a new source into the raw collection and tell the LLM to process it. Example flow: the LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates related entity and concept pages in the wiki, and appends an entry to the log. A single source might touch 10–15 wiki pages.

**Query**: You ask a question against the wiki. The LLM searches relevant pages, reads them, and synthesizes an answer with citations. Answers can take different forms — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas. Important insight: **good answers can be archived back into the wiki as new pages**.

**Lint**: Periodically ask the LLM to do a health check on the wiki. Look for: contradictions between pages, outdated claims that have been superseded by updated sources, orphan pages without inbound links, important concepts that are mentioned but missing their own page, missing cross-references, data gaps that could be filled by a web search.

## Index and Log

Two special files help the LLM (and you) navigate a growing wiki:

- **index.md** is content-oriented. It's a table of contents for everything in the wiki — every page listed with a link, a one-line summary, and optional metadata (like date or number of sources). Organized by category (entities, concepts, sources, etc.).

- **log.md** is chronological. It's an append-only record of what happened and when — ingestions, queries, lint passes. Tip: if each entry starts with a consistent prefix (e.g. `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools — `grep "^## \[" log.md | tail -5` gives you the last 5 entries.

## Optional: CLI tools

- **qmd**: Local markdown search engine with hybrid BM25/vector search and LLM reranking, all on-device. It has both a CLI and an MCP server.
- **Obsidian Web Clipper**: Browser extension that converts web articles to markdown.
- **Download images locally**: Configure the attachment folder path in Obsidian settings.
- **Obsidian's graph view**: The best way to see the shape of your wiki.
- **Marp**: Markdown-based slide deck format.
- **Dataview**: Obsidian plugin that runs queries over page frontmatter.

## Why this works

The tedious part of maintaining a knowledge base isn't the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noticing when new data contradicts an old claim, staying consistent across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update cross-references, and can touch 15 files at once.

The human's job is to curate sources, guide the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.

This idea is related in spirit to Vannevar Bush's Memex (1945) — a personally curated knowledge base with associative trails between documents. Bush's vision was closer to this than what the web eventually became — private, actively curated, with the connections between documents being as valuable as the documents themselves. The part he couldn't solve was who does the maintenance work. The LLM takes care of that part.
