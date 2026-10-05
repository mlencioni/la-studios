# Hallway test kit: My Day prototype

**Goal:** find out whether someone who has never seen Habitrak can log their day from the widget without help.
**Pass bar (spec section 7):** first log within 60 seconds, 5 of 5 testers; testers can explain moment vs. stretch in their own words.
**Device:** an older Samsung Galaxy, chosen on purpose to check backward compatibility. Write down its model and Android version (Settings > About phone > Software information) in the results log. Open the prototype in the phone's browser or the Claude app: [Habitrak My Day](https://claude.ai/artifact/WUubEax4UCCx9ph9F5SGS3). Share the link with yourself first so it opens on the phone.

## Old-phone checks (before the first tester)

- Update Chrome and Samsung Internet as far as the phone allows. If the prototype doesn't load or the buttons do nothing, note the browser version; the prototype needs a browser from about 2021 or later (Chrome 88 or newer).
- Time how long the page takes to open and how quickly a tile responds. The spec target is feedback within 300 ms of a tap.
- Try the largest font size (Settings > Display > Font size) on one tester run. Tile labels must not be cut off in a way that hides what they are.

## Who to ask

5 people, no more than 1 who has heard about Habitrak. Aim for a mix:

- 2 who would never call themselves "techy"
- 1 who smokes, drinks, or is cutting back on something
- 1 under 30, 1 over 50

## Before each test

1. Tap **Reset sample day** (under the notes) and open the **First run** tab.
2. Say only this: *"This is an early design for an app. I'm testing the app, not you. Please think out loud."*
3. Start a timer when you hand over the phone. Don't explain, point, or help. If they're stuck for 30 seconds, note it, then move on.

## Tasks (read each one aloud, exactly)

| # | Say | Watch for | Pass |
|---|---|---|---|
| 1 | "Set this up for yourself." | Do they pick things that fit them? Do they notice Smoke and Drink? | Taps Next and Add widget unaided |
| 2 | "You just had a coffee. Log it." | Do they look for the app or use the widget? | Logs coffee from the widget in under 60 seconds from hand-over |
| 3 | "You're starting work now." | Do they understand a tile can be running? | Work tile turns solid; Now line shows Work |
| 4 | "Oops, that coffee was a mistake. Fix it." | Do they see Undo in the widget? | Undoes within 5 seconds, or finds Edit in the app |
| 5 | "You're done with work and going for a walk." | Do they tap Walk directly or try to stop Work first? | Walk running, Work stopped (either path) |
| 6 | "Show me what your morning looked like." | Do they open the app and read the ribbon? | Points to the right part of the ribbon |

## After the tasks (2 minutes)

1. "What's the difference between Coffee and Work in this app?" (Write their exact words.)
2. "What would make you stop using this after a week?"
3. "If you saw this in the Play Store, what would you expect it to do?"

## Results log

Copy one row per tester into the [iteration log](iteration-log.md).

Phone: model ______, Android version ______, browser and version ______

| Tester | Task 1 | Task 2 (seconds) | Task 3 | Task 4 | Task 5 | Task 6 | Moment vs. stretch, their words | Biggest stumble |
|---|---|---|---|---|---|---|---|---|
| 1 | | | | | | | | |
| 2 | | | | | | | | |
| 3 | | | | | | | | |
| 4 | | | | | | | | |
| 5 | | | | | | | | |

## Limits of this test

- The prototype is a web page showing a pretend home screen. It can't test adding a real widget, the Samsung home-screen grid, the Quick Settings tile, or how fast native code runs on old hardware. Those get tested on the first Android build.
- Mark is the first user, not a tester. His feedback goes in the log separately.
