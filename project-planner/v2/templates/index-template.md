# Index template

This file has two templates.

## 1. `plans/index.md` (one index for all plans)

Create it with the first plan. It lists every plan, its versions, and which version is current, so the user and any agent know which version to follow. Update it when a plan or a version is created and when the current version changes. A new version is "current" as soon as it is created. Old versions stay as history.

```markdown
# Plans — Index

| Plan title | Versions | Current version | Folder path |
|------------|----------|-----------------|-------------|
| <plan title> | v1, v2 | v2 | plans/plan-<title>/ |
```

## 2. Version index (inside one version folder)

Create this file only when a version is split into several files. It lists every file of that version and its step progress, so the user and any agent can find things fast.

```markdown
# <Plan title> <vX> — Index

## Files
| File | What it contains | Status |
|------|------------------|--------|
| <path/file.md> | <short description> | draft / agreed / needs update |

## Step progress
Status: not started | in progress | done | needs rework

| Step | Status |
|------|--------|
| <Step name> | not started |

## Next step
<Which step comes next>

## Open questions
See the "Open questions" section in each file.
```
