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
