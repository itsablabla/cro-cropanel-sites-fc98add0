# Guarantee not near purchase — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Medium (2-5 days)

## Problem
The rural-internet page mentions shopping with confidence, but the plans pages where users commit to a plan lack any guarantee or return-policy reassurance.

## Evidence (from the live site)
> h2: SHOP WITH CONFIDENCE
> h2: The Fastest Rural & On-the-Go Internet in the USA
> ctas: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE

## Current state
cta: CHECK COVERAGE | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE; notes: Guarantee mentioned on rural-internet page but not on plans pages.

## Required change
notes: Place the confidence guarantee or a return-policy statement directly on the plans pages next to the pricing.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Place the confidence guarantee or a return-policy statement directly on the plans pages next to the pricing.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_guarantee_not_near_purchase` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
