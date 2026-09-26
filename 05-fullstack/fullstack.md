# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

_____

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| invites | id, sender email, recipient email, status, user id, created at | Created in Prompt 1 (Schema Expansion). Replaces the old hardcoded dashboard metrics: seat/invite counts on the dashboard now come from real rows in this table instead of a fixed number. |
| Accounts | id, name, domain, owner, seats, status, risk, health, mrr, user id, created at | Customer workspace records. Scoped to the signed-in user via user id, so each account belongs to one user. Replaces the 5 hardcoded fixture accounts from the prototype. |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Every user must sign up or sign in (email/password or Google) before reaching the dashboard, cohort table, or guided path. Four tables are scoped to the signed-in user by an owner field: accounts, invites, teammate invites, and playbook launches. Verified with two test accounts: account A and account B each see a different account list, confirming Row-Level Security correctly isolates each user's records.

Four tables are shared and read-only for everyone: activation steps, playbooks, user voices, and baseline metrics. These hold reference content (the guided path steps, the 3 playbook options, the churn quotes, and baseline metrics) that every signed-in user needs to see the same way, so no per-user scoping applies.

The auth boundary is Supabase Row-Level Security, enforced at the database level rather than only hidden in the UI.

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | o message or button. A new account with no data just showed a blank space. | an active empty state with a "Get Started" call-to-action button. |
| Bad / malicious input | untested, no guard against invalid or unexpected input. | input is safely ignored with no crash |
| Failure / offline | a failed or slow request left the screen stuck with no feedback. | no crash, but no visible error message either, which is still a gap |

## Stress test results

_What you threw at it, and what held / broke._

_____
