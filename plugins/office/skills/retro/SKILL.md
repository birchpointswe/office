---
name: retro
description: Run a retrospective in the Chief of Staff after a big piece of work ends or a rough week, and turn each lesson into a lasting change. Use when the user says "retro", "retrospective", "what did we learn", "why does this keep happening", or when a large project or a run of problems wraps up. Finds what went wrong and right, the shared causes, and routes each fix to the file or agent that owns it. Also checks whether the last retro's changes stuck.
---

# Retro

A retro that ends as a summary in chat is wasted. The result is changes: a rule, a fact,
new instructions text, or a board item, each written where the next task reads it.

Run it in the Chief of Staff. It reads every agent's files, so it sees problems that cross
agents.

## Gather

Pick the stretch with the user: one project, or the last week or two. Then read, for every
agent involved:

- the Done and Questions for me sections of `notes.md`, and the topic notes
- `board.md`, especially items that sat in Waiting or Now for a long time
- `inbox/<folder>/done/`, for handoffs that bounced or took days
- `reference.md`, for facts that turned out wrong

Ask the user one question: "What was annoying or went wrong, in your own words?" Their
answer counts more than anything in the files.

List what went wrong, in order: redone work, a note that went to the wrong agent, a draft
the user rewrote, a question asked twice, a date missed, a fact that was wrong. Also list
what went right because of how the Office works, so the fixes don't break it.

## Find the causes

- Group the problems. Several often share one cause, such as an agent whose area is too
  broad, a rule nobody wrote down, or a fact kept only in chat.
- For each cause, name the smallest change that would have prevented it.
- Drop one-offs that can't happen again.

## Check the last retro

If `chief-of-staff/retros/` doesn't exist, this is the first retro: create it and skip
this section. Otherwise open it and read the latest one. For each change it listed, check
the file it names. Say which changes landed and which didn't, and whether each missed one
is still needed. A change that didn't land goes back on the list.

## Route each change

| Kind of change | Where it goes | Who writes it |
|---|---|---|
| A rule for every agent | `office.md`, under Rules | the Chief of Staff |
| A rule for one agent | a handoff note to that agent, which adds it to its `notes.md` | that agent |
| New instructions for a project | a block for the user to paste into that project's instructions field | the user |
| A permanent fact | a handoff note to the owning agent, for its `reference.md` | that agent |
| Work to do | the owning agent's board, through a handoff note | that agent |
| An agent's area split or merged | the setup skill's "Splitting an agent", or checkup | the user, guided |
| A change to how the user works | tell the user plainly | the user |

Follow the one-writer rule. The Chief of Staff edits only its own files and `office.md`.

## Report

Write `chief-of-staff/retros/<date>.md`:

    # Retro <date>: <what it covered>

    ## Changes
    - <change>: <where it went>, <status: done, sent, or waiting on the user>

    ## Went well, keep doing
    - <item>

    ## Last retro
    - <change>: landed, or missed and why

Then give the user a short summary in chat: the few changes that matter most, and anything
waiting on them, such as an instructions block to paste. Send the handoff notes before you
finish, so the retro's changes are already on their way.
