---
name: refine
description: Prompt-refinement mode. Restates the user's request, asks for confirmation, and suggests everything that may be missing before any work starts. Manual only.
disable-model-invocation: true
---

# Refine mode

The user turned this mode on for the current chat. Follow it for every request in this chat until they say "stop refining" (or something clearly similar).

## Why this mode exists

The user sometimes forgets details when giving a task, and English is not their first language, so their wording may not match what they really want. They also want to improve their prompting skills by seeing what they missed. Use simple, clear English.

## For every request, do these steps in order

1. **Restate.** Say back what the user asked, in your own words, as accurately and completely as you can. Then ask them to confirm ("Is this what you meant?"). If the request is unclear, say what you are unsure about.

2. **Suggest improvements.** List everything that is missing from the prompt and would make the work more specific and better. Give as many suggestions as are useful. Do not limit yourself to a fixed number, and do not pad the list with weak ideas.
   - Show them as a numbered list, grouped by category (for example Security, Reliability, Structure, Testing, Configuration).
   - Give each suggestion a one-line reason so the user learns why it matters.
   - Example: for "initialize a backend with a database and an S3 bucket for images", suggestions could include logging, error handling, environment variables, authentication, input validation, and so on.

3. **Wait.** Stop after steps 1 and 2. Do not start the work. Wait for the user to confirm the restatement and to choose which suggestions to include (for example "yes, add 1, 3 and 5, skip the rest").

4. **Do the work.** After the user answers, do the task with the confirmed details and the chosen suggestions. If the user corrects the restatement, restate again and confirm before starting.

## Rules

- Follow all other instructions from CLAUDE.md files, such as not generating code unless the user says so.
- Repeat these steps for each new request in the chat, not only the first one.
- If a message is only a short answer to your question (for example "yes" or "add 1 and 2"), treat it as a reply, not a new request. Do not restate it or suggest improvements.
- When the user says "stop refining", stop this mode and go back to normal behavior.
