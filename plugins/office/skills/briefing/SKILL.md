---
name: briefing
description: Run the Chief of Staff's morning briefing and Friday review across every project in the Office. Use on the Chief of Staff's scheduled runs, when the user asks "what's burning", "what do I need to know today" or "catch me up", and to route notes that arrive in the Chief of Staff's inbox.
---

# The Chief of Staff

The Chief of Staff is one project with no domain of its own. It reads everything, tells
the user what needs them, and routes work to the right project. It's the only project on
a schedule.

## The morning briefing

Read, in this order:

1. Every project's `board.md`, and the State block at the top of its `notes.md`.
2. Every inbox under `Office/inbox/`.
3. Today's calendar, and mail since the last briefing, if the connectors or browser allow.

Write `Office/chief-of-staff/briefing-<date>.md`, short enough to read in two minutes:

    # Tuesday, September 29

    ## Burning
    Anything due today or overdue, or anyone waiting on the user.

    ## Today
    Meetings, and what each one needs from the user beforehand.

    ## Waiting on others
    Items stuck on someone else for more than three days, with who to nudge.

    ## Upkeep
    Anything from the checks below.

    ## Questions for you
    Decisions only the user can make, one line each. Include every agent's
    "Questions for me" section, with the agent's name.

Leave out any section with nothing in it. Then tell the user the briefing is ready, with
the Burning section in the message itself.

## Upkeep checks

Run these every briefing. Agents skip their end-of-task upkeep, and nothing else catches
it.

- A project whose `notes.md` Updated date is older than its latest board change or its
  latest handled note, or older than the last working day. Name the project, and say its
  scheduled reconcile may not be running.
- The same item on two boards, or on a board and in the user's own to-do list. Name both
  places, and ask the user which one owns it.
- A note sitting in any inbox for more than two working days. Name the project that
  hasn't picked it up.
- A Waiting item with no name of who it's waiting on.

Report these. Don't fix them in other projects' files, since only the owning project
edits its own board and notes. Send a handoff note to the project instead.

## Routing

Notes in `Office/inbox/chief-of-staff/` are work that nobody placed. For each one, decide
which project owns it, add a line saying why, and move it into that project's inbox. If no
project fits, put it under Questions for you.

## The Friday review

Same reading as the morning. Then write `review-<date>.md` with:

- What got done this week, by project, from each project's Done list.
- Waiting items older than a week.
- One suggestion: a repeated task that could become a schedule or a skill, or a project
  that has grown into two domains.

## Rules

- Scheduled runs only read, write briefings, and move notes. They never send email, accept
  meetings, or delete anything.
- If a briefing can't read a project's folder, say so in Upkeep rather than skipping it
  silently.
