# Habitrak 2.0: marketing and everyday-user audit

**Reviewer:** LA Studios, Marketing and User Usability Director
**Artifact reviewed:** [Habitrak 2.0](https://claude.ai/artifact/9TCskQ9y2h9ki736ePsqCT), version `1790830917-a1ba` (Oct 1, 2026)
**Read alongside:** [Product Register and Commercialization Plan](https://claude.ai/artifact/LVG8UNhDgwyzJfiSeRffcj)

## Verdict

Habitrak 2.0 is a strong personal instrument and a weak first product. It does an excellent job for its first user: someone cutting back on cigarettes and vodka who wants exact counts, gaps, packs, bottles, and spend. A stranger who downloads it from Google Play would not understand it, and most of them don't smoke or drink the way it assumes.

The fix is to change what sits at the front of the app, not to delete the work. The front becomes **My Day**: a one-tap record of what you are doing all day. Smoking and drinking become two of the things you can track, with their goal features available to anyone who turns them on.

## Lens 1: the everyday user

Persona: *Dana, 38, works shifts, not technical.* Dana wants to know where the day goes and maybe cut down on coffee. Dana will give an app about 30 seconds.

| # | What Dana hits | Why it hurts | Fix in MVP |
|---|---|---|---|
| 1 | The app opens on a tab titled **Smoke** | Dana doesn't smoke. The first screen says "not for you". | Open on **Today**, with the user's own activities |
| 2 | One screen holds ~67 buttons and 11 "▸" questions (Pack count off?, Bottle level off?, Wrong bottle details?…) | Too many choices; the main action is lost | Home has one row of tiles and nothing else to decide |
| 3 | Words like *gap*, *Resist*, *Finish*, *tumbler*, *standard drinks*, *catch-up pacing* | Jargon learned by the founder in use, not known to newcomers | Plain verbs: "Coffee", "Start work", "Stop" |
| 4 | Mark's setup is built in: vodka brands, Red Bull sizes, Yeti tumblers, 14-second pour | Reads as somebody else's app | Presets chosen at onboarding; no brand names |
| 5 | "Connecting to your private log…" then disabled buttons | First impression is a wait and a dead screen | Works offline from the first second; sync later |
| 6 | No onboarding | Dana doesn't know what to tap first | 2 screens: pick what to track, add the widget |
| 7 | Logging requires opening the app and scrolling | Logging has to happen in the moment, or not at all | Home-screen widget is the primary surface |
| 8 | Many corrections (pack fix, bottle level, forgot, time edit) | Valuable for accuracy; overwhelming up front | One "Edit" on any timeline row; inventory is v1.1 |

### Keep these, they are right

- One tap, then an **Undo** bar. This is the core habit loop and it works.
- 48px buttons, dark mode, phone-first layout.
- Neutral, non-judging language ("No judging, just your numbers").
- "A limit is a ceiling, not a budget." Keep this as the goals philosophy.
- Honest late logging (forgot / catch-up with a time window).

## Lens 2: marketing

| # | Issue | Risk | Recommendation |
|---|---|---|---|
| 1 | Five names in use: Habitrak, Habitrack, habitrak, Habit Tracker, Consumption tracker | Weak search presence; looks unfinished | Pick **Habitrak** everywhere. Check Play Store and domain availability before locking it |
| 2 | Leads with smoking and alcohol | Narrow market. Play content rating, ad policy, and review scrutiny are tougher when tobacco and alcohol lead the listing | Lead with "see your day"; habits are a feature, not the headline |
| 3 | No visual identity: no icon, no wordmark, no screenshot story | Can't build a store listing | Wordmark and icon derived from the day ribbon (see prototype) |
| 4 | The best idea is hidden: *habits interact* (smoking pace while drinking, sleep after heavy nights) | This is the differentiator no single-habit app has | Name it in the listing: "See how your day connects" |
| 5 | Positioned as a quit tool | Puts off people who aren't ready to quit, the larger group | "Awareness first" as the brand promise. Never "quit" in the headline |
| 6 | Doctor summary is the strongest paid feature but isn't built | Weak paid tier at launch | Keep the free MVP; doctor summary leads v1.x paid tier |

## Lens 3: getting to Android

The current plan ships Android as a **Trusted Web Activity** (TWA). A TWA is a full-screen browser tab. It **cannot provide a home-screen widget**, a Quick Settings tile, or an ongoing notification with a Stop button. If My Day is the primary widget, the TWA plan doesn't work as written.

Recommendation, for Mark's decision: use **Capacitor on Android as well as iOS**. The web app stays the app; a small native Kotlin module provides the widget (Jetpack Glance) and writes into the same local store the web app reads. This also lines up Android with the iOS plan, which already needs a widget for Guideline 4.2. Details in [`02-mvp-spec.md`](02-mvp-spec.md).

## Bottom line

Keep 2.0 running as Mark's personal tracker and as the "habit goals" engine. Build the MVP around My Day, with smoking and drinking as optional trackers on top.
