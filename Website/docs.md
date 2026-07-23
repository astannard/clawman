---
layout: page
title: Docs
eyebrow: Install and configure
lede: Getting Clawman running takes about thirty seconds. Getting him tuned to your repo takes a bit longer, and this page covers both.
permalink: /docs/
---

## Install

**From the Marketplace** — search for *Clawman* in the Extensions view, or install directly from the [Marketplace listing]({{ site.marketplace }}).

**From the command palette** — <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, then:

```
ext install clawman.clawman
```

**From a VSIX** — download the latest from [Releases]({{ site.repo }}/releases), then:

```bash
code --install-extension clawman-1.4.0.vsix
```

Requires VS Code 1.85 or later.

---

## First run

Open the Clawman panel from the activity bar. He scans on open — a typical repo takes under a second, a large monorepo a few seconds.

You'll get a list of every context file, grouped by directory, each with a state and a one-line reason.

If the list is empty and you expected files, check:

- The files are inside the open workspace folder
- They aren't matched by `.gitignore` (or set `clawman.respectGitignore` to `false`)
- They match a recognised name or a pattern in `clawman.includeGlobs`

---

## Commands

All available from the command palette.

| Command | Default binding | What it does |
|---|---|---|
| `Clawman: Rescan workspace` | <kbd>Cmd</kbd>+<kbd>Alt</kbd>+<kbd>K</kbd> | Full rescan |
| `Clawman: Show conflicts` | — | Filter to conflicts only |
| `Clawman: Tidy up` | — | Resolve trivial findings, with a diff preview |
| `Clawman: Archive file` | — | Mark the current file out of scope |
| `Clawman: Explain this finding` | — | Why Clawman flagged it |

---

## Configuration

Settings live under `clawman.*` in your `settings.json`.

```jsonc
{
  // Scan when the workspace opens
  "clawman.scanOnStartup": true,

  // Days a file can sit untouched before it's a stale candidate
  "clawman.staleThresholdDays": 60,

  // Skip paths matched by .gitignore
  "clawman.respectGitignore": true,

  // Extra patterns to treat as context files
  "clawman.includeGlobs": [
    "docs/ai/**/*.md",
    ".cursor/rules/*.mdc"
  ],

  // Never flag these, even if they look stale
  "clawman.alwaysArchive": [
    "**/legacy/**"
  ],

  // strict | balanced | relaxed
  "clawman.conflictSensitivity": "balanced"
}
```

### Conflict sensitivity

- **`strict`** — flags any directive that differs, including phrasing. Noisy, but catches everything. Useful for a one-off audit.
- **`balanced`** — flags semantic disagreements. The default, and the right choice for daily use.
- **`relaxed`** — only flags direct contradictions like two different values for the same command.

### Per-project settings

Commit a `.vscode/settings.json` with your `clawman.*` block so everyone on the team gets the same scan behaviour. This matters more than it sounds: if one person's Clawman flags a conflict and another's doesn't, you'll spend a meeting on it.

---

## Understanding a finding

Every finding has a state, a reason, and a location. Click any of them to jump to the exact line.

**Stale** shows you the file's last-modified date and the commit activity in the paths it describes. If the reason doesn't hold — a file can be old and perfectly correct — archive it, and Clawman stops asking.

**Conflict** shows both excerpts side by side. Resolve it by editing either file, or by archiving one. Clawman re-checks on save.

**Dead reference** shows the path as written and where he looked for it. Usually a rename that a context file missed.

---

## Troubleshooting

**The scan is slow.** Turn off `scanOnStartup` and rescan manually, or narrow `includeGlobs`. Very large monorepos with deep `node_modules` are the usual culprit — check `respectGitignore` is on.

**Too many conflicts.** Drop `conflictSensitivity` to `relaxed` and work up. A repo that's never been audited will light up the first time; that's the tool working.

**A file keeps getting flagged and it's fine.** Archive it. That's what archive is for, and it persists in workspace state.

**Findings don't update after an edit.** Clawman re-checks on save, not on keystroke. Save the file, or run `Clawman: Rescan workspace`.

---

## Contributing

Clawman is MIT licensed and developed in the open at [{{ site.repo | remove: 'https://' }}]({{ site.repo }}).

Bug reports want: VS Code version, Clawman version, and the shape of the context files involved. You don't need to share their contents — file names and structure are usually enough.

Feature arguments belong in [issues]({{ site.repo }}/issues). The bar for adding something is whether it helps you trust your context files more.
