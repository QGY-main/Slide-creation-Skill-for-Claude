# How to Use This Skill

## Deeper content-structure guidance

The rules in SKILL.md (action titles, ghost deck test, one idea per slide) are deliberately kept short so they apply to any kind of deck — pitches, school projects, internal updates, research talks. For decks with a heavier argument to make (research talks, grant briefings, technical proposals, competition submissions being judged on reasoning), the structure below goes further. Draw on it — don't apply it wholesale to every deck. A five-minute pitch deck and a thesis defense need different amounts of this; use judgment about which parts actually fit the deck in front of you.

**When to lean on this more heavily:** the audience is evaluating an argument or evidence (judges, panels, advisors, reviewers), not just absorbing an update.

**When to lean on it lightly or skip it:** the deck is narrative/inspirational, sales-oriented, or very short — rigid structure can flatten it.

### Narrative spine

Pick one structure and apply it consistently across the deck:
- **Situation → Complication → Resolution** — what was known, what's broken/missing, what your work contributes. Good default for most argument-driven decks.
- **Funnel** — broad context → specific gap → approach → findings → implications.
- **Answer first** — lead with the conclusion, then support it. Best for time-pressured or senior audiences (grant panels, executives) who may not stay for the full build-up.

State the central question or claim explicitly by slide 2 or 3 — don't bury it. Pick one argument to make well rather than trying to cover everything; move secondary material to an appendix.

### Exhibit discipline (for data/chart-heavy slides)

- One exhibit (chart, table, diagram) per slide.
- Annotate the key finding directly on the chart (arrow, highlight, callout) rather than making the audience hunt for it.
- Self-sufficient test: could someone get the point from the slide alone, without the presenter talking? If not, add an annotation.
- Prefer a graph over a table unless exact values matter.
- Figure on one side, interpretive text on the other (evidence first, then interpretation) reads more naturally than mixing them.

### Deck architecture (for structured/argument decks)

A useful default skeleton — adapt slide count and which sections merge based on time/format:
title → motivation/context → the question or claim being made → method/approach → results (one finding per slide) → discussion/implications → conclusions (stays on screen for Q&A) → references → appendix (backup slides, anticipated Q&A).

Don't end on a bare "Thank You" or blank slide — end on conclusions/next-steps.

### Timing (when the deck is tied to a spoken time slot)

Roughly one slide per minute of talk time is a reasonable budget. If the user gives a time limit, use that to sanity-check the slide count in Step 4's outline before building.

### Common mistakes worth checking for

Topic-label titles instead of action titles; presenting too much (no clear single argument); evidence without a stated "so what"; uncited borrowed figures/data; text too small to read from the back of a room; inconsistent fonts/colors/alignment; slides included that won't actually get discussed; ending on "Thank You" instead of conclusions.

---

## Using this skill on Claude

### Claude.ai (web / desktop / mobile app)

1. Get the `slide-deck-creator` folder (or a `.skill`/zip of it).
2. Open **Settings → Capabilities → Skills** (naming may vary by plan/version).
3. Upload the folder or file. Claude will automatically consult it whenever a conversation involves building a slide deck or presentation.

### Claude Code / Claude API / Claude Platform

1. Place the `slide-deck-creator/` folder in your skills directory (e.g. `/mnt/skills/user/` in a sandboxed environment, or wherever your Claude Code setup looks for user skills).
2. Make sure `SKILL.md` sits at the top level of that folder — required for discovery.
3. Reload/restart the session so it's picked up in the available-skills list.

This skill also depends on Claude's built-in `pptx` skill for the actual file construction — that ships with Claude already, nothing extra to install.

## Using this on other AI platforms

Skills in this exact packaged form (`SKILL.md` + reference files, auto-discovered) are a Claude-specific mechanism. Other assistants (e.g. ChatGPT, Gemini, or a general LLM API) don't have this loading system, but you can still get most of the value:

- **Custom instructions / system prompt:** paste the contents of `SKILL.md` (and the relevant parts of `how-to-use.md`) into the platform's custom-instructions, system-prompt, or "project/GPT instructions" field. This won't auto-trigger the way a Claude skill does — you'll want to reference it explicitly at the start of a session (e.g. "use my slide deck creator instructions for this").
- **File upload / project knowledge:** if the platform supports attaching reference files to a project or thread (e.g. ChatGPT Projects, Gemini Gems), upload `SKILL.md` and `references/how-to-use.md` there so the model can pull from them.
- **No native .pptx-building skill:** the actual file-generation step assumes Claude's `pptx` skill. On another platform you'll need to ask it to either write python-pptx / pptxgenjs code you run yourself, or describe the deck in enough detail to build in PowerPoint/Google Slides manually — the interview and content-structure guidance still apply, only the final build step changes.
- **Web fetch differences:** the design-research step (Step 3) assumes the platform can fetch or search the web. If it can't, paste in relevant excerpts from the sites in `references/design-sources.md` yourself, or skip straight to the content interview.
