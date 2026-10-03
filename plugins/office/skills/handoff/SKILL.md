---
name: handoff
description: Pass work from this project to another project in the Office, or process notes other projects sent here. Use when the user says "tell <project> to...", "hand this to...", "send this to...", when work turns up that belongs to another area, and at the start of every task to read this project's inbox.
---

# Handoffs

Projects can't message each other directly. Each agent has one inbox file,
`Office/inbox/<folder>.md`, using its Folder in the Agents table of `office.md`. A handoff
is a note added to the end of another agent's inbox file. That agent handles it on its
next scheduled reconcile, or sooner if the user opens it.

Agents only add and edit text. Never move, rename or delete a file in the Office: Cowork
asks the user before every delete, so a delete stops the work and hands the user a chore.

## Sending a note

Add a section to the end of `Office/inbox/<their folder>.md`. Leave everything above it
as it is:

    ## 2026-09-29 14:05 ET, from Accounts: Follow up with Acme's new VP of Sales
    Needed: Follow up with Acme's new VP of Sales about the pilot.
    Done when: A meeting is booked, or Acme says no.
    Context: Dana at Acme introduced her on Sep 26. Her email is in the
    Acme thread from that day. She's new, so keep it short.

- The heading carries the stamp, the sender and a short title, so the note can be found
  again.
- Write it for a reader who knows nothing about your conversation. They won't see it.
- One request per note. Two requests are two notes. The Chief of Staff's list of an
  agent's problems is the one exception.
- Name the date anything is due, and where to find the detail.
- If the inbox file is missing, create it with the heading `# Inbox: <their name>`.
- Then tell the user: "I've passed that to Prospecting."

If you don't know which agent should take it, send it to `inbox/chief-of-staff.md` and
the Chief of Staff routes it.

## Receiving a note

At the start of every task, read `Office/inbox/<your folder>.md`. For each note:

1. Do it now, or add it to your board.
2. Add one line to the Done section of your `notes.md`:
   `- 2026-09-29 14:05 ET: from Accounts, "Follow up with Acme's new VP": added to board`.
3. Edit the note's section out of your inbox file by replacing only that section's exact
   text with nothing. Never rewrite the whole file from a copy you read earlier: another
   agent may have added a note since. Keep the `# Inbox` heading and every other note.
4. Re-read the inbox file, and handle any note that arrived meanwhile.

The Done line is the record that the note was handled. An empty inbox file means
nothing is waiting.

If a note asks for something outside your area or you can't do it, write the reason in
the Done line and add the note to the Chief of Staff's inbox before you remove it.

## Never

- Never edit another agent's board or notes to "save a step". Send the note.
- Never change another agent's notes in its inbox file. Add yours at the end. Only the
  inbox's owner removes notes.
- Never move, rename or delete an inbox file or any other file.
