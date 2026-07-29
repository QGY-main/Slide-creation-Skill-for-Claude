# Slide Deck Creator — Claude Skill

A Claude skill that interviews you about your presentation, researches current
slide-design best practices, and builds a polished .pptx deck.

## What this skill does

- Asks structured questions about your deck's purpose, audience, content, and style
- Lets you supply reference websites for content/data Claude should pull from
- Pulls current design best practices from a curated list of design-tip sites:
  - Garr Reynolds — Presentation Zen design tips
  - Microsoft PowerPoint Design Ideas blog
  - Microsoft PowerPoint creative layouts/ideas blog
  - Microsoft Support — effective presentation tips
  - EDUCAUSE Presenter Concierge resources
- Drafts a slide-by-slide outline (with action titles + a "ghost deck" check) for
  your approval before building anything
- Offers deeper content-structure guidance (narrative spine, exhibit discipline,
  deck architecture) for argument-driven decks like research talks or competition
  submissions
- Builds the final .pptx using Claude's built-in `pptx` skill

## How to use / install this skill

See `references/how-to-use.md` for full details, including:
- How to load it into Claude.ai, Claude Code, and the Claude API/Platform
- How to adapt it for other AI platforms that don't support this skill format natively

## Folder structure

```
slide-deck-creator/
├── SKILL.md
├── README.md
└── references/
    ├── design-sources.md
    └── how-to-use.md
```
