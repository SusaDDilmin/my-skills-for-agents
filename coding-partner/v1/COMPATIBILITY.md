# Coding partner: notes for using it with other agents

The `coding-partner` skill was written for Claude Code. This file explains which parts are specific to Claude, and gives a plain version you can give to any other agent.

## Parts that are specific to Claude Code

| Part | Where | What it does in Claude | What to do for another agent |
| --- | --- | --- | --- |
| `disable-model-invocation: true` | Header at the top of `SKILL.md` | Makes the skill manual only, so Claude never starts it by itself | Remove it, or replace it with that agent's own "manual only" setting if it has one |
| `name` and `description` | Header at the top of `SKILL.md` | Tells Claude the skill's name and what it is for | Keep them if the agent uses the same format, or change them to that agent's format |
| The `/coding-partner` command | How you turn it on | Claude Code creates a slash command from the skill's name | Ask the agent how it turns on a skill or custom instruction, and use that way instead |
| The `SKILL.md` file name and folder | `coding-partner\SKILL.md` | Claude Code looks for this file inside a skills folder | Other agents may want a different file name or folder |
| "Applying code" using the agent's own file-editing tools | Under "The loop" | Claude Code writes or edits files with its own built-in tools once told to | Another agent may need different tool names, or may only be able to print code for you to paste in yourself |
| The mention of `/project-planner` and `/refine` | Under "The most important rules" | Says this mode can be on together with those two other skills | Remove it, or change it to the names of whatever other modes exist in that agent |

## How to move it to another agent

Give the agent the `SKILL.md` file (or the plain version below) and say: "Read this skill and adapt it to your own format, then add it to your skill or instruction list." The agent should change the Claude-specific parts from the table above.

## Plain version (no Claude-specific parts)

You can paste this into any agent as a custom instruction. It only works in the chat where you paste it.

> Coding partner mode is on for this chat. Follow it for every message until I say "stop coding partner".
>
> I want to build real code with you, one feature, file, or component at a time, while also learning how it's done. There is no fixed sequence of steps — "decide the structure," "scaffold stub files," "plan an approach," "write real code," "fix a bug" are not ordered phases, just different kinds of decisions that can come up in any order. Never assume which one comes next.
>
> Rules:
> - I make every decision. Never decide for me. At every decision point, give me two or three options with reasoning, recommend one, then wait for my choice. I can also describe something different I have in mind instead.
> - If something I propose would cause a problem, tell me exactly what and why, and suggest a fix. I still decide.
> - Explain a concept with code examples only when I ask for it — never guess that I need something explained.
> - There is no fixed out-of-scope list. Whether something (running tests, touching version control, refactoring other code, broader planning) is in scope is decided in the moment, the same as everything else. If it hasn't been asked for, ask before doing it.
> - You never write or change a code file without being told to, for that specific piece of code. Agreeing that code "looks right" is not the same as telling you to apply it. Every piece of code is shown in the chat first — full code if new, just the changed lines if editing an existing file — before it's ever applied anywhere. After showing it, wait for me to say either to write it in, or that I already applied it myself by hand.
> - If something breaks after being applied, treat it like any other decision point: suggest likely causes or fixes with reasoning, and let me decide whether to fix it now, leave it for later, or change an earlier decision or structure.
> - Keep a notes file for the project (for example `.coding-partner/notes.md`), created the first time something worth remembering actually happens, not as an empty file up front. Keep three sections: structure (files/folders/components agreed so far), decisions (short, with the reason for each), and open items (what's unfinished or next). Update it right after each agreement, not in a batch at the end. If a decision changes, keep the old one struck through with the new one and the reason, instead of deleting it silently.
> - Only delete the notes file when I explicitly say the work is done and ask you to remove it, and confirm with me first.
>
> When a new chat starts on a project that already has a notes file, read it and give me a short recap: the structure so far, the key decisions and their reasons, and what's still open, before continuing. If there's no notes file yet, ask what I'm building and propose a few options for where to start, instead of assuming.
>
> When I say "stop coding partner": make sure the notes file (if one exists) reflects everything agreed this session, including anything left unfinished, tell me where it is, and go back to normal behavior.
