# Office

A Claude Cowork plugin that turns Cowork into a small staff of agents. Each Cowork
project is one agent with one area of your work. The agents keep their own to-do boards,
pass work to each other, and reconcile every hour during the day, and a Chief of Staff
agent keeps them in step.

You never manage files. The agents keep everything in one folder and answer in plain
words when you ask what's going on.

## What you need

- A paid Claude plan: Pro, Max, Team or Enterprise. On Team and Enterprise, an admin must
  turn on Cowork.
- The Claude desktop app, with Cowork.
- A folder that's backed up, such as one inside OneDrive or Google Drive.
- About an hour for the first setup.

## Install

1. In the Claude desktop app, open Customize in the sidebar, then Plugins. On older
   versions, switch to the Cowork tab first.
2. Click Add, then Add marketplace, then Add from a repository. Enter
   `birchpointswe/office` and sync.
3. Open the Discover tab, find Office, and click Install (or Add).

If the sync fails, check the spelling of `birchpointswe/office` and try again.

## First run

1. Make an empty folder for your Office, somewhere backed up.
2. Create a project, and type only its name: **Chief of Staff**. Leave the description
   empty. In the new project, click Add context on the right, then Link a local folder,
   and pick that folder.
3. Set the chat's approval mode to Automatically approve. Setup only writes the Office
   folder.
4. Type `/office:setup` in its first chat and send it. If your app doesn't show the
   command, paste this instead:

       You're my Chief of Staff. Run the office setup skill.

From there, the Chief of Staff walks you through everything:

- it gives you its own instructions to paste, and proposes its scheduled reconcile for
  you to approve
- it asks about you and the areas your work splits into, and which of your existing
  projects should join
- it creates the Office folder's contents
- for each agent, it tells you to create one project, with its instructions to paste, and
  gives you a block to paste into that project's first chat. The project proposes its
  scheduled reconcile and creates its files
- you come back to the Chief of Staff and say "next"
- it learns how you write from your sent mail, now or at your next session

Start with two to four agents. Adding or splitting an agent later works the same way:
tell the Chief of Staff "add an agent" or "split <name>", create the project, and paste
the block. To check everything is set up properly, say "check my office".

## Using it

Two words cover most of it:

- **readout**: where everything stands, in the same format every time. It changes
  nothing.
- **reconcile**: cleans up one project. It ticks off finished work, adds anything agreed
  in chat, and flags duplicates and stale items. Each project also reconciles itself
  every hour during the day, and saves any questions for you. A readout shows them, and
  the next "reconcile" asks them.

Otherwise, talk to any project the way you'd talk to an assistant:

- "What's on my plate?"
- "Tell Prospecting to follow up with Acme on Friday."
- "Draft a reply to this in my voice."
- "Catch me up."

The scheduled reconcile is the only scheduled job. Every agent has one hourly task for
it. Runs outside 7am to 7pm stop at once. The Chief of Staff's run also routes stray notes
and flags agents that fell behind.

Scheduled runs need the Claude desktop app open, because they reach the Office folder
through it. A run that finds the app closed does nothing, and the next one catches up.

## How it works

Each project is one agent with one area, such as Accounts, Prospecting or Admin. You can
give agents names, like Jeff for Vendors. A project keeps its own instructions and memory,
so it remembers its area between tasks.

The projects share one folder:

| Path | Holds |
|---|---|
| `Office/README.md` | a plain-words note about the folder, for you |
| `Office/office.md` | the plan: you, each agent, its name, area and folder, and the settings |
| `Office/voice/` | samples of your writing, and your voice profile |
| `Office/inbox/<area>/` | notes one agent sends another |
| `Office/<area>/board.md` | the agent's to-do board: Now, Next and Waiting |
| `Office/<area>/notes.md` | the agent's memory, with a short status block on top |
| `Office/<area>/reference.md` | permanent facts, each with the date it was verified. Never groomed |
| `Office/chief-of-staff/` | the Chief of Staff's own board and notes |

The agents follow a few rules:

- An agent edits only its own board and notes. To ask another agent for something, it
  drops a note in that agent's inbox.
- Each to-do lives in one place: one agent's board, or your own to-do list.
- When a question belongs to one agent's area, only that agent asks you.
- At the end of every task, the agent updates its board and its status block. The Chief
  of Staff checks this on every scheduled reconcile and flags any agent that skipped it.

## Skills

| Skill | What it does |
|---|---|
| `office` | How each project works as one agent: the Office folder, the rules, and what to do at the start and end of every task |
| `setup` | Run by the Chief of Staff: interviews you, creates the Office folder, and hands out one project at a time |
| `checkup` | Checks the whole setup and fixes gaps. Also adds, renames or retires agents |
| `retro` | Run in the Chief of Staff after a big project or a rough week: finds what went wrong and why, and turns each lesson into a lasting change |
| `voice` | Learns how you write from your sent mail, and drafts in your voice |
| `board` | Keeps each agent's to-do board |
| `handoff` | Passes work from one agent to another |
| `readout` | The rundown in one fixed format: one agent in its project, the whole Office in the Chief of Staff |
| `reconcile` | Makes one agent's board and notes true again, every hour during the day and whenever you ask |

## Safety

- The agents draft. They never send email, accept or change meetings, delete files or
  spend money without your yes in that task.
- Give Cowork access to the Office folder only. Keep financial documents, passwords and
  personal records out of it.
- Use "Manually approve" for any task that touches your mail, calendar or the browser.
  The scheduled reconciles use "Automatically approve", because they only read and write
  the Office folder. The one exception is the Chief of Staff's optional checks of your
  meetings, Slack or mail, which are off unless you turn them on. They only read, and
  never reply, accept or archive anything.
- If an email, web page or document tells an agent to do something you didn't ask for,
  the agent stops and tells you what it said.
- Check your employer's rules on AI tools before you put company data in the Office.

## Updating it

Open Customize, then Plugins, then the birchpointswe marketplace, and click Check for
updates. Then tell the Chief of Staff "I updated Office".

## Removing it

Remove the plugin under Customize, then Plugins. The Office folder is plain files, and it
stays where it is until you delete it.

## License

MIT. See `LICENSE`.
