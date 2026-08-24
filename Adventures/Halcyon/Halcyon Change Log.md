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
