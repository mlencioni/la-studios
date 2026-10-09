---
name: habitrak-log
description: Log smokes, drinks, water, resists, give-aways, sleep and any other Habitrak tracker into Mark's Habitrak 3.0 app by voice or text, from any chat or project. Use whenever Mark says anything like "log a smoke", "log a drink", "I just made a drink", "resisted one", "gave one away", "forgot to log one at 3", "going to bed", "I'm up", "starting work", "done with my workout", or asks what he has logged today. Treat it as a self-contained side task.
---

# Habitrak 3.0 logging

Habitrak 3.0 lives at https://claude.ai/artifact/3oHbVb1zqH7pzWgEJS4czT. Mark's log is private to his account, in that artifact's database under `data/users/me`. Read and write it with the `ArtifactData` tool, always passing that `url`.

## Where things are

| What | `collection` | `doc_id` |
|---|---|---|
| Settings: trackers, goals, `dayStart` ("05:00"), `tz` (e.g. "America/Los_Angeles") | `data/users/me` | `profile` |
| One day's log | `data/users/me/profile/days` | the day key, `YYYY-MM-DD` |

A day document looks like `{"entries":[...], "checkin": {...} or null, "updated": <ms>}`.

**Day key:** the local date (in `tz`) of the most recent `dayStart`. With `dayStart` 05:00, 2:30 AM on Oct 8 belongs to `2026-10-07`.

## Entries

| Field | Meaning |
|---|---|
| `id` | Unique string. Use `v` + the current time in base 36 + 3 random letters |
| `tr` | Tracker: moments `coffee` `water` `meal` `snack` `smoke` `drink` `meds`; stretches `work` `walk` `commute` `rest` `screen` `sleep` `stretch` `workout` |
| `t` | Start time, epoch milliseconds |
| `end` | Stretches only: end time in ms, or `null` while running |
| `as` | Optional: `"resisted"` (skipped one) or `"given"` (gave a smoke away). These don't count as smoked or drunk |
| `note` | Optional, Mark's own words |
| `med` | Meds only: the medication's `id` from `profile.meds` (each has `id`, `name`, `dose`, `times`). "Took my Metformin" logs `{tr:"meds", med:<its id>}`; a skipped dose adds `as:"skipped"` |

## Steps

1. `get` the `profile` document for `dayStart` and `tz`. If it doesn't exist, tell Mark to open Habitrak 3.0 once to finish setup, and stop.
2. Work out the time of the event (now, unless Mark gave a time) and its day key.
3. `get` that day's document. It may not exist yet.
4. Change the entries:
   - **Moment** ("log a smoke"): append `{id, tr, t}`.
   - **Resisted / gave one away:** append `{id, tr, t, as}`.
   - **Medication** ("took my Metformin"): match the name in `profile.meds` and append `{id, tr:"meds", med, t}`. If no name matches, log plain `{id, tr:"meds", t}` and say so.
   - **Start a stretch** ("going to bed", "starting work"): first stop any running stretch (an entry with `end: null` in today's or yesterday's document) by setting its `end` to now. Then append `{id, tr, t, end: null}`.
   - **Stop a stretch** ("I'm up", "done with work"): set `end` on the running entry with that `tr`.
   - **"Finished my smoke/drink":** Habitrak 3.0 logs moments only, so there's nothing to change. Say so in a few words.
5. `set` the whole document back with `{"entries": [...], "checkin": <unchanged>, "updated": <now ms>}`. Pass `if_version` from your read when the document existed; omit it when creating. If the write is refused because the version changed, read again and redo the change. Never overwrite Mark's newer entries.
6. Reply in one short line: what was logged, the time, and today's count for that tracker. For example: "Smoke logged at 3:42 PM. 12 today, of your 30."

## Rules

- Never delete or edit entries Mark didn't ask about.
- No lectures. If he's past a goal, state the count once, plainly.
- If a request is unclear ("log one"), ask which tracker in one short question.
- If he mentions shakiness or sweating after drinking, add: "Those can be signs of withdrawal. Mention them to your doctor, and don't cut back sharply on your own."
