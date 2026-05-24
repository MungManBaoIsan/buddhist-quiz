# Development Journal — Buddhist Quiz – Buddhānubuddha Pavat

A chronological log of key developments, decisions and learnings throughout this project.

---

## 2026-05-14 — Deployed Buddhist Quiz as a live mobile-first app on GitHub Pages

**Type:** Milestone

**What I built or did**
I took the Buddhist Quiz app — which previously ran locally in PyCharm using Flask — and rebuilt it as a single standalone `index.html` file with no backend needed. I expanded the question set from 25 cards (Chapters 5–11) to 39 cards covering Chapters 2–11, and added several mobile-first features. Then I deployed it live to GitHub Pages so it's accessible on any phone, anywhere.

**Why I did it this way**
Flask runs a local Python server — great for development, but it can't be shared as a link or opened on a phone without setup. A standalone HTML file runs directly in any browser with no installation. GitHub Pages hosts it for free. I also wanted to challenge myself to build the whole app without relying on any external tools or frameworks (no dependencies at all).

**How it works**
All the HTML, CSS, and JavaScript lives inside one `index.html`. The card flip uses a 3D CSS `transform: rotateY()` animation. Swipe navigation listens for `touchstart` and `touchend` JavaScript events and compares finger positions to detect a left or right swipe. Chapter filter pills sit in a horizontally scrollable row. Score tracking and the session-complete screen are all handled in plain JavaScript variables — no library needed.

**What this means for the app**
The app is now live at https://mungmanbaoisan.github.io/buddhist-quiz/ and works on iPhone and Android without any installation. It's a real, shareable study tool — I can send the link to other monks and they can open it straight from their phone.

**What I learned**
- How to deploy a static site (a site with no server) to GitHub Pages — push the HTML file to the right branch and it goes live automatically
- How to build a 3D card flip animation using only CSS `transform` properties
- How to detect swipe gestures on a touchscreen using JavaScript touch events
- How to structure a complete app inside one HTML file with no external tools or libraries
- The key difference between a Flask app (needs Python running) and a standalone HTML file (runs in any browser, anywhere)

**References / Conversations**
Built with help from Claude Code (Anthropic).

---

## 2026-05-14 — Merged portfolio docs into main and cleaned up the feature branch

**Type:** Learning / Milestone

**What I built or did**
I ran the portfolio-update skill to add `JOURNAL.md` and `README.md` to the Buddhist Quiz repo. I then worked through merging the feature branch into `main` and deleting the feature branch once everything was safely landed.

**Why I did it this way**
The feature branch had done its job — the docs were written and ready. Merging into `main` is the standard step to make changes "official" in the repo. Deleting the branch afterwards keeps the repo clean.

**How it works**
This turned into more of a git detective session than expected. The feature branch (`feature/your-feature-name`) had a completely different git history from the remote `main` branch — because the local git repo is rooted at the home folder (`C:\Users\joshk`) rather than the project folder itself. The remote `main` had `index.html` at the repo root (what GitHub Pages actually serves), while the feature branch had files stored at a deep nested path. Merging directly would have deleted the live app.

Instead, I checked out `origin/main`, wrote `JOURNAL.md` and `README.md` at the repo root (so they appear correctly on GitHub), committed, pushed, and then deleted the feature branch both locally and from GitHub.

**What this means for the app**
The Buddhist Quiz repo on GitHub now has a proper, full README visible to anyone who visits the repo — covering features, tech stack, setup instructions, and the developer journey. The live app at `https://mungmanbaoisan.github.io/buddhist-quiz/` remained untouched throughout. The repo is clean — one branch (`main`), no stale feature branches.

**What I learned**
- Always check where the git root is (`git rev-parse --show-toplevel`) before doing branch work — a repo rooted at the home directory behaves differently from one in a project folder
- When two branches have diverged histories, a standard merge or push will be rejected — you need to understand what each branch contains before deciding how to combine them
- GitHub Pages serves files from the repo root — so `index.html` needs to live there, not in a subfolder
- Cleaning up a feature branch (`git branch -d` + `git push origin --delete`) is a small but important habit for keeping a repo tidy

**References / Conversations**
Worked through with Claude Code (Anthropic). Git conflict diagnosed by checking `git rev-parse --show-toplevel`, `git log`, and `git diff origin/main..main --stat`.

---

## 2026-05-14 — Built a desktop-optimised version of the Buddhist Quiz

**Type:** Feature

**What I built or did**
I built a second version of the Buddhist Quiz — `index_desktop.html` — designed specifically for studying at a laptop or desktop screen. It has a completely different layout from the mobile version: a fixed sidebar showing the chapter list, question counts, and a live score panel, while the main area stays focused on the card itself.

**Why I did it this way**
The mobile version is great on a phone, but the layout doesn't make full use of a large screen. A sidebar-based dashboard feels more natural at a desk — you can see your progress at a glance without tapping through menus. I also wanted to add keyboard shortcuts, which only make sense on a desktop where there's a keyboard to use.

**How it works**
The layout uses CSS to fix the sidebar in place on the left while the card area takes up the remaining space. Keyboard shortcuts are handled by a JavaScript `keydown` event listener — `Space` flips the card, arrow keys navigate, `K` marks Known, `R` marks Review Again. The typography uses Cormorant Garamond (loaded from Google Fonts — a free service that provides web fonts), which gives the cards a more classical, book-like feel. Decorative corner accents on the cards are drawn in pure CSS using `::before` and `::after` pseudo-elements (invisible extra elements attached to a real element, used for decoration).

**What this means for the app**
The quiz now has two purpose-built versions for two different study contexts — phone in hand during a break, or laptop open at a desk. Both are live on GitHub Pages and shareable as plain links.

**What I learned**
- How to listen for keyboard input in JavaScript using `addEventListener('keydown', ...)`
- How to load a custom font from Google Fonts with a single `<link>` tag
- How to use CSS `::before` and `::after` pseudo-elements for purely decorative effects
- That designing for a specific screen size (rather than trying to be responsive) can produce a much more focused, polished result

**References / Conversations**
Built with help from Claude Code (Anthropic).

---

## 2026-05-24 — Expanded the Buddhist Quiz from 39 to 71 cards with three study modes and a rewards system

**Type:** Feature / Milestone

**What I built or did**
I took the existing 39-card mobile-first quiz app and expanded it significantly over one session. The deck now covers all chapters (Ch.1–13 plus an Extra question) with 71 unique flashcards. I added two new study modes — Multiple Choice and Fill-in-Blank — on top of the existing Flashcard mode. I also built a full gamification system with streaks, XP, levels, and milestone badges.

**The key features added:**
- Three study modes: Flashcard (for reading and absorbing), Multiple Choice (four options, auto-graded), Fill-in-Blank (keyword match for short cards, self-grading for long ones)
- Three difficulty levels: Easy (60s timer, easier distractors), Medium (40s, hard distractors), Hard (24s, hand-crafted distractors and negative questions)
- 71 cards: the original 39 plus new cards for Ch.1 (7 cards), Ch.2 (9 new cards), Ch.5 (1 new card), Ch.12 (11 new cards), Ch.13 (1 new card), and Extra (1 card)
- Textbook-exact answers in Multiple Choice and Fill-in-Blank — answers are quoted directly from the Thai national exam textbook
- Gamification: streaks, XP (10 per correct answer), 9 thematic levels (Seeker through Enlightened), 9 milestone badges, and calm encouraging messages
- Per-user localStorage persistence for XP, level, best streak, and earned badges — each person who opens the link gets their own independent progress, stored only in their own browser
- A "How to use" note explaining the two styles of answers (explanatory in Flashcard mode, textbook-exact in the other two modes)
- Sidebar scrollbar added to the desktop version for long chapter lists

**What I tried and then removed:**
- Manual Save/Load buttons: I built these so users could save their deck position and return later. Removed after testing — it added complexity and felt out of place. The lesson: invisible auto-save (for rewards only) is better than visible buttons.
- Full session persistence (deck position, score, answered cards): same issue. Simplified to persist only the reward state, not where you are in the deck.

**Why I did it this way**
The app is used by monks and Buddhist students preparing for the Thai national Buddhanubuddha Pravat exam. The exam is written, so students need to reproduce the exact textbook phrasing — not just recognise it. That is why Multiple Choice and Fill-in-Blank show the textbook-exact answers while Flashcard mode shows fuller explanatory text. Two styles, two purposes.

**How it works (for the non-obvious parts)**
The 80/10/10 distractor split for Multiple Choice: 80% of cards have hand-crafted wrong answers (factually adjacent to the correct one — similar Pali terms, similar numbers), 10% use answer-fragment mixing (real fragments recombined into wrong wholes), and 10% are negative "which is NOT" questions (one fabricated item among real ones). The fill-in-blank hybrid grader classifies each card as short-factual (keyword match with a diacritic-insensitive accept-list) or long-explanation (type-then-reveal-then-self-grade). The gamification uses the browser's built-in localStorage (a way for websites to save data directly on your device, without a server) so each person's progress is stored privately on their own phone or computer.

**What this means for the app**
The app is now a proper multi-mode study tool covering the full exam syllabus, not just a simple flashcard set. It can be shared with one link and every person who opens it gets their own account-free progress tracking.

**What I learned**
- How to design grading logic that handles short and long answers differently, rather than forcing one approach on everything
- That localStorage is enough for simple per-user persistence without needing a server or accounts
- That removing a feature (Save/Load) can make an app feel better, not worse — simplicity matters
- How to write genuinely difficult multiple-choice wrong answers: they need to be factually adjacent, not just topically adjacent
- That "make it fun" and "keep it calm" are not opposites — the gamification uses Buddhist-themed language and a temple aesthetic so rewards feel appropriate rather than jarring

**References / Conversations**
Built with help from Claude Code (Anthropic) in a single extended session. Prompt decisions documented in `/prompts/` — see the prompt library for the governing style guide, grading spec, and gamification spec.

---
