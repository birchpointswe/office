---
name: handoff
description: Pass work from this project to another project in the Office, or process notes other projects sent here. Use when the user says "tell <project> to...", "hand this to...", "send this to...", when work turns up that belongs to another area, and at the start of every task to read this project's inbox.
---

# Handoffs

Projects can't message each other directly. A handoff is a note file dropped in another
project's inbox folder. That project handles it on its next scheduled reconcile, or sooner
if the user opens it.

## Sending a note

Look up their folder in the Agents table of `office.md`. Write one file per handoff at
`Office/inbox/<their folder>/<date>-<short-title>.md`:

    To: Prospecting
    From: Accounts
    Date: 2026-09-29
    Needed: Follow up with Acme's new VP of Sales about the pilot.
    Done when: A meeting is booked, or Acme says no.
    Context: Dana at Acme introduced her on Sep 26. Her email is in the
    Acme thread from that day. She's new, so keep it short.

- Write it for a reader who knows nothing about your conversation. They won't see it.
- One request per note. Two requests are two notes. The Chief of Staff's list of an
  agent's problems is the one exception.
- Name the date anything is due, and where to find the detail.
- Then tell the user: "I've passed that to Prospecting."

If you don't know which project should take it, send it to `inbox/chief-of-staff/` and
the Chief of Staff routes it.

## Receiving a note

At the start of every task, read every file in `Office/inbox/<your folder>/`:

1. Do it now, or add it to your board.
2. Add a line at the bottom: `Outcome: <what you did>, <date>`.
3. Move the file to `inbox/<your folder>/done/`.

If a note asks for something outside your area or you can't do it, add the reason as
the Outcome and send it on to the Chief of Staff.

## Never

- Never edit another project's board or notes to "save a step". Send the note.
- Never delete a note. Moving it to `done/` is the record that it was handled.
