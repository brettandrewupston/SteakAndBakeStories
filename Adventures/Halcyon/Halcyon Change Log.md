# Halcyon (Paradise Rebuilt) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Halcyon.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Halcyon.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

Entries from 16/08/2026 to 22/08/2026 predate this split and are in the
project-root `Change Log Archive.md`.

## 25/08/2026

- `Halcyon.json` — NPC schedules. Every NPC now carries `usualLocation` and a per-phase `schedule`, so the engine's WHO IS WHERE block runs on this Adventure (it emitted nothing before — no NPC had a routine, so the model placed people by feel). Location names verified against the JSON's `locations` list; presence block rendered headless from the starting location. Needs a push to go live. Calls: every contestant is at The Site for Build Block by format; Dorian is the one roaming (null) Evening slot, since his role is walking in on a flat scene; Renata is the only person scheduled into The Sunken Villa (After Dark — she holds the key); Cody's After Dark went to the villas, not The Site, so the overnight-fixing mystery isn't given away by a timetable.

## 24/08/2026

- All 6 `uniforms` entries shortened from a 73-word average (max 94) to 43
  (max 47). Length is the only thing this changes: the garments, colours,
  insignia, what each one bares and the tone words are preserved, and "dripping with sex appeal and unmistakably provocative"
  survives verbatim on every entry. Only the repeated restatements of
  "revealing" were cut. No engine change.
  - Same rule now applied to every Adventure. The uniform clause is the
    longest single clause in an image prompt and it is repeated once per
    character in a composite, so it is the cheapest thing to shorten and the
    most expensive thing to leave long. Ceiling is ~40 words plus whatever
    that Adventure's closing clause costs.
- `locationScenery` authored for all 12 locations, ~21 words each — the room,
  two or three fixed physical features and its light. These now carry the
  image prompt's setting line, which until today was the bare location name.
  The engine mechanism is generic and is written up in full in the engine log
  at `Generator/Steak and Bake Stories/Change Log.md`.
- `imageStyle` gained `professional photo`, placed with the other style
  tokens and ahead of the framing instruction:
  `painted anime style, professional photo, front on shot`
  A photographic quality token paired with a painted style token lifts
  detail, lighting and coherence without the render losing the style.
## 23/08/2026

- Setup fields gained `nameSets` (male and female first-name pools) and
  lost the now-dead `default`/`required` flags, as part of the
  skip-the-setup-screen change —
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

## 22/08/2026
- Time phases authored: `timePhases` `Morning Call / Build Block / Golden
  Hour / Evening / After Dark`, `startingPhase` `Morning Call` — a shooting
  day, not a calendar day. Engine mechanic in the engine log, 22/08/2026.
- Gained title-card art on the Adventure Selection screen. `Assets/TitleCards/ParadiseCard.webp`
  is the hosted copy registered as this Adventure's `coverUrl`; the
  full-size PNG beside it is the local master (see the project-root
  `Change Log.md` for the export convention). Engine feature, written
  up in full in `Generator/Steak and Bake Stories/Change Log.md`.
- The free-text **Appearance** box in `setupFields` is replaced by four
  grouped dropdowns — Hair style, Hair colour, Body type, Skin colour —
  each with a default and with per-option image-prompt phrasing. Engine
  feature (`select` field type, field grouping, composed player
  appearance), written up in full in
  `Generator/Steak and Bake Stories/Change Log.md`. Needs re-uploading to R2.
- Premise line corrected to eight contestants; the roster has seven
  contestant NPCs plus the player, and the premise said seven total.
- Mara Quinn renamed **Vela Quinn** (token `Mara` -> `Vela`). The name
  Mara belongs to the Hollowburn protagonist, and two Maras across two
  Adventures is a debugging trap; Vela pairs with her twin Nova and
  collides with nothing in this Adventure's text. Applied across
  Halcyon.json (name, token, bio and identity text, loreEntries label and
  URL), Adventures/Halcyon.txt (roster, twin-tell note, storyline list),
  and the lore files — Lore/Halcyon/npc-mara-quinn.txt is now
  npc-vela-quinn.txt, and npc-nova-quinn.txt's references to her sister
  were updated with it. The open item recording the pending rename is
  gone from the outline, and Hollowburn's cross-reference to it now states
  the rename as done. Still outstanding: the renamed lore file and the
  updated Halcyon.json need uploading to R2, where the old
  npc-mara-quinn.txt key is now orphaned.
- Gained the **tropic** UI skin (resort-and-building-site palette, hi-vis and hazard tape, Bebas Neue / Barlow). Engine feature, written up in full in `Generator/Steak and Bake Stories/Change Log.md`.
