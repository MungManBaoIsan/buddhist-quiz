# Reasoning: Gamification System Spec

This document captures the thinking behind the prompt — not just what it does, but why it ended up this way.

## Goal

Add a sense of progress and reward to a study app that is otherwise pure content — without making it feel like a game, and without clashing with the calm, respectful Buddhist aesthetic. The app is used by monks and Buddhist students preparing for a serious national exam, so loud rewards or cartoon animations would feel wrong.

## Iteration history

**v1 — session-only streaks and badges, no persistence.** The first version added streaks and milestone badges that reset each time you load the app. Clean and simple, but the user wanted more: XP, levels, and persistence so that progress accumulates over time.

**v2 — this spec.** Added:
- **XP and levels**: 10 XP per correct answer, 9 thematic level names (Seeker through Enlightened), shown as a level ring and XP progress bar. The level names were chosen to reflect a Buddhist study path — secular enough to be appropriate for an academic context, thematic enough to fit the app.
- **Encouraging messages**: quiet italic text at streak milestones, phrased calmly ("A kindled flame. Keep it burning."). No exclamation marks, no "Awesome job!".
- **localStorage persistence**: XP, level, best streak, and earned badges auto-save after every answer. No save button, no reload prompt.

**The key design decision on persistence**: the user previously asked to remove the Save/Load feature because it "complicates it." So for v2, I separated reward persistence (background, automatic, no UI) from session persistence (deck position, score — which was deliberately *not* persisted). Each visit starts fresh on a card, but your lifetime progress quietly accumulates. The user confirmed this was the right balance.

## Failure modes the final version handles

- **Rewards resetting on page load**: the localStorage auto-save runs after every answer, so even a sudden tab close preserves the last state.
- **Per-device isolation**: because progress is stored in the browser's own storage (not on a server), each person who opens the app URL gets their own completely separate progress. No accounts, no setup, no one seeing anyone else's data.
- **Incognito mode**: progress does not survive if someone uses a private browsing window. This is a known limitation of localStorage and is documented in the app's "how to use" note.
- **Gamification in Flashcard mode**: streaks and XP do not accumulate in Flashcard mode. That mode is for reading, not testing — rewarding it with points would distort the learning incentive.

## Outcome

Shipped in both the mobile and desktop versions. The streak flame, XP bar, and level display sit unobtrusively in the sidebar on desktop and in the top bar on mobile. Badge toasts appear for a few seconds then fade. The calm gold-on-dark temple aesthetic is maintained throughout.

## What I'd change next

Add a lifetime stats view (total questions answered, accuracy rate over time) so users can track improvement across many sessions — not just their current level and best streak.

## Tags

`agent-workflow` `content` `other`
