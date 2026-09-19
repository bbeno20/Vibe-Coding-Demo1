# Engineering Handoff Note

> Module 4 · Production Specs. Open the black box, make the build legible to an engineer.

## What this is

_One paragraph an engineer can read in 60 seconds._

This is a single-view, entirely client-side prototype that tests one hypothesis: a guided week-one activation path will push week-one activation above 40% and cut 90-day churn. There is no backend — every account, playbook, metric, and state is hard-coded fixture data or local React state, and that is deliberate: the PRD scopes persistence, APIs, and integrations out. Three tabs (Overview, Guided Path, Readout) are switched by state inside one component, not by routes. If you understand RetentionEngineWorkspace, you understand the whole app. The riskiest thing a new engineer can do is treat it as a real product skeleton and start wiring real data into the readout — the numbers there are reviewer-controlled fiction used to test the kill-switch decision ("Hypothesis failed → pivot").

## Architecture (plain language)

- **Frontend:** One route (/) renders a single stateful component, RetentionEngineWorkspace, which owns all state and switches between the three views. Code is organized by feature under src/features/retention-engine/: overview/ (metrics, quotes, cohort table, account detail sheet), guided-path/ (a coordinator plus five step screens), readout/ (the outcome switch and kill-switch panel), and model/ (types and all fixtures). No data lives in components, and styling uses design tokens only.
- **Backend / data:** None. No database, server functions, or API routes. "Loading" is a 1.5 second timeout, and "errors" are a Simulate error toggle. The data is 5 accounts, 24 generated import rows, 3 playbooks, and three fixed readout snapshots.
- **Key flows:** Cohort triage: Overview, then filter or search, then open an account detail sheet, then "Guide this account" jumps into the Guided Path.
Activation path: Import, At-risk picker, Invite teammate, Launch playbook (the aha action), Activated. Launching flips the readout to the "lift" outcome.
Kill switch: on the Readout tab, choose "Hypothesis failed" to see the flat results and the pivot panel.

## What's solid vs. what's duct tape

| Area | State | Notes |
|---|---|---|
| Data & state structure | solid | All data lives in model/ (types and fixtures), and components hold no fixtures. State lives in one place, RetentionEngineWorkspace. Every list has real data / loading / empty / error states with approved copy, and styling uses design tokens only. Lint and production build pass, and each flow was checked in a browser. |
| Readout & simulated behavior | rough | The readout numbers are three hard-coded snapshots switched by a reviewer-facing toggle, not live data. Loading is a 1.5 second timeout, and errors come from a Simulate error toggle. State resets on refresh, and tabs are state, not routes, so there is no deep linking or browser back. A production build must remove the toggles and compute results from real cohorts. |

## Risks & assumptions for the team

This stays a prototype. Wiring a real backend into the readout or cohort table without a data contract would make the fixture-shaped types misleading.
The outcome switch and Simulate error toggles are reviewer tools and must not ship in a user-facing build.
It deploys to an edge/Worker runtime, so future server code must avoid Node-only packages.
Tailwind classes must be literal strings (no interpolation), and no new colors or fonts.
Tab buttons attach click handlers about 2 seconds after load, so headless scripts must wait.
The hypothesis framing (40% activation, kill switch) is treated as settled, and its copy is hard-coded across screens.

## How to run it

```
bun install
bun run dev      # http://localhost:8080
bun run lint
bun run build    # the real gate

No environment variables, secrets, or services are required. To see the full story: Overview → filter the cohort → open Northstar Labs → "Guide this account" → walk all five steps (flip "Simulate error" once on Import or Launch to see retry) → Readout → switch to "Hypothesis failed" for the kill switch. Companion docs: RETENTION-ENGINE-PRD.md (scope, requirements, open questions) and RETENTION-ENGINE-README.md (hypothesis, screens, flow).
```
