# Ambiguous CONTINUE button — dev spec
Site: nomadinternet.com · Priority 6 · Medium · Effort: Low (0.5-2 days)

## Problem
The form submit button reads only CONTINUE, which does not tell visitors what action they are confirming or what happens next.

## Evidence (from the live site)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
cta: CONTINUE; notes: Button text is ambiguous.

## Required change
cta: Check My Coverage or See My Options; notes: Change submit button label to something specific.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Change submit button label to something specific.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_ambiguous_continue_button` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
