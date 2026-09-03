# Road to Nine

The Sept 2 Parts Marketplace Audit landed at **8.0/10** and named the distance
to 9 exactly: a short unproven list, not more code review. The auditor's own
words — "the code cannot earn those points on this machine; only staging and a
human walk can." Nothing below is a re-grade; every line is a proof.

Rendered version: https://claude.ai/code/artifact/efad3acd-a29f-4fd8-95dd-8f2a34251ad9

## 01 — Code the team pushes now (dev machine, no staging)

| Item | What | Cost |
| --- | --- | --- |
| A7 | Part offers in the buyer's `/offers` inbox show a bare "Listing" — show the part's title and thumbnail (the test site shows the intended behavior) | ~1 hr |
| A8 | Add `/part` pages to the sitemap | ~30 min |
| A11 | Bump the 19px inline "came off" build link to a tappable size | ~30 min |
| A10 | Apply the photo-parity call (decision below) | 1 line |
| Admin (5/10) | Land the admin build — its session is already in flight | in flight |
| Observability (6/10) | Log + alert on every Accept-charge attempt, success, refusal, and crash-resume. The money path must not fail silently before staging | ~half day |

**Owner decision (A10), blocking one line:** the car's money gate arms at
1 photo while the wizard and the whole parts system demand 2.
**Recommendation: require 2 everywhere.** It's one line today; it's a
migration after launch.

## 02 — Staging proofs (one afternoon)

- **S1** Photo upload end-to-end: add a part with 2 real photos; see them on the part page, bench card, and strip. (Local S3 is dead by design — this is the first real upload.)
- **S2** One test-mode Stripe charge: commit at an ask, Accept as the seller, watch the 5% fee charge and the part flip to pending.
- **S3** Trigger and eyeball the offer emails (new offer, accept, expiry reminder) in a real inbox — first live run of the A6 cron fix.

## 03 — The human walk (Chad, ~30 min, signed in)

The auditor doesn't enter passwords; these screens have never been under a
human hand. Use the test site as the script:

1. Your garage → Put it on the bench, leaving "what's included" empty. **Pass:** the button stays dark and names the missing fact; never orange.
2. Fill the third fact, submit, open the new part page. **Pass:** three labeled fact lines; the money line reads "You pay the seller."
3. From a second account, commit at the ask; open your offers as the seller (BenchPartOwnerPanel — A5's unwalked screen). **Pass:** Accept flips the part to pending; Decline returns it to the bench, no charge.
4. Edit the ask on a part with a committed offer. **Pass:** the pending charge refuses (consent guard, proven over curl, now over glass).
5. Walk wizard step 4 on a car listing end to end. **Pass:** no dead ends.

## 04 — Definition of done

Re-run the audit against staging when: A7/A8/A10/A11 closed, admin landed,
money-path alerting live, S1–S3 proven, and the five-step walk passes. Then —
and only then — the ship order. That one stays with the owner.

Out of scope for nine (absent by design per the audit): carts, shipping,
escrow, site-wide parts search, typed part offers, reviews machinery. Adding
any of those does not move the score; it moves the launch date.

Total new engineering: roughly two focused days plus the admin work in flight.
