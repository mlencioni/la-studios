# Private test plan: My Day

**Rule:** nobody outside L&A sees Habitrak until the MVP closed test on Google Play.
**Goal:** find out whether someone who has never seen Habitrak can log their day from the widget without help, without showing it to anyone early.
**Pass bar (spec section 7):** every first-run task can be finished unaided in the walkthrough; at the closed test, first log within 60 seconds of install, and testers can explain moment vs. stretch in their own words.

| Step | Who | When | What it catches | What it can't catch |
|---|---|---|---|---|
| 1. Design walkthrough | Claude, as the usability director | Now | Unclear labels, dead ends, steps a first-timer can't guess, layout problems at phone width and large font | How real people actually behave |
| 2. Mark's own use | Mark, on an older Samsung Galaxy | When Mark decides | Friction in daily logging, speed on old hardware, older-browser problems | Whether a stranger understands it (Mark knows the design too well) |
| 3. Closed test | 10 to 20 invited testers on Google Play | At MVP | Real first-time understanding, the 60-second first log, what makes people stop | Nothing before MVP; that's the point |

Findings from every step go in the [iteration log](iteration-log.md).

## Step 1: Design walkthrough

Each task is walked through as three personas, on a 360-pixel-wide phone screen (the old Galaxy's width), in light and dark, and at the largest font size:

- **Dana, 38, shift worker, not technical.** Wants to see where the day goes.
- **Sam, 52, cutting back on smoking.** Larger text, impatient with setup.
- **Mark, the first user.** Smokes and drinks, wants exact counts.

At each step, the walkthrough asks four questions:

1. Will they know what to do here?
2. Will they see the control that does it?
3. Will they connect the control's label to what they want?
4. After tapping, will they know it worked?

Any "no" is a finding, rated **Blocker** (task can't be done), **Major** (done, with confusion or a wrong turn), or **Minor** (polish).

## Step 2: Mark's own use

**Phone setup:** record the Galaxy's model and Android version (Settings > About phone > Software information). Update Chrome and Samsung Internet as far as the phone allows. The prototype needs a browser from about 2021 or later (Chrome 88 or newer).

**Each day, for as long as Mark chooses:**

- Log a real day in the prototype (it resets on reload, so this is about feel, not data).
- Note anything slow, confusing, or annoying, with the time. Feedback after a tap should feel instant (spec target: under 300 ms).
- Try one session at the largest font size (Settings > Display > Font size).

Phone: model ______, Android version ______, browser and version ______

## Step 3: Closed test survey (at MVP)

Testers install from the closed test link, then answer in the app or a form:

| # | Task | Pass |
|---|---|---|
| 1 | Set it up for yourself | Finishes first run unaided |
| 2 | You just had a coffee. Log it. | Logs from the widget within 60 seconds of install |
| 3 | You're starting work now. | Work shows as running |
| 4 | That coffee was a mistake. Fix it. | Uses Undo or Edit |
| 5 | Done with work, going for a walk. | Walk running, Work stopped |
| 6 | Show what your morning looked like. | Finds it on the day ribbon |

Follow-up questions:

1. What's the difference between Coffee and Work in this app?
2. What would make you stop using this after a week?
3. If you saw this in the Play Store, what would you expect it to do?
