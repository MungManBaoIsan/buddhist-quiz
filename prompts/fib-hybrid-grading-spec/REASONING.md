# Reasoning: Fill-in-Blank Hybrid Grading Spec

This document captures the thinking behind the prompt — not just what it does, but why it ended up this way.

## Goal

I wanted to add a fill-in-blank study mode to the Buddhist Quiz app. The problem was that the 71 cards are a very mixed bag: some have short one-word answers ("Ānanda"), others have 80-word explanatory paragraphs. A single grading approach doesn't work for both types.

## Iteration history

**v1 — pure keyword match considered.** My first thought was keyword matching for everything. Rejected because Pāli terms have so many valid spellings and forms (Ānanda / Ananda / Venerable Ananda) that any strict matching would wrongly fail correct answers constantly.

**v2 — pure self-grading considered.** The fallback option: show the question, let the user type anything, then reveal the answer and let them decide if they got it right. Rejected because self-grading becomes inconsistent over time — people mark themselves more generously when tired, more harshly when they've just got something wrong. No reliable feedback.

**v3 — hybrid (this spec).** The insight was that the problem isn't grading; it's classification. Short cards (single name, number, or term) can be graded objectively by keyword match with a generous accept-list. Long cards (processes, narratives, comparisons) are genuinely hard to grade automatically because there are too many valid phrasings. For those, self-grading is actually the right answer — but it must come *after* active recall. The user types their answer first, then sees the textbook text, then marks themselves.

## Failure modes the final version handles

- **Diacritic mismatch**: "Ananda" should match "Ānanda". The accept-list uses diacritic-insensitive matching. Example: `accept: ["Ananda", "Ānanda", "Venerable Ananda"]`.
- **Multiple valid forms**: some terms have a short form and a full form both accepted by the exam. The accept-list covers both.
- **Self-grading consistency**: active recall is forced before the answer is revealed on long cards. The user can't see the answer first and then "remember" they knew it.
- **Wrong card type classification**: 20 of 71 cards are keyword cards; 51 are self-grade. The classification was done manually, card by card, and verified by checking that each keyword card's accept-list terms actually appear in the card's textbook answer text.

## Outcome

Shipped in both the mobile and desktop versions of the app. 58 keyword accept-list entries verified — every accepted term confirmed present in its card's answer text before shipping. Long cards show the textbook-exact `tb` field on reveal, not the longer explanatory paragraph.

## What I'd change next

Add a "near-match" flag for borderline cases — where the user typed something close but not in the accept-list — so the app can suggest "did you mean X?" rather than just marking it wrong. This would reduce frustration from minor spelling differences not covered by the accept-list.

## Tags

`classification` `content` `extraction`
