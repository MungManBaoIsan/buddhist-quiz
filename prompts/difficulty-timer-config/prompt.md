# Difficulty and Timer Configuration

> **Category:** agent-workflow
> **Model used:** claude-sonnet-4-6
> **Project area:** Buddhist Quiz — Buddhānubuddha Pavat
> **Status:** production
> **Last updated:** 2026-05-24

## What this prompt does

Configures three genuinely distinct difficulty levels so learners can start gently and progress to exam-pressure conditions — with each level clearly different in both time allowed and the quality of wrong answers shown.

## The prompt

```
Configure three difficulty levels for a Buddhist Studies flashcard quiz app:

Easy:
- Timer: 60 seconds per question
- Multiple Choice distractors: drawn from other chapters (cross-topic, easy to eliminate)
- Purpose: gentle warm-up, builds familiarity with content

Medium:
- Timer: 40 seconds per question
- Multiple Choice distractors: hand-crafted plausible distractors + negative questions (same as Hard)
- Purpose: exam-condition practice with a little more breathing room

Hard:
- Timer: 24 seconds per question
- Multiple Choice distractors: hand-crafted plausible distractors + negative questions
- Purpose: maximum challenge, closest to real exam time pressure

Rules:
- Timer applies to Multiple Choice and Fill-in-Blank modes only
- Flashcard mode is always untimed (it's for reading and absorbing, not testing)
- Changing difficulty takes effect from the next card — no mid-card restart
- Timer expiry marks the card for review, reveals the correct answer, and auto-advances

Features tried and deliberately removed:
- Manual Save/Load buttons: built but removed — added complexity without enough benefit for users
- Full session persistence (deck position + score): built but removed — only reward data persists
```

## Inputs

User selection of Easy / Medium / Hard via a UI toggle. Applied globally to the current session.

## Expected output

A configuration object with `{ timerSeconds: number, distractorMode: "cross-chapter" | "hard", negativeQuestions: boolean }` per level.

## Related files

- Reasoning: [`REASONING.md`](./REASONING.md)
- Evaluation rubric: [`rubric.yaml`](./rubric.yaml)
- Version history: [`versions/`](./versions/)
