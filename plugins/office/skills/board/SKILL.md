---
name: board
description: Keep this project's to-do board in the Office. Use when the user adds, finishes, defers or reprioritizes work, asks "what's on my plate" or "what's next", and at the end of every task. Covers the board's three groups, how to word an item, and what never goes on a board.
---

# The board

Each agent has one board at `Office/<folder>/board.md`, using its Folder in `office.md`.
Only this agent edits it.

The board is always this file. It isn't your built-in to-do list, which has no Waiting
group. Read and edit `board.md` directly, and never move Office work into the built-in
list.

    # Accounts board
    Updated: 2026-09-29 14:05 ET

    ## Now
    - Renewal deck for Acme (due Oct 3)

    ## Next
    - Pricing sheet for Beta Corp
    - Quarterly review prep (due Oct 10)

    ## Waiting
    - Signed order form from Beta Corp (waiting on Dana, since Sep 25)

## The groups

- **Now**: work in progress. Keep it to one or two items.
- **Next**: the queue. The first item is what happens next. To change priority, move the
  line.
- **Waiting**: blocked on someone or something. Every Waiting item names who it waits on,
  and since when.

## Items

- One line each: what, in the user's words, plus a due date if there is one.
- Detail goes in `notes.md` under a heading. The board is only the list.
- Permanent facts go in `reference.md`, never on the board.
- When an item is done, delete it and add one line to the Done section of `notes.md`
  with the date. A board shows only what's still open.
- Update the `Updated:` stamp (date and time) whenever you change the board.

## Showing the board

When the user asks what's on their plate, answer in plain words: what's in progress,
what's next, and what's stuck and on whom. Don't paste the file. If the user asks across
all their work, read every project's board and group the answer by project.

## What never goes on a board

- Passwords, account numbers, or other credentials.
- Anything the user asked to keep private.
- Items the user tracks in their own to-do app. Ask which one should own it, and keep it
  in one place only.
