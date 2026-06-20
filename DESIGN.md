# find-skill — design

Date: 2026-06-20

## Goal

A Claude Code skill that discovers skills **not currently installed** and recommends the best matches for a stated need. Discover-and-recommend only — no install, no system modification.

## Decisions

| Question | Decision |
|---|---|
| End goal | Discover + **recommend** (no install) |
| Sources | Official marketplace (local cache) · GitHub · curated awesome-lists. **No** general web search. |
| GitHub access | Degradation chain: authed `gh` → public REST API (no auth) → WebSearch fallback |
| Dedup | Exclude/flag skills already installed (the core requirement) |
| Ranking | Relevance first, popularity (stars / `unique_installs`) + recency (`pushedAt`, not `updatedAt`) as tiebreak |
| Popularity floor | GitHub raw search must clear **≥10 stars** (applied via `stars:>=10` query qualifier); marketplace + curated lists exempt. Sub-floor repos only if a standout fit, labeled `early-stage (N★)`. Rationale: don't surface 2-star unvetted noise as a recommendation. |
| Count | Top 5 (fewer is fine — no padding with low-star repos) |
| Build style | Pure-instruction skill (markdown only, no helper script) |
| Distribution | Standalone git repo; install by **symlink** into `~/.claude/skills/` |

## Flow

keywords → list installed (dedup set) → search 3 sources → merge/dedup/rank → top 5 with links + install hint → footer note on any degraded source.

## Source mechanics

- **Marketplace:** `jq` filter over `~/.claude/plugins/plugin-catalog-cache.json` (`catalog.plugins` is an object keyed by `name@marketplace`; `unique_installs` = popularity).
- **GitHub:** `gh search code/repos` when authed; else public `search/repositories` REST API; else WebSearch + WebFetch. Repo-search hits (gh/REST) are text matches — verify each candidate actually contains a `SKILL.md` (via `gh search code filename:SKILL.md repo:…` or WebFetch) before it enters the top 5; drop or label `unverified` otherwise.
- **Lists:** WebSearch + WebFetch curated indexes (e.g. `awesome-claude-code`).

## Out of scope (YAGNI)

Installing, general web search, result caching, scoring engine.
