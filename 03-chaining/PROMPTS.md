# PROMPTS.md: Living Prompt Pack

> Module 3 · Prompt Chaining. Re-architect the build with prompt chains; capture the reusable ones here.

## How to use this pack

_Each prompt is a reusable step. Chain them: the output of one becomes the input to the next._

## Prompt chain: [name your flow]

### Step 1: Expand, build new screens in a strict sequence
```
I'm building on the existing Retention Engine prototype. Match the attached screenshots exactly: dark utility rail, compact top bar, tabbed workspace, Manrope font, and the existing teal/coral tokens in src/styles.css. Do not add new colors or fonts.

Right now each step in the Guided Path is only a card with a "Complete and continue" button. Replace that with real screens, built in this order:

1. Import: a screen showing the 24 sample accounts loading in as a table, with a count and a "Continue" button.
2. At-risk picker: a list of accounts with usage signals. The user selects one (default Northstar Labs), and the selection carries forward.
3. Invite teammate: an email field, a role dropdown, and a "Send invite" button. Show the invited teammate in a small list after sending.
4. Launch playbook (the aha action): a playbook picker with 2 to 3 options, a preview of what it will do, and a "Launch playbook" button.
5. Activated: a confirmation screen showing Northstar Labs is now Activated, with a link to the Readout tab.

Work through each screen in order. After each one, confirm the progress bar and checklist update before building the next. Keep everything in prototype state only.
```

### Step 2: Behavior, hard-code the states
```
Add loading, error, and empty states to the Guided Path and Readout. Use the exact copy below. Do not rewrite it or add extra text.

Guided Path, loading (about 1.5 seconds after clicking "Complete and continue" on Import and Launch playbook):
- Import: "Importing 24 accounts..."
- Launch: "Launching playbook for Northstar Labs..."

Guided Path, error (add a small "Simulate error" toggle so I can preview it):
- Import: "We couldn't import your accounts. Check your connection and try again." Button: "Retry import"
- Launch: "The playbook didn't launch. Your progress is saved." Button: "Retry launch"

Readout, loading: "Loading cohort results..."
Readout, empty: "No results yet. Data appears once the cohort has been live for 24 hours."

Use the same segmented-toggle pattern the Overview cohort table already uses for Data / Loading / Empty / Error. Errors should use the existing destructive token. Don't change any other screen.
```

### Step 3: Refine, one surgical polish
```
First, review the outcome switch on the Readout tab (currently "Live Data / Positive Lift / No Lift") and list what is unclear or hard to notice about it. Keep that list to 3 items or fewer.

Then make one change. Rename the options to "Still measuring", "Hypothesis worked", and "Hypothesis failed". Add a short caption above the switch: "Preview an outcome". Make the selected state stronger using existing tokens. The kill-switch panel should still appear when "Hypothesis failed" is selected.

Don't change anything else.
```

## Reusable techniques learned

- Attach screenshots so new screens match the existing design
- Build screens in a fixed order so each one anchors the next
- Write exact copy for every loading, empty, and error state
- Add a toggle to preview unhappy paths that can't happen on their own
- Have the AI list problems first, then make one targeted change
- End with "Don't change anything else" to limit what the AI touches

## What broke (and the fix)

_Where a single mega-prompt failed and chaining fixed it._

Problem: Expand removed the "AHA ACTION" badge from step 4, which I didn't ask it to change. Fix: sent a one-line follow-up ("Restore the AHA ACTION badge on step 4. Don't change anything else") and it was restored in one pass.
Problem: The 24 sample accounts reuse the same names with numbers added (Northstar Labs 2, 3), so the table looks fake. Fix: [add one if you fixed it, or write "left as is, fine for a prototype"].
