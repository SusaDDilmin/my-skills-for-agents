# My Skills

This folder is a record of the skills I have created for AI agents. It is a backup and a list, not the master copy. The skills that Claude Code actually uses live in its own skills folder.

**This folder:** `E:\Agentic AI Usage\My Skills`
**Where Claude Code keeps its skills:** `C:\Users\susad\.claude\skills`

## My skills

| Skill | What it does (in plain language) | Folder |
| --- | --- | --- |
| `refine` | When I turn it on in a chat, the agent says back what I asked and checks that it understood me. Then it lists everything I may have forgotten, so I can choose what to add before any work starts. It helps me improve my prompts. | `refine\` |

## How this folder is organized

Each skill has its own folder. Inside it:

- `SKILL.md` is the current version, ready to copy into a skills folder.
- `SKILL.v1.md`, `SKILL.v2.md` and so on are saved versions. When I improve a skill, I save the new version with the next number and update `SKILL.md` to match, so old versions are never lost.
- `COMPATIBILITY.md` (where it exists) explains which parts are specific to Claude Code and what to change for another agent.

## How to use a skill from this folder

Give the skill's folder to Claude and say: "Add this to your skill list." Claude copies it into its skills folder.

For another agent, give it the skill and the `COMPATIBILITY.md` file, and ask it to adapt the skill to its own format.

## Changelog

- `refine` v1 — first version. Created 2026-09-30.
