# Android first: release path

Rules and fees change. Each item marked **verify** must be checked against current Google documentation when it's reached.

## Stage 0. Design lock (now)

- [x] Audit 2.0 from marketing and everyday-user views ([01](01-ux-audit-2.0.md))
- [x] MVP spec with My Day as the primary widget ([02](02-mvp-spec.md))
- [x] Interactive prototype (`prototype/my-day.html`)
- [x] Mark approves the open decisions in spec section 8 (Oct 5, 2026)
- [ ] Play Store name search for Habitrak
- [x] Web home decided: habitrak.lencioni.io (Oct 5, 2026)
- [x] Private test step 1: design walkthrough of the prototype, Oct 5, 2026 ([findings](06-walkthrough-findings.md))
- [ ] Private test step 2: Mark uses the prototype on the Galaxy S5 Active and Motorola Razr 2020 (start date: Mark's call)
- [ ] Icon, wordmark, 5 screenshots

## Stage 1. Build

- [ ] Decide the oldest Android version Habitrak supports. Proposal: **Android 6.0 (API 23)**, matching the Galaxy S5 Active, if the Capacitor and Jetpack Glance versions we build on still allow it (**verify** both; newer releases may require Android 7 or later). The app still targets the current API level Play requires
- [ ] Foldable check on the Razr 2020: fold and unfold keep state; ongoing notification on the outer display
- [ ] Repo scaffold: web app (Vercel) + Capacitor Android project (no Trusted Web Activity)
- [ ] Local SQLite store shared by web UI and widget
- [ ] Glance widget 4×2 and 1×1, checked on Samsung One UI 4×5 and 5×5 home grids; Quick Settings tile; ongoing notification for stretches
- [ ] No account at first launch; backup prompt on day 3
- [ ] Supabase sync with row-level security, only after backup is turned on
- [ ] TalkBack pass; font scale 200% pass; dark theme pass
- [ ] Old-phone pass on the Galaxy S5 Active: cold start time, tap-to-feedback under 300 ms, battery use of the ongoing notification, older Android WebView
- [ ] Import of Mark's 2.0 history as the first real dataset

## Stage 2. Play Console

- [ ] D-U-N-S number for Lencioni & Associates (start now: it can take weeks; not set up as of Oct 5, 2026)
- [ ] Play Console account as an **organization** (personal accounts created after Nov 2023 must run a closed test with a minimum number of testers for a minimum number of days before production; **verify** current numbers)
- [ ] App signing by Google Play; upload key stored in the password manager
- [ ] Privacy policy and account-deletion page at habitrak.lencioni.io (Vercel, DNS record in lencioni.io)
- [ ] Data safety form: data collected (app activity, health-adjacent), encrypted in transit, deletable
- [ ] Health apps declaration (**verify** whether tracking alcohol and tobacco counts as health features)
- [ ] Content rating questionnaire. Alcohol and tobacco references may raise the rating; listing copy leads with day tracking
- [ ] Target API level meets the current Play requirement (**verify**)

## Stage 3. Test and launch

- [ ] Internal test: Mark + 2
- [ ] Closed test: 10 to 20 invited testers, at least 2 weeks. This is private test step 3 and the first time anyone outside L&A sees Habitrak; testers get the 6-task survey from the [test plan](05-private-test-plan.md)
- [ ] Store listing from [04](04-store-listing-draft.md)
- [ ] Production rollout at 20%, then 100%

## Stage 4. iOS follows

Same Capacitor project, WidgetKit widget, Siri quick-log, TestFlight. The widget is the native feature that answers Guideline 4.2.
