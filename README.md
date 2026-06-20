# find-skill

<p align="center">
  <img src="assets/find-skill-mascot.png" alt="find-skill mascot: a pixel-art fox explorer in an adventurer's hat kneeling beside a treasure chest of gold and stars" width="200">
</p>

A Claude Code skill that **finds skills you don't have yet.**

Ask "is there a skill for X?" and it searches the official plugin marketplace, GitHub, and curated awesome-lists, throws out anything you've already installed, and hands you the **top 5 matches with links** — ranked by relevance, then popularity. It only recommends. It never installs or touches your system.

## Install

Copy the skill into your personal (user-level) skills dir:

```sh
git clone https://github.com/<you>/claude-find-skill.git
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
rm ~/.claude/skills/find-skill
```
