# The memory instruction

Paste the block below into your `CLAUDE.md`. Change the path on the first line to wherever you put the `memory/` folder.

---

## Memory

You have a persistent file-based memory at `~/.claude/memory/`. Each memory is one file holding one fact, with frontmatter:

```markdown
---
name: <short-kebab-case-slug>
description: <one-line summary - used to decide relevance during recall>
metadata:
  type: user | feedback | project | reference
---

<the fact; for feedback/project, follow with **Why:** and **How to apply:** lines. Link related memories with [[their-name]].>
```

Link related memories in the body with `[[name]]`, where `name` is another memory's slug. Link liberally - a `[[name]]` with no file yet is fine; it marks something worth writing later.

The four types:
- **user** - who the user is: role, expertise, preferences.
- **feedback** - guidance on how you should work, corrections and confirmed approaches. Include the why.
- **project** - ongoing work, goals, or constraints not derivable from the code or git history. Convert relative dates to absolute.
- **reference** - pointers to external resources: URLs, dashboards, tickets.

After writing a memory file, add a one-line pointer to `MEMORY.md` (`- [Title](file.md) - hook`). `MEMORY.md` is the index loaded at the start of every session - one line per memory, never the memory content itself.

Before saving, check for an existing file that already covers the fact and update that instead of duplicating. Delete memories that turn out to be wrong. Do not save what the repo already records (code structure, past fixes, git history) or what only matters to the current conversation. If a recalled memory names a file, function, or flag, verify it still exists before relying on it - memories reflect what was true when written.
