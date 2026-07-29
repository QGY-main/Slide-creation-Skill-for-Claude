# Evaluation: Slide-Deck-Creator Skill vs. No Skill

This document describes how to test whether the `slide-deck-creator` skill actually
improves the decks Claude produces, and how to have an independent judge model
(ChatGPT) score the two outputs head-to-head. 

## Why an external judge

Claude shouldn't grade its generated content. Using ChatGPT as the judge avoids the
 bias of asking the same model to evaluate its own output, and gives you a second, independent opinion on which deck is
actually better.

## Models used

- **Deck generation:** Claude Sonnet 5, Low reasoning effort.
- **Judging:** GPT-5.5 Thinking (ChatGPT).

## Procedure

### 1. Prompt

> Use a single, identical prompt for both runs so the comparison is fair. This
> evaluation uses the following prompt:

> Create a 5-slide presentation on the topic “Technology.” The presentation should have a modern, professional, and clean design with
> consistent blue, white, and dark grey color scheme. Use minimal text, relevant icons, and high-quality visuals. Keep each slide visually
> balanced and easy to read.

> Slides:

> 1. Title – Technology: Shaping the Future with an engaging cover image.
> 2. Introduction – Define technology and explain its importance in everyday life.
> 3. Key Technologies – Briefly introduce AI, robotics, cloud computing, and the Internet of Things.
> 4. Benefits & Challenges – Summarise the advantages and disadvantages of technological advancements.
> 5. Conclusion – Recap the main points and end with a forward-looking statement about the future of technology.
> 6. Use a professional layout, clear headings, and concise bullet points throughout.

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

ChatGPT can't open a raw `.pptx` reliably in every context, hence:

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


### 4. Record the verdict

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

