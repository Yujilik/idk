# idk — help

Brainstorming partner. Asks the right questions at the right time to unstick thinking. Keeps a live document of the conversation at `idk-[topic].md` (loose file in whatever directory you're working in, by default).

Note: this skill is written in English but speaks your language by default (`LANGUAGE=mirror`). If you write in Portuguese, it answers in Portuguese, names sections in Portuguese, etc.

## Getting started

Talk naturally. Any of these opens a session:

- "help me think about X"
- "I'm stuck on Y"
- "I don't know where to start with Z"
- "brainstorm about W"
- "I need to decide between A and B"

If the current directory already has sessions (`idk-*.md`), the skill first lists what it found and asks whether to continue one or open a new one. If there are none, it asks for a 2-4 word topic and creates `idk-[topic].md` in the directory you're in.

Session files are **always loose** (one markdown per topic, directly in the directory) unless you explicitly ask to organize into a subfolder.

## Modes

**Adaptive (default).** Starts Socratic, pulls a framework when the problem shape is clear, goes back to Socratic when new ambiguity appears.

**Adversarial (opt-in).** Activate with: "challenge this", "play devil's advocate", "push back on me", "sparring mode", "poke holes", "break my idea". Attacks the idea to find holes. Deactivate with "pause".

## Session commands

| I want to... | I say... |
|--------------|----------|
| Open session (or continue existing) | One of the opening triggers above, or "start a brainstorm on X" |
| See my sessions | "list brainstorms" |
| Continue a specific session | "resume brainstorm X" (or pick one during opening) |
| Request a specific framework | "run 5 whys / swot / pre-mortem / [name]" |
| Redirect when the skill auto-applied a framework | "switch" or "explore more" |
| Enter critic mode | "challenge this" |
| Go back to normal | "pause" |
| Close session | "close this session" |
| See framework usage stats | "idk stats" / "my frameworks" |
| Organize into a subfolder | "create a dir for this" / "put it in a folder" |

## Available frameworks

5 Whys, MECE, SWOT, Pre-mortem, SCAMPER, Eisenhower, Decision Tree, Weighted Pros/Cons, Jobs-to-be-Done, First Principles, Inversion, Wheel of Life.

You don't need to decide which one to use. The skill detects the problem shape and:

- **Applies directly** when the shape is canonical (ex: "I'm torn between A and B" → pros/cons; "I'm drowning" → Eisenhower). Redirect with "switch" if you don't like it.
- **Offers 2-3 options** when multiple frameworks fit.
- **Stays Socratic** while the shape is still fuzzy.

Want to jump ahead? Ask explicitly: "run 5 whys", "apply pre-mortem". Prefer to always pick yourself? Set `AUTO_APPLY_FRAMEWORKS=false` in `.idkonfig`.

## Config

See `.idkonfig.example` at the skill root. Main variables:

- `LANGUAGE` — output language (default: mirror yours)
- `SESSIONS_DIR` — where to look for and save docs (default: `.` = cwd)
- `DEFAULT_MODE` — `adaptive` or `adversarial`
- `TONE` — optional tone override
- `AUTO_APPLY_FRAMEWORKS` — `true` applies on high confidence; `false` always offers
- `DEFAULT_FRAMEWORK_*` — pins your preferred framework per domain (use "idk stats" to find out which)

## Principle

> *The right question at the right moment unclogs more than ten well-crafted answers.*

If `idk` is answering too much instead of asking, say "fewer answers, more questions". If it's asking too much without direction, say "give me your take".
