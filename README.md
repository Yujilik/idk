# idk

A brainstorming partner skill for Claude Code and ClaudeAI. It asks the right questions at the right moment to unstick your thinking, and keeps a live document of the conversation as you go.

The name comes from "I don't know", which is honestly where most good brainstorm sessions start.

## Why this exists

I built `idk` because I needed it. I kept getting stuck in my own head, circling the same thoughts, not knowing how to get them out. I wanted something that could sit with me, ask the right thing at the right time, and help me actually see what I was trying to say.

So yeah, this came from a real need. If you've ever stared at a blank doc or spiraled on a decision, hopefully it helps you too.

## Core idea

> *The right question at the right moment unclogs more than ten well crafted answers.*

`idk` isn't really about giving you answers. It's about asking you things in a way that helps you find your own. The main output isn't chatbot text, it's a markdown file the two of you build together while you talk.

## Language

The skill itself is written in English (so more people can read and contribute), but it **speaks your language by default** (`LANGUAGE=mirror`). Write to it in Portuguese and it replies in Portuguese, names sections in Portuguese, all of it. The English source is just the underlying structure. The conversation and the live doc adapt to you.

## Structure

```
idk/
├── SKILL.md              # Claude Code version (filesystem based)
├── README.md             # This file
├── .idkonfig.example     # Config template (Claude Code only)
├── references/           # Loaded on demand by Claude Code version
│   ├── frameworks.md
│   ├── adversarial.md
│   ├── templates.md
│   └── help.md
└── ClaudeAI/
    └── SKILL.md          # claude.ai version (self contained, artifact based)
```

There are two flavors of the skill in this repo:

- **Claude Code version** (root `SKILL.md`): uses the filesystem. Session live docs are loose `idk-[topic].md` files in whatever directory you invoked the skill from. Supports cross session features (list, resume, stats) via `Glob`. References load on demand.
- **claude.ai version** ([`ClaudeAI/SKILL.md`](ClaudeAI/SKILL.md)): self contained in a single file with inline catalogs. Uses **artifacts** for the live doc because claude.ai doesn't have a per user filesystem. One conversation equals one session. No cross session features.

## How it works

1. **Opens a session.** Talk to it like a person. Stuff like "help me think about X" or "I'm stuck on Y" works great. `idk` first checks for existing `idk-*.md` files in the current directory. If it finds any, it lists them and asks if you want to continue one. If not, it asks for a 2 to 4 word topic and creates `idk-[topic].md`.
2. **Adaptive conversation.** It starts Socratic to map out what's going on. When the shape of the problem is obvious, the skill **just applies a framework** (5 Whys when you're vaguely unhappy, weighted pros and cons when you're torn between A and B, pre mortem when the plan is basically decided, etc). You can always redirect with "switch" or "explore more". When things are ambiguous, it offers you 2 or 3 options. Goes back to Socratic whenever new ambiguity shows up.
3. **Adversarial mode, if you want it.** Say "challenge this", "play devil's advocate", or "push back on me" to flip into sparring mode. `idk` will poke at your assumptions, look for holes, and call out fallacies. Exit with "pause" whenever you've had enough.
4. **Live doc.** The `idk-[topic].md` file updates on every substantive turn. It holds the problem, context, options you've considered, current (tentative) decision, open questions, and next steps.
5. **Resume.** "resume brainstorm X" (or pick a session when you open the skill) loads the doc, summarizes where you left off, and picks things back up.
6. **Close and telemetry.** "close this session" marks the final state (resolved, parked, or abandoned), timestamps it, and records which frameworks got used. After a few sessions, try "idk stats". The skill reads your history, shows which framework you tend to work best with, and offers to set a default in `.idkonfig`.
7. **Subfolder, opt in.** Files sit loose by default. If you want them in a folder, just ask: "create a dir for this" or "put it in a folder".

## Scope

Generalist. It figures out the domain in the first few turns and adapts:

- **Technical project**: engineering vocabulary, frameworks like MECE and pre mortem
- **Personal decision**: 5 Whys, Eisenhower, Wheel of Life
- **Writing or content**: thesis, argument, evidence, hierarchical outline
- **Business or product**: SWOT, JTBD, pre mortem
- **Generic**: pure Socratic until things get clearer

If it guesses the domain wrong, it'll switch templates without losing anything you've already written.

## Installation and usage

### Claude Code (desktop / CLI)

1. Put the `idk/` folder wherever Claude Code loads skills from.
2. Claude picks it up automatically via `SKILL.md` and its frontmatter.
3. Open a conversation in any working directory and use one of the triggers listed in [references/help.md](references/help.md). Session files get created in the cwd.

### claude.ai (web and mobile, including iOS and Android)

1. Zip the contents of the [ClaudeAI/](ClaudeAI/) folder (just the `SKILL.md` inside) into `idk.zip`.
2. On claude.ai web: Settings → Customize → Skills → Upload skill → pick `idk.zip`.
3. On mobile: once it's uploaded on the web, the skill is available in any conversation on your account, including the mobile apps.
4. Open a conversation and use any trigger (*"help me think about X"*, *"tô empacado"*, whatever feels natural). The live doc shows up as an **artifact** in the side panel. Close with *"close this session"* to get the full template shaped summary.

**Heads up on the claude.ai version:** one conversation equals one session. There's no `idk stats`, no resume across conversations, and no `.idkonfig`. You state your preferences inline or in the Project's custom instructions. The acceptance test is that closing a session produces a filled out template in the artifact.

## Configuration

See [.idkonfig.example](.idkonfig.example). Supported variables:

- `LANGUAGE`: output language (default: `mirror`, follows you)
- `SESSIONS_DIR`: where to save docs (default: `.`, your cwd)
- `DEFAULT_MODE`: `adaptive` or `adversarial` (default: `adaptive`)
- `TONE`: optional override (`more_terse`, `more_warm`, `more_blunt`)
- `AUTO_APPLY_FRAMEWORKS`: `true` (default) applies directly on high confidence, `false` always asks first
- `DEFAULT_FRAMEWORK_*`: preferred framework per domain (technical, personal, writing, business, generic)

Copy it to `.idkonfig` to turn it on. Resolution order: cwd `.idkonfig` (per project), then skill dir `.idkonfig` (global), then defaults.

## Frameworks available

Full catalog in [references/frameworks.md](references/frameworks.md): 5 Whys, MECE, SWOT, Pre mortem, SCAMPER, Eisenhower Matrix, Decision Tree, Weighted Pros and Cons, Jobs to be Done, First Principles, Inversion, Wheel of Life.

`idk` offers one when the problem shape fits. You can also just ask for one directly.
