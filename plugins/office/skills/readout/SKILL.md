---
name: readout
description: Give the user the rundown across their whole Office in one fixed format. Use when the user types /readout or says "readout", "what's the rundown", "where do things stand", "what's on the board" or "what needs me". Reads every project's board, notes and inbox, and changes nothing.
---

# Readout

The readout is the one answer to "where do things stand". It always has the same sections
in the same order, so the user learns where to look. Run it from any project.

## Read

1. Every project's `board.md`, and the State block at the top of its `notes.md`.
2. Every inbox under `Office/inbox/`.
3. The latest briefing in `Office/chief-of-staff/`, if it's from today.

Change nothing. The readout only reads. Cleanup is the reconcile skill.

## Answer in chat, in this format

    Needs you
    - Decisions or replies only the user can give, one line each, with the project.
      Include every agent's "Questions for me" section.

    Due
    - Anything due today, overdue, or due in the next two days, with the date.

    In progress
    - <Project>: the Now items, one line each.

    Blocked
    - Waiting items, with who it's waiting on and since when.

    Upkeep
    - Stale notes, duplicate items, inbox notes older than two working days, and Waiting
      items with no name.

- Leave out any section with nothing in it, and say "Nothing needs you" if the first
  section is empty.
- Plain words. Name projects and people, never file names.
- Keep it short enough to read in one minute. The user asks for detail on one item if they
  want it.
- If a project's folder can't be read, say so under Upkeep.

## After the readout

If Upkeep has entries, end with one line: "Say reconcile in <project> to clean that up."
