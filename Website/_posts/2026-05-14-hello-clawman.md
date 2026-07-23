---
title: "Clawman 1.0 — somebody has to keep the shelf tidy"
version: "1.0.0"
tags: [release]
lede: "Eleven context files, two of them arguing, one describing a directory that was deleted in March. Here's the extension that came out of noticing."
date: 2026-05-14 09:00:00 +0000
---

This started with a bad afternoon of debugging.

Claude had been getting steadily worse on one of our repos. Not dramatically — just enough that everyone had quietly started double-checking its output, then quietly started using it less. The assumption in the room was that something had changed on the model side.

Nothing had changed on the model side. What had changed was that we had, over about four months, accumulated eleven context files. Two of them gave opposite instructions about the test command. One described a directory structure we'd refactored away in March. Three had been written by someone who left in February and nobody had opened since.

Claude was reading all of it. Every single time. And doing an admirable job of trying to satisfy eleven documents that did not agree with each other.

## The failure mode

Context rot is invisible in a way that most technical debt isn't.

A broken build fails loudly. A slow query shows up in a dashboard. But a context file that stopped being true six weeks ago produces output that is subtly, unfalsifiably a bit worse — and the natural place to assign blame is the model, because the file is not something anyone is looking at.

Nobody reads context files. That's not a criticism, it's a structural fact: they're written once, at a moment of high intention, and then they're infrastructure. You don't reread your `.gitignore` either.

The difference is that a stale `.gitignore` doesn't quietly instruct an assistant to do the wrong thing several hundred times a week.

## What 1.0 does

Clawman lives in your sidebar and does one unglamorous job: he finds every context file in the workspace and tells you which ones you can still trust.

- **Discovery** — `CLAUDE.md` at any depth, `.claude/` directories, skills, memory files. Including the ones you forgot about, which in our case was four of the eleven.
- **Staleness** — not "this file is old," which is useless, but "this file hasn't changed while the code it describes has changed forty-one times." With the date and the count, so you can disagree with him.
- **Conflicts** — the expensive one. Two files both loaded into context, both authoritative, giving different instructions. You get both excerpts and a jump-to-line on each.
- **Archive** — because some files are old and completely fine, and a tool that can't take *no* for an answer is a tool you uninstall.

## What he deliberately doesn't do

He doesn't rewrite your context files. Deciding what's true about your codebase is a judgement call and it isn't his.

He doesn't have opinions about your architecture. He's a clerk.

He doesn't send anything anywhere. No telemetry, no uploads, no account, no network calls at all. He reads files on disk and that is the entire surface area.

## Try it on a repo you've had a while

The first scan on an established project is usually uncomfortable. That's the tool working — it's showing you a thing that was already true and simply wasn't visible.

[Install for VS Code]({{ site.marketplace }}), open the panel, and see what's in there.
