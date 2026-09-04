# Promptophyte

**Grow a real software project from a single prompt — no coding experience required.**

---

## What this is

Promptophyte is a free, reusable prompt — plus a plain-language handbook that
teaches you how to use it — for people who want to build a small piece of
personal software with an AI, and who have *genuinely* never done anything
like this before. Not developers looking for a faster workflow. People who
know how to find a file and browse the web, and not much more than that.

The idea is in the name: *-phyte* means "a growing thing." You bring one or
two sentences describing what you want. The prompt turns your AI coding tool
into a patient product manager that interviews you — in plain English, at
your pace — until the project is defined well enough that the AI can build it
without guessing. A whole project grows out of that one prompt.

## Two ways to start

**Quick way — [`quickstart.md`](quickstart.md).** A short prompt, about
five questions, gets you to something running on your own computer fast.
Use this to find out whether your idea works before committing to the full
process. You can move up to the full version later and hand it your
half-built prototype.

**Full way — [`meta-prompt.md`](meta-prompt.md).** The complete interview.
It asks about scale, your experience level, and then works through the
project a couple of topics at a time, producing a set of planning
documents before it builds. Use this for anything you'll actually rely on.

> **Heads up: the full meta-prompt is long** — about 600 lines. That's
> deliberate; every paragraph is there to stop the AI guessing about
> something you'd care about. You don't read it yourself — you paste it and
> answer what it asks — but if it feels like a lot to start with, use the
> quickstart and come back to it.

Either way:

1. **Read the handbook first.** Start with [Level 1](handbook/level-1.md) —
   a ground-up walkthrough of the whole process, using one running example
   the entire way. Keep [Level 2](handbook/level-2.md) open in another tab
   for whenever a specific word (Docker, localhost, linter, and the rest)
   stops you and you want the real explanation behind it.
2. **Paste the prompt into your AI tool** as your first message, with your
   one- or two-sentence idea dropped into the spot marked for it near the
   top.
3. **Answer its questions.** With the full meta-prompt you can reply
   "accept defaults" at any step.

## Which AI tool should I use?

Promptophyte is just carefully written English, so it works with any tool
that can hold a conversation and write files. But they are not all equally
good at following a long, detailed set of instructions like the
meta-prompt.

**Works well:**

- **[Claude Code](https://claude.com/claude-code)** — a tool from Anthropic
  that runs in a terminal, a desktop app, or your browser. This is what the
  meta-prompt was designed and tested against. It reads and writes files,
  can run the project to check it works, and keeps long instructions
  straight. New to it? See
  [**Setting up Claude Code**](setup-claude-code.md).
- **[Claude](https://claude.ai)** or **[ChatGPT](https://chatgpt.com)** on
  their current top models — good for the interview and for smaller builds
  where you copy the files out by hand.
- **Cursor**, **GitHub Copilot**, and similar editor-based assistants —
  fine if you already have one set up.

**Be a bit careful with:**

- **Free tiers of small or older models.** A prompt as long as the
  meta-prompt can get silently cut off or only half-followed — it skips
  questions, or forgets a rule it agreed to a page earlier. The tell: it
  stops asking you questions and just starts building.
- **Tools that edit files or run commands without showing you first.**
  Being unable to judge whether a command is safe is exactly the situation
  this project is written for — so you want a tool that shows its work and
  waits for you.
- **Anything that asks you to paste a password, an API key, or card
  details into the chat.** Promptophyte never needs those. If a tool or a
  step asks, stop and find out why.
- **Unofficial "wrappers," browser extensions, or sites** offering cheap
  or free access to a big-name model. Your idea and your code pass through
  whoever runs it. Prefer the real thing from the company that makes the
  model.

**Also worth knowing:** the more capable agentic tools can run down paid
credits over a long build, and whatever you use, your project is sent to
that company's servers — pick one whose privacy policy you're okay with.

## Where this fits

There are already excellent frameworks for spec-driven and agent-driven
development — GitHub Spec Kit, BMAD, GSD, and others. Promptophyte is **not**
competing with those. They're built for people who already write code and
want more structure around an AI. Promptophyte is for the step before that:
the person who doesn't code at all and needs an on-ramp. If you outgrow this
and find yourself wanting one of those heavier frameworks, that's the tool
working — go take the next step.

## What's in here

```
quickstart.md          The short prompt — fastest path to something running.
meta-prompt.md         The full reusable prompt. The complete interview.
setup-claude-code.md   How to install and start Claude Code, from scratch.
handbook/level-1.md     The full beginner walkthrough.
handbook/level-2.md     A deeper-dive glossary for terms that come up.
```

## Feedback and questions

- **Something in the handbook is confusing, wrong, or missing?** Open an
  issue — there's a [short feedback form](../../issues/new/choose) for
  exactly this. "I got lost here and didn't know what to do" is a genuinely
  useful report.
- **Have a question, or built something with this?**
  [Discussions](../../discussions) is the place — questions in Q&A, and
  we'd love to see what you made in Show and tell.

By taking part you agree to the [Code of Conduct](CODE_OF_CONDUCT.md): this
is a space where it's safe to not know things yet.

## License and contributing

Licensed under [Creative Commons Attribution 4.0 International](LICENSE)
(CC BY 4.0) — use it, adapt it, share it, including commercially, as long as
you give credit.

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

© 2026 Promptophyte contributors
