# Gamification System Spec

> **Category:** agent-workflow
> **Model used:** claude-sonnet-4-6
> **Project area:** Buddhist Quiz — Buddhānubuddha Pavat
> **Status:** production
> **Last updated:** 2026-05-24

## What this prompt does

Designs the rewards and progression system for the quiz app — streaks, XP, levels, and badges — in a calm Buddhist temple aesthetic, with each user's progress auto-saved to their own device.

## The prompt

```
Design a gamification system for a Buddhist Studies flashcard app with the following requirements:

Tone: calm and thematic — Buddhist temple aesthetic (gold on dark background), serene language, no confetti or sound effects

Mechanics to include:

1. Streak counter
   - Tracks consecutive correct answers in the current session
   - Resets to zero on any wrong answer
   - Displays current streak and session-best streak
   - Visual: a small flame icon that glows as the streak grows

2. XP and levels
   - 10 XP per correct answer, plus a small streak bonus
   - 9 thematic level names in order: Seeker, Novice, Student, Disciple, Adept, Scholar, Sage, Elder, Enlightened
   - Shown as a level ring and XP progress bar
   - Reaching a new level triggers a brief calm "Level Up" toast notification

3. Milestone badges (9 total, earned in-session)
   - First Step: answer your first question correctly
   - Kindling: 5 correct in a row
   - Steady Flame: 10 correct in a row
   - Unbroken: 20 correct in a row
   - Diligent: 25 total correct in the session
   - Devoted: 50 total correct in the session
   - Halfway: see 36 of the 71 cards
   - Complete Path: see all 71 cards
   - Flawless: finish with 100% accuracy
   Each badge announced by a gentle toast at the moment it is earned

4. Encouraging messages
   - Quiet italic text shown at streak milestones
   - Phrased calmly, e.g. "A kindled flame. Keep it burning." or "Your concentration deepens."

Persistence (auto-save, no buttons):
- Save to browser localStorage automatically after every answer
- Persist: XP total, current level, lifetime best streak, earned badges
- Do NOT persist: deck position, current score, answered cards (session resets each visit)
- Each user's data is stored only in their own browser
- Sharing the app URL gives each person their own independent, separate progress

Scope:
- Track answers in Multiple Choice and Fill-in-Blank modes
- Flashcard mode tracking is passive (streaks do not count in Flashcard mode)
```

## Inputs

Answer events from the quiz engine: `{ correct: boolean, cardIndex: number, mode: "mc" | "fib" | "flash" }`.

## Expected output

Updated reward state: `{ xp, level, streak, bestStreak, badges[] }`. Toast notifications for badge unlocks and level-ups. Encouraging message string at streak milestones (5, 10, 20, 30).

## Related files

- Reasoning: [`REASONING.md`](./REASONING.md)
- Evaluation rubric: [`rubric.yaml`](./rubric.yaml)
- Version history: [`versions/`](./versions/)
