---
name: checkup
description: Check that the user's Office is set up properly, and change its setup. Use when the user says "check my office", "checkup", "is everything set up", "reconfigure", "I updated Office", or wants to add, split, rename or retire an agent, or change how often reconcile runs. Run in the Chief of Staff. Verifies every agent's files, instructions and schedules, then walks the user through each gap.
---

# Checkup

Run this in the Chief of Staff, after setup and whenever something seems off. It reads
the Office folder, compares it with `office.md`, and fixes gaps with the user one at a
time.

## Check

For every agent in `office.md`, using its Folder column:

- Its folder has `board.md`, `notes.md` and `reference.md`, and `notes.md` opens with a
  State block.
- Its board has `## Now`, `## Next` and `## Waiting` headings.
- Its inbox file `inbox/<folder>.md` exists.
- Its State Updated time is less than a day old. If it's older, its scheduled reconcile
  probably isn't running, or its task has no Office folder.
- Its inbox holds no note older than two working days.

For the Chief of Staff:

- Its own board, notes and inbox file exist.
- Its State Updated time is less than a day old, which shows its scheduled reconcile
  runs.

Then look for folders in the Office that `office.md` doesn't list, and agents listed with
no folder. A line under Planned is an agent still being set up: check that it was handed
out, and skip the other checks for it.

You can't see Cowork's project list, instructions fields or schedules. For those, ask the
user to confirm, one question each, only for agents that look stale:

- "Does <Name>'s project have the Office instructions pasted in?"
- "Does <Name> have its scheduled reconcile, as the Schedule line in `office.md` says?"
  If it still has briefing tasks, or a reconcile task whose prompt doesn't start with
  "Run the scheduled reconcile", the user deletes them.
- "Open Scheduled tasks, open <Name>'s Scheduled reconcile task itself, and check it has
  the Office folder: <path>. If not, edit the task and add it." A folder added to one run
  doesn't carry over, and a project's linked folder doesn't reach its tasks.

## After a plugin update

Older versions of Office leave setup behind that the new skills contradict. On the first
checkup after an update, and whenever the user says "I updated Office":

- **office.md.** If it's missing, write it from the folders and ask the user to confirm
  it. If it lacks the template's headings (User, the Agents table, Settings, Rules,
  Retired), rewrite it to the template in the setup skill, keep every fact, and ask the
  user to confirm. If it has no Schedule line, ask which reconcile times the agents run,
  and add one. If it has no Time zone line, ask for the user's time zone and add one. If
  it has no Checks line, add `Checks: none`.
- **Inboxes.** If `office.md` has no `Inbox: one file per agent` line, the inboxes are
  folders of note files. For each agent, create `inbox/<folder>.md` with its heading, and
  copy in every note still waiting in `inbox/<folder>/` (the files outside `done/`), one
  section each, as the handoff skill lays out. Then add `Inbox: one file per agent` to
  Settings. Leave the old folders as they are. No skill reads them again, so they never
  need cleaning up.
- **Old files.** Look for files the current skills never create, such as `setup/`
  recipes, task logs, or briefings. List them. Once the user agrees, replace the contents
  of any file that gives agents instructions with one line: `Retired by checkup on
  <date>. Ignore this file.` Never move or delete it.
- **Instructions fields.** You can't read other projects' instructions. For each agent,
  fill in the agent instructions block from the setup skill's step 5 with its row in
  `office.md`, give it to the user, and ask them to replace the old text. Tell them to
  remove any line that names a skill the plugin no longer has, such as briefing.
- **Scheduled tasks.** Ask the user to delete tasks for retired jobs (morning briefing,
  Friday review) and any reconcile task whose prompt doesn't start with "Run the
  scheduled reconcile". Then propose each missing task with the prompt from the setup
  skill. Ask the user to check that every reconcile task has the Office folder in the
  task's own settings.
- **Your own instructions.** Compare them with the Chief of Staff block in the setup
  skill, and give the user the new block if they differ.

Report these under To fix, like any other gap.

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
- **Split an agent:** the setup skill's "Splitting an agent".
- **Rename an agent:** the user renames the project in the sidebar. Update the name in
  `office.md`, and send the agent a note so it updates its own notes. Its folder keeps
  its name, so nothing moves.
- **Retire an agent:** ask where its open items go. Send each one as a handoff note to
  its new owner, mark the agent retired in `office.md`, and tell the user to delete its
  scheduled reconcile task. Keep its folder.
- **Change reconcile frequency:** one hourly task is the default. For faster pickup, add
  a second hourly task starting at :30. For slower, replace it with daily tasks at set
  times. Update the Schedule line to match. Each run uses part of the user's plan, so
  change one agent at a time and check usage after a day.
