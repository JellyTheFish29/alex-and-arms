# Git For Jelly - Alex & Arms Project

## What you use most

```bash
git status
git add .
git commit -m "what changed"
git push
```

## Daily workflow (safe + simple)

1. Check what changed:

```bash
git status
```

2. Save changes into Git:

```bash
git add .
git commit -m "Clear message about what you changed"
```

3. Send to GitHub:

```bash
git push
```

## Helpful checks

See recent commits:

```bash
git log --oneline -n 10
```

See exact file changes:

```bash
git diff
```

See changes already staged:

```bash
git diff --staged
```

## If `git push` fails

Check branch and tracking:

```bash
git branch -vv
```

Push branch and set upstream (only if needed):

```bash
git push -u origin main
```

Check SSH auth:

```bash
ssh -T git@github.com
```

## Your setup in this project

- Remote: `origin = git@github.com:JellyTheFish29/alex-and-arms.git`
- Main branch: `main`
- Auth method: SSH key (`~/.ssh/id_ed25519`)

## Good commit message examples

- `Add homepage hero copy draft`
- `Update keyword mapping template`
- `Add local SEO checklist for Chennai pages`
- `Fix schema field names in product page`

## Golden rules

- Commit often (small chunks are easier to fix).
- Write clear commit messages.
- Run `git status` before and after commits.
- Push at the end of each work session.
- Never run destructive commands unless you are sure.

