# Buddhist Quiz – Buddhānubuddha Pavat

A multi-mode study app for the Thai national Buddhist Studies exam — covering **71 questions across all chapters (Ch.1–13 + Extra)**. Choose how you want to study: flip flashcards, test yourself with multiple choice, or challenge yourself with fill-in-the-blank. Available in a mobile-first touch version and a desktop dashboard with keyboard shortcuts.

**Mobile (iPhone & Android):** https://joshuablakemorekay.github.io/buddhist-quiz/
**Desktop (laptop & monitor):** https://joshuablakemorekay.github.io/buddhist-quiz/index_desktop.html

---

## Study Modes

### Flashcard mode
Flip a card to reveal the full explanatory answer — written to help you understand the *why* behind each fact, not just memorise it. Use this mode first, before testing yourself.

### Multiple Choice mode
Four options per question. The wrong answers are deliberately plausible — they use similar Pāli terms, similar numbers, or similar names to the correct answer, so you can't eliminate them by topic alone. You have to know the specific fact.

### Fill-in-Blank mode
A key word is removed from each answer and you type it in. Short factual cards (a single name, number, or term) are graded automatically — the app accepts all valid spellings of Pāli terms (for example, "Ananda" matches "Ānanda"). Longer explanation cards ask you to type your recall first, then reveal the textbook answer so you can judge yourself honestly.

> **Note on answers:** Flashcard mode shows fuller explanatory text — good for learning. Multiple Choice and Fill-in-Blank show answers exactly as they appear in the Thai national exam textbook — good for exam prep.

---

## Difficulty Levels

| Level | Timer | Wrong answers in Multiple Choice |
|---|---|---|
| **Easy** | 60 seconds | Drawn from other chapters — easy to eliminate by topic |
| **Medium** | 40 seconds | Hand-crafted plausible distractors |
| **Hard** | 24 seconds | Hand-crafted distractors + negative "which is NOT" questions |

The timer runs in Multiple Choice and Fill-in-Blank only. Flashcard mode is always untimed.

---

## Features

### Both versions
- **71 cards** covering Chapters 1–13 and the Extra question, fully cross-referenced with Thai exam years (2006–2023)
- **Three study modes** — Flashcard, Multiple Choice, Fill-in-Blank
- **Three difficulty levels** — Easy, Medium, Hard with per-question timer
- **Chapter filter** — study one chapter at a time or the full deck
- **Shuffle mode** — randomise card order so you don't memorise the sequence
- **Score tracking** — mark cards as "Know It" or "Review Again" as you go
- **Session complete screen** — see your score at the end of each round
- **How to use overlay** — explains the two answer styles (tap the ⓘ button)

### Rewards (per-user, saved automatically)
Your progress is saved in your browser — no account needed. Each person who opens the link gets their own independent rewards.

- **Streak counter** — tracks consecutive correct answers with a small flame icon
- **XP and levels** — earn 10 XP per correct answer and climb through 9 thematic ranks: Seeker → Novice → Student → Disciple → Adept → Scholar → Sage → Elder → Enlightened
- **Milestone badges** — 9 achievements to unlock (First Step, Kindling, Steady Flame, Unbroken, Diligent, Devoted, Halfway, Complete Path, Flawless)
- **Encouraging messages** — quiet, calm phrases at streak milestones

### Mobile version
- Swipe left/right to navigate between cards
- Scrollable chapter filter pills at the top of the screen
- iPhone safe-area support (layout adjusts correctly around the notch)
- Tap to flip cards with a smooth 3D animation

### Desktop version
- Fixed sidebar with chapter list, question counts, and live score panel
- Keyboard shortcuts: Space to flip, arrow keys to navigate, K for Known, R for Review
- Sidebar scrolls independently when the chapter list is long
- Cormorant Garamond typography for a classical, book-like feel

---

## Built With

| Part | Technology |
|---|---|
| Structure | HTML |
| Styling | CSS (3D flip animations, decorative accents, responsive layout) |
| Logic | Vanilla JavaScript (no frameworks, no libraries) |
| Fonts | Google Fonts (Cinzel + EB Garamond — mobile; Cormorant Garamond — desktop) |
| Storage | Browser localStorage (for per-user reward persistence) |
| Hosting | GitHub Pages |

---

## How to Use It

### Live (no setup needed)
- **Mobile:** https://joshuablakemorekay.github.io/buddhist-quiz/
- **Desktop:** https://joshuablakemorekay.github.io/buddhist-quiz/index_desktop.html

Just open the link on any device. Your XP, level, best streak, and badges save automatically in your browser.

---

## Project Structure

```
buddhist-quiz/
├── index.html              ← Mobile version (live on GitHub Pages)
├── index_desktop.html      ← Desktop dashboard version
├── README.md               ← This file
├── JOURNAL.md              ← Development log — decisions, learnings, milestones
├── prompts/                ← Prompt library (documented AI prompts used to build this)
│   ├── README.md               ← Index of all prompts
│   ├── CHANGELOG.md            ← How each prompt evolved over time
│   ├── flashcard-answer-style-guide/
│   ├── fib-hybrid-grading-spec/
│   ├── mc-distractor-80-10-10-spec/
│   ├── difficulty-timer-config/
│   └── gamification-spec/
└── scripts/
    └── eval_runner.py      ← Automated rubric runner for the prompt library
```

---

## My Journey

### 2026-05-14 — Deployed Buddhist Quiz as a live mobile-first app on GitHub Pages

I took the Buddhist Quiz app — which previously ran locally in PyCharm using Flask — and rebuilt it as a single standalone `index.html` file with no backend needed. I expanded the question set from 25 cards (Chapters 5–11) to 39 cards covering Chapters 2–11, and added mobile-first features including swipe gestures, chapter filter pills, and iPhone safe-area support.

**Key things I learned:**
- How to deploy a static site to GitHub Pages — push the file, it goes live, no server needed
- How to build a 3D CSS card flip animation using `transform: rotateY()`
- How to detect swipe gestures using JavaScript touch events
- The difference between a Flask app (needs Python) and a standalone HTML file (runs anywhere)

### 2026-05-14 — Built a desktop-optimised version with keyboard shortcuts

I built a second version of the app — `index_desktop.html` — designed for studying at a laptop. It has a fixed sidebar showing the chapter list and live score, keyboard shortcuts for hands-free navigation, Cormorant Garamond typography, and decorative corner accents on cards.

**Key things I learned:**
- How to listen for keyboard input in JavaScript using `addEventListener('keydown', ...)`
- How to load a custom font from Google Fonts with a single `<link>` tag
- That designing for a specific screen size can produce a more focused, polished result than trying to be responsive

### 2026-05-24 — Expanded to 71 cards with three study modes, difficulty levels, and gamification

I expanded the deck from 39 to 71 cards covering the full exam syllabus (Ch.1–13 + Extra). I added Multiple Choice and Fill-in-Blank modes, three difficulty levels with a per-question timer, and a full rewards system (streaks, XP, levels, badges).

**Key things I learned:**
- How to design grading logic that handles short and long answers differently — keyword match where it works, self-grading where it doesn't
- That localStorage (browser-side storage) is enough for per-user persistence with no server or accounts needed
- That removing a feature (Save/Load buttons) can make an app feel better, not worse — simplicity matters
- How to write genuinely difficult multiple-choice wrong answers: they need to be factually adjacent (same vocabulary, similar numbers), not just topically adjacent
- That a calm, thematic rewards system can feel appropriate in a Buddhist study context — "make it fun" and "keep it respectful" are not opposites

---

## Prompt Library

The `/prompts` folder documents the key AI prompts used to design and build this app's features — the flashcard style guide, the grading logic, the distractor strategy, the difficulty system, and the gamification spec. Each prompt has a full reasoning document (why it's structured the way it is) and an automated evaluation rubric that runs on every push.

This folder is portfolio evidence of prompt engineering, not just vibe-coding.

**View the prompt library:** [prompts/README.md](./prompts/README.md)

---

## What's Next

- [ ] Add audio pronunciation for Pāli terms
- [ ] Lifetime stats view — total questions answered and accuracy rate over time
- [ ] Exam Simulation mode — one timer for the whole session, not per question

---

## About the Developer

I'm Josh — a British Buddhist monk learning to code while living at a monastery in Thailand. I built this app to help myself (and other monks) study for the Thai national Buddhist Studies exam. It started as a local Flask app in PyCharm and grew into a fully deployed multi-mode study tool.

GitHub: https://github.com/joshuablakemorekay

---

## What I Learned (Overall)

Building this project taught me that you don't need a complex setup to ship something real. A single HTML file, a free GitHub account, and plain JavaScript was enough to build a working study tool — deployed live, shareable with one link, and now used by monks studying for a national exam.

The bigger lesson from the v2 expansion: **design decisions matter more than code volume.** Choosing *how* to grade fill-in-blank answers (keyword match vs self-grade, depending on card type) required more thinking than writing the code. Getting the wrong answers *wrong-in-the-right-way* for Multiple Choice required understanding the exam content, not just copying patterns. That thinking is what makes a study tool actually useful.
