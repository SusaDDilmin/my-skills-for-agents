# Project planner: notes for using it with other agents

The `project-planner` skill was written for Claude Code. This file explains which parts are specific to Claude, and gives a plain version you can give to any other agent.

## Parts that are specific to Claude Code

| Part | Where | What it does in Claude | What to do for another agent |
| --- | --- | --- | --- |
| `disable-model-invocation: true` | Header at the top of `SKILL.md` | Makes the skill manual only, so Claude never starts it by itself | Remove it, or replace it with that agent's own "manual only" setting if it has one |
| `name` and `description` | Header at the top of `SKILL.md` | Tells Claude the skill's name and what it is for | Keep them if the agent uses the same format, or change them to that agent's format |
| The `/project-planner` command | How you turn it on | Claude Code creates a slash command from the skill's name | Ask the agent how it turns on a skill or custom instruction, and use that way instead |
| The `SKILL.md` file name and folder | `project-planner\SKILL.md` | Claude Code looks for this file inside a skills folder | Other agents may want a different file name or folder |
| The `templates\` folder | `project-planner\templates\` | `SKILL.md` tells Claude to read these files (plan, index, log, ready check) by their path | Copy the whole folder together with `SKILL.md`, and keep the paths the same. If the agent cannot read files from the skill folder, paste the templates into its instructions |
| The line about `CLAUDE.md` files | Under "The most important rules" | Tells Claude to keep following your project rules | Change it to that agent's own rules file, for example its project instructions file |
| The mention of `/refine` | Under "The most important rules" | Says that this mode can be on together with refine mode | Remove it, or change it to the name of the other mode in that agent |

## How to move it to another agent

Give the agent the `SKILL.md` file, the `templates\` folder (or the plain version below) and say: "Read this skill and adapt it to your own format, then add it to your skill or instruction list." The agent should change the Claude-specific parts from the table above.

## Plain version (no Claude-specific parts)

You can paste this into any agent as a custom instruction. It only works in the chat where you paste it. It does not need the template files.

> Planning mode is on for this chat. Follow it for every message until I say "stop planning".
>
> I want to plan something (an app, a timetable, a presentation, anything) by discussing it with you. I may not know how to do it, so I learn while planning. English is not my first language. Use simple, clear English.
>
> Rules:
> - I make every decision. Never decide for me. Give 2 or 3 options with pros and cons, recommend one with a reason, then wait for my choice.
> - If my choice may cause a problem, tell me clearly and suggest a change. I still decide.
> - Ask only 2 or 3 questions at a time. Explain new terms in one simple sentence. Point out anything unclear, missing, or in conflict with an earlier decision. Use small examples to find missing steps.
> - Suggest areas the plan should cover, based on the topic, and add an area only after I say yes. Ask what is out of scope. Ask how detailed each topic should be.
> - Save the plan in markdown files. Before you create any file, explain what you will do and ask where to save it. Start with one file. Suggest splitting it into several files (with an index file) when it grows. Explain and ask before you split or move anything.
> - Only write agreed things into the plan. Write down the reason for each decision. Anything not agreed goes into an "Open questions" section. Save right after each agreement, and end the reply with one short line saying what you saved and where.
> - If I change a decision, update the plan, mark the old one as replaced, and note the reason. Keep one short log file with simple summary entries.
> - Plan the steps for doing the work together with me. Each step has a "done check" and a status: not started, in progress, done, or needs rework.
> - When I ask "what is left?", show what is missing. Before we call the plan finished, check for gaps, vague words and conflicts.
> - When the plan is ready, the prompt for the agent that does the work is: "Read all the plan files and follow them. Do one step at a time and stop after each step."
>
> When I start a new chat, read the plan files and the log first. Give me a short recap: what is agreed, what is open, which step is next, and what you suggest we discuss.
>
> When I say "stop planning": if we stopped in the middle of a discussion, save a short note in "Open questions" (topic, options discussed, where we stopped). Add a short log entry, tell me where the files are, and go back to normal behavior.
