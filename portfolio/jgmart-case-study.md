# Case study — JG Mart (jgmart-hermes)

Status: pilot / pre-seed. This write-up separates what the repo claims from what an outside reviewer can verify. It does not invent revenue, order counts, or customer interviews.

## Problem

Japan Garden City (Dhaka) is a dense residential complex. The public README targets about 1,700 families across 27 buildings in 4 clusters, with grocery supply modeled from Krishi Market roughly 800m away. The product bet is that a downloadable app is the wrong interface: residents already live in WhatsApp, and a courier can run a cluster route without a marketplace middleman.

That problem statement is plausible. It is not evidence that those 1,700 families are users.

## Solution

Public implementation in [jgmart-hermes](https://github.com/FahadIbrahim93/jgmart-hermes):

- Static HTML/CSS/JS PWA, no frontend framework, service worker cache called out as v6.
- WhatsApp-native order handoff (public number in the README: +8801870489448) plus Supabase (Postgres, Auth, RPC) for catalog and operator dispatch.
- Admin path: Supabase Auth with a PIN fallback.
- Python validation scripts and a GitHub Actions validate/deploy path. README cites 45/45 HTML checks and 17/17 Python checks.
- Live URL claimed: https://jg-mart.vercel.app

The architecture is appropriate for a pilot: one complex, one catalog, one operator, no app store.

## Results

Verified from the public repo on 2026-10-06:

- A deployed-style PWA and schema exist.
- Catalog scope is documented as 82 products in 10 categories.
- Quality gates are claimed (HTML/Python checks, Actions on main).

Not verified, and must not be pitched as results:

- 1,700 families are an addressable-market figure, not an acquired-user figure.
- 51% gross margin is a model (removing middlemen), not a measured P&L.
- No public order volume, retention, delivery-time, or refund numbers.
- No third-party confirmation that the pilot is operating daily.

## What a hiring manager should take from this

The interesting part is constraint choice: WhatsApp instead of an app, cluster routing instead of a city marketplace, vanilla PWA instead of a framework. The weak part is metric language. Label TAM, model, and actuals in three different columns before this goes into a proposal.

## Next honest milestone

Publish one week of operations with definitions: orders placed, orders delivered, median handoff time, stockout count, and gross margin on those orders. Until that table exists, the case study stops at "pilot built".
