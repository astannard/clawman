# Clawman — Brand Guidelines

**Version 1.0** · A VS Code extension for managing Claude context files.

---

## 1. The short version

| | |
|---|---|
| **Name** | Clawman (always one word, always lowercase in the wordmark, capitalised in prose) |
| **Category** | VS Code extension for managing Claude context files |
| **Tagline** | *Context, in good claws.* |
| **One-liner** | Clawman keeps your CLAUDE.md files honest — finds them, sorts them, and tells you when they've gone stale. |
| **Personality** | Meticulous · Warm · Dry · Direct |
| **Primary colour** | Shell `#E1552C` |
| **Typefaces** | Bricolage Grotesque (display) · Inter (text/UI) · JetBrains Mono (code) |

---

## 2. Brand story

### The problem nobody watches

Context files start clean. One `CLAUDE.md`, written carefully on a good afternoon.

Six weeks later there are eleven of them. Two contradict each other about the test command. One describes a directory that was deleted in March. Three were written by someone who has since left. Nobody has read any of them since the day they were created.

Except Claude. Claude reads them every single time.

This is the quiet failure mode of working with AI on a real codebase: the instructions rot, and the rot is invisible. Your assistant gets worse and you assume it's the model.

### The character

Clawman is the one who noticed.

He's a small, extremely serious creature who lives in your sidebar and takes filing more seriously than anyone has ever taken filing. He's part crustacean, part archivist. He has one job and he is unbearably good at it: he knows where every context file is, what's in it, when it was last true, and which two of them are arguing.

He is not a genius. He does not have opinions about your architecture. He is a **clerk** — and a clerk is exactly what this problem needed. The claw is a precision instrument. It picks up one thing, it puts it exactly where it goes, it doesn't drop it.

### Why "Clawman"

Three readings, all intended:

1. **The claw** — precision, grip, one thing at a time, never dropped.
2. **Claude's claw** — the appendage that actually handles things on Claude's behalf.
3. **The man** — a person, not a platform. Someone whose job this is.

### What we're not

We're not an "AI-powered orchestration layer." We're not going to supercharge anything. Clawman does an unglamorous, specific job with obvious care, and the brand should feel like that: **useful, a bit funny, never inflated.**

---

## 3. Positioning

**For** developers who work with Claude on real codebases
**Who** have accumulated context files they no longer trust
**Clawman is** a VS Code extension
**That** finds, organises, and audits every Claude context file in the project
**Unlike** editing markdown by hand and hoping
**Because** stale context is invisible until it's expensive.

### Audience

Working developers, mid-to-senior, pragmatic. They are sceptical of AI marketing and allergic to hype. They have already been disappointed by three extensions this month. They will install something because a colleague said "this fixed the annoying thing," not because of a landing page.

**The implication for the brand:** earn trust through specificity. Show the actual problem. Name the actual files. A screenshot beats an adjective.

---

## 4. Personality

Four traits, each with its guardrail. The guardrail matters as much as the trait.

**Meticulous, not fussy.**
Clawman cares about detail because detail is the product. He does not lecture you about your habits or block you from shipping.

**Warm, not cute.**
There's a character here and he has feelings about filing. But he never baby-talks, never uses mascot voice, never says "oopsie."

**Dry, not snarky.**
The humour is understatement. *"Not touched since March. Still true?"* — not *"Wow, this file is ANCIENT 💀."* Never make the user the punchline.

**Direct, not curt.**
Say the thing in the fewest words that are still kind. Brevity is respect, not coldness.

---

## 5. Tone of voice

### Five rules

1. **Lead with the noun.** Say what happened to what. *"Two files disagree about your test command"* — not *"We detected a potential inconsistency."*
2. **Short sentences. Concrete words.** If a sentence needs a comma to survive, it probably needs a full stop instead.
3. **Never inflate.** Banned: *seamlessly, effortlessly, supercharge, revolutionise, leverage, unlock, game-changing, next-generation, powerful, magic.*
4. **Address the user as "you." Refer to the product as "Clawman."** Use "we" only in the changelog and human-signed writing.
5. **One joke per screen, maximum.** The humour is seasoning. A tool that's constantly winking is a tool you stop trusting.

### Grammar and conventions

- **Clawman** — capitalised in prose, lowercase in the wordmark. Never "ClawMan," "clawMan," or "Claw Man."
- No exclamation marks in product UI. One is permitted in the changelog per release, if genuinely earned.
- No emoji in product UI. Sparingly in README and release notes.
- Sentence case for all headings, buttons, and labels. Never Title Case.
- Oxford comma: yes.
- File names always in `monospace`.

### Do / don't

| Context | ✅ On brand | ❌ Off brand |
|---|---|---|
| Empty state | No context files yet. Write a `CLAUDE.md` and it'll show up here. | Get started on your AI journey! 🚀 |
| Stale file | Not touched since 12 March. Still true? | ⚠️ WARNING: Outdated context detected! |
| Conflict | `CLAUDE.md` and `.claude/testing.md` disagree about your test command. Claude reads both. | Potential inconsistency identified across context sources. |
| Success | Tidied. 3 files merged, 1 archived. | Success! Your context has been seamlessly optimised! |
| Error | Couldn't read `.claude/skills/`. Permissions, probably. | An unexpected error occurred. |
| Marketing | Your assistant is only as good as the notes you left it. Clawman keeps the notes honest. | Supercharge your AI workflow with next-generation context orchestration. |

### Sample copy

**Marketplace description (opening)**

> Every Claude context file in your project, in one place — with the stale ones flagged and the contradictions surfaced.
>
> Clawman scans your workspace for `CLAUDE.md`, `.claude/` directories, skills, and memory files, then shows you what's actually in them. Which ones haven't changed since the code they describe. Which two are giving Claude opposite instructions. Which one nobody has opened since it was written.
>
> Claude reads all of it, every time. Clawman makes sure that's a good thing.

**Website hero**

> # Context, in good claws.
> Claude reads your context files every single time. Clawman makes sure they're still worth reading.
>
> `[ Install for VS Code ]`   `[ See how it works ]`

**Release note**

> ### 1.4.0
> Clawman now notices when a context file describes a directory that no longer exists. He's been wanting to mention it for a while.
>
> - Added dead-path detection for file references in context files
> - Conflict view now shows both excerpts side by side
> - Fixed: symlinked `.claude/` directories were being skipped

---

## 6. Logo

### The mark

An asymmetric pincer forming a **C**, gripping a small rounded rectangle — a file. Three readings in one shape: claw, C for Clawman, and the core function of holding a context file securely.

The upper prong is heavier and longer than the lower. That asymmetry is what stops it reading as a plain letter C. Don't even it out.

| File | Use |
|---|---|
| `logo/clawman-mark.svg` | Two-tone mark. Default. |
| `logo/clawman-mark-mono.svg` | Single colour via `currentColor`. Small sizes, engraving, one-colour print. |
| `logo/clawman-lockup.svg` | Mark + wordmark, for light backgrounds. |
| `logo/clawman-lockup-dark.svg` | Mark + wordmark, for dark backgrounds. |

> **Production note:** the lockup SVGs set the wordmark as live `<text>`. Convert to outlines before shipping so rendering doesn't depend on the font being available.

### Clearspace

Minimum clearspace on all sides = **the width of the gripped file rectangle** (¼ of the mark's height). Nothing enters that zone — no text, no rules, no other logos.

### Minimum sizes

| Context | Minimum |
|---|---|
| Mark, screen | 16 px (VS Code activity bar) |
| Mark, print | 8 mm |
| Lockup, screen | 120 px wide |
| Lockup, print | 30 mm wide |

Below 20 px, use the **mono** mark. The two-tone file rectangle muddies at small sizes.

### Colourways

1. **Shell on light** — `#E1552C` prongs, `#F5825B` file, on Sand or white. Default.
2. **Shell-400 on dark** — `#F5825B` prongs, `#FBE3D8` file, on Deep. Default for dark UI.
3. **Mono ink** — all `#0C1013`, for one-colour light applications.
4. **Mono reversed** — all `#FAF6F0`, for one-colour dark applications and photography.

### Misuse

Never:

- Recolour the mark outside the four approved colourways
- Stretch, skew, rotate, or flip it
- Add gradients, bevels, glows, or drop shadows
- Outline the wordmark or change its typeface
- Place the mark inside a circle, badge, or rounded-square container that isn't the app icon
- Rebuild the mark from scratch — use the supplied SVGs
- Set the lockup vertically or re-space the mark and wordmark
- Put it on a busy photograph without a solid colour field behind it

---

## 7. Colour

Warm shell against cold deep water. The orange is the only loud thing in the system, and it stays loud by being rare.

### Brand

| Token | Hex | Role |
|---|---|---|
| `shell-100` | `#FBE3D8` | Tint fills, subtle highlight backgrounds |
| `shell-400` | `#F5825B` | Primary on dark backgrounds, hover states |
| **`shell-500`** | **`#E1552C`** | **Primary brand colour. The default.** |
| `shell-600` | `#C4441F` | Pressed states; brand text on light backgrounds |
| `shell-700` | `#A83817` | Small brand text on light where AA is required |

### Neutrals — dark (default UI)

| Token | Hex | Role |
|---|---|---|
| `deep-900` | `#10161B` | Canvas |
| `deep-800` | `#171F26` | Raised surface |
| `deep-700` | `#1F2A33` | Cards, panels, inputs |
| `deep-600` | `#2C3A45` | Borders, dividers |

### Neutrals — light

| Token | Hex | Role |
|---|---|---|
| `sand-100` | `#FAF6F0` | Canvas |
| `sand-200` | `#F1E9DE` | Raised surface |
| `sand-300` | `#E2D7C7` | Borders, dividers |
| `ink-900` | `#0C1013` | Body text on light |

### Silt (secondary text, both modes)

| Token | Hex | Role |
|---|---|---|
| `silt-300` | `#A8B4BE` | Secondary text on dark |
| `silt-500` | `#6E7C88` | Disabled, placeholder, icon strokes |
| `silt-600` | `#5A6772` | Secondary text on light |
| `silt-700` | `#4A555F` | Emphasised secondary text on light |

### Status — the file-health scale

This is the product's spine. Every context file has one of four states, and each has exactly one colour.

| State | Meaning | On dark | On light | Text on light |
|---|---|---|---|---|
| **Fresh** — Kelp | Current and consistent | `#3FBF89` | `#1F9D6B` | `#12744F` |
| **Stale** — Buoy | Untouched while the code moved | `#F5BE4A` | `#E8A317` | `#8A5A00` |
| **Conflict** — Anemone | Two files disagree | `#F0577F` | `#D92D5C` | `#B81F4C` |
| **Archived** — Silt | Deliberately out of scope | `#A8B4BE` | `#6E7C88` | `#5A6772` |

### Colour rules

1. **Shell is never a status colour.** Brand orange means "Clawman" — action, identity, brand. It never means "warning." Buoy amber sits close to Shell in hue; keeping them functionally separate is the whole reason the status scale is defined independently. If they'd ever appear adjacent, put a neutral between them.
2. **One Shell per view.** One primary button, or one active state, or one accent — not three. If everything's orange, nothing is.
3. **Dark is the default.** Clawman lives in an editor. Design dark first, then derive light.
4. **Status colour is never the only signal.** Always pair with an icon and a text label — for colour-blind users and for scannability.
5. **Never tint large surfaces with Shell.** No orange page backgrounds, no orange cards. Fills use `shell-100` at most.
6. **Borders are one step, not two.** `deep-600` on dark, `sand-300` on light. Don't invent intermediate greys.

### Accessibility

All body-size pairings meet **WCAG AA (4.5:1)**; the light-mode `-700` status variants exist specifically for this. Verified ratios:

| Pairing | Ratio |
|---|---|
| `ink-900` on `sand-100` | 17.8 : 1 |
| `sand-100` on `deep-900` | 16.9 : 1 |
| `silt-300` on `deep-900` | 8.6 : 1 |
| `silt-600` on `sand-100` | 5.4 : 1 |
| `shell-400` on `deep-900` | 7.1 : 1 |
| `shell-600` on `sand-100` | 4.7 : 1 |
| `ink-900` on `shell-500` | 5.0 : 1 |
| `kelp-700` / `buoy-700` / `anemone-700` on `sand-100` | 5.4 / 5.5 / 5.8 : 1 |

`shell-500` on light (3.5:1) is **large text and graphics only** — use `shell-600` or `shell-700` for body copy.

---

## 8. Typography

Three families. Each has one job and does not do the others.

### Bricolage Grotesque — display

Headlines, the wordmark, marketing hero copy. It has a slightly irregular, hand-cut quality that carries the "warm and characterful" half of the brand without tipping into novelty.

- Weights: 600 Semibold, 700 Bold, 800 ExtraBold
- Tracking: `-0.02em` at 32 px+, `-0.03em` at 56 px+
- Line height: 1.05–1.15
- **Only for text above 24 px.** It is not a body face and gets noisy at small sizes.

### Inter — text and UI

Body copy, UI labels, buttons, tables, documentation. Neutral, boring, extremely legible. That is the point — it lets Bricolage and Shell do the personality work.

- Weights: 400 Regular, 500 Medium, 600 Semibold
- Tracking: `0` at body sizes, `-0.01em` at 20 px+
- Line height: 1.5 body, 1.35 UI labels
- Enable `tnum` for any column of numbers

### JetBrains Mono — code

File paths, code snippets, diffs, terminal output, keyboard shortcuts. Every filename in the product and in this documentation is monospace.

- Weights: 400 Regular, 500 Medium
- Line height: 1.6
- Ligatures **off** — they misrepresent what's actually in the file

### Scale

| Step | Size / line height | Family & weight | Use |
|---|---|---|---|
| Display | 56 / 60 | Bricolage 700 | Hero only, one per page |
| H1 | 40 / 44 | Bricolage 700 | Page title |
| H2 | 30 / 36 | Bricolage 600 | Section |
| H3 | 22 / 30 | Inter 600 | Subsection |
| Body L | 18 / 28 | Inter 400 | Marketing body |
| Body | 16 / 24 | Inter 400 | Default |
| Small | 14 / 20 | Inter 400 | UI, table cells, captions |
| Micro | 12 / 16 | Inter 500 | Labels, badges, metadata |
| Code | 14 / 22 | JetBrains 400 | Paths, snippets |

### Typography rules

1. **Never set body copy in Bricolage.** Nothing under 24 px.
2. **Never set headings in JetBrains Mono.** Monospace means "this is literal text from a file," and it should keep meaning only that.
3. **Two weights per screen.** Regular plus one emphasis weight. Weight contrast should carry hierarchy before size does.
4. **Measure: 60–75 characters** for body text. Marketing copy sits at the lower end.
5. **Sentence case everywhere.** No all-caps except Micro-step badges, which take `0.06em` tracking.
6. **Never fake a weight.** No synthetic bold or italic — load the real cut.

### Fallbacks

```css
--font-display: 'Bricolage Grotesque', 'Inter', system-ui, sans-serif;
--font-text:    'Inter', system-ui, -apple-system, 'Segoe UI', sans-serif;
--font-code:    'JetBrains Mono', 'SF Mono', Menlo, Consolas, monospace;
```

All three are open source, which matters: a developer tool should ship a brand that anyone can rebuild without a licence.

---

## 9. Layout, shape and motion

**Spacing** — 4 px base unit. Use 4, 8, 12, 16, 24, 32, 48, 64, 96. Nothing between.

**Radii** — `4px` inputs and badges · `8px` cards and buttons · `12px` panels and modals · `999px` pills only. The mark's file rectangle uses the same visual language; keep corners consistently soft.

**Borders** — 1 px, always. Emphasis comes from surface elevation and colour, not thicker strokes.

**Elevation** — on dark, elevate with surface colour (`deep-900` → `deep-800` → `deep-700`), not shadow. On light, one shadow only: `0 1px 3px rgba(12,16,19,.08), 0 1px 2px rgba(12,16,19,.04)`.

**Motion** — 120 ms for state changes, 200 ms for entrances, `cubic-bezier(.2,0,0,1)`. Nothing bounces. Clawman is precise; precise things don't wobble. Respect `prefers-reduced-motion`.

**Iconography** — 1.5 px stroke, round caps and joins, 24 px grid, matched to the mark's weight. Lucide is the recommended set.

---

## 10. Applications

**VS Code activity bar icon** — mono mark, 24 px, `currentColor` so it inherits VS Code's own active/inactive theming. Never the two-tone version.

**Marketplace icon** — 128 × 128. Two-tone mark on `deep-900`, mark occupying 60% of the canvas, centred.

**README hero** — dark lockup on `deep-900`, 320 px wide, centred, with the tagline in Inter 400 `silt-300` beneath it.

**Website hero** — Display in Bricolage 700 `ink-900` on `sand-100`, or `sand-100` on `deep-900`. One Shell CTA. A product screenshot beats an illustration every time.

**Social / OG image** — 1200 × 630, `deep-900` background, dark lockup upper-left, tagline in Display size, mark bleeding off the lower-right corner at ~40% scale in `deep-800`.

---

## 11. Quick check before shipping

- [ ] Is there exactly one Shell accent in this view?
- [ ] Is every status colour paired with an icon *and* a label?
- [ ] Is all display type above 24 px, and all body type in Inter?
- [ ] Are all file paths in JetBrains Mono?
- [ ] Sentence case throughout — no Title Case, no all-caps?
- [ ] Zero exclamation marks, zero banned words?
- [ ] At most one joke on screen?
- [ ] Does the copy name the actual thing — the file, the count, the date?
- [ ] Does the mark have full clearspace, in an approved colourway?
- [ ] Does every text pairing clear 4.5:1?

---

*Clawman brand guidelines v1.0. Source files in `brand/`. Interactive reference: `brand/style-guide.html`.*
