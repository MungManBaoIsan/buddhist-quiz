# Reasoning: Difficulty and Timer Configuration

This document captures the thinking behind the prompt — not just what it does, but why it ended up this way.

## Goal

Give the app three difficulty levels that feel genuinely different from each other — not just "Easy is slow, Hard is fast." I wanted learners to be able to start gently, build confidence, and then step up to something that actually simulates the time pressure of the national exam.

## Iteration history

**v1 — Easy 30s / Medium 20s / Hard 12s.** The first timer values were too compressed. Medium and Hard felt almost identical in practice, and 12 seconds on Hard was so fast that students spent more time panicking than thinking.

**v2 — Easy 60s / Medium 40s / Hard 24s.** Wider gaps between levels. 60 seconds on Easy is genuinely relaxed — enough to read the full answer options carefully. 24 seconds on Hard is tight but not impossible for someone who knows the material.

**v2 also changed the distractor content for Medium**: originally, Medium used same-chapter random distractors (easier) while Hard used hand-crafted ones. The user correctly pointed out that Medium and Hard should have the same *content* difficulty — only the time pressure should differ. So Medium was upgraded to use the hand-crafted distractor set.

## Features tried and removed

**Manual Save/Load buttons.** I built Save and Load buttons so users could manually preserve their deck position and return to the same card later. User feedback: "doesn't feel effective enough, doesn't really work properly and complicates it." Removed. The complication wasn't worth the benefit — most study sessions are short enough that you don't need to save mid-deck.

**Full session persistence.** I built localStorage-based auto-save of the deck position, score, and answered cards, with a resume prompt on reload. Same feedback: too complicated, the resume modal added friction. Removed. What does persist (quietly, without prompts) is the reward state — XP, level, best streak, and earned badges. That's the data that accumulates meaningfully across many sessions.

## Outcome

Shipped. Both the mobile and desktop versions have an Easy / Medium / Hard selector. The timer runs in Multiple Choice and Fill-in-Blank modes only — Flashcard mode is always untimed because it's for reading and absorbing, not testing under pressure. Timer expiry marks the card for review, reveals the correct answer, and auto-advances.

## What I'd change next

Add a fourth "Exam Simulation" mode with a total time limit for the whole session (not per card), mirroring how real exam conditions work. Per-card timers don't fully replicate the experience of managing a fixed total time across many questions.

## Tags

`agent-workflow` `other`
