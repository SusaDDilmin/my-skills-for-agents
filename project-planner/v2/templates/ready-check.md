# Ready check

Run this before saying the plan is finished. Go through the plan and report gaps in simple English. Do not fix gaps yourself: list them and let the user decide.

## Checks
1. **Goal:** Is it clear what "finished" looks like?
2. **Limits:** Are deadline, time, budget, tools and audience written down where they matter?
3. **Areas:** Is every area the user confirmed filled in to the level of detail they chose?
4. **Out of scope:** Is it written what is NOT included?
5. **Decisions:** Does every decision have a reason?
6. **Conflicts:** Do any two decisions contradict each other?
7. **Open questions:** Is anything still undecided? Each one must be decided or moved to out of scope.
8. **Vague words:** Are there unclear phrases such as "fast", "nice", "later", "etc." that an agent could read in different ways?
9. **Steps:** Are the steps in a sensible order? Does each step have a "done check"?
10. **Enough detail to follow:** Could an agent follow the plan without guessing? If it would have to guess, list what is missing.
11. **Index and log:** Are they up to date (if the plan has several files)?
12. **New version sections:** For a new version, are the "Previous plans" and "Starting point (what already exists)" sections filled in?
13. **New version questions:** Are the goal question and the unfinished-steps question decided?
14. **Who does each step:** Does every step say who carries it out (user or agent)?
15. **Agent steps:** Does every agent step say which parts of the plan it must follow?
16. **Plans index:** Does `plans/index.md` list this version, and does it mark the right current version?
17. **Handoff folder:** Does the handoff prompt name the exact version folder?

## Report format
- What is complete.
- What is missing or unclear (numbered list, one line each).
- Your suggestion for what to discuss next.

When the user agrees nothing important is missing, give them the handoff prompt (from "Steps and the final handoff" in `SKILL.md`):

> Read all the files in `plans/plan-<title>/<vX>` and follow them. Do exactly what the plan says, nothing more and nothing less. Do one step at a time and stop after each step. Do only the steps marked "agent". When you reach a step marked "user", stop and tell me. If something is missing or unclear, stop and ask me.
