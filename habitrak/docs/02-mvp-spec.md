# Habitrak MVP: My Day

**Owner:** LA Studios, Marketing and User Usability Director
**Status:** Draft 2, Oct 5, 2026. All four open decisions approved by Mark on Oct 5 (section 8).
**Prototype:** [`../prototype/my-day.html`](../prototype/my-day.html), also published as the *Habitrak My Day* artifact.

## 1. Positioning

**One line:** Tap what you do. See your day.

**Promise:** Habitrak shows you where your day actually goes, with one tap per moment and no judgment.

**Who it's for, in launch order:**

1. **The day-tracker.** Wants to see where time goes: work, breaks, coffee, walks, meals, sleep. Not technical. Logs from the home screen or not at all.
2. **The cutter-backer.** Already counting something (cigarettes, drinks, coffee, vapes) and wants to see it in the context of the whole day. This is Mark, and the 2.0 goal features serve this group.
3. **Later:** clinicians and programs who receive a summary (paid tier, post-MVP).

**What makes it different:** habits are shown on the same day ribbon as everything else, so the connections show up on their own. Coffee after a short night, a smoke at every work milestone, a second drink when the walk got skipped.

## 2. The primary widget: My Day

The home-screen widget **is** the product. The app exists to set it up and to look back.

### Two kinds of things you track

| Kind | One tap does | Examples | Shown as |
|---|---|---|---|
| **Moment** | Logs one, right now | Coffee, Water, Smoke, Drink, Meal, Snack, Meds | A tick on the day ribbon and a count on the tile |
| **Stretch** | Starts it; tap again to stop. Starting another stops the current one | Work, Chores, Walk, Commute, Rest, Screen time, Sleep, Stretch, Workout | A colored band on the day ribbon; "Now: Work · 1h 12m" |

Only one stretch runs at a time. That keeps the model simple enough to explain in one sentence: *"Tap a moment when it happens. Tap a stretch to start it, tap again to stop."*

### Widget sizes (Android, Jetpack Glance)

| Size | Content | Purpose |
|---|---|---|
| **4×2 (default)** | Now line, 24-hour day ribbon, 4 tiles with today's counts | The primary widget |
| 2×2 | Now line, 4 tiles, no ribbon | Smaller home screens |
| 1×1 | One tile (user picks). Tap to log | Single habit people want to count fast |
| Quick Settings tile | Start/stop the current stretch or log the user's top moment | Logging from the pull-down shade |
| Ongoing notification | While a stretch runs: "Work · 42m" with **Stop** | Required by Android for visible running state; also a second log surface |

### Widget rules

- Every tap gives feedback in the widget within 300 ms (count increments, tile pulses), and the app is never opened by a tile tap.
- Undo: tapping the same moment tile within 5 seconds offers **Undo** in the widget's Now line instead of a second log. Opening the app shows the full Undo bar.
- The day ribbon runs from the user's wake time, not midnight, so late nights stay on "today".
- No numbers that need explaining in the widget. Counts only.

## 3. App screens (MVP)

| Screen | Job | Content |
|---|---|---|
| **Today** | Log and look at today | Now card with Stop, day ribbon, all tiles in a 3×3 grid (up to 9 trackers), timeline newest first with Edit and Undo |
| **Week** | See patterns, and fix any past day | 7 day ribbons stacked, each starting 8 hours before the day start (drawn lighter) so the night before is visible; tap a day to open it, edit or delete its entries, and add anything missed (moments with a time, stretches with start and end, overnight stretches like Sleep included); step back to earlier days. Totals per tracker, one plain-language observation |
| **Trends** | See averages over time | Range 7, 30, 90 days or All. One card per tracker: average a day (sleep: a night), change against the previous period of the same length, resisted and given-away rates, and a daily bar chart with the average marked; tap a bar for its value. Medication doses taken out of doses due. Averages count only days with something logged |
| **Goals** | Opt-in limits for any moment | Ceiling per day and minimum wait between (the 2.0 "gap"), framed as a ceiling, never a budget |
| **Me** | Settings | Trackers, wake time, theme, export, delete account and data |

Onboarding is two screens: **pick what to track** (presets, up to 9, change anytime) and **add the widget** (Android pin-widget prompt).

## 4. Scope

### In the MVP (Android first)

- Moments and stretches, user-chosen from presets, renameable, with color; up to 9 trackers so Today shows a full 3×3 grid
- 4×2 widget, 1×1 widget, Quick Settings tile, ongoing notification
- Today, Week, Goals (ceiling and wait time), Me
- Edit time on any entry; late logging with a time window (from 2.0)
- **Medications** (added Oct 9, 2026): a list in Trackers with name, dose and due times. Today shows a reminder banner for any dose that is due and not logged: Took it now, Took it at the due time, Skip, or remind in 30 minutes. The Meds tile asks which medication. Reminders show only while the app is open; phone notifications come with the Android build
- **Fix any day, not just today** (added Oct 9, 2026 from Mark's use): "Add something you missed" on Today and on every past day. On Today, a time later than now counts as last night, so a forgotten night of Sleep can be added the next morning. An end earlier than the start means the next morning
- Works fully offline; account optional at first launch, needed only for sync and backup
- Light and dark themes, 48dp targets, TalkBack labels on every tile
- Export to CSV; delete all data in-app (store requirement)

### Carried from 2.0, after MVP (v1.1+)

| Feature | Release |
|---|---|
| Why chips and notes on a moment ("Why this one?") | v1.1, opt-in per tracker |
| Supplies: packs, bottles, cartons, stock on hand | v1.1 |
| Drink detail: pour, mixer, glass, standard drinks, calories | v1.2 |
| Morning check-in and sleep table | v1.1 |
| Doctor summary (paid) | v1.2 |
| Drive check, wearables, gesture detection | After launch, native |

### Not in the MVP

Brand names, prices, spend math, streaks, social features, ads, AI insights.

## 5. Language rules (from the 2.0 principles, made enforceable)

- Tile labels are nouns the user chose: "Coffee", not "Log caffeine intake".
- One sentence per explanation, never wrapping on a 360dp screen.
- No "quit", "fail", "relapse", "streak broken". Goals say "ceiling" and "wait".
- Every toast names what happened: "Coffee logged · 2:47 PM". Always with Undo.

## 6. Architecture (decided Oct 5, 2026)

Habitrak ships in a **Capacitor** shell on both Android and iOS. The original plan's Android Trusted Web Activity is dropped, because a TWA can't host a home-screen widget, a Quick Settings tile, or an ongoing notification.

| Layer | Choice |
|---|---|
| App UI | The web app (Vercel build), loaded in Capacitor |
| Widget, Quick Settings tile, ongoing notification | Native Kotlin module with Jetpack Glance (Android); WidgetKit later on iOS |
| On-device data | SQLite, shared by the web UI and the widget. Every tap is written here first, so logging works offline and instantly |
| Backup and sync | Supabase with row-level security, only after the user turns on backup |

Full native (Kotlin/Compose, then Swift) stays the fallback if Capacitor fails store review or widget performance targets.

## 7. Acceptance criteria for "MVP design done"

1. In the design walkthrough, every first-run task can be finished without help; at the MVP closed test, testers log their first moment from the widget within 60 seconds of install.
2. Closed-test testers can explain moment vs. stretch in their own words after 1 day (survey question).
3. No screen in the MVP needs scrolling to reach its primary action on a 360×640dp phone.
4. Every 2.0 feature is either in the MVP, scheduled in section 4, or explicitly cut.
5. Store listing draft, icon, and 5 screenshots approved.

## 8. Decisions (approved by Mark, Oct 5, 2026)

| # | Decision |
|---|---|
| 1 | Android shell is **Capacitor**, not a Trusted Web Activity |
| 2 | Name locked: **Habitrak**, everywhere (app, listing, docs, agents). Play Store and domain availability still to be checked |
| 3 | Smoke and Drink appear at sign-up but are **not pre-selected** |
| 4 | **No account at first launch.** Logs stay on the phone; backup is offered after day 3 |
| 5 | Repo workflow: commit straight to the branch until MVP; pull requests start after MVP |
| 6 | Web home for MVP: **habitrak.lencioni.io** (privacy policy, account deletion, support). A dedicated domain can come later |
| 7 | Nobody outside L&A sees Habitrak before MVP. Testing runs in three private steps ([test plan](05-private-test-plan.md)): design walkthrough, Mark's own use on a **Galaxy S5 Active** and a **Motorola Razr 2020**, then the Google Play closed test at MVP. Mark decides when step 2 starts. The S5 Active sets the backward-compatibility floor (proposed: Android 6.0); the Razr covers a tall, folding screen to check backward compatibility. The oldest supported Android version is set from that phone before the build starts |
| 8 | Up to **9 trackers** (was 8), so Today shows a complete 3×3 grid. The widget still shows the first 4 (3 at large text) |
