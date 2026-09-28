---
name: setup
description: Set up the user's Office, run by the Chief of Staff. Use when the user pastes the onboarding block into a new Chief of Staff project, says "set up my office", or says "next" during setup. Interviews the user, creates the Office folder, then hands out one project at a time, each with a block the user pastes into that project's first chat so the project sets itself up from inside.
---

# Setting up the Office

The Chief of Staff runs setup. The user created it as a Cowork project on an empty folder,
and that folder becomes the Office folder. From here the user talks only to the Chief of
Staff, and goes into another project only to create it and paste one block.

You can create folders and files, but you can't create Cowork projects or change the
user's settings. For those, give one short instruction and wait.

If this chat isn't in a project named Chief of Staff, stop and tell the user: "Create a
new Cowork project called Chief of Staff on an empty folder, and paste the onboarding
block into its first chat."

Every agent's setup starts the same way: its instructions, then its scheduled reconcile.
The Chief of Staff goes first.

The scheduled reconcile runs every 3 hours, at 7am, 10am, 1pm, 4pm and 7pm, every day.
Cowork has no 3-hour cadence, so it's five daily tasks, one per time, each named
"Reconcile <time>" with the prompt "Run the scheduled reconcile." Use "Automatically
approve", since they only read and write the Office folder. It's the only scheduled job
in the Office, and every agent gets the same five.

## 1. The Chief of Staff's instructions and schedule

Give the user this block to paste into this project's instructions field:

    You're my Chief of Staff. The Office folder is this project's folder. Use the office
    skill for everything. You run setup and checkup, route notes nobody placed, and
    flag agents that fall behind.

Then create the five scheduled reconcile tasks in this project, or give the clicks.

Wait until the user confirms both, then start the interview.

## 2. Interview

Ask one question at a time:

1. Their name, role and company, and who they mostly deal with.
2. The areas their work splits into. Suggest two to four to start. An area is a domain,
   such as Vendors or Marketing, and one agent can cover several related topics.
3. Existing Cowork projects they want in the Office. For each, which area it belongs to.
   Projects that are only topics can fold into one agent, or stay outside the Office.
4. Whether they'd like person names for the agents, such as Jeff for Vendors. If yes,
   agree a name for each, and check it doesn't match a real contact.
5. Whether their employer has rules about AI tools and company data. If yes, keep company
   data out until they've checked.

Then confirm the plan in one short list: each agent's name if any, its area, and whether
it's new or an existing project.

## 3. Create the Office

In this project's folder, create:

    README.md                   plain words for the user: what this folder is
    office.md                   the plan from the interview: user, agents, areas, folders
    chief-of-staff/board.md
    chief-of-staff/notes.md     with a State block
    chief-of-staff/reference.md
    inbox/chief-of-staff/done/
    voice/samples/

Write the chief of staff's own board and notes now.

## 4. Global instructions

Give the user this text in one block, and tell them where it goes: in the desktop app,
the menu, then Claude, then Settings, then Account. If their screen differs, ask them to
describe it and find the field with them.

    I'm <name>, <role> at <company>.
    My Office folder is at <path>. When a task touches my work, use the office skill.
    Never send email, accept or change meetings, delete files or spend money without
    asking me first.

## 5. One project at a time

Every new agent, now or later, follows the same flow: the user creates a project, pastes
one block into its first chat, and does what that project tells them. For each agent in
the plan, in order:

**A new project.** Tell the user, in two lines:

    Create a project called "<Name> (<Area>)" with "Use an existing folder", and pick
    the Office folder: <path>. Then paste this into its first chat:

Then the project block, in one copyable block:

    You're <Name>, the <Area> agent in my Office. The Office folder is this project's
    folder. Use the office skill for everything.
    Your area: <two lines on what this agent covers and what it doesn't>.
    Set yourself up now:
    1. Give me one block to paste into this project's instructions field.
    2. Schedule five daily tasks, at 7am, 10am, 1pm, 4pm and 7pm, each with the
       prompt "Run the scheduled reconcile." If you can't create them yourself,
       tell me the clicks.
    3. Create <area>/board.md, <area>/notes.md with a State block,
       <area>/reference.md, and inbox/<area>/done/.
    4. Drop a note in inbox/chief-of-staff/ saying you're set up and what you own.
    5. Tell me to go back to the Chief of Staff and say "next".

**An existing project.** The project keeps its own folder, so it needs the Office folder
added as context. Tell the user:

    Open your "<existing name>" project, add the Office folder (<path>) under its
    Context, and rename it "<Name> (<Area>)" if you like. Then paste this into a new
    chat in it:

Then the same block, with two changes: "The Office folder is at <path>" in place of
"this project's folder", and step 3 adds "Fill the board and notes from what you already
know about this project."

**Then wait.** When the user says "next", read `inbox/chief-of-staff/`. If the project's
note is there and its board and notes exist, move the note to `done/`, record the agent
in `office.md`, and go to the next agent. If not, say what's missing and help the user
finish it.

## 6. Voice

Run the voice skill to build the user's voice profile, so drafts sound like them.

## 7. Finish

Run a readout, so the user sees every agent in one place. Then run the checkup skill,
and fix anything it finds.

## Adding an agent later

The user says "add an agent" to the Chief of Staff. Ask interview questions 2 and 4 for
the new area, add it to `office.md`, and run step 5 for that one agent.

## Splitting an agent

The user says "split <Name>", or an agent's board has grown two areas. Agree the new area
and name with the user, add it to `office.md`, and run step 5 for the new agent. Then
send the old agent a handoff note that lists the items moving to the new agent. The old
agent moves them on its next reconcile, since only an agent edits its own board.
