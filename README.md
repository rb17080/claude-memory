# claude-memory

Give Claude a memory. Right now it forgets you the moment a chat ends - every new session, it wakes up blind. This makes it remember: your voice, your rules, the mistake it should never repeat. And it's just plain text files you can open and read. No database, no black box.

## The difference, in one look

**Without memory** - every session, from zero:

> **You:** Draft a reply to this recruiter.
> **Claude:** Sure! Here's a friendly, professional draft: "I am thrilled and excited about this incredible opportunity..."
> **You:** No. I never write like that. I told you last time.
> **Claude:** Understood! Could you tell me about your preferred tone?

**With memory** - it already knows:

> **You:** Draft a reply to this recruiter.
> **Claude:** *(reads memory: writes plain and punchy, hyphens not em dashes, never gushes)*
> Here's a draft in your voice: "Thanks for reaching out. I'm open to hearing more - what's the team and the scope?"

Same tool. The second one just remembers who you are.

## How it works

Dead simple:

1. **A folder of tiny notes.** One fact per file. "This user writes plain, never gushes." "This project's database is critical - always back up before touching it."
2. **An index** (`MEMORY.md`) that lists every note in one line.
3. **An instruction** that tells Claude: read the index when we start, and write a new note whenever you learn something worth keeping.

That's the whole engine. Claude reads the index at the start of each session, opens any note that looks relevant, and adds new ones as it goes. No vector search, no API - just text a human can read, edit, and grep.

## Install

1. Copy the `memory/` folder into your Claude setup (e.g. `~/.claude/memory/`).
2. Paste the block from [`INSTRUCTIONS.md`](INSTRUCTIONS.md) into your `CLAUDE.md` (the file Claude reads at the start of every session), fixing the path to match where you put the folder.

That's it. Next session, Claude reads its memory. Start telling it things, or just work - it writes notes on its own.

## What's in this repo

- `INSTRUCTIONS.md` - the block you paste into `CLAUDE.md`. **This is the actual product** - it's what makes Claude use the folder.
- `memory/MEMORY.md` - an empty index, ready to fill.
- `memory/examples/` - a few fake notes so you can see the shape. Delete them once you get it.

Your real notes live on your machine and never leave it. This repo is the empty machine - you fill it.

## License

MIT
