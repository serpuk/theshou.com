# theshou.com

The global home of **Shou** (AI local host for places). Today a static holding page; it will become
the global marketing site (home, channel pages per country, GTM pages), like shou-landing is for shou.be.

This repository is **public**: never commit secrets, strategy, pricing drafts or customer data.
The plan lives in the private repo shou-backend: `docs/theshou-global-plan.md`; tasks are in the
Strybai Build workspace "theshou.com" (pillar build#28).

## Working from Claude Code in the cloud (claude.ai/code)

- **No local memory there.** Project knowledge lives in the CLAUDE.md files of shou-backend, shou-frontend,
  shou-landing and theshou.com, plus shou-backend `docs/project-notes.md` (product state, open follow-ups,
  how-tos) and `docs/theshou-global-plan.md`. Put new durable facts there, not in a session.
- **Pull requests:** the cloud GitHub proxy blocks `gh pr …` / `gh issue …` (GraphQL). Open the PR with the
  session's **Create PR** button, or REST:
  `gh api repos/serpuk/theshou.com/pulls -f title='…' -f head=<branch> -f base=main -f body='…'`.
  Merge (only when the user asks): `gh api -X PUT repos/serpuk/theshou.com/pulls/<n>/merge -f merge_method=merge`.
  Branch deletion and tags are refused by the proxy; leave merged branches.
- **No production access:** no Fly login, no database keys, no Vercel / Supabase dashboards. Write dry-run
  scripts and ask the user to run them; read public data through `https://shou-backend.vercel.app/api/…`.
  Never put a secret in the environment's plain variables (the model can read them).
- **Pages:** shou.be and app.shou.be challenge cloud-server traffic (Vercel Firewall), so checks from the cloud
  may get a 429 challenge; use `shou-backend.vercel.app` URLs or headless Chrome and say when a page could not
  be checked.
- **Strybai Build:** reference tasks with `build#N` and close them with `closes build#N` in the PR; editing the
  board itself needs the user's login.

## Rules
- Static HTML, no build step. Vercel project serves the repo root (`vercel.json`: clean URLs,
  www → apex redirect, security headers).
- Same brand as shou.be: violet near-black ground `#0b0810`, pink→orange gradient
  (`#ff3d8b` → `#ff9b3d`), Fraunces (display) + Inter (text), the gradient-bars icon.
- Only claim what is live: Shou runs in Belgium (shou.be). No prices on the home page, no invented
  testimonials or customer logos.
- No analytics or cookies yet. Adding any tracking needs a privacy page first.
- Email from theshou.com needs SPF, DKIM and DMARC first (DNS at Combell, like shou.be).
- Every indexable page: canonical, `<title>` ≤ ~60 characters, meta description ≤ ~160.
- Commit / push / deploy only when the user asks.
