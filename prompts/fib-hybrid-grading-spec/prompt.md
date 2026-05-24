# Fill-in-Blank Hybrid Grading Spec

> **Category:** classification
> **Model used:** claude-sonnet-4-6
> **Project area:** Buddhist Quiz — Buddhānubuddha Pavat
> **Status:** production
> **Last updated:** 2026-05-24

## What this prompt does

Defines the grading logic for the fill-in-blank study mode — using keyword matching for short factual cards and self-grading for long explanation cards, so every card is tested in the way that makes most sense for that type of answer.

## The prompt

```
Design a fill-in-blank grading system for a Thai Buddhist Studies flashcard app with the following rules:

Short factual cards (single key term, name, number, or short phrase):
- Use keyword match grading
- Accept multiple spelling variants (diacritic-insensitive, so "Ananda" matches "Ānanda")
- Mark the card correct if any accepted term appears in the typed answer
- Reveal the full textbook answer after grading (whether correct or not)

Long explanation cards (multi-sentence or paragraph answers):
- Show the question and a text input
- On submit: reveal the textbook-exact answer
- Ask the user to self-grade: "Got it" or "Review again"
- Active recall must happen before the answer is revealed

Classification rule:
- Short factual: the exam tests a specific name, number, or term (1–3 key words)
- Long explanation: the answer requires understanding of a process, comparison, or narrative

Accept-list format (for keyword cards):
Each card has an accept: [] array listing all valid spellings and variants.
Example: accept: ["Ananda", "Ānanda", "Venerable Ananda"]
Matching is case-insensitive and checks if any accepted term appears anywhere in the typed answer.
```

## Inputs

A flashcard with `question`, `answer`, and `type` fields (`"keyword"` or `"selfgrade"`). For keyword cards, also an `accept` array of valid terms.

## Expected output

For keyword cards: pass/fail result based on whether any accepted term appears in the typed input. For self-grade cards: the textbook answer is revealed and the user marks themselves.

## Related files

- Reasoning: [`REASONING.md`](./REASONING.md)
- Evaluation rubric: [`rubric.yaml`](./rubric.yaml)
- Version history: [`versions/`](./versions/)
