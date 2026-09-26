# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

https://first-value-flight.lovable.app

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| accounts | id, name, domain, owner, seats, status, risk, health, mrr, user id, created at | Customer workspace records, scoped to the signed-in user |
| invite | id, sender email, recipient email, status, user id, created at | Drives the Overview dashboard numbers, defaults to pending status |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Every user must sign up or sign in (email/password or Google) before reaching the dashboard, cohort table, or guided path. Four tables are scoped to the signed-in user by an owner field: accounts, invites, teammate invites, and playbook launches. Verified with two test accounts: account A and account B each see a different account list, confirming Row-Level Security correctly isolates each user's records. Four tables are shared and read-only for everyone: activation steps, playbooks, user voices, and baseline metrics, since they hold reference content every user needs to see the same way.

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | Blank space, no message or button | Active empty state with icon, heading, explanation, and a "Get Started" button, shown on both the invites banner and the cohort table |
| Bad / malicious input | Untested, no guard against unexpected input | Searching the cohort table with nonsense text returns no crash and no results, rather than an error |
| Failure / offline | A failed or slow request could leave the screen stuck with no feedback | Triggering Simulate error does not freeze the screen |

## Stress test results

_What you threw at it, and what held / broke._

Ran the Ghost User test: checked what a brand-new signed-in account with no data sees on the Overview screen. Result: an active empty state, not a dead end. The invites banner shows "No invites sent yet" with a "Get Started" button, and the cohort table shows "No new accounts yet" with an icon, explanation, and its own "Get Started" button. The empty state held on both areas of the screen.
