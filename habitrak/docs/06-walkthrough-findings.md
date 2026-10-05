# Private test step 1: design walkthrough findings

**Run:** Oct 5, 2026, by Claude as LA Studios Marketing and User Usability Director
**Build tested:** prototype v3 ([Habitrak My Day](https://claude.ai/artifact/WUubEax4UCCx9ph9F5SGS3)), fixed in v4 the same day
**Method:** the six tasks in the [private test plan](05-private-test-plan.md), walked as Dana, Sam, and Mark, on a 360-pixel-wide screen (the old Galaxy's width), light and dark, at normal and about 130% text size. Each step asked: will they know what to do, see the control, connect its label, and know it worked?

**Result:** 2 blockers, 5 major, 3 minor. Every blocker and major is fixed in the prototype. Three items carry into the build.

| # | Severity | Task | What a first-timer would hit | Fix |
|---|---|---|---|---|
| 1 | Blocker | 1, 3 | After first run, the home screen showed a full sample day with **Work already running**. "You're starting work" made the tester tap Work, which stopped it. A fresh install also showed a coffee goal ("4 of 4") nobody set | Fixed: finishing first run starts an empty day with goals off, as a real install would |
| 2 | Blocker | 4 | "That coffee was a mistake": after the 5-second Undo is gone, nothing removes an entry. Edit only moves its time | Fixed: Edit now offers **Delete**, with Undo |
| 3 | Major | 3, 5 | A running stretch tile shows only its time ("1h 12m"). Nothing says that tapping it again stops it | Fixed: the widget's Now line shows a **Stop** button while a stretch runs, matching the app's Now card |
| 4 | Major | all | On the phone itself, the prototype drew a phone frame inside the phone, leaving about 300 pixels of screen | Fixed: on phone-width screens the frame drops and the prototype fills the screen. Needed for step 2 |
| 5 | Major | 2 | At large text, widget labels cut off ("Coff…") and "4 of 4" wrapped onto 2 lines | Fixed: the widget shows counts only, and drops to 3 tiles at large text. **Build rule:** Glance widget goes to 3 tiles at font scale 130% and up |
| 6 | Major | 4 | Undo in the widget was underlined text about 32 pixels tall, under the 48dp touch target | Fixed: Undo and Stop are 40+ pixel buttons. **Build rule:** 48dp in Glance |
| 7 | Major | 1 | At large text, the Stretches list (Work, Sleep) sits below the fold with no cue. A tester could tap Next without seeing it | Fixed: the footer shows "5 of 8 picked · more below" until the list is scrolled to the end |
| 8 | Minor | 1 | Widget-order badges looked random (Coffee 2, Water 4, Work 1) | Fixed: defaults now follow a sensible order (Coffee, Work, Water, Walk), so at large text the 3-tile widget still includes a stretch. Copy explains the numbers |
| 9 | Minor | Goals | "Ceiling a day" is unfamiliar wording | Fixed: the label says "Most a day". The ceiling idea stays in the one-line explanation above it |
| 10 | Minor | 2 | The widget's idle line said "since wake 6:50", which means nothing on a new install | Fixed: removed |

## Carried into the build

- A stretch's **end time** can't be edited yet, only its start. Needed before the closed test.
- **Week** still shows sample past days after first run. A real install starts empty, so Week needs a designed empty state ("Your week fills in as you log").
- **Reordering** widget tiles is by un-picking and re-picking. Drag to reorder belongs in the build's Trackers screen.

## What passed

- The moment vs. stretch split is explained at the point of choice ("Tap when it happens" / "Tap to start, tap again to stop") and needs no tutorial.
- Every tap names its result in a toast, with Undo.
- Switching stretches (Work to Walk) works in one tap with no extra step.
- No horizontal scrolling at 360 pixels, in either theme.

## Next

Step 2, Mark's own use on the old Galaxy, starts when Mark decides.
