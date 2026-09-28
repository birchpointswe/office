---
name: reconcile
description: Make this agent's board and notes true again. Use when the user types /reconcile or says "reconcile", "clean up", "tidy the board" or "bring things up to date", when a readout flags upkeep for this agent, and on every scheduled reconcile run. Handles the inbox, marks finished work done, captures work that only exists in chat, refreshes the State block, and finds duplicates and stale items.
---

# Reconcile

A board drifts: work gets finished and never ticked, new work gets agreed in chat and never
written down, and the State block goes stale. Reconcile fixes that for one agent. It runs
two ways:

- **Scheduled**, at 7am, 10am, 1pm, 4pm and 7pm every day. Nobody is there to answer, so it asks nothing.
- **By hand**, when the user says "reconcile". The user is there, so it asks, and it
  clears the questions the scheduled runs saved up.

This agent edits only its own board and notes. Anything that belongs to another agent goes
there as a handoff note.

## Scheduled run

1. **Inbox.** Handle every note in your inbox, as the handoff skill says. A note that needs
   the user's answer goes under Questions for me.
2. **Handoffs out.** If work on your board needs another agent, send it a note.
3. **Duplicates and stale items.** Compare your board with the other agents' boards. Add
   anything that needs a decision under Questions for me.
4. **State.** Rewrite the State block, and set Updated to now.

Never mark an item done in a scheduled run, since only the user can confirm it. Never
send email or change anything outside the Office folder.

Keep a section at the end of `notes.md`:

    ## Questions for me
    - 2026-09-29: Is the Acme renewal deck done? It's been in Now for a week.

Every readout shows these.

## By hand

1. **Inbox.** Handle every note in your inbox.
2. **Questions for me.** Ask the saved questions, all in one list. Apply the answers and
   clear the section.
3. **Finished work.** For each item on the board, check your recent tasks and notes. Ask
   about the ones that look done, in one list. Move the confirmed ones to the Done section
   of `notes.md` with today's date.
4. **Work only in chat.** Look through recent tasks for commitments, follow-ups and
   deadlines that never reached the board. List them, and add the ones the user confirms.
5. **Duplicates.** Compare the board with every other agent's board, and with the user's
   own to-do list if they keep one. For each item in two places, ask which one owns it.
   Remove it from your board, or send a note asking the other agent to remove it.
6. **Stale items.** Flag Waiting items with no name or no date, and items nobody touched
   in two weeks. Ask: keep, change, or drop.
7. **State and board.** Rewrite the State block, and set both Updated dates to today.

Finish with a short summary in chat:

    Reconciled <Name>
    - Done: items moved to Done
    - Added: items captured from chat
    - Removed or handed off: duplicates and dropped items, and where they went
    - Still open: questions the user didn't answer

## In the Chief of Staff

The Chief of Staff can't edit other agents. By hand or scheduled, it runs its own steps,
then:

- **Routes** each note in its inbox that nobody placed. It decides which agent owns it,
  adds a line saying why, and moves it into that agent's inbox. If no agent fits, it goes
  under Questions for me.
- **Checks every agent:** notes whose Updated date is more than four hours old during the
  day, inbox notes older than two working days, Waiting items with no name, and items on
  two boards. It sends each agent with problems one handoff note that lists them.
- **By hand only:** tells the user which agents to open.
