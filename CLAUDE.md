# theshou.com

The global home of **Shou** (AI local host for places). Today a static holding page; it will become
the global marketing site (home, channel pages per country, GTM pages), like shou-landing is for shou.be.

This repository is **public**: never commit secrets, strategy, pricing drafts or customer data.
The plan lives in the private repo shou-backend: `docs/theshou-global-plan.md`; tasks are in the
Strybai Build workspace "theshou.com" (pillar build#28).

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
