# Competing primary CTAs — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
The hero presents two equally prominent CTAs, 'SHOP MEN' and 'SHOP WOMEN', splitting user focus and delaying the primary action of exploring products.

## Evidence (from the live site)
> Hero section contains both 'SHOP MEN' and 'SHOP WOMEN' buttons with no visual hierarchy, as seen in the body_sample: 'SHOP MEN SHOP WOMEN'.
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN' and 'SHOP WOMEN' with no subheadline explaining the brand's unique selling points.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Two CTAs of equal weight; user must choose a gender before seeing products, adding friction.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Single primary CTA 'Shop All' to reduce decision paralysis; secondary links to Men/Women can be placed in nav or below the fold.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Single primary CTA 'Shop All' to reduce decision paralysis; secondary links to Men/Women can be placed in nav or below the fold.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_primary_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
