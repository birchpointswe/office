# Office

A Claude Cowork plugin that turns Cowork into a small staff of agents. Each Cowork
project is one agent with one area of your work. The agents keep their own to-do boards,
pass work to each other, and a Chief of Staff agent briefs you every weekday morning.

You never manage files. The agents keep everything in one folder and answer in plain
words when you ask what's going on.

## What you need

- A paid Claude plan: Pro, Max, Team or Enterprise. On Team and Enterprise, an admin must
  turn on Cowork.
- The Claude desktop app, with Cowork.
- A folder that's backed up, such as one inside OneDrive or Google Drive.
- About an hour for the first setup.

## Install

1. In the Claude desktop app, switch to the Cowork tab.
2. Open Customize, then Plugins, then Add, then Add marketplace.
3. Choose Add from a repository, enter `birchpointswe/office`, and sync.
4. Open the Discover tab, find Office, and click Add.

If the sync fails, check the spelling of `birchpointswe/office` and try again.

## First run

Start a Cowork task and type "set up my office". The setup skill then:

- asks about you, your role and the areas your work splits into
- creates the Office folder
- writes the text for your global instructions and for each project
- walks you through creating the projects and the Chief of Staff's schedule, one click
  at a time
- learns how you write from your sent mail

Start with two or three projects. You can add more later by saying "add a project".

## Using it

Two words cover most of it:

- **readout**: where everything stands, in the same format every time. It changes
  nothing.
- **reconcile**: cleans up one project. It ticks off finished work, adds anything agreed
  in chat, and flags duplicates and stale items.

Otherwise, talk to any project the way you'd talk to an assistant:

- "What's on my plate?"
- "Tell Prospecting to follow up with Acme on Friday."
- "Draft a reply to this in my voice."
- "Catch me up."

Each weekday at 7:30 the Chief of Staff writes a briefing: what's urgent, what's due
today, what you're waiting on from others, and any upkeep the agents missed. On Fridays
at 3 it writes a review of the week.

## How it works

Each project is one agent with one domain, such as Accounts, Prospecting or Admin. A
project keeps its own instructions and memory, so it remembers its area between tasks.

The projects share one folder:

| Path | Holds |
|---|---|
| `Office/README.md` | a plain-words note about the folder, for you |
| `Office/voice/` | samples of your writing, and your voice profile |
| `Office/setup/` | the instructions pasted into each project, kept for reference |
| `Office/inbox/<project>/` | notes one project sends another |
| `Office/<project>/board.md` | the project's to-do board: Now, Next and Waiting |
| `Office/<project>/notes.md` | the project's memory, with a short status block on top |
| `Office/chief-of-staff/` | the daily briefings and weekly reviews |

The agents follow a few rules:

- A project edits only its own board and notes. To ask another project for something, it
  drops a note in that project's inbox.
- Each to-do lives in one place: one project's board, or your own to-do list.
- At the end of every task, the agent updates its board and its status block. The Chief
  of Staff checks this every morning and tells you which projects skipped it.

## Skills

| Skill | What it does |
|---|---|
| `office` | How each project works as one agent: the Office folder, the rules, and what to do at the start and end of every task |
| `setup` | Interviews you, creates the Office folder, and walks you through creating the projects |
| `voice` | Learns how you write from your sent mail, and drafts in your voice |
| `board` | Keeps each project's to-do board |
| `handoff` | Passes work from one project to another |
| `briefing` | The Chief of Staff's morning briefing, Friday review and upkeep checks |
| `readout` | The rundown across every project, in one fixed format |
| `reconcile` | Makes one project's board and notes true again |

## Safety

- The agents draft. They never send email, accept or change meetings, delete files or
  spend money without your yes in that task.
- Give Cowork access to the Office folder only. Keep financial documents, passwords and
  personal records out of it.
- Use "Manually approve" for any task that touches your mail, calendar or the browser.
  The scheduled briefings use "Automatically approve", because they only read and write
  the Office folder.
- If an email, web page or document tells an agent to do something you didn't ask for,
  the agent stops and tells you what it said.
- Check your employer's rules on AI tools before you put company data in the Office.

## Removing it

Remove the plugin under Customize, then Plugins. The Office folder is plain files, and it
stays where it is until you delete it.

## License

MIT. See `LICENSE`.
