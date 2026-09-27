---
name: setup
description: Set up the user's Office for the first time, or add a new project to it. Use when the user says "set up my office", "add a project", "I want an agent for...", or when the office skill finds no Office folder. Interviews the user, creates the folder, and writes the instructions the user pastes into each Cowork project and into global instructions.
---

# Setting up the Office

You can create folders and files, but you can't create Cowork projects or change settings.
So you prepare everything, and the user does a few clicks with you walking them through.
Go one step at a time and wait for the user between steps.

## Interview

Ask, one question at a time:

1. Their name, role and company, and who they mostly deal with.
2. The areas their work splits into. Suggest two or three at most to start: Office works
   best when each project has a clear area, and more can come later.
3. Which tools they use: mail, calendar, documents, CRM. Which ones Claude is connected to,
   and which ones they'd sign into through the browser instead.
4. Whether their employer has rules about AI tools and company data. If yes, keep company
   data out until they've checked.
5. Where they want the Office folder. Recommend a folder inside OneDrive or Google Drive,
   so it's backed up and on every device.

## Create the folder

Create the layout from the office skill: `README.md`, `voice/samples/`, one
`inbox/<domain>/done/` per project plus `inbox/chief-of-staff/done/`, and one folder per
project with a starting `board.md` and `notes.md`.

Write `README.md` for the user in plain words: what the Office is, that the agents keep
these files, and that they never need to open them.

## Write the instructions

Write `Office/setup/<domain>.md` for each project, using this template:

    You're the <Domain> agent for <name>, <role> at <company>.
    Your domain: <two lines on what this project covers and what it doesn't>.
    The Office folder is at <path>. Use the office skill at the start and end of every
    task.
    Draft anything <name> will send in their voice, using the voice skill. Never send it.

Write `Office/setup/chief-of-staff.md` the same way, with this domain line: "You have no
domain of your own. You run the briefing skill, route notes, and check the other
projects' upkeep."

Write `Office/setup/global-instructions.md` with:

    I'm <name>, <role> at <company>.
    My Office folder is at <path>. When a task touches my work, use the office skill.
    Never send email, accept or change meetings, delete files or spend money without
    asking me first.
    Write like me, using the voice skill, and keep it short.

## Walk the user through

1. **Global instructions.** Settings, then Cowork, then Global instructions. Paste the text
   from `global-instructions.md`.
2. **One project per domain.** In the sidebar, click + next to Projects, then "Use an
   existing folder", and pick `Office/<domain>/`. Paste its instructions from
   `setup/<domain>.md`. Then add the whole `Office/` folder under Context.
3. **The Chief of Staff** the same way, on `Office/chief-of-staff/`.
4. **The schedule.** Inside the Chief of Staff project, create a scheduled task:
   - "Morning briefing", weekdays at 7:30 in the morning: "Run the morning briefing."
   - "Friday review", Fridays at 3 in the afternoon: "Run the Friday review."
   Use "Automatically approve" for these, since they only read and write the Office folder.
5. **Inbox checks, optional.** By default a project reads its inbox when the user opens
   it. For a project that should pick up notes on its own, ask how often: every 15
   minutes, every 30, or only when opened. Cowork's shortest schedule is hourly, so make
   one hourly task per slot, each starting at a different minute: four tasks at :00, :15,
   :30 and :45 for every 15 minutes, or two at :00 and :30. Each task's prompt: "Check the
   inbox and handle any notes." Tell the user that every check uses part of their plan's
   allowance, so start with one project.
6. **Voice.** Run the voice skill to build the profile. This is the step users notice most,
   so do it on day one.

Finish by running one real task in one project, start to end, so the user sees a board
update and a note land.

## Adding a project later

Run the same interview question 2 for the new area, then create its folders, its setup
file and its inbox. Walk the user through step 2 for that project only, and add a line to
each existing project's notes saying the new project exists and what it covers.
