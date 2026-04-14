---
name: second-brain
description: Build and maintain a compounding personal knowledge base — a cross-linked, cited markdown wiki that gets smarter with every source ingested, query answered, and answer filed back.
---

# Second Brain — A Knowledge Base That Compounds

Most AI tools (NotebookLM, ChatGPT uploads, basic RAG) re-derive answers from scratch every time. A second brain is different. It's a **compiled, interlinked wiki** that the LLM maintains for you. Every new source updates multiple pages. Every good answer gets filed back. Every week the brain is smarter than it was last week.

You curate sources and ask questions. The LLM does the summarizing, cross-referencing, filing, and bookkeeping.

## Quick Start

```
/second-brain init research
# Scaffolds ./second-brain/research/

/second-brain ingest path/to/article.md
# Reads the source, summarizes, cross-links, flags contradictions, logs

/second-brain query "what do we know about X?"
# Reads index, finds relevant pages, synthesizes with [Source:] citations,
# offers to file the answer back

/second-brain explore      # Surface unexplored connections
/second-brain lint         # Health check: contradictions, stale claims, orphans
/second-brain prep "Q3 planning review"   # One-page briefing from the brain
/second-brain status       # All focus areas, page counts, last-ingest dates
```

## When to Use This Skill

- You're accumulating knowledge about a domain (a market, a codebase, a set of customers, a research area) and want it to stick
- Before writing a doc, making a decision, or prepping a meeting, you want to pull together everything you already know
- You've noticed the same research keeps getting re-done because prior work gets buried
- You want persistent, queryable memory for stakeholders, decisions, customer insights, competitive intel, domain learning — anything you return to repeatedly
- You want to replace scattered notes, bookmarks, and chat histories with one cited, linked, compounding store

## Core Concept: The Compounding Loop

```
Sources (raw/)  →  Wiki (wiki/)  →  Queries (outputs/)  →  File back into wiki/
         ↑___________________________________________________________|
                       Knowledge compounds every cycle
```

Unlike standard skills that produce one-shot outputs, the brain **evolves**. Run it for a month and the brain knows your domain well enough to answer most prep questions instantly.

---

## Architecture

### Default Location

By default, all focus areas live under `./second-brain/` at the root of whatever project you're working in. This keeps the brain git-commitable and travels with the repo. On first `init`, the skill confirms the root; you can override to `~/second-brain/` for a cross-project personal brain, or any other path.

```
./second-brain/
├── README.md                         # How the brain works (created once)
└── {focus-slug}/                     # One folder per focus area
    ├── CLAUDE.md                     # Per-focus schema (rules for this brain)
    ├── raw/                          # Immutable source documents
    │   └── assets/                   # Images, screenshots, diagrams
    ├── wiki/                         # LLM-maintained compiled knowledge
    │   ├── index.md                  # Catalog of every page, one-line each
    │   ├── log.md                    # Append-only activity log
    │   └── *.md                      # Wiki pages (one per concept)
    └── outputs/                      # Briefings, reports, lint reports
```

### Default Focus Areas (Generic)

Offered at first `init`; the user can pick any, skip them, or define their own slug:

| Slug | What goes in it |
|---|---|
| `knowledge-base` | General reference: concepts, definitions, how-things-work, your running understanding of a domain |
| `research` | Sources you're gathering on a specific question or investigation |
| `projects` | Active project context, decisions made, architecture notes, retrospectives |
| `people` | Stakeholder profiles, preferences, past interactions, relationship history |
| `decisions` | Decision history, rationale, alternatives considered, outcomes, revisit triggers |
| `domain` | Your ongoing learning in a field: frameworks, lessons, mental models, patterns |

**Optional PM-oriented preset** (offer if the user's work is product-management-adjacent): `product-knowledge`, `competitive-intelligence`, `customer-insights`, `stakeholders`, `decisions`, `domain-knowledge`.

The user can always create arbitrary focus areas (`nps-program`, `phd-thesis`, `marathon-training`, `quantum-computing-notes` — anything).

### Wiki Page Conventions

Every wiki page starts with:

```yaml
---
title: <Page Title>
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
source_count: <n>
status: draft | working | stable
---
```

Followed by a one-paragraph summary, then the body.

**Cross-linking rules:**
- Use `[[page-name]]` Obsidian-style links between pages. Link aggressively.
- Every factual claim cites its source inline: `[Source: filename.md]`
- When a new source contradicts an existing claim: flag both, cite both, note which is more recent. **Never silently overwrite.**

**Index and log:**
- `wiki/index.md` — catalog, updated on every ingest. Organize by category.
- `wiki/log.md` — append-only. Format: `## [YYYY-MM-DD] {action} | {one-line description}` where action is `init | ingest | query | explore | lint | update`.

---

## Context Routing Logic (Internal)

Before running any mode, check:

| Mode | Check first | Then |
|---|---|---|
| `init` | Does `./second-brain/{slug}/` already exist? | If yes, do not clobber. Ask whether to use existing or pick new slug. |
| `ingest` | Which focus area does this source belong to? | If ambiguous, ask. A single source can be ingested into multiple focus areas. |
| `query` | Which focus area(s) are relevant? | Read all relevant `wiki/index.md` files first, then drill. |
| `prep` | Which focus areas touch this topic? | Pull from all of them; cite across. |
| `lint`, `explore` | Operates on one focus area at a time. | Ask which if not specified. |
| `status` | Scan `./second-brain/*/` | Report per-focus counts. |

**Graceful degradation:**
- If `agent-browser` is installed (`which agent-browser`), use it to scrape URLs during `ingest`. If not, use the `WebFetch` tool. If neither is available, ask the user to paste the content manually. Do not prompt them to install anything unless they ask.
- If the brain doesn't exist yet and the user asks a query, offer to run `/second-brain init` first.

---

## Mode 1: `init` — Scaffold a New Focus Area

**Trigger:** `/second-brain init [focus-slug]`

### Flow

**Confirm root path (first time only):** if no `./second-brain/` exists anywhere in the tree, ask: *"I'll put the brain at `./second-brain/` (project-local, git-commitable). Use this or a different path?"*

**If slug provided:** slugify (lowercase, hyphens, no special chars) and proceed.

**If no slug:** ask one question at a time:

1. "What do you want to build a knowledge base around? (a domain, a project, a set of people, a research question — anything you're accumulating knowledge about)"
2. "What are 3-5 things you're always trying to stay on top of within that area?"
3. "Any URLs or files you'd like to seed the brain with right now? (optional — you can always add more later)"

Or offer the default focus areas and let them pick one or more.

### Scaffold

Create:
- `./second-brain/{slug}/raw/assets/`
- `./second-brain/{slug}/wiki/`
- `./second-brain/{slug}/outputs/`
- `./second-brain/{slug}/CLAUDE.md` (per-focus schema, template below)
- `./second-brain/{slug}/wiki/index.md` (bootstrap)
- `./second-brain/{slug}/wiki/log.md` (with the `init` entry)

### Per-focus `CLAUDE.md` Template

```markdown
# {Focus Title} — Second Brain Schema

## What This Is
A personal knowledge base about {focus}. The human curates sources and asks questions. The LLM writes and maintains the entire wiki.

## Architecture
- raw/ contains immutable source documents. Never modify files in raw/.
- raw/assets/ holds images and diagrams referenced by sources.
- wiki/ is LLM-owned: pages, cross-references, index, log.
- outputs/ holds generated briefings, reports, and lint reports. Promote valuable outputs into wiki/ as new pages.

## Wiki Conventions
- Every page: its own .md file, YAML frontmatter (title, created, last_updated, source_count, status), one-paragraph summary.
- [[page-name]] cross-links. Link aggressively.
- Every factual claim cites source: [Source: filename.md].
- On contradiction: flag both claims, cite both, note recency. Never silently overwrite.

## Index and Log
- wiki/index.md: catalog of every page with a one-line description, organized by category.
- wiki/log.md: append-only. Format: `## [YYYY-MM-DD] action | Description`. Actions: init, ingest, query, explore, lint, update.

## Ingest Workflow (when a source lands in raw/)
1. Read the full source.
2. Summarize key takeaways to the user.
3. Create or update a summary page in wiki/.
4. Update wiki/index.md.
5. Update ALL relevant existing pages — one source often touches many.
6. Add backlinks from existing pages to new content.
7. Flag contradictions with existing content.
8. Append entry to wiki/log.md.

## Query Workflow (when the user asks a question)
1. Read wiki/index.md to find relevant pages.
2. Read those pages, following [[links]] for connected context.
3. Synthesize answer with citations to wiki pages.
4. Render in the best format: wiki page, comparison table, briefing, slide outline, or visualization.
5. If the answer is substantial, offer to file it back into wiki/.
6. If the question reveals a gap, flag it and suggest what sources would fill it.

## Focus Areas
- {interest 1}
- {interest 2}
- {interest 3}
```

### Bootstrap `wiki/index.md`

```markdown
# Wiki Index — {Focus Title}

_Last updated: {today}_

Maintained by the LLM. Every page listed with a one-line summary.

_(No pages yet. Add sources to raw/ and run `/second-brain compile` to build the wiki.)_
```

### Bootstrap `wiki/log.md`

```markdown
# Wiki Log — {Focus Title}

Append-only record of all wiki activity.

## [{today}] init | Knowledge base scaffolded
Focus: {focus}. Interests: {interests}. Ready for first sources.
```

### Scrape Initial URLs (if provided)

For each URL:
1. Check `which agent-browser`.
2. If available: open → wait networkidle → extract text from `article` (fallback `main`, then `body`) → get title → save as `raw/{slugified-title}.md` → close.
3. If not available: use `WebFetch`, or ask the user to paste content into a new file in `raw/`.

### Finish

After scaffolding, print the next-steps summary and point the user to the Starter Prompts section below.

---

## Mode 2: `ingest` — Add a Source

**Trigger:** `/second-brain ingest <path-or-url> [--focus=<slug>]`

### Flow

1. **Locate source.** If URL and `agent-browser` is available, scrape into `raw/`. If local file outside the brain, copy into `raw/` with a descriptive slug. If already in `raw/`, proceed.
2. **Identify focus area.** Use `--focus` flag if passed. Otherwise infer from content and ask to confirm. A source can be ingested into multiple focus areas (e.g., a user interview touches both `customer-insights` and `product-knowledge`).
3. **Read fully.** Don't skim.
4. **Discuss takeaways.** Summarize the 3-5 key claims to the user before writing anything. Let them redirect if they want a different angle.
5. **Write/update wiki:**
   - Create or update the relevant summary page in `wiki/`.
   - Update `wiki/index.md` (new page entry + any category reorganization).
   - Update ALL other pages where this source adds, confirms, or contradicts a claim.
   - Add backlinks from existing pages to new content.
   - On contradiction: flag explicitly with both citations, note recency.
6. **Log.** Append `## [YYYY-MM-DD] ingest | {filename} — touched N pages` to `wiki/log.md`.
7. **Report.** Tell the user exactly which pages were created or updated so they can scan the diff.

**One source at a time produces better wikis than batch ingest.** Encourage the user to ingest individually and discuss takeaways. Use `compile` only for bulk catch-up.

---

## Mode 3: `query` — Ask the Brain

**Trigger:** `/second-brain query "<question>" [--focus=<slug>]`

### Flow

1. **Identify focus area(s).** Use `--focus` if given. Otherwise pick the most relevant — if the question crosses focus areas, read multiple indexes.
2. **Read `wiki/index.md`** for each relevant focus area.
3. **Drill into pages.** Follow `[[links]]` for connected context. Stop when you have enough; don't read everything.
4. **Synthesize answer.**
   - Every factual claim cites `[Source: wiki-page.md]` or `[Source: raw-source.md]`.
   - If evidence is thin, say so. If the wiki has contradictions on this topic, surface them.
   - Render in the best format: prose, comparison table, briefing, slide outline, decision matrix.
5. **Offer to file back.** "Save this as `wiki/{suggested-name}.md` and update the index?" If yes, do it and append an `update` entry to the log.
6. **Flag gaps.** If the question surfaced something the wiki doesn't cover well, suggest 1-3 sources that would fill the gap.

---

## Mode 4: `compile` — Batch Build/Rebuild

**Trigger:** `/second-brain compile [--focus=<slug>]`

Use when many sources have landed in `raw/` at once and you want the LLM to process them all. Weaker than one-at-a-time ingest but valuable for initial bootstrap or catch-up.

### Flow

1. For each file in `raw/` not yet in the log as ingested:
   - Run the full ingest workflow.
2. After the batch, show the updated `wiki/index.md` so the user can see the shape of what was built.
3. Append a batch entry to the log: `## [YYYY-MM-DD] compile | Processed N sources, touched M pages`.

---

## Mode 5: `explore` — Find Unexplored Connections

**Trigger:** `/second-brain explore [--focus=<slug>]`

### Flow

1. Read `wiki/index.md` and scan all pages for topics that appear in multiple contexts but aren't directly linked.
2. Identify the 5 most interesting unexplored connections.
3. For each: explain what insight it might reveal and what source would confirm it.
4. Offer to create new pages or cross-references for confirmed connections.
5. Save the explore session as `outputs/explore-YYYY-MM-DD.md` and log it.

---

## Mode 6: `lint` — Health Check

**Trigger:** `/second-brain lint [--focus=<slug>]`

### Checks

- Contradictions between pages
- Stale claims superseded by newer sources (check against `last_updated` and source dates)
- Orphan pages with no inbound `[[links]]`
- Important concepts mentioned across pages but never given their own page
- Missing cross-references (same entity named but not linked)
- Claims without `[Source:]` citations

**Output:** `outputs/lint-report-YYYY-MM-DD.md` with each issue, location, and suggested fix. Also suggest 3 sources that would fill the biggest gaps. Append `lint` entry to log.

Run roughly weekly or after every 10 ingests.

---

## Mode 7: `prep` — One-Page Briefing

**Trigger:** `/second-brain prep "<topic>"`

### Flow

1. Identify which focus areas touch the topic (can be multiple).
2. Read relevant indexes and pages.
3. Produce a one-page briefing structured as:
   - **Current state** — what we know, with citations
   - **Key tensions** — contradictions, open debates, trade-offs
   - **Open questions** — what the wiki can't answer yet
   - **Recommendation** — what I'd argue for, given the evidence
4. Save to `outputs/briefing-{topic-slug}-YYYY-MM-DD.md` and log.
5. Offer to also file the briefing as a wiki page if it's evergreen.

This is the mode most users reach for most often. It turns the brain into a 5-minute prep ritual before any meeting, decision, or doc.

---

## Mode 8: `status` — Brain Dashboard

**Trigger:** `/second-brain status`

Report:
- All focus areas under `./second-brain/`
- Per focus area: page count, raw source count, last-ingest date, top 5 most-linked pages (hubs), count of orphan pages, count of open contradictions flagged
- Brains that haven't been touched in >30 days (stale)
- Suggested next action per focus area ("lint overdue", "low source count", "big gap flagged in last query")

---

## Integrations

The brain compounds only when outputs flow into it and questions flow out of it. Two simple patterns.

### Pattern A: Feed Skill Outputs Into the Brain

After any skill produces a durable artifact, offer to file it:

```
/<any-skill>  →  /second-brain ingest <output-path> --focus=<slug>
```

Natural pairings (using skills elsewhere in this repo):

| Skill | Target focus area |
|---|---|
| `meeting-notes` | `decisions` + topic-relevant focus |
| `decision-doc` | `decisions` |
| `user-research-synthesis`, `voice-of-customer`, `user-interview` | `customer-insights` or `research` |
| `competitor-analysis`, `win-loss-analysis`, `sales-battlecard` | `competitive-intelligence` |
| `weekly-review`, `post-mortem`, `feature-results` | `domain` or `projects` |
| `stakeholder-tactics` | `people` |
| `quick-research` | `research` |

### Pattern B: Pull Brain Context Into Skill Inputs

Before running any skill that needs evidence or context:

```
/second-brain query "<specific ask>" --focus=<slug>  →  paste into /<any-skill>
```

Or use `prep` for a full briefing:

```
/second-brain prep "<topic>"  →  start /<any-skill>
```

Natural pairings:

| Skill | What to pull from the brain |
|---|---|
| `prd-draft`, `prd-lite` | Background section: domain, user, competitive context with citations |
| `daily-plan` | What you know about today's meeting topics |
| `meeting-agenda`, `interview-guide` | `/second-brain prep` on the topic or interviewee |
| `strategy-sprint`, `write-prod-strategy` | Evidence base from all relevant focus areas |
| `decision-doc`, `decision-council` | Related past decisions — don't re-litigate old debates |
| `business-case-builder`, `opportunity-sizing` | Market and customer context for the assumptions |

None of this is hardcoded. If you use a skill that produces useful knowledge, ingest its output. If you use a skill that needs context, query the brain first. That's it.

---

## Starter Prompts

Copy-paste versions of every mode. These are the operational manual for the brain.

### Initialize a New Focus Area

> `/second-brain init research`

Or interactively:

> `/second-brain init`
>
> (Answer: What area? What 3-5 things do you want to stay on top of? Any seed URLs?)

### Compile a Batch of Sources

Drop multiple files into `./second-brain/{focus}/raw/` then:

> `/second-brain compile --focus=research`
>
> Read the CLAUDE.md at ./second-brain/research/. Then process every file in raw/ not yet logged as ingested. For each: read fully, create or update a summary page in wiki/, update index.md, update all relevant existing pages, add backlinks, flag contradictions, log the ingest. When done, show me the updated index.md so I can see the shape.

### Ingest One Source (Preferred)

> `/second-brain ingest path/to/source.md --focus=customer-insights`
>
> Read the source fully. Summarize the 3-5 key takeaways to me first. Once we've discussed, update the wiki: create/update the summary page, update index, update all relevant existing pages, add backlinks, flag contradictions, log. Show me which pages you created or updated.

**One at a time with discussion produces dramatically sharper wikis than batch `compile`.**

### Scrape a URL Into `raw/`

> `/second-brain ingest https://example.com/article --focus=research`

If `agent-browser` is installed, the skill will scrape automatically. Otherwise `WebFetch` is used, or the user is asked to paste content manually.

Install agent-browser (optional):
```
npm install -g agent-browser && agent-browser install
```

### Health Check

> `/second-brain lint --focus=customer-insights`
>
> Run the full lint workflow per CLAUDE.md. Output to outputs/lint-report-[date].md. Flag contradictions, stale claims, orphan pages, missing cross-references, claims without source citations. Suggest 3 sources that would fill the biggest gaps.

Run weekly, or after every 10 ingests.

### Explore Connections

> `/second-brain explore --focus=knowledge-base`
>
> Read wiki/index.md. Identify the 5 most interesting unexplored connections between existing topics. For each, explain what insight it might reveal and what source would confirm it. If any are strong enough, create new wiki pages or add cross-references and update the index.

### Status Dashboard

> `/second-brain status`
>
> Scan every focus area under ./second-brain/. Report page counts, raw source counts, last-ingest dates, top 5 hub pages, orphan counts, open contradictions, and any brain that hasn't been touched in >30 days.

### Working Queries

Use these once a focus area has 10+ wiki pages.

**Explore what you know:**

> `/second-brain query "What are the 5 biggest gaps in this knowledge base? What do I think I know that's only backed by a single source? What should I research next to strengthen the weakest areas?" --focus=research`

> `/second-brain query "What patterns keep showing up across multiple sources? What themes are emerging that I might not have noticed?" --focus=customer-insights`

**Spot contradictions and staleness:**

> `/second-brain query "What claims in the wiki contradict each other? Which source is more recent or reliable for each contradiction?" --focus=research`

> `/second-brain query "Which wiki pages are most likely outdated based on newer sources? Prioritize what needs refreshing."`

**Prep a meeting:**

> `/second-brain prep "Q3 roadmap review with Maya"`

Will produce a one-page briefing structured as current state → key tensions → open questions → recommendation, with citations. Saved to `outputs/briefing-*.md`.

**Pull a background section for a doc:**

> `/second-brain query "I'm writing a <doc type> for <topic>. Pull everything relevant from the wiki — background, prior art, open questions, constraints — into a section I can paste. Cite sources so I can link to them."`

**Synthesize a segment or entity:**

> `/second-brain query "Pull together everything the wiki knows about <entity>. What we know, where my understanding is thin, what to verify." --focus=<slug>`

**Make a decision:**

> `/second-brain query "I'm deciding between Option A and Option B for <context>. Based on everything in the wiki, what evidence supports each? Where is the data strong and where am I guessing? File the analysis back into wiki/." --focus=decisions`

**Generate shareable outputs:**

> `/second-brain query "Based on everything in wiki/, write a 500-word executive briefing on <topic>. Cite sources. Structure: current state, key tensions, open questions, recommended next steps. Save to outputs/."`

> `/second-brain query "Create a comparison table of <entities> across <dimensions>. Render as markdown. Save to outputs/."`

### The Compounding Loop

The single most important habit: **file good answers back into the wiki.**

After any query that produced a substantial answer:

> Save that answer as a new wiki page under {focus}/wiki/ and update the index.

A comparison, an analysis, a briefing, a pattern you noticed — these are all knowledge. If they stay in chat history they disappear. If they go back into the wiki, every future query gets smarter.

That's the whole system. Sources go in. Wiki gets compiled. You query it. Good answers go back. Knowledge compounds.

---

## Anti-Patterns

**Batch-ingesting everything on day one.**
- Why it's problematic: You skip the discussion that produces sharp summaries. The wiki ends up shallow.
- Instead do: Ingest one source at a time for the first 10-20. Use `compile` only after you've developed a feel for the shape of the domain.

**Letting query answers stay in chat.**
- Why it's problematic: The brain only compounds if answers flow back in. A briefing that disappears into chat history is wasted work.
- Instead do: After any substantial answer, accept the "file back?" offer. It takes one click.

**Silently overwriting contradictions.**
- Why it's problematic: The wiki becomes unreliable. You lose the ability to see how your understanding evolved.
- Instead do: Always flag both claims, cite both, note recency. Let the reader judge.

**Skipping citations.**
- Why it's problematic: Uncited claims rot. Six months later you can't tell if something is grounded or guessed.
- Instead do: Every factual claim gets `[Source: filename.md]`. No exceptions.

**Creating 10 focus areas on day one.**
- Why it's problematic: Most will stay empty. The brain feels like scaffolding, not a tool.
- Instead do: Start with 2-3 that match the work you're doing this month. Add more only when you have sources for them.

---

## Tips for Best Results

- **Ingest one source at a time** whenever you can. Discuss takeaways. That discussion is where the brain gets sharp.
- **File good answers back.** The single most important habit. A briefing that stays in chat disappears. A briefing filed as a wiki page makes every future query smarter.
- **Run `lint` weekly** or every 10 ingests, whichever comes first. Catches contradictions before they metastasize.
- **Use `prep` before every meeting or decision.** Five minutes of brain-assisted prep beats an hour of scrambling.
- **Let it grow organically.** Start with what's in front of you.
- **Obsidian is optional but lovely.** Point Obsidian at `./second-brain/` and the `[[links]]` become clickable plus you get the graph view. Any markdown viewer works.
- **Git-friendly by design.** The brain is all markdown. Commit it. You get history, diff, and undo for free.

---

## Portability

The brain is pure markdown in a predictable folder layout. That means:

- **Obsidian-compatible.** Open `./second-brain/` as an Obsidian vault and `[[links]]` become clickable with a free graph view.
- **Git-versionable.** Commit it. Every ingest, lint, and update shows up as a diff.
- **Tarball-shareable.** Each focus area is self-contained. Zip `./second-brain/{slug}/` and hand it to a teammate.
- **Editor-agnostic.** Any markdown viewer works. VS Code, Typora, Bear, `cat`.
- **LLM-portable.** The per-focus `CLAUDE.md` carries the schema. Any Claude session pointed at the folder can continue the brain.

---

## Scale Notes

The index-based approach holds up to ~100 raw sources and a few hundred wiki pages per focus area. Beyond that:
- Consider splitting a focus area into sub-areas (e.g., `competitive-intelligence` → `comp-enterprise`, `comp-smb`)
- Consider adding a search tool like [qmd](https://github.com/tobi/qmd) (local markdown search, BM25/vector hybrid, works as CLI or MCP server)

---

## Success Criteria

A healthy brain after a month of use:
- At least one focus area with 20+ wiki pages and 10+ raw sources
- Regular `log.md` entries — ideally a few per week
- `lint` has been run at least 2-3 times and acted on
- `prep` has been used before at least one meeting or doc
- You can ask the brain a question about your domain and get a cited answer faster than you could reconstruct it from memory

---

## Related Skills

- **[learning-journal](../learning-journal/skill.md)** — A lightweight alternative for capturing learning moments chronologically without maintaining a full wiki. Use `learning-journal` when you want quick capture and periodic review; use `second-brain` when you want cross-linked, cited, queryable knowledge that compounds. The two can coexist: a learning-journal entry can become a source for `second-brain ingest` if it grows into something worth linking.
- **[project-context](../project-context/skill.md)** — A single-file architecture/tech-stack reference for a codebase. Simpler than a full brain. Can live as one wiki page inside a `projects` focus area if you want, but stands on its own for lightweight needs.
- **[meeting-notes](../meeting-notes/skill.md)** — Produces structured meeting outputs that are natural sources for `second-brain ingest --focus=decisions` or the topic-specific focus area.
- **[decision-doc](../decision-doc/skill.md)** — Produces decisions that belong in the `decisions` focus area. Query the brain first to pull related past decisions before running it.
- **[quick-research](../quick-research/skill.md)** — Its research briefs are ideal first sources when you're seeding a new `research` focus area.
