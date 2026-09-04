# Promptophyte
### Level 1 — A ground-up guide to building software with an AI, for someone who's never done it before

*This is Level 1 — the full walkthrough at a comfortable altitude.
There's a companion document, **Level 2: Going Deeper**, for whenever
a specific term (Docker, localhost, linter, and the rest) stops you
mid-question and you want the real explanation behind it. You don't
need it to follow along here — just know it's there.*

---

## Before We Start

If you know how to open a file browser, find a file, and browse the
web — you already have everything you need to get started. Everything
else in this handbook, we'll build from there.

Here's the secret nobody tells you up front: **you are never going to
write a line of code.** Your job is to be the *Product Manager* — the
person who decides *what* gets built and *why*, in plain English. An
AI coding assistant does the actual typing. Your job is closer to
being a good client than being a programmer: you know what you want,
you know what "done" looks like, and you ask good questions when
something doesn't sound right.

Everything in this handbook exists to help you do that job well — and
we'll use a running example the whole way through: **TidyList**, a
simple shared to-do and grocery list for two people living together.
It's small, it's realistic, and it's the kind of project this whole
process is built for.

---

## Part 1: The Big Picture

### What is a "Product Manager," really?

In a company, a Product Manager doesn't write code, doesn't design the
buttons, and doesn't set up the servers. Their whole job is to answer
one question over and over, from every angle: **"What, exactly, are we
building, and why?"**

That sounds simple. It isn't. "I want a shared to-do list for my
household" sounds like a complete idea — but it's actually missing
about thirty decisions. Can more than one person edit it at the same
time? What happens if two people are editing the same item at once?
Does it work from your phone when you're not home, or only on your
home WiFi? What happens if the server it's running on crashes and
loses everything?

None of those questions are "technical" in the sense of requiring you
to know how to code. They're all questions about *how you actually
want to use the thing* — which means you're the only person who can
really answer them. An AI left to guess will make a reasonable-sounding
choice and move on, and you won't find out it guessed wrong until
you're using the app and something breaks in a way that annoys you.

### Why not just say "build me an app" and see what happens?

You could. It would even produce *something*. But here's what tends to
go wrong: the AI fills in every gap with its own best guess, and AI
coding assistants have a specific bad habit — they tend to guess
*big*. Ask for a simple shared list, and left alone, an AI will often
quietly add user accounts, a login screen, and a permissions system
"just in case," because those are common patterns in real software.
That's not a small app anymore. That's hours of extra, unwanted
complexity, for a feature you never asked for and now have to
maintain.

The fix isn't "give better instructions in one shot." It's **asking
the right questions in the right order, before any code gets written**
— which is exactly what "the meta-prompt" is for.

---

## Part 2: Words You'll See

A short glossary — just enough to follow along. You don't need to
memorize this; come back to it whenever a term trips you up. (For a
deeper dive on several of these — repository, commit, and more — see
Level 2. And once you actually start the interview, the AI will keep
building a personalized glossary of every term specific to *your*
project — more on that in Part 6.)

- **File** — a single document on a computer (a photo, a text
  document, a piece of code). You already know this one.
- **Folder** — a container that holds files, and can hold other
  folders. Also one you already know.
- **Repository (or "repo")** — think of it as a special folder for a
  software project that also keeps a complete history of every change
  ever made to it, so nothing is ever truly lost, and you can always
  see who changed what and when.
- **Code** — the actual instructions that make an app work, written in
  a programming language. You'll see it, but you'll never need to
  write it.
- **Terminal** — a plain, text-only window where you type commands
  instead of clicking icons. It looks intimidating the first time and
  becomes completely ordinary by the third.
- **AI coding agent** — the AI that actually writes and edits the
  code. Think of it as an extremely fast, extremely literal junior
  developer who needs clear instructions and occasional supervision.
- **Prompt** — the instructions you give an AI. "The meta-prompt" is
  just one very well-built prompt, designed to interview *you* before
  any building starts.
- **Commit** — a saved checkpoint of the code at a specific moment,
  with a short note describing what changed. Like a save point in a
  video game, except every save point is kept forever.

---

## Part 3: What the Meta-Prompt Actually Is

The meta-prompt is a single, long, reusable set of instructions. You
paste it in at the very start of a new project, fill in one sentence
describing your idea, and it turns the AI into an interviewer —
walking you through a structured set of questions about the app you
want to build, in plain language, before a single line of code gets
written.

Think of it like a contractor walking through a house renovation with
you before swinging a hammer: "Do you want the wall load-bearing or
not? Where do you want outlets? One bathroom or two?" Every one of
those questions is cheap to answer *now* and expensive to fix *later*.
The meta-prompt is that same walkthrough, but for software.

It's built around three ideas that matter enough to say up front:

1. **Nothing gets assumed.** Every meaningful decision gets asked
   about explicitly, in a multiple-choice format, so you're choosing
   between real options instead of guessing what's possible.
2. **The questions scale to you and the project.** A weekend
   experiment doesn't get asked the same 13 categories of questions as
   something you intend to run for years — and someone who's never
   done this before gets a different level of explanation than someone
   who has. More on both in a moment.
3. **The answers become the AI's marching orders.** Everything you
   decide during the interview gets turned into written instruction
   files the AI reads before and during every work session — so it
   doesn't forget your answers three conversations from now.

---

## Part 4: The Mechanics — What This Actually Looks Like on Screen

Here's the literal, step-by-step version:

1. **Open whichever AI coding tool you're using** — this could be
   Claude Code, or even just a plain chat conversation with Claude,
   depending on what you have access to. Any of them work; the
   meta-prompt itself does the heavy lifting.
2. **You'll fill in one sentence** describing your idea, right at the
   top of the prompt, in your own words. No jargon required — "an app
   where my roommate and I can both check off items on a shared
   grocery list" is a completely sufficient sentence.
3. **First, it checks whether you'd be reinventing the wheel.** Before
   anything else, the AI does a quick search for existing free or
   open-source projects that already do roughly what you described,
   and gives you a plain-language summary: what's out there, how close
   a fit it looks, and what real gap (if any) is still left. It'll
   then ask you directly whether you'd rather adapt something that
   already exists or still build this yourself. Building it yourself
   is always a perfectly good answer, even when something close
   already exists — this step is just there so that's a choice you're
   making on purpose, not by accident.
4. **Then it asks one question**, always: how big is this project?
   (More on this in Part 5 — it changes everything else.)
5. **Then it asks one more question**: how much experience do you
   have with this kind of thing? (More on this in Part 6 — it changes
   how much explaining happens along the way.)
6. **Then it interviews you**, one or two topics at a time, always
   explaining *why* it's asking before it asks. You'll see something
   like:

   > **PM 101:** Loading, empty, and error states are what a screen
   > shows while something's happening, when there's nothing to show
   > yet, or when something goes wrong — designing for these up front
   > is the difference between an app that feels finished and one that
   > feels like a rough sketch.
   >
   > **Question:** Should we design explicit loading/empty/error
   > states for each screen, or leave it to the framework's defaults?
   > 1. Design them explicitly (recommended for anything you'll use
   >    regularly)
   > 2. Leave it to defaults (fine for a quick prototype)

   You just pick a number, or type your own answer if none of the
   options fit. If you genuinely don't have a preference, you can also
   just say "you pick" — the prompt is built to offer its own
   recommendation and let you accept it instead of forcing you to
   have an opinion on everything.
7. **Once every relevant question is answered**, the AI writes out a
   set of files — instructions, documentation, a project plan — that
   become the permanent record of everything you decided (Part 8
   covers what these actually are).
8. **Then, and only then, does building start.** From here it feels
   more like watching a very fast, very communicative contractor work
   — it'll tell you what it just built, in plain language, after every
   meaningful chunk (Part 9).

---

## Part 5: How Big Is This Thing?

Once the prior-art check is out of the way, you'll be asked to pick
one of three sizes. This matters *enormously* — it decides how many
of the questions in Part 7 actually get asked, so a weekend experiment
doesn't get put through the same wringer as something meant to last
years.

- **Prototype/experiment** — "I just want to see if this idea even
  works, and it's fine if I throw it away." Only a handful of the
  most basic questions get asked. Fast, disposable, low-commitment.
- **Small personal/self-hosted app** — "This is a real tool I'll
  actually use, probably just me or a small group, running on
  something I control." **This is TidyList.** Every category gets
  asked, but the AI is instructed to keep the heavier-duty questions
  (like automated deployment pipelines) at their lightest, simplest
  version rather than the full enterprise treatment.
- **Growing app** — "I expect this to have real, ongoing usage, or
  grow substantially over time." Everything gets asked, in full, no
  shortcuts.

If it's not obvious which one fits, the prompt is instructed to just
ask you rather than guess — so you never have to figure this out
alone.

---

## Part 6: How Much Do You Already Know?

This is a separate question from Part 5, and it doesn't get asked
about the *project* — it gets asked about *you*. It exists because
"explain everything from scratch" is exactly right for some people and
actively patronizing for others, and the meta-prompt has no way of
knowing which one you are unless it asks.

- **None** — "I've genuinely never done anything like this before."
  Every question gets a plain-language explanation first, the AI
  checks that you actually understood before moving on rather than
  assuming one explanation landed, and it keeps a running, personal
  **Glossary** (see Part 8) of every term it explains, in the order it
  actually came up for your project.
- **Some** — "I've picked up bits and pieces." Explanations still
  happen, just kept brief.
- **Experienced** — "I already know this territory." The hand-holding
  gets skipped by default — you can always ask for an explanation of
  anything specific, but you won't be told what a database is unless
  you ask.

If you're not sure which one describes you, "None" is always a safe
choice — worst case, you get a little more explanation than you
strictly needed, which costs you nothing but a few extra sentences.

---

## Part 7: The Interview, Category by Category

Here's every topic you'll actually get asked about, explained in
plain language, with what it might mean for TidyList specifically.
You won't get every single one of these on every project — Part 5
decides which apply — but this is the full map.

### 1. Core Features & Scope
**The question:** What absolutely has to work for this to count as
"done"? And — just as important — what are we deliberately *not*
building, even if it sounds like a nice extra?
**Why it matters:** Without a clear "not doing this" list, an AI
tends to quietly build things you never asked for, because they seem
like natural additions. Saying "no login system, no notifications, not
right now" up front keeps the project the size you actually wanted.
**For TidyList:** Add an item, check it off, delete it, and everyone
sharing the list sees the same thing — that's it. No accounts, no
notifications, not in version one. *(A Non-Goal isn't permanent — if
you change your mind down the road, just say so. The AI is instructed
to flag that it conflicts with an earlier decision, confirm you
actually want to reverse it, and update the paperwork to match, rather
than either refusing outright or quietly building it without telling
you the project's own documentation is now out of date.)*

### 2. UI/UX & Interaction Design
**The question:** What does this look like and feel like to use — does
it even need a visual screen, and how polished should it be?
**Why it matters:** Decisions here (like "does this need to work well
on a phone screen, not just a laptop") are cheap to plan for up front
and expensive to bolt on after the fact.
**For TidyList:** Simple pages, minimal styling (not a fancy component
library), and it has to work well on both a phone and a laptop, since
everyone using it will be checking it from their own device.

### 3. Architecture & Environment
**The question:** How does this actually get built and run — is it a
single file you just run directly, or something more involved? And if
it's sharing a computer with other projects, how much of that
computer's resources can it use? Also: what operating system does this
actually need to run and be set up on — and is that the same computer
the AI is coding on right now, or a different one?
**Why it matters:** Source code by itself doesn't run — something
always has to turn it into a working program, and that "something"
should be chosen on purpose, not out of habit. And commands genuinely
differ between operating systems — something Windows and something
Mac/Linux each expect can look completely different (a Windows setup
never uses `sudo`, for instance) — so this needs a real answer, not an
assumption based on wherever the AI happens to be working.
**For TidyList:** A single lightweight script, no complicated build
process, running on a small home server. Everyone reaches it through
an ordinary browser, so nobody's own computer needs its own setup step
at all. *(If "single script vs. containers" doesn't quite make sense
yet, Level 2 has a full breakdown of what a container actually is.)*

### 4. Performance & Data
**The question:** If more than one person uses this, what happens when
two people edit the same thing at nearly the same moment? And if the
data itself will change shape over time, how do those changes get made
safely?
**Why it matters:** This isn't a hypothetical — it *will* happen the
first time two people are looking at the list at once, and if nobody
decided what should happen, the app decides for you, silently.
**For TidyList:** Simplest option — if two people save changes at
nearly the same moment, the most recent one wins. No complicated
merging.

### 5. Security & Compliance
**The question:** Who can actually reach this app in the first place —
just your home network, or from anywhere? And how are outside code
libraries the app depends on kept safe and up to date?
**Why it matters:** This should be a deliberate choice, not something
that happens to you by accident because of how the network was set up
later.
**For TidyList:** Home network only, nothing exposed to the public
internet. *(Level 2 walks through exactly what "home network only" vs.
"public internet" means in practice — localhost, LAN, VPN, and the
rest of that vocabulary.)*

### 6. Reliability & Fault Tolerance
**The question:** What happens when something breaks? If real data is
being stored, how does it survive a crash, and who's checking on
upkeep tasks (like making sure logs aren't quietly filling up the
disk) over time?
**Why it matters:** These are the chores that don't cause a problem
the day the app ships — they cause a problem three months later, when
nobody remembers to check.
**For TidyList:** A simple, periodic copy of the data file as a
backup, checked on manually rather than automated.

### 7. Maintainability
**The question:** Can you (or the AI, months from now) pick this
project back up easily? Can you get your own data out in a plain
format if you ever need to? And how do we prove a feature actually
works, not just that the code looks right?
**Why it matters:** "The code looks correct" and "the feature actually
works when you use it" are different claims — plenty of real bugs only
show up when something is actually clicked, saved, and reloaded.
**For TidyList:** One setup script gets it running from scratch, and
every feature has to be proven working by actually using it — not just
reading the code back.

### 8. Codebase Navigability & AI-Agent Context Management
**The question:** How does the AI keep track of a growing project
without getting lost or forgetting earlier decisions?
**Why it matters:** This one's entirely about helping the *AI* work
well, session after session — it doesn't change what you experience
using the app, but it changes how reliably it gets built and
maintained correctly over time.
**For TidyList:** Kept simple — one instructions file at the top of
the project rather than a separate one for every folder, since the
app itself is small.

### 9. CI/CD & Release Process
**The question:** How does a finished change actually make it into the
running app — automatically, or do you approve each one? Is there a
safety check that runs before anything ships?
**Why it matters:** This is what stops a broken change from reaching
the app you actually use.
**For TidyList:** Skipped for now — changes get pulled and run
manually. Nothing wrong with adding this later if the project grows.
*(Level 2 covers what CI/CD, a "pipeline," and staging vs. production
actually mean, for whenever this one does come up.)*

### 10. Observability
**The question:** If something breaks, how do you find out?
**Why it matters:** This is different from #6 — Reliability is about
surviving a problem, Observability is about *noticing* one happened at
all.
**For TidyList:** A basic log file that records errors — nothing
fancy needed at this scale.

### 11. Project Continuity & Decision Log
**The question:** Should the AI keep a running written record of *why*
it made each significant decision, so a future session (which starts
with zero memory of past conversations) doesn't quietly contradict an
earlier choice?
**Why it matters:** Every AI coding session starts fresh — this is the
project's memory.
**For TidyList:** Yes, kept lightweight — a short note per real
decision, not a novel.

### 12. Licensing *(skipped for private projects)*
**The question:** Only relevant if you'd ever share or open-source
this project — what license governs how others can use your code?
**For TidyList:** Skipped — it's just for your own household.

### 13. Development Tooling & Automation
**The question:** Which free, automatic helper tools should watch this
project for mistakes — a spell-checker for code, essentially?
**Why it matters:** These don't change what the app *does* — they
catch small mistakes (a typo, an outdated dependency, a committed
password) automatically, before they become real problems.
**For TidyList:** Just the lightest, nearly-free basics — a
formatter/linter that runs before anything is saved, and a check for
outdated or risky dependencies. Nothing else earns its keep at this
size. *(Level 2 explains exactly what a linter and formatter are
actually doing behind the scenes.)*

---

## Part 8: What You Get at the End of the Interview

Once the questions are done, the AI writes several files. You'll never
need to write these yourself — just know what they're *for*, so
they're not just mysterious files sitting in a folder:

- **The Product Requirements Document (PRD)** — the master summary of
  everything you decided: what the app does, what it deliberately
  doesn't do, and why. If you ever forget "wait, did we decide to add
  logins later or not?" — this is where you look.
- **The root instructions file (CLAUDE.md)** — this one isn't really
  for you, it's the AI's own rulebook for this specific project,
  written from everything you both decided. It's why the AI doesn't
  "forget" your answers between conversations.
- **The Module Index** — a running table of contents for the project
  itself, so the AI (or a completely fresh session) can find the right
  part of the code without having to re-read the whole thing every
  time.
- **The starter automation pipeline** *(only if you asked for one)* —
  the actual working setup for the automatic checks decided in
  category 9 and 13, ready to go from the first change rather than
  something built later.
- **The Decision Log** — the running diary of *why* things were built
  the way they were, so a choice made in week one doesn't get silently
  undone in week six by an AI that's forgotten the reasoning.
- **The Task Checklist** — every "Must Have" feature broken into small,
  ordered steps, checked off as each one is actually built and proven
  to work. This is the one you'll actually want to glance at mid-build
  — it's a running answer to "what's done and what's left," instead of
  having to piece that together from memory of past recaps.
- **The Glossary** *(only for the None or Some experience level from
  Part 6)* — every term explained during your interview or build,
  written down live, in your own words, as it came up. This becomes a
  personalized reference built from exactly the concepts that actually
  came up for your project — not a generic document written for a
  hypothetical reader.

---

## Part 9: What Building Actually Looks Like

Once the interview's done and building starts, here's what to expect
— this part is genuinely just watching and occasionally answering a
question, nothing technical required from you:

1. **It double-checks its own paperwork first.** Before touching any
   code, the AI re-reads everything decided so far and checks it for
   contradictions — did a later answer accidentally conflict with an
   earlier one? If it finds one, it stops and flags it to you rather
   than quietly picking a side.
2. **It checks its own toolbox next.** The AI checks whether everything
   it needs (the right software, the right versions) is actually
   available on the computer it's working on, tells you plainly what's
   missing before going further, and confirms that matches the
   operating system decided in category 3 — flagging it plainly if the
   two don't match, rather than assuming any setup instructions written
   for one will work on the other.
3. **It narrates as it goes**, in plain language — after finishing a
   real chunk of work, you'll get a short recap: what it built, why it
   made a notable choice, what's next, and the Task Checklist updates
   to match. If you want more detail on anything, just ask "why" —
   it'll go deeper, but only when you ask.
4. **It proves things actually work**, not just that the code reads
   correctly — for something like saving a grocery item, that means
   it actually adds one through the app and checks it's really there
   afterward, the same way you would.
5. **It asks before doing anything risky or permanent** — saving
   changes permanently to the project's history, or deleting anything,
   always gets flagged to you first with a plain explanation of what
   changed, rather than happening silently in the background.

---

## Part 10: Why the AI Says No Sometimes

Every project also comes with a set of standing rules that apply no
matter what — think of these less as restrictions and more as the
same kind of safety habits a good contractor already has, regardless
of which house they're working on:

- It won't rewrite an entire file for a small fix — small, targeted
  changes only, so a one-line bug fix doesn't turn into an
  unrecognizable file.
- It double-checks that a tool or code library actually works the way
  it thinks before relying on it, instead of trusting its own memory.
- It matches the complexity of the solution to the size of the
  project — no enterprise-grade complexity on a small household app.
- If the same fix fails twice in a row, it stops and explains what's
  going wrong in plain language instead of quietly trying variations
  of something that isn't working.
- It never permanently saves a change, or deletes/resets anything,
  without telling you what it's about to do first and getting your
  go-ahead — even if the technical settings would otherwise allow it.

If it ever tells you "no, not without checking with you first" — that's
the system working exactly as intended, not something going wrong.

---

## Cheat Sheet — Once You've Read Everything Else Once

- **You never write code.** Your job is deciding what and why.
- **Paste the meta-prompt in, fill in one sentence about your idea.**
- **First, it checks if something like this already exists** —
  building it yourself is still a fine answer even if it does.
- **Answer the size question next** — it decides how much else gets
  asked.
- **Then it asks how much experience you have** — answer honestly;
  "None" costs you nothing but a few extra sentences of explanation.
- **Every question comes with a plain-language "why" before it's
  asked** — if it doesn't make sense, ask it to explain differently.
- **You can say "you pick"** if you don't have a preference — the
  prompt is built to offer its own recommendation.
- **Nothing permanent happens without it telling you first** — a
  saved checkpoint, a deletion, anything risky always gets flagged.
- **After building starts, you'll get a plain-language recap after
  each chunk of work** — ask "why" any time you want more detail.
- **If you're ever lost, come back to Part 2** for the glossary, check
  **Level 2** for a deeper dive on a specific term, or just ask the AI
  to explain whatever tripped you up in simpler terms. There's no such
  thing as a bad question here.
