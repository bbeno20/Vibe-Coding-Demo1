# Iteration: Analytics, Sprint, Final Recommendation

> Module 6 · Evals & Iteration. Read the analytics, run an iteration sprint, present with evidence.

## What the evidence says

_What real usage showed: numbers if your tool has analytics, counted behaviour if it does not. Put the signal that matters on screen._

- **Primary signal:** 0 of 1 peer testers completed the core flow unprompted, and the identified a pain-pont was the "Invite one teammate" page, which ties directly to the baseline metric of 1.4 seats per account.
- **What moved:** 4.17 views per visit and 6m 2s average duration show people explored the product rather than leaving immediately.
- **What didn't:** 33% bounce rate, and the one peer tester who tried the flow got stuck at a weak point.

_Observed behaviour: reach 1; core action 0; stall point Invite one teammate; explained away NA; own first run _____._

## Iteration sprint

| Change | Hypothesis | Result |
|---|---|---|
| Added a "Skip for now" option on the Invite teammate step, so the guided path no longer blocks progress on waiting for a teammate to respond. | Removing the invite as a hard gate will let more users reach Launch playbook (the aha action), since the stall wasn't about the concept, it was about depending on someone else's response. | Skip option appears and lets the user continue; progress bar and checklist still update correctly |

## Peer feedback

1 peer replied on the thread. "Was not clear what would be the outcome of inviting my team at this step" for the "Invite one teammate" page.

## The recommendation

**Decision:** ☐ Go  ☑ Iterate  ☐ Kill

_The evidence that justifies the call:_

0 of 1 peer testers completed the guided path unprompted, stalling at "Invite one teammate." Analytics show /auth and / tied for most-visited page out of 6 total visitors, and a 33% bounce rate, suggesting friction early in the flow rather than a rejection of the core concept.

## Final showcase

- **Demo link:** https://first-value-flight.lovable.app
- **The one-sentence story:** A guided activation path that walks a new account to its first retention playbook, but only if it stops gating that path on a teammate accepting an invite the user can't control.
- **Where it landed on the Confidence Line (M2 → now):** Started assuming the guided path itself would drive activation. Real usage shows the concept holds interest (4.17 views per visit, 6m 2s average duration), but one dependency, waiting on a teammate to respond, is the actual point of failure, not the guided path structure.
