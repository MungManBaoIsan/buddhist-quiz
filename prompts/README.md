# Prompt Library — Buddhist Quiz App

[![Prompt Eval](https://github.com/joshuablakemorekay/buddhist-quiz/actions/workflows/prompt-eval.yml/badge.svg)](https://github.com/joshuablakemorekay/buddhist-quiz/actions/workflows/prompt-eval.yml)

This folder documents the key prompts used to build the **Buddhist Quiz — Buddhānubuddha Pavat** app. It exists as portfolio evidence of prompt engineering, evaluation, and iteration — not just "I asked Claude to do X."

Each prompt directory has:
- **prompt.md** — the exact prompt used (quoted verbatim)
- **REASONING.md** — why the prompt is structured the way it is, what earlier versions got wrong, and what I'd change next
- **rubric.yaml** — criteria with executable pass conditions that run automatically on every push

## Index

| Prompt | Category | What it does | Iterated? |
|---|---|---|---|
| [`flashcard-answer-style-guide`](./flashcard-answer-style-guide/) | content | Standardises all 71 flashcard answers to a consistent exam-ready style | Yes (v1 → v2) |
| [`fib-hybrid-grading-spec`](./fib-hybrid-grading-spec/) | classification | Designs keyword-match grading for short cards and self-grading for long ones | Yes (v1 → v3) |
| [`mc-distractor-80-10-10-spec`](./mc-distractor-80-10-10-spec/) | content | Generates plausible wrong answers using a deliberate 80/10/10 technique mix | Yes (v1 → v2) |
| [`difficulty-timer-config`](./difficulty-timer-config/) | agent-workflow | Configures three genuinely distinct difficulty levels with timers and distractor types | Yes (v1 → v2) |
| [`gamification-spec`](./gamification-spec/) | agent-workflow | Designs the XP, levels, streak, and badge system with per-user localStorage persistence | Yes (v1 → v2) |

## Featured iterations

Prompts where the v1 → final journey shows the most learning:

### [`fib-hybrid-grading-spec`](./fib-hybrid-grading-spec/)

This one went through the clearest thinking. My first instinct was keyword matching for everything — rejected because Pāli terms have so many valid spellings. My second instinct was self-grading for everything — rejected because it becomes inconsistent over time. The final insight was that the real problem is **classification**, not grading: short cards suit keyword matching; long explanation cards suit self-grading. The prompt captures that classification logic clearly.

### [`mc-distractor-80-10-10-spec`](./mc-distractor-80-10-10-spec/)

The first version just pulled wrong options randomly from the same chapter — topically close but obviously off. The final spec introduces three deliberate techniques: hand-crafted plausible distractors (80%), answer-fragment mixing for list cards (10%), and negative "which is NOT" questions (10%). The split was chosen to match card types, not just to hit a number.

## Skills demonstrated

- [x] **Prompt design** — every prompt has a documented goal and structure
- [x] **Iteration** — see `REASONING.md` files for the v1 → final journey on each prompt
- [x] **Evaluation** — every prompt has a rubric with executable pass conditions
- [x] **Automated testing** — rubrics run on every push via [`prompt-eval.yml`](../.github/workflows/prompt-eval.yml)
- [x] **Regression prevention** — `--fail-under 0.8` blocks merges that drop score below threshold
- [x] **Documentation** — every prompt has a REASONING.md explaining the *why*, not just the *what*
- [x] **Honesty about failures** — removed features (Save/Load, session persistence) are documented in the relevant REASONING.md

## How to read this folder

- **90 seconds:** read this index and pick one featured iteration to skim
- **5 minutes:** read this index plus the REASONING.md of two prompts
- **Longer:** read the [CHANGELOG](./CHANGELOG.md) then run the eval runner

## Running the evaluations locally

```bash
pip install pyyaml
python scripts/eval_runner.py --provider mock
```

This validates every prompt against its rubric using deterministic fixtures (no API costs). See [`results-summary.md`](./results-summary.md) for the latest run.

To run against the real API:

```bash
export ANTHROPIC_API_KEY=your_key_here
python scripts/eval_runner.py --provider anthropic
```

## Changelog

See [`CHANGELOG.md`](./CHANGELOG.md) for a chronological view of how these prompts evolved.
