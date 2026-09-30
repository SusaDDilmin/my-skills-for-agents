# My Skills

This folder is a record of the skills I have created for AI agents. It is a backup and a list, not the master copy. The skills that Claude Code actually uses live in its own skills folder.

**This folder:** `E:\Agentic AI Usage\My Skills`
**Where Claude Code keeps its skills:** `C:\Users\susad\.claude\skills`

## My skills

| Skill | What it does (in plain language) | Folder |
| --- | --- | --- |
| `refine` | When I turn it on in a chat, the agent says back what I asked and checks that it understood me. Then it lists everything I may have forgotten, so I can choose what to add before any work starts. It helps me improve my prompts. | `refine\` |
| `project-planner` | A planning partner for anything: an app, a study timetable, a presentation. I discuss my plan with the agent. It asks a few questions at a time, gives options with reasons, and warns me if a choice may cause a problem. I make every decision. It saves only what we both agree on into plan files, so I end up with a complete plan and one short prompt to build it step by step. | `project-planner\` |

## How this folder is organized

Each skill has its own folder. Inside it:

- `SKILL.md` is the current version, ready to copy into a skills folder.
- `SKILL.v1.md`, `SKILL.v2.md` and so on are saved versions. When I improve a skill, I save the new version with the next number and update `SKILL.md` to match, so old versions are never lost.
- `templates\` (only `project-planner` has it) holds extra files that `SKILL.md` reads. Copy this folder together with `SKILL.md`, and keep the paths the same.
- `COMPATIBILITY.md` (where it exists) explains which parts are specific to Claude Code and what to change for another agent.

`project-planner` uses a different layout: one folder per version. Each version folder is complete, and nothing is duplicated.

- `project-planner\v1\` and `project-planner\v2\` each hold their own `SKILL.md`, `templates\` and `COMPATIBILITY.md`.
- The highest number is the current version. Copy the files inside that folder (not the folder itself) into the skills folder. Claude Code keeps only the current version, directly in `project-planner\`.
- When I improve the skill, I add a new folder with the next number, so old versions are never lost.

## How to use a skill from this folder

Give the skill's folder to Claude and say: "Add this to your skill list." Claude copies it into its skills folder.

For another agent, give it the skill and the `COMPATIBILITY.md` file, and ask it to adapt the skill to its own format.

## Changelog

- `refine` v1 — first version. Created 2026-09-30.
- `project-planner` v1 — first version. Created 2026-09-30.
- `project-planner` v2 — handles changes to existing plans: a `plans\` folder with one folder per plan and one folder per version, `plans\index.md` and `plans\track.md`, a start question (continue, new version, or new plan), self-contained new versions that take context from old ones, "Previous plans" and "Starting point" sections, user or agent steps, a stricter handoff prompt, experiments during planning, and old-style plans moved only with permission. Created 2026-09-30.
