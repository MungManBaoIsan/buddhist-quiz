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
