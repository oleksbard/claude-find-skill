# find-skill

<p align="center">
  <img src="assets/find-skill-mascot.png" alt="find-skill mascot: a pixel-art fox explorer in an adventurer's hat kneeling beside a treasure chest of gold and stars" width="200">
</p>

A Claude Code skill that **finds skills you don't have yet.**

Ask "is there a skill for X?" and it searches the official plugin marketplace, GitHub, and curated awesome-lists, throws out anything you've already installed, and hands you the **top 5 matches with links** — ranked by relevance, then popularity. It only recommends. It never installs or touches your system.

> Built to the standard Agent Skill format — a folder with a `SKILL.md` and YAML frontmatter — as documented in Anthropic's [anthropics/skills](https://github.com/anthropics/skills) repo.

## Install

Copy the skill into your personal (user-level) skills dir:

```sh
git clone https://github.com/oleksbard/claude-find-skill.git
cp -R claude-find-skill/find-skill ~/.claude/skills/find-skill
```

Restart Claude Code (or start a new session) and it's available in every project.

> Developing the skill? Symlink instead so edits go live without re-copying: `ln -s "$PWD/claude-find-skill/find-skill" ~/.claude/skills/find-skill`

## Use

Just ask, in any session:

```sh
/find-skill is there a skill for writing changelogs?
/find-skill find me a skill that reviews terraform
/find-skill what skills exist for screenshot testing?
```

## Example

```sh
/find-skill UI_UX design skills  

⏺ All five verified as real skills. Here's your shortlist for UI/UX design — community skills you don't have, each confirmed to contain a SKILL.md:

  baoyu-design — Run "Claude Design" locally: turn a request into polished UI mockups, prototypes, wireframes & decks as self-contained HTML
    Source: GitHub · ★ 1,655 · pushed 2026-06
    Link: https://github.com/JimLiu/baoyu-design
    Why: The most general-purpose pick — full design-artifact workflow (mockups→prototypes→decks) without needing claude.ai/design; tuned for Opus 4.8.
    Get it: git clone https://github.com/JimLiu/baoyu-design  (not run for you)

  nothing-design-skill — Generate UI in the "Nothing" design language: monochrome, Swiss typography, industrial
    Source: GitHub · ★ 2,500 · pushed 2026-04
    Link: https://github.com/dominikmartn/nothing-design-skill
    Why: Most-starred design skill out there; reach for it when you want one strong, opinionated aesthetic rather than generic output.
    Get it: git clone https://github.com/dominikmartn/nothing-design-skill  (not run for you)

  hue — Learns any brand (URL, name, or screenshot) and turns it into a complete design system: color tokens, type, spacing, components
    Source: GitHub · ★ 715 · pushed 2026-06
    Link: https://github.com/dominikmartn/hue
    Why: The "UX consistency" angle — every UI your assistant builds matches a defined brand system. Pairs well with a builder skill.
    Get it: git clone https://github.com/dominikmartn/hue  (not run for you)

  styleseed — Design-judgment engine: 74 rules, 48 components, 7 brand skins (Toss/Stripe/Linear/Notion/Raycast/Arc/Vercel), motion system, 15 /ss-* skills + a11y audits
    Source: GitHub · ★ 554 · pushed 2026-06
    Link: https://github.com/bitjaru/styleseed
    Why: The most comprehensive toolkit here — teaches design judgment (scaffold, tokens, motion, accessibility, review) rather than one look. Anti-"AI slop."
    Get it: git clone https://github.com/bitjaru/styleseed  (not run for you)

  refactoring-ui-plugin — 10 design-review skills based on Refactoring UI (visual hierarchy, typography scale, spacing, contrast, empty states…)
    Source: GitHub · ★ 173 · pushed 2026-04
    Link: https://github.com/gnurio/refactoring-ui-plugin
    Why: Complements the builders above — a critique lens to evaluate and fix existing UI, not just generate it.
    Get it: git clone https://github.com/gnurio/refactoring-ui-plugin  (not run for you)

  ---
  Already covered — not listed as new: You have artifact-design active (Anthropic's distinctive-frontend design skill). The marketplace's frontend-design (829k installs) is the same capability, so I left it off.

  Dropped by the verify step: plugin87/ux-ui-agent-skills (227★) looked strong but has no SKILL.md — it ships as slash-command .md files, not skill format. Usable, but not a drop-in skill.

  One adjacent option (different category): if you design in Figma, figma@claude-plugins-official (136k installs) does design-token extraction and design→code — /plugin install figma@claude-plugins-official.
  It's a tool integration, not a design-craft skill, so it's outside the top 5.

  ▎ GitHub searched via REST API + WebFetch — run gh auth login for sharper, code-level (SKILL.md) results.
  ▎ Curated awesome-list (hesreallyhim/awesome-claude-code) skipped — its index is mid-reconstruction.

```

## Sharper GitHub results (optional)

GitHub *code* search needs auth. Without it the skill falls back to the public API and web search — still works. For the best results:

```sh
gh auth login
```

## What it won't do

- Install, clone, or download anything for you
- Recommend skills you already have
- Search the open web beyond GitHub + marketplace + curated lists

## Uninstall

```sh
rm -rf ~/.claude/skills/find-skill
```

## License

[MIT](LICENSE)
