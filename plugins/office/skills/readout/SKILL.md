---
name: readout
description: Give the user the rundown in one fixed format. Use when the user types /readout or says "readout", "what's the rundown", "where do things stand", "what's on the board" or "what needs me". In an agent's project it covers that agent. In the Chief of Staff it covers the whole Office, grouped by what the user has to do. It only reads and changes nothing.
---

# Readout

The readout is the one answer to "where do things stand". It always has the same sections
in the same order, so the user learns where to look. It changes nothing. Cleanup is the
reconcile skill.

Check each claim against the files before you repeat it. A board line that says "waiting
on Dana" is a claim until the notes or inbox back it up.

## In an agent's project

Read your `board.md`, your `notes.md` (State and Questions for me) and your inbox. Answer
in 10 lines at most, in this order:

    Needs you
    - What's blocked on the user, and every Questions for me item, one line each.

    Now
    - The current item.

    Next
    - The top three items.

    Waiting on others
    - Who, and for what, since when.

    Health
    - State Updated time, and any inbox note older than two working days.

## In the Chief of Staff

Read every agent's board, State, Questions for me and inbox, and your own. Group the
answer by what the user has to do, never by agent:

    Due soon
    - Anything due today, overdue, or due in the next two days, with the date and agent.

    Quick yes or no
    - Questions the user can answer in one word, with the agent that asked.

    Decisions
    - Questions that need thought, grouped by agent.

    Across agents
    - Work one agent waits on from another, and which agent it sits with. Flag any two
      agents waiting on each other.

    Health
    - Agents with stale State, old inbox notes, Waiting items with no name, or items on
      two boards. Name any agent whose folder you couldn't read.

- Leave out any section with nothing in it. Say "Nothing needs you" if every section is
  empty except Health.
- Plain words. Name agents and people, never file names.
- Keep it short enough to read in one minute. The user asks for detail on one item if
  they want it.

## After the readout

If Health has entries, end with one line: "Say reconcile in <agent> to clean that up."
