---
title: "1.4 — he noticed the directory wasn't there"
version: "1.4.0"
tags: [release, detection]
lede: "Context files describe directories. Directories move. Clawman now resolves every path mentioned in every context file and flags the ones that have gone."
date: 2026-07-09 11:00:00 +0000
---

Clawman has been wanting to mention this for a while.

Context files are full of paths. *"Auth logic lives in `src/auth/`."* *"Migrations go in `db/migrate/`, never in `db/`."* *"See `docs/architecture/overview.md` for the full picture."* These are the most useful sentences in a context file, because they orient the assistant before it starts searching.

They're also the sentences most likely to be quietly wrong, because directories move and nobody greps the context files afterwards.

## Dead path detection

Every path mentioned in every context file now gets resolved against the actual workspace. Ones that don't exist get flagged with the path as written and where Clawman looked:

```
DEAD REFERENCE · CLAUDE.md:22

  "Auth logic lives in src/auth/"

  No such path. Closest match: src/services/auth/
  (renamed in 4f2a91c, 6 weeks ago)
```

Where the git history makes it obvious — a rename in a single commit — you get the closest match and the commit that did it. Where it doesn't, you just get told the path is gone, which is still the useful half.

It also checks:

- **Commands against `package.json`** — a context file telling Claude to run `npm run lint:strict` when that script was removed two months ago
- **Relative links between context files** — `.claude/` files referencing each other after a reorganisation
- **Config files by name** — references to a `.eslintrc` that became `eslint.config.mjs`

## What this turned up

I ran it across eight repos, including three that had been through Clawman 1.3 and come out clean.

Every single one had at least one dead path. The median was four. The worst had nineteen, in a context file that had been rewritten wholesale after a restructure — except the restructure happened twice, and the second one wasn't reflected anywhere.

The pattern is consistent: dead paths cluster in the *oldest and most confidently-written* sections of a context file. The paragraph someone sat down and composed carefully at the start of the project is exactly the paragraph describing a structure that no longer exists.

That's an uncomfortable thing to learn about documentation in general, and I don't have a tidy conclusion about it.

## Also in this release

- Conflict view now shows both excerpts without expanding, when they're short enough to fit
- Added `clawman.alwaysArchive` for glob patterns that should never be flagged — for vendored or generated context files you don't control
- The panel remembers scroll position between rescans
- Fixed: dead path detection ignoring paths inside fenced code blocks, which was the correct call about 80% of the time and is now configurable
- Fixed: rescanning a workspace with no context files showed a spinner indefinitely

## Next

The thing I keep circling is **ownership**. A context file with no clear author, last touched by someone who left, is a different kind of risk from one the current team actively maintains — and git already knows which is which.

Not sure yet whether that's a state, a signal that feeds staleness, or just a column. If you have a view, [the issue is open]({{ site.repo }}/issues).
