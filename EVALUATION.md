# Evaluation: Slide-Deck-Creator Skill vs. No Skill

This document describes how to test whether the `slide-deck-creator` skill actually
improves the decks Claude produces, and how to have an independent judge model
(ChatGPT) score the two outputs head-to-head. Fill in the **Results** section
after you've run the procedure — this file ships as a template, not a claim.

## Why an external judge

Claude shouldn't grade its own homework. Using ChatGPT as the judge avoids the
obvious bias of asking the same model (and the same skill-writer) to evaluate
its own output, and gives you a second, independent opinion on which deck is
actually better.

## Models used

- **Deck generation:** Claude Sonnet 5, Low reasoning effort.
- **Judging:** GPT-5.5 Thinking (ChatGPT).

Keep these fixed across both runs — if you swap either model, note it clearly,
since a different generation or judge model invalidates a direct comparison
with prior results.

## Procedure

### 1. Use this prompt, run it twice

Use a single, identical prompt for both runs so the comparison is fair. This
evaluation uses the following prompt (a single-slide, detailed keynote-style
design brief):

> Create one professional keynote-style presentation slide titled "The Intelligence Explosion: Why AI is Different This Time".
>
> **Overall Objective:** Design a slide that immediately captures attention and communicates that artificial intelligence is fundamentally different from previous technological revolutions because it compounds knowledge, learns continuously, and accelerates itself.
>
> **Layout**
> - Use a 16:9 widescreen layout.
> - Divide the slide into approximately 40% text (left) and 60% visuals (right).
> - Maintain generous whitespace with a clean, premium appearance.
>
> **Color Palette**
> - Background: dark navy (#071A2F) with a subtle radial gradient.
> - Accent colors: Electric blue (#3FA9F5), Cyan (#4FF2E9), White (#FFFFFF).
> - Avoid bright reds or distracting colors.
>
> **Typography**
> - Title: Inter Bold or SF Pro Display Bold, ~36–42 pt, white.
> - Body: Inter Regular, 20–24 pt, light gray (#EAEAEA).
> - Highlight important keywords in cyan.
>
> **Left Side Content**
> Title: "The Intelligence Explosion"
> Subtitle: "AI is not just another tool—it is a system that continuously improves, compounds knowledge, and amplifies human capability."
> Three concise key points (each under 12 words):
> - Learns from every interaction instead of remaining static.
> - Automates reasoning, not just repetitive work.
> - Improves faster as more people use and refine it.
>
> **Right Side Visual**
> A clean vector-style illustration showing a glowing AI core in the center, with interconnected nodes radiating outward, each representing a domain (Healthcare, Finance, Education, Science, Manufacturing, Cybersecurity). Curved glowing lines connect every node back to the AI core. Around the outside, faint mathematical equations and binary digits subtly fade into the background. The visual should communicate exponential growth and knowledge propagation rather than robotics.
>
> **Background Details**
> Very subtle grid pattern, soft glowing particles, thin circuit-like lines in the corners, low opacity (10–15%) so they do not distract.
>
> **Design Principles**
> Modern Apple keynote aesthetic, minimal text, high contrast, premium corporate technology style, no clip art, no stock-photo look, consistent spacing and alignment.
>
> **Speaker Impact**
> The audience should understand the main message within 5 seconds. The slide should feel inspiring, futuristic, and suitable for presenting to investors, judges, or senior executives at an AI innovation competition.

**Run 1 — Without the skill:** Start a fresh Claude Sonnet 5 (Low) conversation
with the skill *not* installed, and give it the prompt above. Let Claude
build the slide however it normally would.

**Run 2 — With the skill:** Start another fresh Claude Sonnet 5 (Low)
conversation with `slide-deck-creator` installed, give it the exact same
prompt, and go through its normal flow (interview questions, outline
confirmation, build). Note: since this prompt is a single fully-specified
slide rather than an open-ended deck request, the skill's interview step may
have little left to ask — that's fine, let it proceed as it naturally would
rather than forcing extra questions.

Keep both conversations independent — don't let one influence the other, and
don't hand-edit either output afterward.

### 2. Get both decks into a judge-readable form

ChatGPT can't open a raw `.pptx` reliably in every context, so convert both
decks to a form it can actually see:

- Export each `.pptx` to PDF (PowerPoint/Keynote/Google Slides: File → Export/Download → PDF), or
- Take a screenshot of each slide and combine them into one image-per-slide set.

Do this identically for both decks so the comparison stays fair.

### 3. Give ChatGPT (GPT-5.5 Thinking) the judging prompt

Open a new chat with GPT-5.5 Thinking. Upload both PDFs/image sets (labelled
**Deck A** and **Deck B** — don't tell it which one used the skill, to avoid
bias) and use a prompt like:

> "You are judging two slide decks made from the same prompt: [paste the
> original prompt]. Score each deck 1-5 on: (1) clarity of the core message,
> (2) whether slide titles alone tell a coherent story, (3) visual design
> quality (layout, whitespace, typography, color use), (4) information density
> (not too sparse, not too crowded), (5) overall persuasiveness for the stated
> audience. Give a score per category per deck, a short justification for each
> score, and then state which deck is better overall and why."

Paste ChatGPT's full response into the Results section below, unedited.

### 4. Repeat for a second, different prompt (recommended)

One comparison can be noisy. Running the same A/B test on a second, unrelated
prompt (different topic/audience) makes the result more trustworthy before you
draw a conclusion.

### 5. Record the verdict

Fill in the table below from ChatGPT's scores, and note the overall winner it
named for each run.

## Results

*(Fill in after running the procedure above. Delete this note once populated.)*

### Run 1 — Prompt: "The Intelligence Explosion" slide brief (see Procedure above)
Generation model: Claude Sonnet 5 (Low). Judge model: GPT-5.5 Thinking.

| Category | Deck A (no skill) | Deck B (with skill) |
|---|---|---|
| Clarity of core message | | |
| Titles tell a coherent story | | |
| Visual design quality | | |
| Information density | | |
| Persuasiveness for audience | | |

**ChatGPT's stated overall winner:** _[paste here]_

**ChatGPT's justification:** _[paste here]_

### Run 2 — Prompt: `[paste prompt used]`
Generation model: Claude Sonnet 5 (Low). Judge model: GPT-5.5 Thinking.

| Category | Deck A (no skill) | Deck B (with skill) |
|---|---|---|
| Clarity of core message | | |
| Titles tell a coherent story | | |
| Visual design quality | | |
| Information density | | |
| Persuasiveness for audience | | |

**ChatGPT's stated overall winner:** _[paste here]_

**ChatGPT's justification:** _[paste here]_

## Notes

- A judge model's scores are subjective, exercise caution when viewing

