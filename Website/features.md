---
layout: page
title: Features
eyebrow: What Clawman does
lede: One job, done thoroughly. Clawman finds every Claude context file in your project, works out which ones are still true, and tells you where they disagree.
permalink: /features/
---

## The file-health scale

Every context file Clawman finds gets exactly one of four states. This is the spine of the whole extension — everything else is in service of getting this right.

| State | What it means | What to do |
|---|---|---|
| **Fresh** | Changed recently, consistent with everything else | Nothing |
| **Stale** | Untouched while the code it describes kept moving | Read it. Confirm or fix. |
| **Conflict** | Another file gives Claude opposite instructions | Resolve. This one costs you the most. |
| **Archived** | Deliberately out of scope | Nothing. You told him to ignore it. |

The list sorts worst-first. Conflicts, then stale, then everything else — because that's the order you'd actually work through it.

---

## Discovery

Clawman scans the workspace for the files Claude reads:

- `CLAUDE.md` at any depth, including nested per-package files in a monorepo
- `.claude/` directories and everything in them
- `.claude/skills/` skill definitions, including `SKILL.md` front matter
- Memory files and agent definitions
- `.mdc` and other convention files, if you point him at them

Anything matched by `.gitignore` is skipped by default. You can override that per-pattern in settings.

<div class="callout" markdown="1">
**Monorepos.** Clawman groups results by package and shows which `CLAUDE.md` actually applies at a given path, so you can see what Claude sees when it's working in `packages/api` specifically.
</div>

---

## Staleness detection

A file isn't stale because it's old. It's stale because the world moved and it didn't.

Clawman compares each context file's last-modified date against commit activity in the paths that file talks about. A `CLAUDE.md` describing `src/auth/` that hasn't changed while `src/auth/` has seen forty commits is the signal. A README-style file in a stable corner of the repo is left alone.

You get a date and a reason, never a bare warning:

> Not touched since 12 March. `src/auth/` has changed 41 times since.

---

## Conflict detection

The expensive failure. Two files, both loaded, both authoritative, giving opposite instructions.

Clawman extracts directives — commands, rules, prohibitions, file paths, naming conventions — and compares them across every file that would be in context at the same time. When two disagree, you get both excerpts side by side with line numbers, and a jump-to-line on each.

It catches:

- **Command conflicts** — two files, two different test commands
- **Rule conflicts** — one file says always, another says never
- **Convention conflicts** — disagreement on naming, structure, or style
- **Scope overlap** — two files claiming authority over the same directory

---

## Dead reference checking

Context files love to describe directories that no longer exist. Clawman resolves every path mentioned in every context file and flags the ones that have gone.

Also catches references to commands that aren't in `package.json` scripts any more, and links to files that have moved.

---

## Working with what he finds

- **Merge** — combine two overlapping files, with a diff preview before anything is written
- **Archive** — mark a file out of scope. It stays on disk and stays visible, just stops being flagged.
- **Jump to line** — every finding links straight to the exact line
- **Bulk tidy** — resolve everything trivial in one pass, and see a summary of what changed

Nothing is written without showing you the diff first.

---

## Settings worth knowing

| Setting | Default | What it does |
|---|---|---|
| `clawman.scanOnStartup` | `true` | Scan when the workspace opens |
| `clawman.staleThresholdDays` | `60` | How long before an untouched file is a candidate for stale |
| `clawman.respectGitignore` | `true` | Skip ignored paths |
| `clawman.includeGlobs` | `[]` | Extra patterns to treat as context files |
| `clawman.conflictSensitivity` | `"balanced"` | `strict`, `balanced`, or `relaxed` |

---

## What Clawman doesn't do

Worth being clear about, because a tool that overpromises is a tool you stop trusting.

- **He doesn't write your context files.** He tells you which ones are wrong. Fixing them is a judgement call and it's yours.
- **He doesn't have opinions about your architecture.** He's a clerk, not a reviewer.
- **He doesn't send anything anywhere.** No telemetry, no uploads, no account, no network calls. He reads files on disk.
- **He doesn't run Claude.** Clawman is about the files Claude reads, not the conversation.

<div class="callout" markdown="1">
Missing something you need? The [dev log]({{ '/blog/' | relative_url }}) covers what's coming, and [issues]({{ site.repo }}/issues) is the right place to argue for it.
</div>
