# Social proof isolated — dev spec
Site: nomadinternet.com · Priority 4 · High · Effort: Medium (2-5 days)

## Problem
Customer testimonials appear only on the homepage and rural-internet page, while the plans pages where users choose a plan and price show no reviews or social proof.

## Evidence (from the live site)
> h2: Real Stories from Real Users
> h2: The Fastest Rural & On-the-Go Internet in the USA
> h2: $99.95 /month

## Current state
notes: Testimonials on homepage and rural-internet page, but not on plans pages.

## Required change
notes: Add customer testimonials or review snippets to the plans pages near pricing and coverage CTAs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add customer testimonials or review snippets to the plans pages near pricing and coverage CTAs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_social_proof_isolated` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
