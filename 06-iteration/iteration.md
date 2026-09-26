# Iteration: Analytics, Sprint, Final Recommendation

> Module 6 · Evals & Iteration. Read the analytics, run an iteration sprint, present with evidence.

## What the evidence says

_What real usage showed: numbers if your tool has analytics, counted behaviour if it does not. Put the signal that matters on screen._

- **Primary signal:** 0 of 1 peer testers completed the core flow (Import → Invite → Launch) unprompted, and the one stall point identified was "Invite one teammate," the exact step tied to the baseline's weakest metric (1.4 seats per account).
- **What moved:** Visitors explored meaningfully once in: 4.17 views per visit and 6m 2s average duration suggest people didn't bounce immediately, they clicked around and spent real time on the product.
- **What didn't:** A 33% bounce rate means a third of visitors left after a single screen. More importantly, 0 of 1 peer testers got past the invite step without help, directly contradicting the M2 hypothesis that a guided path alone would drive activation. The friction is concentrated at team invite, the same seat-adoption problem the original baseline metrics (1.4 seats/account) were meant to test.

_Analytics snapshot: visitors 6; page views 25; views per visit 4.17; duration 6m 2s; bounce 33._

_Observed behaviour: reach 1; core action 0; stall point Invite one teammate; explained away NA; own first run _____._

## Iteration sprint

| Change | Hypothesis | Result |
|---|---|---|
| Added a "Skip for now" option on the Invite teammate step, so the guided path no longer blocks progress on waiting for a teammate to respond. | Removing the invite as a hard gate will let more users reach Launch playbook (the aha action), since the stall wasn't about the concept, it was about depending on someone else's response. | Skip option appears and lets the user continue; progress bar and checklist still update correctly |

## Peer feedback

I was not clear what would be the outcome of inviting my team at this step

## The recommendation

**Decision:** ☐ Go  ☐ Iterate  ☐ Kill

_The evidence that justifies the call:_

0 of 1 peer testers completed the guided path unprompted, stalling at "Invite one teammate." Analytics show /auth and / tied for most-visited page out of 6 total visitors, and a 33% bounce rate, suggesting friction early in the flow rather than a rejection of the core concept.

## Final showcase

- **Demo link:** https://first-value-flight.lovable.app
- **The one-sentence story:** A guided activation path that walks a new account to its first retention playbook, but only if it stops gating that path on a teammate accepting an invite the user can't control.
- **Where it landed on the Confidence Line (M2 → now):** Started assuming the guided path itself would drive activation. Real usage shows the concept holds interest (4.17 views per visit, 6m 2s average duration), but one dependency, waiting on a teammate to respond, is the actual point of failure, not the guided path structure.
