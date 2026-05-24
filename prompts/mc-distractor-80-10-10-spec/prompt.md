# Multiple Choice Distractor — 80/10/10 Technique Mix

> **Category:** content
> **Model used:** claude-sonnet-4-6
> **Project area:** Buddhist Quiz — Buddhānubuddha Pavat
> **Status:** production
> **Last updated:** 2026-05-24

## What this prompt does

Generates multiple-choice wrong answers (called distractors) using a deliberate 80/10/10 mix of three techniques — so that on Hard difficulty, students can't eliminate wrong options by topic alone and must actually know the specific fact.

## The prompt

```
Generate multiple-choice distractors for a Thai Buddhist Studies exam flashcard app using the following 80/10/10 technique mix:

Option A — Hand-crafted plausible distractors (80% of cards):
- Write 3 wrong answers per card that are factually adjacent to the correct answer
- Use similar Pali terms, similar numbers, similar names, or similar concepts
- A student must know the specific fact to eliminate each wrong option
- Never use an answer that is partially correct or arguably valid

Option B — Answer-fragment mixing (10% of cards):
- Apply to multi-part list cards (e.g. "name the five X")
- Recombine real fragments from the correct answer into plausible-sounding wrong wholes
- Example: pair the correct lifespan with the wrong continent, or the right caste with the wrong precept count

Option C — Negative "which is NOT" questions (10% of cards):
- Apply to numbered-list cards where testing all items matters
- Rewrite the question as "Which of the following is NOT one of the X?"
- Include 3 real items from the textbook as options
- Add 1 fabricated item that sounds plausible but does not appear in the textbook
- The fabricated item is the correct answer to pick

Difficulty mapping:
- Hard and Medium: use hand-crafted distractors and negative questions
- Easy: draw wrong options from other chapters (cross-topic, easy to eliminate by subject)
```

## Inputs

A flashcard with `question`, `answer` (textbook-exact), and `chapter`. The technique (A, B, or C) is pre-assigned per card based on the 80/10/10 split.

## Expected output

Three distractor strings per card. For Option C cards: a rewritten question prompt plus three real options and one fabricated option. No distractor may duplicate or partially reproduce the correct answer.

## Related files

- Reasoning: [`REASONING.md`](./REASONING.md)
- Evaluation rubric: [`rubric.yaml`](./rubric.yaml)
- Version history: [`versions/`](./versions/)
