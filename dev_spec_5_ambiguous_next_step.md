# Ambiguous next step — dev spec
Site: nomadinternet.com · Priority 5 · Medium · Effort: Medium (2-5 days)

## Problem
After coverage check, the funnel's next step is unclear due to multiple h1 questions and several CTAs without a clear sequence.

## Evidence (from the live site)
> h1: What Best Describes Your Time on the Road?
> h1: How Do You Use the Internet at Home?
> ctas: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
h1: What Best Describes Your Time on the Road? / How Do You Use the Internet at Home?; cta: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE; notes: Multiple h1 questions and redundant CTAs.

## Required change
h1: One clear question per page; cta: One primary CTA that advances to next step; notes: Structure funnel so each page has one clear question and one primary CTA.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Structure funnel so each page has one clear question and one primary CTA.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_ambiguous_next_step` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
