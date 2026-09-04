# Sell My Project — Test Site

A clickable, phone-first walkthrough of the Sell My Project product, assembled
from the finished workstream deliverables:

- **Parts V1 design spec** ("Parts on the Bench") — the bench, one closer, no second store
- **Phone mockups** ("The Bench, On Screen") — palette lifted verbatim from `smp-web/app/globals.css`
- **Full-system engineering audit** ("Parts Marketplace Audit", Sept 2 2026) — 8.0/10, ready for controlled staging

## Open it

Open `test-site/index.html` in any browser (no build, no server), or view the
published copy: https://claude.ai/code/artifact/a87e110e-a0e7-4752-8d0e-f8c3720eb1e0

## What it covers

- The garage-first **feed** (builds, not a listings mall)
- **RustyK5's garage** — builds, the bench (with sold/pending tags), the shop
- The **1972 K5 Blazer build page** with the "Off this build" strip and armed closer
- **Part pages** in both states: charge-ready (orange closer, fee note) and the
  honest dark state ("The part is here. The story is not.")
- **Put it on the bench** — the two-minute form with its live three-fact gate
- **Offers** — buyer commit flow with fee math, and the seller's Accept/Decline
  (Accept charges the 5% fee and flips the part to pending)
- **Admin** — placeholder shaped to the audit's test data; the real admin build
  is still in flight in its own session
- **About** — workstream status, the audit verdict, and the locked money rules

## Rules honored

Seller fee $0 forever. Buyer fee 5% on Accept, capped at $5,000, card on file.
Nobody holds the money — buyer pays seller at pickup. Orange appears at most
once per screen, only on a closer the server has armed. Three facts or the part
doesn't go up. Sold parts stay visible. No cart, no parts nav, no site-wide
parts search — discovery is the garage and the build.

All data is simulated; photos are placeholders. Nothing touches the real backend.
