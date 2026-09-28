---
name: voice
description: Write emails and messages the way the user writes them. Use for every email, reply, message or note the user will send under their own name, and when the user says "learn how I write" or "update my voice". Builds a voice profile from samples of the user's real sent mail, then drafts in that voice. It only drafts, and the user sends.
---

# The user's voice

People can tell when an email was written by AI, and it costs the sender credibility.
This skill makes drafts read like the user wrote them.

## Build the profile

Do this once at setup, and again when the user says a draft doesn't sound like them.

1. Collect 20 to 40 emails the user wrote and sent, into `Office/voice/samples/`, one file
   each. Mix the recipients: clients, colleagues, their boss, vendors, friends. Use the
   mail connector if there is one. Otherwise ask the user to open their Sent folder in
   the browser so you can copy them. Skip anything confidential.
2. Read all of them. Write `Office/voice/profile.md` with what you actually see, and
   quote real examples for every point:
   - How they open and close, by type of recipient.
   - Sentence length, and how long their emails usually run.
   - Formality: contractions, slang, exclamation marks, emoji, first names.
   - Words and phrases they use often.
   - Words and phrases they never use.
   - How they ask for things, say no, apologize, and follow up.
   - Formatting: bullets or prose, greetings on their own line, sign-off style.
3. Show the user three things from the profile and ask if they're right.

## Draft in the voice

1. Read `Office/voice/profile.md` and the samples closest to this recipient.
2. Match the recipient type. An email to a client and one to a colleague sound different,
   and the profile says how.
3. Draft. Keep it as short as the user's own emails to that kind of person.
4. Check the draft against the list below, and against the words the user never uses.
5. Put facts you don't know in brackets, like [date of the call]. Never invent them.
6. Show the draft. The user edits and sends it. Never send it yourself.

When the user edits a draft before sending, the edit shows how they really write. Ask
whether to save the final version to `samples/`.

## Things that make an email sound like AI

Remove every one of these unless the profile shows the user writes that way.

- Opening with "I hope this email finds you well" or "I wanted to reach out".
- Restating what the other person said before answering it.
- A sentence that only repeats the one before it in other words: "That's why timing
  matters here."
- Saying something is important instead of saying what happens if it goes wrong: "It's
  worth noting that", "This is key".
- Puffed-up words: "delve", "leverage", "seamless", "robust", "crucial", "navigate",
  "foster", "pivotal", "comprehensive", "showcase", "landscape".
- "Serves as" or "functions as" where "is" would do.
- Lists of exactly three things, added for rhythm.
- Counting a list before giving it: "Two things to flag".
- "It's not just X, it's Y", or "X, not Y" when nobody said Y.
- Stacked hedges: "generally", "typically", "it could be argued". One hedge that says
  what's uncertain is fine.
- Bold labels at the start of every bullet.
- A closing line that sums up the email: "Looking forward to hearing your thoughts on
  the above."
- Every paragraph, or every bullet, the same length.
- Em dashes, if the user doesn't use them. Most people don't.
- More enthusiasm than the user ever shows.
