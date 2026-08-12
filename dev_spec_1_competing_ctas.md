# Competing CTAs — dev spec
Site: nomadinternet.com · Priority 1 · Urgent · Effort: Low (0.5-2 days)

## Problem
Multiple different CTAs all leading to the same coverage check create ambiguity about which path to take.

## Evidence (from the live site)
> CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
cta: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE; notes: Multiple competing CTAs on homepage and all pages.

## Required change
cta: One primary CTA for coverage check, secondary actions de-emphasized.; notes: Consolidate coverage-check CTAs into one primary action with a single label.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate coverage-check CTAs into one primary action with a single label.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
