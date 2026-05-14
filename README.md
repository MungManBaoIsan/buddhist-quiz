# Buddhist Quiz – Buddhānubuddha Pavat

A mobile-first flashcard quiz app for studying the Thai national Buddhist Studies exam — covering 39 questions from Chapters 2–11.

**Live app:** https://mungmanbaoisan.github.io/buddhist-quiz/

---

## What It Does

- **Flip flashcards** — tap a card to reveal the answer with a smooth 3D animation
- **Filter by chapter** — use the scrollable chapter pills at the top to study one chapter at a time
- **Track your score** — mark each card as "Know It" or "Review Again" as you go
- **Shuffle mode** — randomise the card order so you don't memorise the sequence
- **Session complete screen** — see your percentage score at the end of each round
- **Swipe to navigate** — swipe left or right on mobile to move between cards
- **Exam year tags** — each card shows which years the question appeared on the Thai national exam
- **iPhone safe-area support** — layout adjusts correctly around the iPhone notch

---

## Built With

| Part | Technology |
|------|------------|
| Structure | HTML |
| Styling | CSS (including 3D flip animations) |
| Logic | JavaScript (no frameworks, no libraries) |
| Local version | Python with Flask |
| Hosting | GitHub Pages |

---

## How to Run It

### Option A — Live (no setup needed)
Open: **https://mungmanbaoisan.github.io/buddhist-quiz/**
Works on iPhone, Android, and any desktop browser.

### Option B — Local (PyCharm + Flask)
1. Clone the repo (download your own copy of the project folder)
2. Open the project in PyCharm
3. Run `pip install flask` in the terminal
4. Right-click `app.py` → Run — the app opens at http://127.0.0.1:5000

---

## Project Structure

```
buddhist_quiz/
├── index.html              ← Standalone version (deployed to GitHub Pages)
├── index_smartphone.html   ← Mobile-specific draft
├── app.py                  ← Flask server for local development
├── requirements.txt        ← Python dependencies (just Flask)
├── README.md               ← This file
└── templates/
    └── index.html          ← Flask template version
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

---

## What's Next

- [ ] Add remaining chapters as more questions are studied
- [ ] Add a progress tracker that remembers cards between sessions (using browser local storage)
- [ ] Add audio pronunciation for Pali terms

---

## About the Developer

I'm Josh — a British Buddhist monk learning to code while living at a monastery in Thailand. I built this app to help myself (and other monks) study for the Thai national Buddhist Studies exam. It started as a local Flask app in PyCharm and grew into a fully deployed mobile-first web app.

GitHub: https://github.com/MungManBaoIsan

---

## What I Learned

Building this project taught me that you don't always need a complex setup to ship something real. A single HTML file, a free GitHub account, and a bit of CSS and JavaScript was enough to build a working study tool — deployed live on the internet.
