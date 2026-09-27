---
name: reconcile
description: Make this project's board and notes true again. Use when the user types /reconcile or says "reconcile", "clean up", "tidy the board" or "bring things up to date", and when a readout or briefing flags upkeep for this project. Marks finished work done, captures work that only exists in chat, refreshes the State block, finds duplicates and stale items, and handles the inbox.
---

# Reconcile

A board drifts: work gets finished and never ticked, new work gets agreed in chat and never
written down, and the State block goes stale. Reconcile fixes that for one project. Run it
in the project that needs it.

This project edits only its own board and notes. Anything that belongs to another project
goes there as a handoff note.

## Steps

1. **Inbox.** Handle every note in `Office/inbox/<your domain>/`, as the handoff skill
   says.
2. **Finished work.** For each item on the board, check this project's recent tasks and
   notes. If it looks done, ask the user once, with all such items in one list. Move the
   confirmed ones to the Done section of `notes.md` with today's date.
3. **Work only in chat.** Look through this project's recent tasks for commitments,
   follow-ups and deadlines that never reached the board. List them for the user, and add
   the ones they confirm.
4. **Duplicates.** Compare the board with every other project's board, and with the user's
   own to-do list if they keep one. For each item in two places, ask the user which one
   owns it. Remove it from this board, or send a handoff note asking the other project to
   remove it.
5. **Stale items.** Flag Waiting items with no name or no date, and items nobody touched
   in two weeks. Ask the user: keep, change, or drop.
6. **State.** Rewrite the State block at the top of `notes.md`: goal, next step, what it's
   waiting on, and anything to watch out for. Set Updated to today.
7. **Board.** Set the board's Updated date to today.

## Report

Finish with a short summary in chat:

    Reconciled <Project>
    - Done: items moved to Done
    - Added: items captured from chat
    - Removed or handed off: duplicates and dropped items, and where they went
    - Still open: questions the user didn't answer

## From the Chief of Staff

If the user runs reconcile in the Chief of Staff, it can't edit other projects. Instead,
run the readout's checks across every project, and send each project with problems one
handoff note that lists them. Then tell the user which projects to open and reconcile.
