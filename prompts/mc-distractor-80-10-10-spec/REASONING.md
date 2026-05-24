# Reasoning: Multiple Choice Distractor — 80/10/10 Technique Mix

This document captures the thinking behind the prompt — not just what it does, but why it ended up this way.

## Goal

Make the Multiple Choice mode genuinely useful for exam preparation, not just a confidence booster. The default approach — pulling wrong options randomly from other cards in the same chapter — was too easy. Students could eliminate wrong answers by topic alone (e.g. a question about relics showing an answer about the Bodhi Tree as a wrong option), without needing to know the specific fact being tested.

## Iteration history

**v1 — same-chapter random distractors.** The first version pulled 3 random answers from other cards in the same chapter. Better than cross-chapter (topically closer), but still obviously off. A student who'd skimmed the chapter could eliminate wrong options without reading carefully.

**v2 — this spec.** The 80/10/10 split was designed to match different card types:

- **Option A (80%)** — hand-crafted distractors for most cards. I wrote 3 wrong answers per card that substitute plausible-but-wrong details: a similar number, a nearby Pāli term, a related character. These require knowing the specific fact, not just the topic.
- **Option B (10%)** — answer-fragment mixing for multi-part list cards. Instead of inventing wrong answers, I recombine fragments of the real answer into wrong wholes. For example, on the "five matters for consideration" card, a wrong option might pair the correct lifespan (100 years) with the wrong location (Uttarakuru instead of Jambudipa).
- **Option C (10%)** — negative questions for numbered-list cards. "Which is NOT one of the five warning signs?" is harder than "Which IS a warning sign?" because it tests knowledge of all five items, not just one.

The technique split was also matched to difficulty level: Easy uses cross-chapter random distractors (easy to eliminate), Medium and Hard both use the hand-crafted set.

## Failure modes the final version handles

- **Accidentally correct distractors**: the automated validation confirmed no distractor duplicates its correct answer. Human review of the hand-crafted content against the textbook remains the user's responsibility.
- **Negative questions requiring fabricated items**: each Option C card includes exactly one fabricated item that sounds plausible (uses appropriate vocabulary and structure) but does not appear in the textbook. The fabricated item is the correct selection.
- **Small chapters with too few cards**: Ch.13 (1 card) and Extra (1 card) cannot draw same-chapter distractors. The spec falls back to cross-deck selection for those cards.

## Outcome

Shipped. 63 Option A/B cards and 8 Option C (negative) cards across 71 total. Technique split: 79% / 10% / 11% — within rounding of the target. All Hard-difficulty cards use the hand-crafted set; no card falls back to random on Hard.

## What I'd change next

Have the user review and sign off on each distractor against the textbook before shipping. The automated check only confirms no distractor equals the correct answer — it cannot confirm that the wrong options are factually accurate representations of what is *not* true. Distractors written to resemble the truth are the hardest content to catch if they're subtly wrong.

## Tags

`content` `classification` `agent-workflow`
