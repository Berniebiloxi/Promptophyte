# Setting up Claude Code

The README recommends [Claude Code](https://claude.com/claude-code) as the
tool the meta-prompt was built and tested against. This page gets you from
nothing to a running session. It's deliberately short — for anything it
doesn't cover, Anthropic's own guide is the source of truth:
**<https://code.claude.com/docs>**.

## First: what you need

- **A paid Claude plan.** Claude Code isn't free. A Claude Pro or Max
  subscription includes it; you can also pay per use through an Anthropic
  Console account. Current options and prices:
  <https://claude.com/pricing>. Start with the smallest plan — you can
  move up later.
- **A folder for your project.** Make an empty folder somewhere you'll
  find it again (e.g. `Documents/my-first-app`). Claude Code works
  *inside* a folder — that's where it puts the files it writes.

That's it. You do **not** need to install a code editor, learn git, or set
anything else up first. Claude Code handles that if your project ever
needs it.

## Pick how you want to run it

There are three ways in. They all use the same thing under the hood, so
pick whichever sounds least intimidating — you can switch later.

### 1. The desktop app — easiest, no terminal

Download the Claude app for your computer, install it like any other app,
sign in, and click the **Code** tab. Everything happens in a normal
window. Download links and details:
<https://code.claude.com/docs/en/desktop-quickstart>.

### 2. In your browser — nothing to install

Go to **<https://claude.ai/code>** and sign in. Good for trying it out
without installing anything. It works on repositories you connect to it
rather than a folder on your computer, so it's a slightly different flow —
fine for a first look.

### 3. The terminal — what the docs assume

The **terminal** (also called the "command line") is a plain text window
where you type commands instead of clicking. On a Mac it's an app called
**Terminal**; on Windows it's **PowerShell** or **Windows Terminal**; on
Linux you already know where it is. It looks bare, but for this you only
need a couple of commands.

**Install it** with the official one-line command from
<https://code.claude.com/docs/en/overview> (copy it from there so you're
always using the current version). At the time of writing it is:

- **macOS / Linux:** `curl -fsSL https://claude.ai/install.sh | bash`
- **Windows (PowerShell):** `irm https://claude.ai/install.ps1 | iex`

Close and reopen the terminal after it finishes.

**Start it** by pointing the terminal at your project folder and running
`claude`:

```
cd path/to/your-first-app
claude
```

(`cd` means "change directory" — it's how you tell the terminal which
folder to work in. On most systems you can type `cd `, then drag the
folder onto the window to fill in the path.)

The first time, it will ask you to log in — follow the prompts and sign in
with the same account as your Claude plan.

## Then what

Once Claude Code is running and logged in:

1. Open [`quickstart.md`](quickstart.md) (or
   [`meta-prompt.md`](meta-prompt.md) if you've read the handbook and want
   the full process).
2. Copy the whole prompt.
3. Paste it in as your first message, with your idea filled into the line
   marked for it.
4. Answer its questions.

## A note on cost

A subscription is a flat monthly fee with usage limits — if you hit the
limit, you wait for it to reset, you don't get a surprise bill. Pay-per-use
through Anthropic Console *can* add up over a long build, so if you go that
route, keep an eye on the usage page early on until you have a feel for it.

## If something doesn't match

Install commands and menu names change over time. If a step here doesn't
line up with what you're seeing, trust the official docs:
**<https://code.claude.com/docs>**. If a step here is *wrong* (not just
out of date on your screen but actually incorrect), that's worth
[an issue](../../issues/new/choose).
