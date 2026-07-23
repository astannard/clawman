---
title: "1.3 — conflicts now show both sides"
version: "1.3.0"
tags: [release, conflicts]
lede: "Telling you two files disagree is only half a finding. This release shows you both excerpts, with line numbers, so you can resolve it without opening anything."
date: 2026-06-18 10:30:00 +0000
---

The most common piece of feedback on 1.0 was some version of: *"okay, but which part?"*

Fair. Clawman would tell you that `CLAUDE.md` and `.claude/skills/testing.md` disagreed, and then leave you to open both files and hunt for it. For a big context file that's a genuinely annoying two minutes, and two minutes of friction is enough that people stop resolving conflicts at all.

## Both excerpts, side by side

Conflicts now expand in place. You get the actual conflicting lines from each file, with line numbers and enough surrounding context to tell whether it's a real contradiction or two statements that merely look similar.

```
CONFLICT · test command

CLAUDE.md:14
  Run the full suite with `npm test` before every commit.

.claude/skills/testing.md:31
  Always use `pnpm test:ci` — `npm test` skips the integration tags.
```

Both line references jump straight to the file. Resolve by editing either one, or by archiving the one that's wrong. Clawman re-checks on save.

## Four kinds of conflict

The detector now classifies what it finds, which mostly matters because it lets you ignore whole categories when they're noisy:

- **Command conflicts** — two files, two different commands for the same job. Highest signal by a distance. This is the one that costs you real time.
- **Rule conflicts** — one file says always, another says never.
- **Convention conflicts** — disagreement about naming, structure, or file layout.
- **Scope overlap** — two files both claiming authority over the same directory. Not always wrong, but worth a look in a monorepo.

## Sensitivity, because the first scan is brutal

A repo that's never been audited lights up. That's accurate, and it's also demoralising, and a demoralising first run is how you lose someone in the first ninety seconds.

So there's now `clawman.conflictSensitivity`:

- `strict` — flags any directive that differs, including phrasing. Noisy. Good for a deliberate one-off audit.
- `balanced` — semantic disagreements only. The default.
- `relaxed` — direct contradictions only, like two different values for the same command. A reasonable place to start on a big old repo, then work up.

## Also in this release

- Conflict detection now understands that a nested `CLAUDE.md` overrides its parent for paths beneath it, rather than reporting the override as a conflict. This was the single largest source of false positives in monorepos.
- Findings re-check on save instead of only on rescan.
- Fixed: symlinked `.claude/` directories were being skipped entirely. If you symlink a shared context directory across repos, 1.0 was silently ignoring all of it.
- Fixed: files with CRLF line endings reported line numbers one off.

## Next

Dead path detection is the thing I keep wanting and it isn't built yet. Context files describe directories constantly, and those directories move. Working on it.
