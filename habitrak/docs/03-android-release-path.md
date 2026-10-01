# Android first: release path

Rules and fees change. Each item marked **verify** must be checked against current Google documentation when it's reached.

## Stage 0. Design lock (now)

- [x] Audit 2.0 from marketing and everyday-user views ([01](01-ux-audit-2.0.md))
- [x] MVP spec with My Day as the primary widget ([02](02-mvp-spec.md))
- [x] Interactive prototype (`prototype/my-day.html`)
- [ ] Mark approves the open decisions in spec section 8
- [ ] 5 hallway tests of the prototype on a real Android phone; log results in [iteration log](iteration-log.md)
- [ ] Icon, wordmark, 5 screenshots

## Stage 1. Build

- [ ] Repo scaffold: web app (Vercel) + Capacitor Android project
- [ ] Local SQLite store shared by web UI and widget
- [ ] Glance widget 4×2 and 1×1; Quick Settings tile; ongoing notification for stretches
- [ ] Supabase sync with row-level security; sign-in optional
- [ ] TalkBack pass; font scale 200% pass; dark theme pass
- [ ] Import of Mark's 2.0 history as the first real dataset

## Stage 2. Play Console

- [ ] D-U-N-S number for Lencioni & Associates
- [ ] Play Console account as an **organization** (personal accounts created after Nov 2023 must run a closed test with a minimum number of testers for a minimum number of days before production; **verify** current numbers)
- [ ] App signing by Google Play; upload key stored in the password manager
- [ ] Privacy policy and account-deletion URL on the Vercel site
- [ ] Data safety form: data collected (app activity, health-adjacent), encrypted in transit, deletable
- [ ] Health apps declaration (**verify** whether tracking alcohol and tobacco counts as health features)
- [ ] Content rating questionnaire. Alcohol and tobacco references may raise the rating; listing copy leads with day tracking
- [ ] Target API level meets the current Play requirement (**verify**)

## Stage 3. Test and launch

- [ ] Internal test: Mark + 2
- [ ] Closed test: 10 to 20 testers, at least 2 weeks
- [ ] Store listing from [04](04-store-listing-draft.md)
- [ ] Production rollout at 20%, then 100%

## Stage 4. iOS follows

Same Capacitor project, WidgetKit widget, Siri quick-log, TestFlight. The widget is the native feature that answers Guideline 4.2.
