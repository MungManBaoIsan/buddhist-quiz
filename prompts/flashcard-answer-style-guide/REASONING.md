# Reasoning: Flashcard Answer Style Guide

This document captures the thinking behind the prompt — not just what it does, but why it ended up this way.

## Goal

I was merging 17 new flashcard answers (Chapters 11–13) with 39 existing answers (Chapters 2–10) into a single 53-card deck (later grown to 71). The two sets had been written at different times with no shared style guide, so they felt like two different apps. I needed every card to read consistently — same length, same use of Pāli terms, same structure — before sharing the app with other monks preparing for the Thai national Buddhist Studies exam.

## Iteration history

**v1 — no governing prompt.** The original 39 answers were written ad-hoc. They were mostly solid, but varied: some started with preamble ("In this context, the Buddha..."), some used hedging ("it is said that"), and Pāli terms were sometimes bracketed and sometimes not.

**v2 — this prompt.** Rather than compressing the existing 39 answers down to match a terser new style, I decided to bring all new cards up to match the established house style of the 39. The prompt codifies that style: full explanatory paragraphs, direct opening, Pāli terms bracketed, no hedging. This was a deliberate choice — the longer style suits the flashcard mode, which is for reading and absorbing rather than testing.

## Failure modes the final version handles

- **No-preamble rule**: earlier drafts sometimes opened with "The Buddha said..." or "In the context of...", which wastes card space and slows reading.
- **Pāli term bracketing**: without this rule, the same term appeared with and without brackets (e.g. "Ayusankhara" vs "Ayu-Sankhara (the relinquishing of vital force)"), making the deck feel inconsistent.
- **No hedging**: "it is said that" and "tradition holds" are fine in an essay, but on a flashcard they signal uncertainty where the exam expects confidence. Removed entirely.
- **The "don't add or remove" rule**: the most important guardrail. The exam has specific correct answers, and the prompt must not cause the AI to paraphrase away a required fact.

## Outcome

Shipped in the live app at https://mungmanbaoisan.github.io/buddhist-quiz/. All 71 cards now follow a consistent style in Flashcard mode. The textbook-exact answers (shorter, from the Thai textbook) are stored separately in a `tb` field used in Multiple Choice and Fill-in-Blank modes — so the style guide applies to the learning-mode text, not the testing-mode text.

## What I'd change next

Add a per-card `max_words` field to the data so the style guide has a hard limit to enforce, not just a soft "3 sentences" rule. The current rule is a little fuzzy for cards that sit on the border between short and long.

## Tags

`content` `classification` `extraction`
