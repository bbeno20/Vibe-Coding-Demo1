# Living PRD

> Module 4 · Production Specs. Refactor for readability; extract a living PRD that stays true as the build evolves.

## Problem

_What user problem does this solve? Tie to the validated hypothesis._

New B2B SaaS accounts fail to reach first value in week one, and that early failure turns into churn within 90 days. Baseline: 30% 90-day churn, 22% week-one activation, 1.4 active seats per account. Hypothesis: a guided week-one path to the "aha" action will raise activation above 40% and lower churn. Kill switch: if activation doesn't move, onboarding isn't the real problem, so pivot.

## Users & jobs

- **Primary user:** The first seat at a new account, usually the buyer (ops lead, eng manager, or founder), deciding in week one whether the product earns a place on their team. Secondary user: the internal reviewer evaluating the experiment.
- **Job to be done:** When I start with a new tool, guide me to the one action that proves value for my team in week one, so I can justify rolling it out before I lose interest.

## Scope

- **In:** Activation overview: baseline metrics, three user quotes, filterable cohort table with account detail panel
Four-step guided path as real screens: Import, At-risk picker, Invite teammate, Launch playbook (the aha action), then an Activated confirmation
Timed loading states and simulated error states with retry
Experiment readout with outcome switch and kill-switch panel, plus loading and empty states
- **Out (explicitly):** Login, accounts, and multi-tenancy
Persistence and any database or API (a reload resets everything)
Real data, integrations, email sending, and real playbook execution
Live experiment measurement (readout numbers are fixed samples)
Billing, permissions, notifications, and production-grade error handling

## Requirements

| # | Requirement | Priority | Acceptance criteria |
|---|---|---|---|
| 1 | Show the three baseline metrics verbatim on the overview | Must | 30% / 22% / 1.4 render with their exact explanations |
| 2 | Show all three user quotes verbatim with attribution | Must | All three quotes and roles visible as prominent evidence |

## Data & events

_What gets stored, what gets tracked._

All data is mocked and nothing persists. Baseline metrics: churn 30%, activation 22%, seats 1.4. Events a real build would track: accounts imported, at-risk account selected, teammate invited, playbook launched (the activation event), outcome previewed, and retries after failure. A production version would need an accounts store, per-step activation timestamps, invite delivery, and experiment results computed from real cohorts.

## Open questions

Is "activated" defined as launching the playbook, or launching it and seeing a first result?
Is 40% the right threshold, and over what cohort window?
Should the guided path be required or skippable, and how do skipped accounts count in the analysis?
How is the control group handled? The readout currently compares before and after, not randomized groups.
Do ops-led, eng-led, and founder-led accounts need different steps?
What sample size and duration justify trusting the kill switch?
