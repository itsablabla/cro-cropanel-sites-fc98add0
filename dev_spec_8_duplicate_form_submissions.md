# Duplicate form submissions — dev spec
Site: nomadinternet.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
Two identical coverage-check forms with CONTINUE submit button appear on each page, causing confusion and potential double submissions.

## Evidence (from the live site)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
cta: CONTINUE; notes: Two identical forms with CONTINUE submit on each page.

## Required change
cta: CONTINUE; notes: Remove duplicate form instance so only one coverage-check form is visible per page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Remove duplicate form instance so only one coverage-check form is visible per page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_form_submissions` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
