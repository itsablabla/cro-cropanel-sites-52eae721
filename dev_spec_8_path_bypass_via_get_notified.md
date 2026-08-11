# Path bypass via Get Notified — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The product page offers a 'Get Notified' CTA for an out-of-stock item, but the page also includes a 'Learn More' CTA that may lead users away from the purchase path, creating a bypass.

## Evidence (from the live site)
> CTAs list includes 'Get Notified' and 'Learn More' on the same product page, as seen in the inventory: 'ctas': ['Shop All', 'Get Notified', 'Learn More', 'Sign Up', 'Shop + -'].

## Current state
h1: Anytime Ankle Sock; cta: Get Notified / Learn More; notes: Two CTAs compete; 'Learn More' may lead to informational content, distracting from the primary action of joining the waitlist.

## Required change
h1: Anytime Ankle Sock; cta: Get Notified; notes: Remove or de-emphasize 'Learn More' to keep focus on the primary conversion action (email capture for restock).

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Remove or de-emphasize 'Learn More' to keep focus on the primary conversion action (email capture for restock).
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_path_bypass_via_get_notified` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
