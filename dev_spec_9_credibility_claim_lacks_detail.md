# Credibility claim lacks detail — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Medium (2-5 days)

## Problem
The site claims to be America's largest wireless internet provider but provides no verifiable evidence such as subscriber counts, awards, or third-party validation near that claim.

## Evidence (from the live site)
> h2: Join America's Largest Wireless Internet Provider Featuring
> h2: As Featured In:

## Current state
notes: Claim without supporting evidence.

## Required change
notes: Add specific supporting evidence such as subscriber numbers, press logos, or independent review ratings adjacent to the claim.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add specific supporting evidence such as subscriber numbers, press logos, or independent review ratings adjacent to the claim.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_credibility_claim_lacks_detail` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
