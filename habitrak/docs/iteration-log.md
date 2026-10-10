# Habitrak iteration log

Newest first. Each entry: what changed, why, and what's next.

## Oct 10, 2026: Enter saves; Chores tracker

- **Enter key (Mark's ask):** Enter now saves in the timeline edit row, "Add something you missed", the medication form (Enter in the time box adds the time) and the morning check-in note. Escape cancels an edit or closes the form.
- **Chores (Mark's ask):** a new stretch, like Work: tap to start, Stop or another stretch ends it. Shows in Trends as time a day.

## Oct 9, 2026: Trends tab, medications and reminders

- **Trends (new tab):** 7, 30, 90 days or All. Each tracker gets its average a day (sleep: a night), the change against the previous period of the same length, resisted and given-away rates for moments, and a daily bar chart with the average as a dashed line. Tap a bar for that day's number. Averages count only days with something logged; sleep averages only nights with sleep logged. Ranges over 120 days show weekly bars.
- **Medications:** add each one in Trackers (name, dose, due times; none means as needed). Saving the first one adds the Meds tile if there's room. The Meds tile asks which one. A dose counts as taken by a Meds entry from 2 hours before it until 2 hours before the next dose.
- **Reminder banner on Today:** shows for a dose that's due and not logged, with Took it now, Took it at the due time, Skip, and In 30 min. When nothing is due, a line shows the next dose. Trends shows doses taken out of doses due for each medication.
- **Limit:** reminders only show while Habitrak is open. Real phone notifications need the Android build (already in the release path).
- **Voice logging:** instructions updated so "took my Metformin" logs against the right medication.

## Oct 9, 2026: Week bars include the night before

- **Mark's ask:** with the day starting at 7 AM, last night's sleep sat at the end of the previous row. Each Week row and the day view now start 8 hours earlier (11 PM to 7 AM for a 7 AM start). The 8-hour lead-in is drawn lighter, with a divider and a bold label at the day start.
- **Unchanged:** totals, averages and each day's timeline still count only the day itself, so nothing is counted twice. The Today bar still starts at the day start.

## Oct 9, 2026: Edit any day, add what you missed

- **Found in Mark's use:** once a day ended, it couldn't be edited, and there was no way to add a forgotten entry. Mark couldn't log last night's sleep in the morning. Not in the requirements before; now it is (spec, MVP scope).
- **Built in 3.0:** Week rows open that day. Each day shows its ribbon and timeline with Edit and Delete, plus "Add something you missed" (tracker, Logged/Resisted/Gave away where it applies, time, or start and end for stretches). Arrows step to the day before or after; "Earlier days" goes back further. Today has the same add form; a time later than now counts as last night.
- **Bug fixed:** a tap made in the first moment after opening, before the day's saved entries arrived, could save over that day. The app now reads the day before writing to it. Reproduced with a slow stand-in store (3 entries lost before, 0 after).

## Oct 7, 2026: Habitrak 3.0 replaces 2.0

- **Mark's call:** 3.0 becomes his daily tracker. 2.0 stays untouched as a read-only backup.
- **Must-haves added to 3.0:** Resisted (for any moment with a goal) and Gave a smoke away; morning check-in after Sleep (feel 1 to 5, symptoms, note) with the withdrawal caution kept from 2.0; Last 7 nights table on Week.
- **Mac:** two-column layout on wide screens; same private log on phone and Mac.
- **History:** 199 entries from 2.0 (146 smokes, 19 drinks, 2 waters, 18 resisted, 12 given, 2 nights) plus 2 check-ins and goals (smoke: 30 a day, 30 min wait; drink: 5 a night, 60 min wait) are staged in 3.0's private storage. The app files them into days in Mark's own time zone the first time he opens it, then marks the import done. Tested against a stand-in store: all 199 landed.
- **Not carried (Mark's choice):** packs, bottle, spending, reason chips. Notes on old entries are kept and shown in the timeline.
- **Voice logging:** new [skill instructions](../skills/habitrak-log/SKILL.md) for 3.0. Mark replaces the old skill in his claude.ai skills settings.

## Oct 7, 2026: Habitrak 3.0, working web app

- **Built:** [Habitrak 3.0](https://claude.ai/artifact/3oHbVb1zqH7pzWgEJS4czT), the My Day design as a usable web app (source: `app/habitrak-3.html`). No sample data and no mock home screen; real clock.
- **Saving:** each person's log is private to their Claude account (one document per day under their own data area). Outside Claude it falls back to saving in the browser, and says so.
- **Includes:** first run (pick trackers, set day start), Today (Now card with Stop, day ribbon, 3×3 tiles, timeline with Edit, end-time editing for stretches, Delete, Undo), Week (7 ribbons, averages over days logged), Goals (most a day, wait between), Trackers (picks, day start, erase everything).
- **Added (Mark's call):** Stretch and Workout in the stretches list, in the app and the prototype.
- **Not in the web form:** home-screen widget, Quick Settings tile, notifications. Those need the Android build.
- **Next:** Mark uses it on the Galaxy S5 Active and Razr 2020 (private test step 2).

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
