# Refine: notes for using it with other agents

The `refine` skill was written for Claude Code. This file explains which parts are specific to Claude, and gives a plain version you can give to any other agent.

## Parts that are specific to Claude Code

| Part | Where | What it does in Claude | What to do for another agent |
| --- | --- | --- | --- |
| `disable-model-invocation: true` | Header at the top of `SKILL.md` | Makes the skill manual only, so Claude never starts it by itself | Remove it, or replace it with that agent's own "manual only" setting if it has one |
| `name` and `description` | Header at the top of `SKILL.md` | Tells Claude the skill's name and what it is for | Keep them if the agent uses the same format, or change them to that agent's format |
| The `/refine` command | How you turn it on | Claude Code creates a slash command from the skill's name | Ask the agent how it turns on a skill or custom instruction, and use that way instead |
| The `SKILL.md` file name and folder | `refine\SKILL.md` | Claude Code looks for this file inside a skills folder | Other agents may want a different file name or folder |
| The line about `CLAUDE.md` files | Under "Rules" | Tells Claude to keep following your project rules | Change it to that agent's own rules file, for example its project instructions file |

## How to move it to another agent

Give the agent the `SKILL.md` file (or the plain version below) and say: "Read this skill and adapt it to your own format, then add it to your skill or instruction list." The agent should change the Claude-specific parts from the table above.

## Plain version (no Claude-specific parts)

You can paste this into any agent as a custom instruction. It only works in the chat where you paste it.

> Refine mode is on for this chat. Follow it for every request until I say "stop refining".
>
> I sometimes forget details when I give a task, and English is not my first language. Use simple, clear English.
>
> For every request I give, do these steps in order:
> 1. Say back what I asked, in your own words, and ask "Is this what you meant?". If something is unclear, say what you are unsure about.
> 2. List everything that is missing from my request and would make the work more specific and better. Give as many suggestions as are useful, not a fixed number. Show them as a numbered list grouped by category, with a one-line reason for each.
> 3. Stop and wait. Do not start the work. Wait for me to confirm and to choose which suggestions to include.
> 4. After I answer, do the work with the confirmed details and the chosen suggestions. If I correct your restatement, restate again and confirm before starting.
>
> If my message is only a short answer to your question, treat it as a reply and do not restate it or suggest improvements. When I say "stop refining", go back to normal behavior.
