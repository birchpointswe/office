---
name: setup
description: Set up the user's Office, run by the Chief of Staff. Use when the user types /office:setup or pastes the onboarding block into a new Chief of Staff project, says "set up my office", or says "next" during setup. Interviews the user, creates the Office folder, then hands out one project at a time, each with a block the user pastes into that project's first chat so the project sets itself up from inside.
---

# Setting up the Office

The Chief of Staff runs setup. The user created it as a Cowork project on an empty folder,
and that folder becomes the Office folder. From here the user talks only to the Chief of
Staff, and goes into another project only to create it and paste one block.

You can create folders and files, but you can't create Cowork projects or scheduled tasks,
or change the user's settings. For those, give one short instruction and wait.

Before step 1, remind the user in one line to keep this chat on "Automatically approve"
for setup, since it only writes the Office folder. Don't wait for an answer.

`<path>` in every block below is the Office folder as the user describes it, such as
"Office, in my OneDrive", from the `Office folder:` line of `office.md`. Never write a
sandbox path such as `/sessions/...` or `/home/claude/...` into a block or a prompt. The
folder's name is enough when the user doesn't know the full path.

If the user's message doesn't make you the Chief of Staff, and your project instructions
don't either: an empty folder, or `/office:setup`, means a new Chief of Staff, so carry
on. An `office.md` in this project's folder, with no instructions naming you as another
agent, means you're the Chief of Staff and its block isn't pasted yet: carry on, and ask
for the paste in step 7. Otherwise stop and tell the user: "Create a new Cowork project
called Chief of Staff on an empty folder, and type /office:setup in its first chat."

Every agent's setup starts the same way: its instructions, then its scheduled reconcile.
The Chief of Staff goes first.

## The scheduled reconcile

The scheduled reconcile is one task per agent, named "Scheduled reconcile", hourly, with
this prompt filled in:

    Run the scheduled reconcile for <Name> (<Area>) in my Office. The Office folder is
    <path>. Use the Office plugin's office and reconcile skills.

The schedule form has no time window. It offers hourly, daily, weekly, weekdays or
manual. Pick hourly. The reconcile skill does nothing outside the hours on the Schedule
line. Use "Automatically approve", since the run only reads and writes the Office folder.
It's the only scheduled job in the Office, and every agent gets one.

You can only propose a scheduled task: its name, schedule, approval mode and prompt. The
user clicks Schedule. Move on. Checkup asks about any task that looks missing. If this
chat can't propose a task, tell the user: open Scheduled tasks, click New task, then
Create with Claude, and paste the prompt.

`office.md` records the schedule on its Schedule line, which the reconcile skill and the
Chief of Staff's stale check read. If the user picks other times, write those instead,
such as `Schedule: daily at 7am, 10am, 1pm, 4pm and 7pm`.

## 1. The Chief of Staff's instructions and schedule

Give the user this block to paste with Add instructions, on the right of this project:

    You're my Chief of Staff. The Office folder is this project's folder. Use the office
    skill for everything. You run setup and checkup, route notes nobody placed, and
    flag agents that fall behind.

Then propose the Chief of Staff's scheduled reconcile, with the prompt "Run the scheduled
reconcile for the Chief of Staff in my Office. The Office folder is this project's folder.
Use the Office plugin's office and reconcile skills." Until step 3 writes `office.md`, its
runs stop without writing anything.

Then start the interview at once. The user pastes and clicks while you ask. Step 7 checks
that both are done.

## 2. Interview

Ask one question at a time:

1. Their name, role, company and time zone, who they mostly deal with, and where the
   Office folder sits on their computer, as they'd say it (for example OneDrive, then
   Office).
2. The areas their work splits into. Suggest two to four to start. One agent can cover
   several related topics in its area, such as Vendors or Marketing.
3. Existing Cowork projects they want in the Office. For each, which area it belongs to.
   Projects that are only topics can fold into one agent, or stay outside the Office.
4. Whether their employer has rules about AI tools and company data. Ask this only if
   question 1 named an employer. If yes, keep company data out until they've checked.

Pick each agent's folder name yourself: lowercase, with hyphens for spaces, such as
`vendors` or `customer-success`. Suggest a person name for each agent that doesn't match a
real contact, and say they can drop the names. Then confirm the plan in one short list:
each agent's name, its area, its folder, and whether it's new or an existing project.

## 3. Create the Office

In this project's folder, create:

    README.md                   plain words for the user: what this folder is
    office.md                   the plan, from the template below
    CLAUDE.md                   the Office-wide instructions, from step 4
    chief-of-staff/board.md
    chief-of-staff/notes.md     with the State, Done and Questions for me sections
    chief-of-staff/reference.md
    inbox/chief-of-staff/done/
    voice/samples/

Write the Chief of Staff's own board and notes now.

`office.md` follows this template. Every skill reads it, so keep the headings and line
names exactly:

    # Office

    ## User
    - Name: Dana Lee
    - Role: Account executive, Acme Corp
    - Works mostly with: customers, partners, the sales team
    - Company data rules: none known
    - Office folder: Office, in OneDrive

    ## Agents
    | Name | Area | Folder | Project |
    |---|---|---|---|
    | Chief of Staff | none | chief-of-staff/ | Chief of Staff |
    | Jeff | Vendors | vendors/ | Jeff (Vendors) |

    ## Planned
    - Marketing, Marketing, marketing/, Marketing, own folder

    ## Settings
    Schedule: hourly, 7am to 7pm
    Time zone: Eastern (New York)
    Checks: none

    ## Rules
    - none yet

    ## Retired
    - 2026-10-15: Events, folded into Marketing

- The Folder column is relative to the Office folder. Every agent's files and inbox use
  it: `<folder>/board.md` and `inbox/<folder>/`. Never derive a path from a name.
- For an existing project that keeps its own folder, add "own folder" after its name in
  the Project column.
- `Planned` lists the agents from the interview that haven't checked in, one line each:
  name, area, folder, project, new or own folder. Write it in step 3. Move a line into the
  Agents table when the agent checks in. The stale check and checkup read only the Agents
  table.
- `Time zone` is the user's. Every Updated stamp and every Schedule hour uses it.
- `Checks` lists the Chief of Staff's optional checks: `meetings`, `Slack`, `mail`, or
  `none`. Step 7 sets it.
- `Rules` holds rules for every agent, from the user or a retro. Every agent reads it at
  the start of every task.
- Add the Chief of Staff's row now. Add every other agent's row when its project checks
  in, never before.
- At step 3 the Agents table holds only the Chief of Staff, Planned holds every other
  agent, and Retired is empty. Jeff, Marketing and Events above are examples.

## 4. Office-wide instructions

Write `CLAUDE.md` in the Office folder:

    When a task touches my work, use the office skill. Never send email, accept or
    change meetings, delete files or spend money without asking me first.

Claude can write folder instructions itself. They load from the second message of a
session, so every project's own instructions still carry its identity.

## 5. One project at a time

Every new agent, now or later, follows the same flow: the user creates a project, pastes
its instructions, pastes one block into its first chat, and does what that project tells
them.

Each agent's instructions follow this block. Fill it in:

    You're <Name>, the <Area> agent in my Office. The Office folder is <path>. Your
    folder in it is <folder>/ and your inbox is inbox/<folder>/. Use the office skill
    for everything. Your area: <two lines on what you cover and what you don't>.

For each line under Planned, in order:

**A new project.** Tell the user:

    Create a project and type only its name, "<Name> (<Area>)". Leave the description
    empty: it isn't the instructions. In the new project, on the right:
    - Click Add instructions and paste this:

      <the agent's instructions block, filled in>

    - Click Add context, then Link a local folder, and pick the Office folder: <path>.

    Then in its first chat, set approval to Automatically approve, and paste this:

Then the project block, in one copyable block:

    You're <Name>, the <Area> agent in my Office. The Office folder is this project's
    folder. Your folder name is <folder>. Use the office skill for everything.
    Your area: <two lines on what this agent covers and what it doesn't>.
    Set yourself up now:
    1. If your instructions don't already name you as <Name>, give me this block to
       paste with Add instructions, on the right of this project:
       <the agent's instructions block, filled in>
    2. Propose one scheduled task named "Scheduled reconcile": hourly, approval mode
       "Automatically approve", prompt: "Run the scheduled reconcile for <Name> (<Area>)
       in my Office. The Office folder is <path>. Use the Office plugin's office and
       reconcile skills." I click Schedule. The form has no time window. The skill stops
       itself outside the Schedule hours. If you can't propose it, tell me the clicks.
    3. Create <folder>/board.md, <folder>/notes.md with the State, Done and Questions
       for me sections, <folder>/reference.md, and inbox/<folder>/done/.
    4. Drop a note in inbox/chief-of-staff/ with your name, area, folder and project
       name, and what you own, so the Chief of Staff can add your row.
    5. Tell me to go back to the Chief of Staff and say "next".

**An existing project.** The project keeps its own folder, so it needs the Office folder
added as context. Tell the user:

    Open your "<existing name>" project, and rename it "<Name> (<Area>)" if you like.
    On the right:
    - Click Add context, then Link a local folder, and pick the Office folder: <path>.
    - Click Add instructions (or edit them) and add this:

      <the agent's instructions block, filled in>

    Then in a new chat, set approval to Automatically approve, and paste this:

Then the same block, with these changes: "The Office folder is at <path>" in place of
"this project's folder", step 3 starts "Inside the Office folder at <path>, create", and
step 3 adds "Fill the board and notes from what you already know about this project."

**Then wait.** When the user says "next", read `inbox/chief-of-staff/` and its `done/`
folder. If the project's check-in note is in either, and its board and notes exist, move
the note to `done/` if it isn't there yet, move its line from Planned to the Agents table
in `office.md` if it isn't there yet, and go to the next line under Planned. If not, say
what's missing and help the user finish it.

## 6. Voice

Step 7 offers it. If the user wants it now, ask them to switch this chat to Manually
approve first, since voice reads their mail. Then run the voice skill, so drafts sound
like them.

## 7. Finish

Ask these in one message: is the Chief of Staff's instructions block pasted and its task
scheduled, do they want the voice profile now or next time, and do they want the global
instructions block for chats outside the Office (most skip it). If they want voice now,
run step 6 after the readout and checkup below.

Leave `Checks: none` unless the interview mentioned meetings, Slack or mail. If it did,
ask one question: "On each scheduled run, should I also look at your meetings, Slack or
mail, and tell you what needs you?" They need the matching connectors. Write the answer on
the `Checks:` line in `office.md`. The Chief of Staff's scheduled task stays on
"Automatically approve", since the checks only read.

If they want the global instructions block: in the desktop app, open Settings and look for Global instructions under
Cowork, or Instructions for Claude under General. If neither is there, ask them to
describe the screen and find the field with them.

    I'm <name>, <role> at <company>.
    My Office folder is at <path>. When a task touches my work, use the office skill.
    Never send email, accept or change meetings, delete files or spend money without
    asking me first.

Then run a readout, so the user sees every agent in one place. Then run the checkup skill,
and fix anything it finds.

## Adding an agent later

The user says "add an agent" to the Chief of Staff. Ask interview question 2 for the new
area, suggest a name, pick its folder name, add its line under Planned, and run step 5
for that one agent. Its row enters the Agents table when it checks in.

## Splitting an agent

The user says "split <Name>", or an agent's board has grown two areas. Agree the new area,
name and folder name with the user, add its line under Planned, and run step 5 for the new
agent. Its row enters the Agents table when it checks in.

Then send the old agent a handoff note that lists the items moving to the new agent. On
its next reconcile, the old agent sends each item to the new agent's inbox as its own
handoff note and removes it from its board. Give the user a new instructions block for the
old agent, with its narrowed area.
