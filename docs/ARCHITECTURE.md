# Hope Theory — public architecture map

Status date: 2026-10-06. Scope: public GitHub only. This is a map of what is actually shipped in public repos, not a claim that every product is in production with paying users.

## System shape

Hope Theory is a portfolio of small products plus a source-of-truth repo. There is no shared monorepo, no shared auth service, and no shared production database.

```
FahadIbrahim93 (profile README)
        |
        +-- devjourney                brand, proposals, site source (not the deploy target)
        |
        +-- FahadIbrahim93.github.io  live portfolio (GitHub Pages)
        |
        +-- product repos             each owns its own deploy, data, and CI
```

Canonical site workflow (already documented in this repo): edit `docs/`, `portfolio/`, or `Freelancing/` here, then copy finished files into `FahadIbrahim93.github.io` and push. This split is a real operational risk: the source of truth and the live site can drift.

## Project register

| Repo | What it is | Stack | Deploy | Data | Honesty note |
|---|---|---|---|---|---|
| emberfall | Arcade shooter + optional command deck | Zero-build JS, Node, SQLite | GitHub Pages + self-hosted Node | Local SQLite; optional Supabase read mirror | Strongest engineering repo. CI, tags, smoke, anti-cheat notes. |
| BugSmasher-HopeTheory | Canvas clicker-defense | React 19, TypeScript, Firebase | Vercel | Firebase | README says NOT CERTIFIED. Large unmerged Dependabot queue. |
| RollON-MVP-Final-V1 | Storefront MVP | React 19, TypeScript, Zustand, Tailwind | Vercel | App-local plus a `server/` tree | Claims 117 tests / 87% coverage. Needs a current CI badge, not a README sentence. |
| LearnWebDev-AI / web-development-with-ai | Course platform | React 19, Vite, Convex, Stripe, Tailwind v4 | Not verified from this audit | Convex | Two near-duplicate repos. Pick one. |
| ai-lead-hunter | Local lead research OS | Python + static dashboard | GitHub Pages (read-only) | Local files | Draft PR #1 still open. Nothing is auto-sent, which is the correct default. |
| jgmart-hermes | Grocery PWA pilot | Vanilla PWA, Supabase, Python checks | Vercel | Supabase | Addressable-market numbers are not customers. See case study. |
| to-let-bd | Rental landing | Static HTML | Unverified | None obvious | Landing, not a marketplace. |
| skateline | Three.js skate prototype | HTML/Three.js | Unverified | None | Open feature issues, no tests found in the issue trail. |
| viral-pet-nix | Single-file dodge game | HTML/JS | Unverified | localStorage intended | 13 open issues, several duplicates. |
| lark-lilac-lagoon-bolt | Scratch | JS | None | None | Author already marked it as not a portfolio highlight. |
| ShopEase | Previously public FastAPI inventory service | FastAPI | Unknown | Unknown | Returned 404 on 2026-10-06. Treat as unpublished. |

## Cross-cutting decisions

1. Prefer a live demo over a private README. This is the right call for a freelance portfolio.
2. Do not share one backend across products until one product has a real operator. Premature platform work would make the repo graph worse.
3. AI-agent copy (lead hunter, ShopEase, "revenue OS") must stay draft-only until a human sends it. ai-lead-hunter already does this. Keep that invariant.
4. Secrets: emberfall documents a publishable Supabase key in the README. Publishable keys are meant to be public, but the project URL plus key still need RLS proven in the repo, not only described.

## What is missing

- No org-level CODEOWNERS, branch protection evidence, or required reviews. History is mostly direct pushes to `main`.
- No single CI dashboard. emberfall has a real gate. Most other repos do not show one.
- Duplicate course repos and a docs repo that is not the site repo.
- Sprint log in this repo last closed on 2026-05-12. It is not the current operating picture.
