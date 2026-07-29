---
name: slide-deck-creator
description: Use this skill whenever the user wants to create, design, or draft a slide deck, pitch deck, or PowerPoint presentation and wants Claude to actively help shape the content — not just format it. Make sure to trigger this whenever the user mentions "slide deck," "presentation," "pitch deck," "PowerPoint," or "slides," even if they haven't given full details yet. This skill drives a structured interview to gather the presentation's goal, audience, content, and reference websites before building anything, pulls in current design best practices from a curated set of design-tip websites, and produces a polished .pptx file. Also use this skill if the user asks how to install, use, or adapt this skill itself on Claude or another AI platform.
---

# Slide Deck Creator

A skill for interviewing the user to gather everything needed for a strong slide deck, researching current design best practices from a curated set of reference websites, and producing a polished .pptx file using the `pptx` skill.

## Workflow

### Step 1: Load the pptx skill first

Before doing anything else, view `/mnt/skills/public/pptx/SKILL.md`. That skill governs the actual mechanics of building the .pptx file (python-pptx / pptxgenjs usage, layout rules, fonts, images, output steps). This skill (slide-deck-creator) governs everything *upstream* of that: interviewing the user, researching design principles, and assembling a clear content brief before handing off to the pptx skill for construction.

### Step 2: Interview the user

Never start building slides from a vague request ("make me a deck about X"). Always run a short interview first. Use `ask_user_input_v0` for discrete choices (audience, tone, length, format) and open follow-up questions for content specifics that can't be reduced to buttons.

Ask about, at minimum:
1. **Purpose & audience** — what is the deck for (pitch, class presentation, internal update, competition submission, etc.), and who is the audience?
2. **Core content** — what are the key points, sections, or story arc the user already has in mind? Do they have existing notes, a doc, or data to pull from?
3. **Length & format** — roughly how many slides, and any fixed constraints (competition slide limit, time limit for the talk)?
4. **Visual style** — tone (formal/technical/playful/minimal), color/brand preferences, whether they have a logo or existing template to match.
5. **Reference websites** — explicitly ask if the user wants to supply any websites for Claude to pull reference content, data, or design inspiration from, beyond the built-in design-tip sources (see Step 3). If they give URLs, fetch and read them before drafting content.

**If any answer is unclear, ambiguous, or incomplete, ask a clarifying follow-up before proceeding — do not guess silently on anything that materially changes the content or structure of the deck.** It's fine to make minor stylistic assumptions (e.g. default color palette) and state them inline, but don't assume the audience, purpose, or core message.

Only move to Step 3 once you have a clear picture of purpose, audience, core content, and rough length.

### Step 3: Pull current design best practices

This skill has a curated reference list of design-tip websites in `references/design-sources.md`. Before drafting slide layouts and visual structure, fetch and skim these sources (using web search / web fetch) to ground your design choices in current best practices, rather than relying purely on memory. Prioritize:

- Slide layout and "less is more" content density principles
- Typography and font-pairing guidance
- Color and contrast guidance
- Storytelling / narrative arc structure for presentations
- Do's and don'ts for data slides and charts

Combine this with any user-supplied reference websites from Step 2 for content-specific facts, data, or inspiration. Cite what you pulled from where when it materially shaped a design or content decision, so the user can trace it back.

Don't dump raw research at the user — synthesize it into concrete decisions (layout choices, slide count per section, visual hierarchy) that feed directly into Step 4.

### Step 4: Draft a content outline before building

Write a short slide-by-slide outline and show it to the user for confirmation before generating the actual .pptx. This is cheap to revise and expensive to redo after full slide construction. Wait for explicit go-ahead ("looks good", "build it", etc.) before proceeding — treat silence or an unrelated reply as *not* confirmation. Always confirm the outline if the deck is more than 10 slides or the content is complex.

For each slide, write:
- **An action title** — a complete sentence stating the takeaway, not just a topic label. ("Revenue grew 40% after the redesign" beats "Revenue Results.") This holds for any deck with an argument to make (pitches, research, project updates), not just academic ones — purely narrative/inspirational decks (e.g. a keynote opener) can use shorter evocative titles instead.
- A 1-2 line description of the content/visual for that slide.

**Ghost deck test:** before showing the outline to the user, read only the slide titles in sequence, nothing else. They should tell the complete story on their own. If they don't, tighten the outline first.

**One idea per slide.** If a slide description is trying to carry two distinct points, split it into two slides rather than cramming both in.

### Step 5: Build the deck

Follow `/mnt/skills/public/pptx/SKILL.md` precisely for the actual construction (library choice, layout code, image handling, output path, delivery via `present_files`). Apply the design principles gathered in Step 3 (whitespace, font pairing, consistent color system, one idea per slide, etc.), plus these baseline standards unless the user's brand/template overrides them:

- Left-align body text; center only titles.
- Consistent margins/grid across all slides (don't let text boxes and figures drift slide to slide).
- Keep body text light — if the audience is reading dense text, they're not listening to the presenter. As a rule of thumb, aim for well under ~40 words of body text on a content slide unless the format specifically calls for more (e.g. a reference/appendix slide).
- Cite any borrowed data, quotes, or figures directly on the slide they appear on (small, muted citation text), and include a references/sources slide at the end if the deck leans on outside material.
- End on a conclusions/next-steps slide, not a bare "Thank You" or blank slide — this is what stays on screen during Q&A.

### Step 6: Quality-check before delivering

Before presenting the final file, run back through it with a short checklist:

```
□ Ghost deck test still passes on the final slide titles
□ One core idea per slide — no crowded slides
□ Font sizes readable at presentation distance (body text not tiny)
□ Consistent fonts/colors/margins throughout
□ Any borrowed data/figures/quotes are cited; sources slide present if needed
□ Last slide is conclusions/next-steps, not a blank "Thank You"
□ Slide count matches the constraint the user gave (competition/time limit)
```

If something fails, fix it before calling `present_files` rather than after.

### Step 7: Deeper structure guidance for argument-driven decks

For decks where the audience is evaluating an argument or evidence (research talks, grant briefings, competition submissions, technical proposals), see `references/how-to-use.md` for a more detailed content-structure guide (narrative spines, exhibit discipline, deck architecture, timing). Draw on it selectively rather than applying it wholesale to every deck — a short pitch deck and a thesis defense don't need the same amount of structure.

### Step 8: Installing or sharing the skill itself

If the user asks how to install this skill, or wants to use it on a platform other than the current one, see the "Using this skill on Claude" / "Using this on other AI platforms" sections of `references/how-to-use.md`.

## Reference files

- `references/design-sources.md` — the curated list of design-tip websites this skill pulls best practices from, plus notes on what to look for in each.
- `references/how-to-use.md` — deeper content-structure guidance for argument-driven decks, plus instructions for installing/using this skill on Claude and adapting it for other AI platforms.
