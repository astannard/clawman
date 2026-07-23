---
layout: page
title: API
eyebrow: Rule packs, machine readable
lede: Clawman's built-in rule pack templates are also published as a small public JSON feed, so other tools can consume the same packs without depending on the extension.
permalink: /api/
---

## rules.json

```
GET {{ site.url }}{{ site.baseurl }}/api/rules.json
```

Returns the rule packs Clawman offers when you generate a `CLAUDE.md` or `.cursorrules` file — the same ones shown, checkbox-selectable, in the sidebar.

```bash
curl {{ site.url }}{{ site.baseurl }}/api/rules.json
```

### Shape

```json
{
  "version": 1,
  "updated": "2026-07-21",
  "packs": [
    {
      "id": "Node/JavaScript",
      "label": "Node / JavaScript",
      "detect": "package.json",
      "template": "## JS Guidelines\n- Use ES6+ syntax.\n- Handle promises with async/await."
    }
  ]
}
```

| Field | Type | Meaning |
|---|---|---|
| `version` | number | Bumped only on breaking shape changes. Pin to it if you depend on the structure. |
| `updated` | string (date) | Last time any pack's template changed. |
| `packs[].id` | string | Stable identifier. Matches the pack names shown in the Clawman sidebar. |
| `packs[].label` | string | Human-readable name. |
| `packs[].detect` | string | The marker file Clawman looks for to decide a project matches this pack. |
| `packs[].template` | string | The Markdown block appended to `CLAUDE.md` / `.cursorrules` when the pack is selected. |

### Stability

Read-only, unauthenticated, no key required. New packs get appended over time; existing `id`s and `detect` values don't change shape without a version bump.

### Caching

This is a static file served with normal CDN caching, not a live endpoint — if you're polling it from a script or CI job, cache on your side too and check it at most once a day.

<div class="callout" markdown="1">
Want a pack that isn't here? Open an [issue]({{ site.repo }}/issues) with the stack, the marker file Clawman should key off, and the rules you'd want in it.
</div>
