# Prompt Changelog

Chronological record of prompt creation and refinement. Newest entries at the top.

---

## gamification-spec

### 2026-05-24 — v2
**Change:** Added XP/levels, encouraging messages, and localStorage persistence. Clarified that session position (deck position, score) is deliberately *not* persisted — only reward state (XP, level, best streak, badges) persists silently.
**Reason:** User wanted persistence across visits, XP progression, and calm thematic tone. Previous version was session-only.
**Impact:** Each user's progress now accumulates across visits with no save button or prompts needed. App now has 9 thematic level names (Seeker → Enlightened).

### 2026-05-23 — v1
**Change:** Initial version. Added session-only streaks and milestone badges.
**Reason:** App needed engagement mechanics without cluttering the calm Buddhist aesthetic.
**Impact:** Streak counter and 9 badge milestones live in the app. Resets each session.

---

## difficulty-timer-config

### 2026-05-24 — v2
**Change:** Widened timer gaps (30/20/12 → 60/40/24 seconds). Upgraded Medium to use the same hand-crafted distractors as Hard.
**Reason:** Original gaps were too narrow — Medium and Hard felt almost identical. Medium needed to be clearly harder than Easy in content, not just time.
**Impact:** Three genuinely distinct difficulty levels: Easy (gentle, cross-chapter distractors), Medium and Hard (hand-crafted distractors + negative questions, different time pressure).

**Also removed:** Manual Save/Load buttons and full session persistence — added complexity without enough benefit. Only reward state persists.

### 2026-05-23 — v1
**Change:** Initial version. Easy 30s / Medium 20s / Hard 12s. Medium used same-chapter distractors; Hard used hand-crafted.
**Reason:** First pass at a difficulty system.
**Impact:** Functional but levels felt too similar in practice.

---

## mc-distractor-80-10-10-spec

### 2026-05-24 — v2
**Change:** Defined the 80/10/10 technique split and mapped techniques to card types. Added Option C (negative "which is NOT" questions) for numbered-list cards.
**Reason:** v1 auto-generated distractors were too easy to eliminate by topic alone. Students needed to know the specific fact, not just the subject area.
**Impact:** 63 hand-crafted distractor cards and 8 negative questions across 71 cards. Hard and Medium difficulty both use this set.

### 2026-05-22 — v1
**Change:** Initial version. Wrong options pulled randomly from other cards in the same chapter.
**Reason:** Needed *some* wrong answers for Multiple Choice to function.
**Impact:** Functional but not genuinely challenging. Easy to eliminate options without knowing the fact.

---

## fib-hybrid-grading-spec

### 2026-05-23 — v3 (final)
**Change:** Settled on hybrid approach: keyword match for 20 short factual cards, self-grading for 51 long explanation cards.
**Reason:** v2 (pure self-grading) was too inconsistent over time. The real insight was that the problem is card *classification*, not grading approach.
**Impact:** 58 keyword accept-list entries verified. Every accepted term confirmed present in its card's textbook answer text.

### 2026-05-23 — v2
**Change:** Tried pure self-grading for all cards.
**Reason:** Avoid the spelling-variant problem of keyword matching.
**Impact:** Rejected — self-grading becomes inconsistent without a consistent external benchmark.

### 2026-05-23 — v1
**Change:** Tried pure keyword matching for all cards.
**Reason:** Most direct approach to grading.
**Impact:** Rejected — Buddhist Pāli terms have too many valid spellings to enforce exact match reliably.

---

## flashcard-answer-style-guide

### 2026-05-22 — v2 (final)
**Change:** Added explicit rules: no preamble, Pāli terms in brackets, no hedging, "do not add or remove required information."
**Reason:** Merging new Ch.11–13 cards with existing Ch.2–10 cards revealed inconsistent style across the deck. Cards needed to read as one coherent set.
**Impact:** All 71 cards now follow a consistent style in Flashcard mode. Explanatory paragraphs for reading/absorbing; textbook-exact `tb` field used separately for testing modes.

### 2026-05-22 — v1
**Change:** No governing prompt. Answers written ad-hoc.
**Reason:** Initial development, no style requirements yet.
**Impact:** Inconsistent: some cards had preamble, some had hedging, Pāli terms bracketed inconsistently.
