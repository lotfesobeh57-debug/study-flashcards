# Study Flashcards

A spaced-repetition flashcard app built on the Leitner system — works for any subject, not tied to one course.

**[Live demo →](https://lotfesobeh57-debug.github.io/study-flashcards/)**

## What it does

Cards move through 5 "boxes." Answer correctly and a card moves up a box, so it gets reviewed less often (1, 2, 4, 7, then 14 days). Answer incorrectly and it resets to box 1, so it's back tomorrow. Review time stays focused on what you're actually still learning, instead of re-reading everything from the top each time.

## Features

- Spaced-repetition scheduling (Leitner system), with per-card progress tracked locally
- Add cards one at a time, or bulk-import a `Q: ... / A: ...` block
- Edit and delete existing cards
- Export/restore backups as JSON — all data lives in the browser's local storage, nothing leaves the device
- Right-to-left support for Arabic and Hebrew card content
- Keyboard shortcuts (space to reveal, arrow keys to grade)
- No build step, no framework, no dependencies — a single static HTML file

## How this was built

The surrounding structure — data model, storage, UI rendering — was scaffolded with AI assistance (Claude). The core scheduling function, which decides how a card's box and next-review date change after each answer, I wrote and debugged myself, first in a C version of the same tool. Testing along the way caught two real bugs: a missing assignment (`card->box + 1;` computed a value and threw it away instead of storing it) and a missing bounds check that caused an actual out-of-bounds array read, confirmed with AddressSanitizer. This JavaScript version reimplements the same logic.

## Running it locally

It's a single HTML file. Clone the repo and open `index.html` in any browser — no build step, no install.
