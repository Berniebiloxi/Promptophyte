# Publishing Your Project

Your AI has built something, and it runs on your own computer. Right now
the only way anyone else sees it is by sitting at your keyboard. This page
is about putting it somewhere a friend can open a link — even just for an
afternoon. It's deliberately short; for anything it doesn't cover, the
official docs linked in each section are the source of truth.

## First: which kind of thing did you build?

Websites come in two broad kinds, and it decides everything below.

- **Static** — a set of files (pages, styling, a bit of code that runs in
  the browser) that don't need anything running behind them. The
  visitor's browser does all the work. Most small tools, pages, and
  simple apps that don't save anything shared between people are static.
- **Needs a backend** — a program has to be running somewhere all the
  time: it saves things to a database, has accounts or logins, or does
  work the browser can't. If your interview with the meta-prompt picked a
  database in category 4, or "reachable from a phone while away from
  home" in category 1, you're probably here.

**How to tell:** ask the AI that built it — "Is this a static site, or
does it need a server or database running to work?" — it will know
immediately. The two free options below are for **static** sites. If
yours needs a backend, skip to the last section.

## Option 1: GitHub Pages

Free, from GitHub, and if the interview put your project on GitHub
(category 3, "where does the project live"), you're most of the way there
already.

1. Your project has to be on GitHub. If it isn't yet, ask your AI: "Put
   this project on GitHub for me" — it will walk you through making a
   free account and do the rest.
2. Open your project on github.com and click **Settings**, then **Pages**
   in the left sidebar (under "Code, planning, and automation").
3. Under **Build and deployment → Source**, choose **Deploy from a
   branch**. Set the branch to `main` and the folder to `/ (root)`.
   Click **Save**.
4. Wait — it can take up to ten minutes the first time. Your link will be
   `https://YOUR-USERNAME.github.io/YOUR-PROJECT/`, and GitHub shows it at
   the top of that same Pages settings screen once it's live.

Two things to know: your main page needs to be a file called `index.html`
at the top level of the project (if your AI named it something else, ask
it to rename it), and the free version of Pages only works on a *public*
project — meaning anyone can read the code, not just see the site. That's
fine for almost everything, but it's one more reason there must never be a
password or key in the files (see the last section).

Official guide: <https://docs.github.com/en/pages/quickstart>

## Option 2: Cloudflare Pages

Also free, and a small step up. It needs a Cloudflare account, but in
return it handles a bit more than pure static: if your project needs a
"build step" (ask your AI — some frameworks turn the code into the final
files first), Cloudflare works it out for you, and it can host small
pieces of server-side code if your AI needs a little of that. It is still
not a home for a full database-backed app.

1. Sign up free at <https://dash.cloudflare.com>.
2. In the sidebar, open **Workers & Pages**, click **Create**, choose the
   **Pages** option, then **Connect to Git** (it may say "Import an
   existing Git repository").
3. Let it connect to your GitHub account and pick your project.
4. On the build-settings screen, if your site is plain files, leave the
   build command empty and the output folder as-is. If your AI told you
   there's a build step, ask it what to put here — it will know.
5. Click **Save and Deploy**. Your link will be
   `https://YOUR-PROJECT.pages.dev`.

From then on, every time your AI saves a change to GitHub, Cloudflare
republishes the site automatically within a minute or two.

Cloudflare has been gradually folding Pages into its Workers product, so
menu names shift over time. If a step here doesn't match your screen,
trust their docs: <https://developers.cloudflare.com/pages/get-started/>

## If yours needs a backend or database

Neither option above runs a program for you around the clock, so a
database-backed app won't work on them. There are two honest paths, and
which one you want depends on how long the link needs to last.

**Just for now — a friend looks at it this afternoon.** Use a *tunnel*: a
free tool that gives your own computer a temporary public link while the
app is running on it. Ask your AI: "Set up a temporary public link to this
app with Cloudflare Tunnel so I can send it to a friend." (ngrok is the
other common one.) The link stops working the moment you close it or shut
your computer — that's the point. Two cautions: anyone with the link can
reach the app, so this is the "public internet" ring from the interview's
category 5 whether you planned for it or not, and you shouldn't leave it
running unattended. [Level 2](handbook/level-2.md) explains what those
rings mean.

**For keeps.** You need a host that keeps a program running all the time,
and the reliable ones cost a few dollars a month — free tiers exist but
come and go. This is exactly the running-cost question from category 3 of
the interview. Ask your AI: "Recommend a place to host this that fits
[free / a few dollars a month], and set up the deployment." Once it's
live, category 9's question — how a bad change gets undone — starts to
matter for real.

## Before you share the link

- **Everything you publish is public.** The files must never contain a
  password, an API key, or anything you'd mind a stranger reading. Your
  AI is under standing rules not to put them there; if the interview
  turned on the secrets scanner in category 13, that's the backstop.
- **Updating is automatic.** Your AI changes something, saves it to
  GitHub, and the published site catches up on its own — a minute or two
  for Cloudflare, up to ten for GitHub Pages.
- **Taking it down is easy.** GitHub: **Settings → Pages**, then the
  three-dot menu next to your live URL has an **Unpublish site** option.
  Cloudflare: delete the project. A tunnel: close it.

## If something doesn't match

Menu names and screens change. If a step here doesn't line up with what
you're seeing, trust the official docs linked above. If a step here is
*wrong* (not just out of date on your screen but actually incorrect),
that's worth [an issue](../../issues/new/choose).
