# Habitrak iteration log

Newest first. Each entry: what changed, why, and what's next.

## Oct 5, 2026: Test phones named

- **Phones:** Galaxy S5 Active (2014, expected Android 6.0.1) as the oldest phone Habitrak supports, and Motorola Razr 2020 (folding, tall screen, outer display). Android versions to be confirmed on the phones.
- **Proposed:** minimum Android 6.0 (API 23), if the build tools still allow it.
- **Fixed:** on short screens like the S5's, the prototype now fits the screen without scrolling to reach the bottom bar.
- **Staying at 9 trackers:** Mark reviewed a 12-tracker mockup and kept 9.

## Oct 5, 2026: Tracker limit raised to 9

- **Changed (Mark's call):** up to 9 trackers instead of 8, so Today's tile grid is a full 3×3 with no gap. The widget still shows the first 4.

## Oct 5, 2026: Private test step 1, design walkthrough

- **Found:** 2 blockers, 5 major, 3 minor ([findings](06-walkthrough-findings.md)). Biggest: a fresh install showed someone else's day with Work already running, and there was no way to delete a mistaken entry after Undo expired.
- **Fixed in prototype v4:** all blockers and majors. On a phone, the prototype now fills the screen, ready for step 2.
- **Carried into the build:** edit a stretch's end time, Week empty state, drag to reorder widget tiles.
- **Next:** step 2 (Mark's own use on the old Galaxy) when Mark decides.

## Oct 5, 2026: Decisions approved

- **Approved by Mark:** Capacitor on Android (TWA dropped); name locked as Habitrak; Smoke and Drink offered at sign-up, not pre-selected; no account at first launch, backup offered after day 3.
- **Updated:** MVP spec (sections 6 and 8), Android release path, prototype notes, and the Commercialization Plan doc (renamed to Habitrak, stack table, Oct 5 decisions, phase 2, Road to publish).
- **Workflow:** commits go straight to the branch until MVP; no pull requests yet.
- **Also decided:** hallway tests come before any build, on an older Samsung Galaxy to check backward compatibility; web home is habitrak.lencioni.io; Play Console isn't set up yet, so the D-U-N-S request starts now.
- **Changed same day:** hallway tests dropped, because Mark wants nobody to see Habitrak before MVP. Replaced by the three-step [private test plan](05-private-test-plan.md): design walkthrough now, Mark's own use when he decides, and the Play closed test at MVP.
- **Next:** step 1, the design walkthrough.

## Oct 1, 2026: My Day direction set

- **Source tracked:** Habitrak 2.0 artifact, version `1790830917-a1ba`. 2.0 stays Mark's live tracker and isn't edited by this work.
- **Done:** audit, MVP spec, Android release path, store listing draft, interactive My Day prototype.
- **Decision proposed:** My Day (moments and stretches on a 24-hour ribbon) is the primary widget; smoking and drinking become optional trackers with goals.
- **Risk raised:** the plan's Android TWA can't host a widget. Capacitor proposed.
- **Next:** Mark's decisions (spec section 8), then hallway tests of the prototype on an Android phone.
