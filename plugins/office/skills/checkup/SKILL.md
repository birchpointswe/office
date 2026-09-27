---
name: checkup
description: Check that the user's Office is set up properly, and change its setup. Use when the user says "check my office", "checkup", "is everything set up", "reconfigure", or wants to add, rename or retire an agent, or change how often reconcile runs. Run in the Chief of Staff. Verifies every agent's files, instructions and schedules, then walks the user through each gap.
---

# Checkup

Run this in the Chief of Staff, after setup and whenever something seems off. It reads
the Office folder, compares it with `office.md`, and fixes gaps with the user one at a
time.

## Check

For every agent in `office.md`:

- Its folder has `board.md` and `notes.md`, and `notes.md` opens with a State block.
- Its board has `## Now`, `## Next` and `## Waiting` headings.
- Its inbox folder and `done/` folder exist.
- Its State Updated date is from the last working day. If it's older, its scheduled
  reconcile probably isn't running.
- Its inbox holds no note older than two working days.

For the Chief of Staff:

- Its own board, notes and inbox exist.
- Its State Updated date is from the last working day, which shows its hourly reconcile
  runs.

Then look for folders in the Office that `office.md` doesn't list, and agents listed with
no folder.

You can't see Cowork's project list, instructions fields or schedules. For those, ask the
user to confirm, one question each, only for agents that look stale:

- "Does <Name>'s project have the Office instructions pasted in?"
- "Does <Name> have an hourly scheduled task, 7am to 7pm?"

## Report

    Office checkup
    - OK: agents with no problems
    - To fix: one line per problem, with the agent
    - Can't check: what only the user can see

Then fix each problem with the user, one at a time. A file you can create, create. A
problem inside another agent's files goes to that agent as a handoff note, since only
the owner edits its own board and notes. A click goes to the user as one short
instruction.

## Change the setup

- **Add an agent:** the setup skill's "Adding an agent later".
- **Rename an agent:** the user renames the project in the sidebar. Update the name in
  `office.md`, and send the agent a note so it updates its own notes. Folders keep their
  area names, so nothing moves.
- **Retire an agent:** ask where its open items go. Send each one as a handoff note to
  its new owner, mark the agent retired in `office.md`, and tell the user to delete its
  scheduled task. Keep its folder.
- **Change reconcile frequency:** hourly is the default. For every 30 minutes, the user
  creates a second hourly task starting at :30. For every 15, four tasks at :00, :15,
  :30 and :45. Each run uses part of the user's plan, so change one agent at a time and
  check usage after a day.
