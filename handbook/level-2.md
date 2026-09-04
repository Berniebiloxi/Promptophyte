# Promptophyte
### Level 2 — Going deeper: the words behind the words

*This is the companion to **Level 1**, which walks through the actual
interview end to end. Come here whenever a specific term stops you
mid-question.*

---

## How to Use This One

Level 1 got you through the whole interview at a comfortable altitude
— what each category asks and why. This one is for when a specific
term stops you mid-question and you want the real explanation, not
just enough to nod along. You don't need to read this front to back.
Bookmark it, and jump to whatever term just came up.

## First — Think of Yourself as a Renovation Client, Not a Builder

A useful way to hold everything in this document: you're the person
who hired a contractor to renovate a house. You don't need to know how
to wire a circuit or frame a wall — but you do need to understand
enough of what the contractor is telling you to make good decisions
and know when something sounds off. That's exactly the level this
handbook is aiming for. Every term below gets tied back to that same
renovation, because a building and a piece of software actually have
to solve a surprising number of the same problems — who's allowed in,
what happens when something breaks, how work gets tracked and
inspected before it's called done.

---

## "Where does this app actually *live*?" — localhost, LAN, VPN, and the public internet

**The building version:** Think of these as concentric rings of who's
allowed into a property. Some areas are private and never see a
visitor. Some are accessible to people who live there, but nobody
else. Some — like a shop on the ground floor — are open to literally
anyone walking in off the street.

**The software version, same rings, inside out:**

- **Localhost** means "only this one computer, talking to itself." No
  network involved at all — the equivalent of a closet that isn't even
  connected to the rest of the building. Nobody else can reach it, not
  even another device in the same room.
- **LAN** (Local Area Network) means "anything connected to this same
  home network" — your phone, your laptop, anyone else's device on the
  same WiFi — same as anyone who actually lives in the house. Off the
  property (off the WiFi), you're locked out.
- **VPN** (Virtual Private Network — a service like Tailscale is a
  common one) is a way to make a device *act* like it's on that home
  network even when it's physically somewhere else — like a spare key
  that works from anywhere, not just when you're standing at the door.
- **The public internet** means anyone, anywhere, unauthenticated —
  the front doors, open to the street.

**Why this comes up:** Category 5 (Security) asks you to pick one of
these on purpose, deliberately, rather than letting it happen by
accident. A typical small household app is set to LAN-only — same idea
as something that only works once you're actually inside the house.

**Related term — reverse proxy:** the software equivalent of someone
at the front door greeting every visitor before deciding which
internal hallway to send them down. It's the thing that sits between
"the public internet" ring and your actual app, deciding who gets
waved through.

---

## "What's a container, and what is Docker?"

**The building version:** Imagine every major system in a house —
heating, plumbing, electrical — got its own fully self-contained unit,
pre-built off-site with everything it needs already inside, and
dropped into place as one sealed piece. You could swap out the whole
heating unit for an upgraded one without touching the plumbing at all,
because they were never tangled together in the first place.

**The software version:** A **container** is a small, sealed package
containing an app *and* everything it needs to run — no more "it
worked on my computer but not on the server" problems, because the
container brings its entire environment with it wherever it goes.
**Docker** is just the most common tool for building and running these
containers.

**Why this comes up:** Category 3 (Architecture) asks whether a
project needs this kind of setup at all. A lot of small projects
don't — a single plain script is enough, the equivalent of a small
standalone unit that doesn't need its own sealed housing. Containers
earn their keep once a project gets complex enough that keeping pieces
cleanly separated actually matters — which is exactly why the
meta-prompt asks this instead of just defaulting to Docker out of
habit.

---

## Frontend, Backend, and what an "API" actually is

**The building version:** The **frontend** is everything a visitor
actually sees and touches — the front rooms, the finishes, the
furniture. The **backend** is everything behind the walls making that
experience possible — the wiring, the plumbing, the systems nobody
checks in on directly. A visitor never needs to know how hot water
gets to the tap; they just expect it to be there when they turn the
handle.

**The software version:** The **frontend** is what you see on screen —
buttons, lists, colors, layout. The **backend** is the part running
elsewhere (on a server, or just a hidden part of the same program)
that actually stores and processes the data. An **API** is the
agreed-upon way the frontend asks the backend for something — like a
standardized request form: the frontend fills it out in a format the
backend already knows how to read, instead of the two sides having to
improvise a new conversation every time.

**Why this comes up:** Category 2 asks whether a project even needs a
visible frontend at all — some tools are backend-only, quietly doing
work with nothing to look at, the software equivalent of a utility
room nobody's meant to visit.

---

## Database, Schema, and Migrations

**The building version:** A **database** is the property's central
filing system — every record, every document, stored in an organized,
retrievable way instead of loose papers in a drawer. A **schema** is
the filing system's actual structure — which drawer holds what, what
fields every record has to include. A **migration** is a controlled,
documented change to that structure — like adding a new required field
to every future record, done in an organized way so old records don't
become unreadable or inconsistent with new ones.

**Why this comes up:** Category 4 asks how your data's structure will
be defined and changed over time — left undecided, an AI will often
just directly edit the "filing system" on the fly, which is how you
end up with some old records missing a field the new ones expect.

---

## Dependencies — and Why the AI Gets Cautious About Them

**The building version:** Almost nothing in a house is built entirely
from scratch — you're relying on a manufacturer for the water heater,
another for the electrical panel, another for the appliances. Each one
is a piece you didn't build yourself but your project now depends on
working correctly.

**The software version:** A **dependency** (or **package** or
**library**) is a piece of pre-written code someone else built that
your project relies on instead of reinventing. Almost every piece of
software uses dozens of these. The catch: you're now trusting that
outside vendor's part to keep working, stay maintained, and not have a
hidden flaw.

**Why this comes up:** Category 5 asks you to require that any new
dependency be named and explicitly justified rather than silently
added — the equivalent of not letting a subcontractor swap in an
unapproved part without telling anyone. This matters more than usual
with an AI builder, because it will occasionally reach for a package
that's outdated, abandoned, or doesn't actually exist.

---

## Linters, Formatters, and Pre-Commit Checks

**The building version:** Think of a final walk-through inspection
before a room is considered finished — checking that outlets are
properly covered and nothing's out of place, catching a problem before
anyone moves in, not after a complaint comes in.

**The software version:** A **linter** automatically scans code for
likely mistakes and bad patterns before anyone sees them. A
**formatter** automatically tidies up the code's layout — spacing,
line breaks — so it's consistently readable no matter who (or what AI)
wrote it. A **pre-commit check** just means these run automatically
right before a change is saved permanently, catching a problem before
it ever becomes part of the project's history.

**Why this comes up:** Category 13 offers this as one of the "nearly
free at any size" automated helpers — the routine inspection that
happens quietly in the background instead of relying on someone
remembering to check manually every time.

---

## CI/CD, Pipelines, and "Staging" vs. "Production"

**The building version:** Imagine every proposed change — a new
layout, a repainted wall — got tested first in an identical, unused
model unit before ever being rolled out to the one someone's actually
living in. That model unit is where mistakes get caught safely, with
zero real-world impact.

**The software version:** **CI/CD** (Continuous Integration/Continuous
Deployment) is the automated process that takes a finished code change
and gets it safely into the real, running app — usually running
automated checks first. A **pipeline** is just the actual sequence of
automated steps that happens (check the code, run tests, deploy). A
**staging environment** is that "model unit" — an identical copy of
the real app where changes get tried out first. **Production** is the
real one, the one actually being used.

**Why this comes up:** Category 9 asks whether you want this kind of
safety net at all, and how automatic it should be. A small household
app often skips it entirely for now — changes just get pulled and run
manually, the equivalent of an owner personally checking something
before it's used again rather than running a formal inspection
program.

---

## Logs and Health Checks

**The building version:** A **maintenance logbook** — every repair,
every alert, timestamped and written down, so if something goes wrong,
there's a record of exactly what happened and when, instead of relying
on memory. A **health check** is like a control panel light that tells
you at a glance whether a system is currently running normally,
without you having to go inspect it in person.

**The software version:** A **log** is exactly the same idea — a
running, timestamped written record of what the app has been doing,
especially when something goes wrong. A **health endpoint** (or
health check) is a simple, automatic way to ask the app "are you okay
right now?" and get a plain yes/no back.

**Why this comes up:** Category 10 (Observability) — this is
specifically about *finding out* something broke, which is a different
problem from *surviving* it (that's category 6). A small household app
usually just keeps a basic log file — no fancy control panel needed at
this size.

---

## Environment Variables and Secrets

**The building version:** Think of a master key system — a property's
actual key codes are never printed on a public sign; they live in a
locked, access-controlled system, separate from the building plans
themselves, which anyone might see.

**The software version:** A **secret** is any sensitive value a piece
of software needs to run — a password, an API key — that should never
be stored directly inside the code itself, since code often ends up
somewhere more people can see it than intended. An **environment
variable** is one common way to hand the app that sensitive value
separately, at the moment it actually runs, instead of baking it
permanently into the project. A **`.env.example` file** is a template
listing *what* values are needed without including the actual secret
ones — like a labeled, empty key rack showing what keys should exist,
without the keys themselves hanging on it.

**Why this comes up:** Category 9 requires that credentials never get
committed to the project's permanent history — one of the standing
guardrails exists specifically to stop this from happening by
accident.

---

## Repositories, Commits, Branches, and Rollbacks — the Deeper Version

Level 1 introduced "repository" and "commit" briefly. Here's the rest
of that picture:

**The building version:** Think of a repository as the complete,
permanent renovation history of a building — every change ever made,
who made it, and when, going back to the original blueprints, with
nothing ever truly erased. A **branch** is like a set of proposed
changes drawn up on a separate copy of the blueprints, so you can
sketch out "what if we moved this wall" without touching the real,
current floor plan until you're sure. **Merging** is folding that
approved sketch into the real, official blueprint. A **rollback** is
exactly what it sounds like — reverting to an earlier, known-good
version, the same way you'd restore a previous floor plan if a
renovation turned out to be a mistake.

**Why this comes up:** This is what makes "nothing is ever truly lost"
from Level 1 actually true in practice — and it's why the standing
guardrail about never committing (permanently saving) without telling
you first matters: a commit becomes part of that permanent history.

---

## Operating Systems, and Why "sudo" Won't Mean Anything to You (Yet)

**The building version:** Different properties, different local
building codes — what counts as an approved fire door, how outlets
have to be grounded, even which side a door has to swing open. Same
underlying job (keep the building safe), different specific rules
depending on where you are.

**The software version:** An **operating system** (Windows, macOS,
Linux) is the base software everything else runs on top of — and each
one has its own way of doing basic things like installing software or
granting permission for a risky action. **`sudo`** is a Linux/Mac
command that means "let me do this as an administrator, just this
once" — it doesn't exist on Windows at all. Windows handles that same
idea differently (usually a "Run as Administrator" option, or an
elevated PowerShell window) — same underlying concept, different local
code, so to speak.

**Why this comes up:** Say a project gets built on one computer but
someone else needs to set it up on a different one — a common,
completely ordinary situation. Category 3 explicitly asks which
operating system a project actually needs to run and be set up on,
precisely so instructions don't accidentally assume the wrong one. A
lot of small apps end up not needing to worry about this at all —
if everyone just reaches the app through an ordinary browser, nobody's
own computer needs its own setup step in the first place. It matters
more for a project that needs installing directly onto whatever
computer someone's using.

---

## A Couple of Smaller Ones, Briefly

- **Caching** — storing a copy of something you'll likely need again
  soon, so you don't have to redo the work of getting it from scratch
  every time. Building equivalent: keeping a stack of a commonly
  requested form on-site instead of driving to the print shop every
  single time someone asks for one.
- **Authentication** — proving you are who you say you are before
  being let in (a login, a password). Different from "network access"
  (Part 1 above, which is about whether you can even reach the door)
  — authentication is what happens *after* you've reached the door.
- **Container image** — the actual sealed, ready-to-run package
  version of a container (see the Docker section above) — think of it
  as the pre-fabricated unit *before* it's actually been installed and
  switched on.

---

## If a Term Still Isn't Landing

That's genuinely normal, and it's not a sign you're missing something
you should already know — this is a real second language. If a term
comes up mid-interview that isn't in here, the AI is instructed to
explain every concept in plain language before asking you to decide
anything, so just ask it to explain that one differently, the same way
you'd ask a contractor to explain a term in a renovation quote you
didn't follow. That question is never a bad one to ask.
