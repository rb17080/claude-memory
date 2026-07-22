---
name: project-example
description: The thing being built - what it is and the one constraint that matters (EXAMPLE - replace with your own)
metadata:
  type: project
---

Building a personal dashboard app (local Python + SQLite). The database holds months of hand-collected data and is not backed up anywhere else.

**Why:** Losing it means losing work that cannot be re-created.
**How to apply:** Back up the database file before any operation that writes to or migrates it. Never run a destructive command against it without saying so first. Related voice rules in [[feedback-example]].
