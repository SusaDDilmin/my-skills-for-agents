# Project planner: notes for using it with other agents

The `project-planner` skill was written for Claude Code. This file explains which parts are specific to Claude, and gives a plain version you can give to any other agent.

## Parts that are specific to Claude Code

| Part | Where | What it does in Claude | What to do for another agent |
| --- | --- | --- | --- |
| `disable-model-invocation: true` | Header at the top of `SKILL.md` | Makes the skill manual only, so Claude never starts it by itself | Remove it, or replace it with that agent's own "manual only" setting if it has one |
| `name` and `description` | Header at the top of `SKILL.md` | Tells Claude the skill's name and what it is for | Keep them if the agent uses the same format, or change them to that agent's format |
| The `/project-planner` command | How you turn it on | Claude Code creates a slash command from the skill's name | Ask the agent how it turns on a skill or custom instruction, and use that way instead |
| The `SKILL.md` file name and folder | `project-planner\SKILL.md` | Claude Code looks for this file inside a skills folder | Other agents may want a different file name or folder |
| The `templates\` folder | `project-planner\templates\` | `SKILL.md` tells Claude to read these files (plan, index, log, track, ready check) by their path | Copy the whole folder together with `SKILL.md`, and keep the paths the same. If the agent cannot read files from the skill folder, paste the templates into its instructions |
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
> Two principles: a plan is followed exactly, no more and no less, so it must be complete and clear enough to be understood in only one way. A plan can be carried out by me or by an agent.
>
> Rules:
> - I make every decision. Never decide for me. Give 2 or 3 options with pros and cons, recommend one with a reason, then wait for my choice.
> - If my choice may cause a problem, tell me clearly and suggest a change. I still decide.
> - Ask only 2 or 3 questions at a time. Explain new terms in one simple sentence. Point out anything unclear, missing, or in conflict with an earlier decision. Use small examples to find missing steps.
> - Suggest areas the plan should cover, based on the topic, and add an area only after I say yes. Ask what is out of scope. Ask how detailed each topic should be.
> - Save the plan in markdown files. Before you create any file, explain what you will do and ask where to create the `plans` folder. All plans of a project live in `plans/`. Each plan has a folder `plans/plan-<title>/` (suggest the title in lowercase words joined by hyphens, and I confirm it), and each version of the plan is in its own folder inside it: `v1`, `v2`, and so on. `plans/index.md` is a table of all plans (plan title, versions, current version, folder path). Inside a version, start with one file. Suggest splitting it into several files (with a small index file in that version folder) when it grows. Explain and ask before you split or move anything.
> - When you start and plans already exist, give me a short summary of them (more detail for the plan marked current in `plans/index.md`, with how many steps are done, and the "last worked on" date from `plans/track.md`). Then ask me to choose: continue the current version, make a new version of an existing plan, or start a completely new plan. Do not guess. For a completely new plan, guess from the titles which other plans may be related and ask if the new plan should use context from them. Take nothing without my yes, and note where carried parts came from.
> - A new version is a self-contained plan in a new version folder, marked current in `plans/index.md`. Never change the old version. Read all old plan files except the logs, and read the old steps only to see which are done. Write new steps fresh. The new plan has a "Previous plans" section (which plan number it is in the chain, which plans it builds on, what it is for) and a "Starting point (what already exists)" section with only the confirmed, relevant facts. In its "Open questions", add first the goal question (update what is built, start over, or something else), then the list of unfinished old steps (name and status only) with the question: reuse, change or drop? Both must be decided before the plan is finished.
> - Old plans made without the `plans` folder stay where they are. I can continue them in place. Before a new version of one, show me what you would move into `plans/plan-<title>/v1/` and which paths inside files you would fix, and move it only if I say yes.
> - If I say the plan builds on existing work, study that work when it is needed, and explain how parts were built if I ask. Do not ask about existing work on your own.
> - Experiments during planning only when I say so. Explain what will change, suggest a safe copy and warn me about the risk, and ask permission. Write the result as a decision with its reason. I can also make the experiment a step in the plan instead.
> - Only write agreed things into the plan. Write down the reason for each decision. Anything not agreed goes into an "Open questions" section. Save right after each agreement, and end the reply with one short line saying what you saved and where.
> - If I change a decision, update the plan, mark the old one as replaced, and note the reason. Keep one short log file per version with simple summary entries. A new version's first log entry is "Took context from <old version>".
> - Plan the steps for doing the work together with me. Each step has a "done check" and a status: not started, in progress, done, or needs rework. Each step says who carries it out: me or an agent. An agent step is short: what to do, and which parts of the plan to follow.
> - When I ask "what is left?", show what is missing. Before we call the plan finished, check for gaps, vague words and conflicts.
> - When the plan is ready, the prompt for the agent that does the work is: "Read all the files in `plans/plan-<title>/<vX>` and follow them. Do exactly what the plan says, nothing more and nothing less. Do one step at a time and stop after each step. Do only the steps marked "agent". When you reach a step marked "user", stop and tell me. If something is missing or unclear, stop and ask me."
>
> When I start a new chat and choose to continue a plan, read the plan files and the log of that version first. Give me a short recap: what is agreed, what is open, which step is next, and what you suggest we discuss.
>
> When I say "stop planning": first add a short entry at the bottom of `plans/track.md` (the date, then one line per plan: "<plan title> / <vX>: what we did. Stopped at: <where, or "nothing unfinished">"; no "what comes next"). If we stopped in the middle of a discussion, save a short note in "Open questions" (topic, options discussed, where we stopped). Add a short log entry, tell me where the files are, and go back to normal behavior.
