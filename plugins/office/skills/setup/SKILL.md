---
name: setup
description: Set up the user's Office, run by the Chief of Staff. Use when the user pastes the onboarding block into a new Chief of Staff project, says "set up my office", or says "next" during setup. Interviews the user, creates the Office folder, then hands out one project at a time, each with a block the user pastes into that project's first chat so the project sets itself up from inside.
---

# Setting up the Office

The Chief of Staff runs setup. The user created it as a Cowork project on an empty folder,
and that folder becomes the Office folder. From here the user talks only to the Chief of
Staff, and goes into another project only to create it and paste one block.

You can create folders and files, but you can't create Cowork projects or scheduled tasks,
or change the user's settings. For those, give one short instruction and wait.

If the user's message doesn't make you the Chief of Staff, and your project instructions
don't either, stop and tell the user: "Create a new Cowork project called Chief of Staff on
an empty folder, and paste the onboarding block into its first chat."

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
user clicks Schedule. Ask them to confirm it shows on the Scheduled tasks page.

`office.md` records the schedule on its Schedule line, which the reconcile skill and the
Chief of Staff's stale check read. If the user picks other times, write those instead,
such as `Schedule: daily at 7am, 10am, 1pm, 4pm and 7pm`.

## 1. The Chief of Staff's instructions and schedule

Give the user this block to paste into this project's instructions field:

    You're my Chief of Staff. The Office folder is this project's folder. Use the office
    skill for everything. You run setup and checkup, route notes nobody placed, and
    flag agents that fall behind.

Then propose the Chief of Staff's scheduled reconcile, with the prompt "Run the scheduled
reconcile for the Chief of Staff in my Office. The Office folder is <path>. Use the
Office plugin's office and reconcile skills." Until step 3 writes `office.md`, its runs
stop without writing anything.

Wait until the user confirms both, then start the interview.

## 2. Interview

Ask one question at a time:

1. Their name, role, company and time zone, and who they mostly deal with.
2. The areas their work splits into. Suggest two to four to start. One agent can cover
   several related topics in its area, such as Vendors or Marketing.
3. Existing Cowork projects they want in the Office. For each, which area it belongs to.
   Projects that are only topics can fold into one agent, or stay outside the Office.
4. Whether they'd like person names for the agents, such as Jeff for Vendors. If yes,
   agree a name for each, and check it doesn't match a real contact.
5. Whether their employer has rules about AI tools and company data. If yes, keep company
   data out until they've checked.

Pick each agent's folder name yourself: lowercase, with hyphens for spaces, such as
`vendors` or `customer-success`. Then confirm the plan in one short list: each agent's
name if any, its area, its folder, and whether it's new or an existing project.

## 3. Create the Office

In this project's folder, create:

    README.md                   plain words for the user: what this folder is
    office.md                   the plan, from the template below
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

    ## Agents
    | Name | Area | Folder | Project |
    |---|---|---|---|
    | Chief of Staff | none | chief-of-staff/ | Chief of Staff |
    | Jeff | Vendors | vendors/ | Jeff (Vendors) |
    | Marketing | Marketing | marketing/ | Marketing (own folder) |

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
- `Time zone` is the user's. Every Updated stamp and every Schedule hour uses it.
- `Checks` lists the Chief of Staff's optional checks: `meetings`, `Slack`, `mail`, or
  `none`. Ask about them in step 7, once every agent is set up.
- `Rules` holds rules for every agent, from the user or a retro. Every agent reads it at
  the start of every task.
- Add the Chief of Staff's row now. Add every other agent's row when its project checks
  in, never before.

## 4. Global instructions

Give the user this text in one block, and tell them where it goes: in the desktop app,
open Settings and look for Global instructions under Cowork, or Instructions for Claude
under General. If neither is there, ask them to describe the screen and find the field
with them.

    I'm <name>, <role> at <company>.
    My Office folder is at <path>. When a task touches my work, use the office skill.
    Never send email, accept or change meetings, delete files or spend money without
    asking me first.

## 5. One project at a time

Every new agent, now or later, follows the same flow: the user creates a project, pastes
one block into its first chat, and does what that project tells them.

Each agent's instructions follow this block. Fill it in and hand it over inside the
project block:

    You're <Name>, the <Area> agent in my Office. The Office folder is <path>. Your
    folder in it is <folder>/ and your inbox is inbox/<folder>/. Use the office skill
    for everything. Your area: <two lines on what you cover and what you don't>.

For each agent in the plan, in order:

**A new project.** Tell the user, in two lines:

    Create a project called "<Name> (<Area>)" with "Use an existing folder", and pick
    the Office folder: <path>. Then paste this into its first chat:

Then the project block, in one copyable block:

    You're <Name>, the <Area> agent in my Office. The Office folder is this project's
    folder. Your folder name is <folder>. Use the office skill for everything.
    Your area: <two lines on what this agent covers and what it doesn't>.
    Set yourself up now:
    1. Give me this block to paste into this project's instructions field:
       <the agent's instructions block, filled in>
    2. Propose one scheduled task named "Scheduled reconcile": hourly, approval mode
       "Automatically approve", prompt: "Run the scheduled reconcile for <Name> (<Area>)
       in my Office. The Office folder is <path>. Use the Office plugin's office and
       reconcile skills." I click Schedule. The form has no time window. The skill stops
       itself outside the Schedule hours. If you can't propose it, tell me the clicks.
    3. Create <folder>/board.md, <folder>/notes.md with the State, Done and Questions
       for me sections, <folder>/reference.md, and inbox/<folder>/done/.
    4. Drop a note in inbox/chief-of-staff/ saying you're set up and what you own.
    5. Tell me to go back to the Chief of Staff and say "next".

**An existing project.** The project keeps its own folder, so it needs the Office folder
added as context. Tell the user:

    Open your "<existing name>" project, add the Office folder (<path>) under its
    Context, and rename it "<Name> (<Area>)" if you like. Then paste this into a new
    chat in it:

Then the same block, with these changes: "The Office folder is at <path>" in place of
"this project's folder", step 3 starts "Inside the Office folder at <path>, create", and
step 3 adds "Fill the board and notes from what you already know about this project."

**Then wait.** When the user says "next", read `inbox/chief-of-staff/` and its `done/`
folder. If the project's check-in note is in either, and its board and notes exist, move
the note to `done/` if it isn't there yet, record the agent in `office.md` if it isn't
there yet, and go to the next agent. If not, say what's missing and help the user finish
it.

## 6. Voice

Offer to build the voice profile now or at the next session. When the user says now, run
the voice skill, so drafts sound like them.

## 7. Finish

Offer the Chief of Staff's optional checks, one question: "On each scheduled run, should
I also look at your meetings, Slack or mail, and tell you what needs you?" They need the
matching connectors. Write the answer on the `Checks:` line in `office.md`. The default is
none. The Chief of Staff's scheduled task stays on "Automatically approve", since the
checks only read.

Then run a readout, so the user sees every agent in one place. Then run the checkup skill,
and fix anything it finds.

## Adding an agent later

The user says "add an agent" to the Chief of Staff. Ask interview questions 2 and 4 for
the new area, pick its folder name, and run step 5 for that one agent. Its row enters
`office.md` when it checks in.

## Splitting an agent

The user says "split <Name>", or an agent's board has grown two areas. Agree the new area,
name and folder name with the user, and run step 5 for the new agent. Its row enters
`office.md` when it checks in.

Then send the old agent a handoff note that lists the items moving to the new agent. On
its next reconcile, the old agent sends each item to the new agent's inbox as its own
handoff note and removes it from its board. Give the user a new instructions block for the
old agent, with its narrowed area.
