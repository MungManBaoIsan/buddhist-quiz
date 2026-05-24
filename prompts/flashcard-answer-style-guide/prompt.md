# Flashcard Answer Style Guide

> **Category:** content
> **Model used:** claude-sonnet-4-6
> **Project area:** Buddhist Quiz — Buddhānubuddha Pavat
> **Status:** production
> **Last updated:** 2026-05-24

## What this prompt does

Standardises every flashcard answer to a consistent, exam-ready style before merging new chapter content with the existing deck — so all 71 cards read as one coherent set.

## The prompt

```
You are editing flashcard answers for a Thai national Buddhist Studies exam (Buddhanubuddha Pavat, Chapters 2–11).

For each answer, apply these rules:
- Maximum 3 sentences for simple factual answers; numbered list for multi-part answers (max 4 items)
- Begin with the direct answer — no preamble
- Include the key Pali term in brackets where the exam expects it, e.g. (Ayu-Sankhara), (Etadagga)
- No hedging language ("it is said that", "possibly")
- Consistent register: formal, concise, exam-ready
- Do not add information not in the original answer
- Do not remove information the exam requires
```

## Inputs

The prompt expects a raw flashcard question and an existing answer draft (or empty answer) as context. No template variables — the rules apply to any card passed as context.

## Expected output

- Starts with the direct fact, name, or numbered item — no filler opening
- Pāli terms are followed by their meaning in plain brackets where exam-relevant
- Multi-part answers use a numbered list (1. 2. 3.)
- No "it is said that", "possibly", "perhaps", or similar hedging
- Length: 1–3 sentences for simple cards; up to 6 numbered items for list cards

## Related files

- Reasoning: [`REASONING.md`](./REASONING.md)
- Evaluation rubric: [`rubric.yaml`](./rubric.yaml)
- Version history: [`versions/`](./versions/)
