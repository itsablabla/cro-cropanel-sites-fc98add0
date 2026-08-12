# Unclear form field labels — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Low (0.5-2 days)

## Problem
The coverage-check forms present five fields each, but the page digest does not reveal what information is requested, so visitors cannot tell what they need to enter.

## Evidence (from the live site)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
cta: CONTINUE; notes: Five fields without visible labels.

## Required change
cta: CONTINUE; notes: Ensure each of the five form fields has a visible, descriptive label.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure each of the five form fields has a visible, descriptive label.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unclear_form_field_labels` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
