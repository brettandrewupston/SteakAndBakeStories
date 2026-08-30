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

## 28/08/2026

- Halcyon.json — `poseVocabulary` removed: the engine never read it (written
  in full in the engine log, 28/08/2026). Needs a re-push.

## 27/08/2026

- Halcyon.json — **identity and uniform text trimmed for the two-character
  composite budget.** Two characters is the composite headcount the Scene
  Image supports, and its prompt was close enough to this backend's
  truncation point that a wordy pose pushed the second character's outfit,
  pose and expression off the end. The rule applied throughout: **identity
  describes the body and face, the uniform describes the clothes** — where an
  identity restated clothing, the uniform clause in the same prompt already
  carried it, so it went; where an attribute was stated several ways, one
  statement stayed. Uniforms lost doubled modifiers only, and **every closer
  survives verbatim** — both closers are proven anchors that keep rendered
  figures adult and are never trimmed. No garment, scar, hair, skin tone or
  age was dropped from any character.
  Ten identities and all six `uniforms` entries touched. The largest cuts
  were identities that described their own uniform: Dorian Vance ended with
  his `production-male` text almost word for word, and Teo Nunes, Renata
  Salas, Josefa Duarte, Ingrid Holm, Roxy Tam, Trev Grubb, Deshawn Price and
  Cody Callahan all restated garments the uniform clause states. Nova and
  Vela Quinn share an identity but for the hair, and share the trim.
  Measured with a one-off composite budget harness, not
  retained (engine log, 27/08/2026), as the pose length at which this
  Adventure's worst pair crosses the line: **89 to 163 chars**. Needs a re-push.

- Halcyon.json — **`altUniforms` and `altPoolUniforms` added: reveal-night
  glamour.** A second complete wardrobe over the same six categories,
  selected by the engine's Alternate outfits row (written in full in the
  engine log, 26/08/2026). Open white shirts and pale linen suits, slip
  dresses and satin jumpsuits, sandals and low heels, the faded palm crest
  moved to a lapel or a hip — the cast dressed for the cameras that pay for
  the island rather than for the build. `altPoolUniforms` is the same night
  at the pool, styled for broadcast. Closing clause verbatim and one
  adult-body fact per entry, same as the standard set. 39 words on average,
  41 at most, against a standard set at 43/47. `uniforms`, `poolUniforms`
  and `clothingStates` untouched. Needs a re-push.

## 26/08/2026

- Halcyon.json — **`uniformsModest` and `poolUniformsModest` removed** with
  the engine's Fan service toggle (see the engine log, 26/08/2026);
  `uniforms` / `poolUniforms` untouched. Needs a re-push.

- Halcyon.json — **NPC identities trimmed.** Each identity dropped its baked
  stance / posture / movement / expression tail (which collided with the
  engine's own pose and expression fields) and any meta, keeping age,
  build, face, hair, eyes and distinctive marks. No uniform text
  touched. Shortens every image prompt. Re-push required.

- Halcyon.json — **`uniformsModest` and `poolUniformsModest` added** (6 + 6
  entries, one per existing category). The engine's Fan service toggle
  (Off by default) draws from these; On uses the original `uniforms` /
  `poolUniforms`, which are unchanged. Same garments worn normally —
  buttoned, knee-length, one-piece, no innuendo — style anchors kept.
  Engine change in Code/Bottom Panel.txt, same day.

## 25/08/2026

- `Halcyon.json` — **story arc.** The Adventure can now end. Three acts on
  milestones: *Wading in* (until the Pool Bar verdict), *The season*
  (until the finale call sheet, or the hidden passive-player fallback
  `the_long_shift`), *The finale*. Ten milestones: `pool_bar_verdict`
  (won/demoted), `hands_spoken_for` (ingrid/cody/unaligned),
  `quinn_split` (broken/held), `staff_question` (backed/sold),
  `west_end_key` → hidden `what_happened_in_2014` → `villa_on_camera`
  (aired/kept), `the_long_shift` (hidden fallback), `finale_called`,
  `the_finale` (won/demoted). Six endings: three `when` (the Villa
  aired, finale won, finale demoted), *Background Artist* as the
  final-act fallback, and two restart-only `anyTime` exits (removed by
  production, walked off set). Renata remains the only route into the
  Sunken Villa. Driven through the real engine arc functions in a
  harness (70 assertions, 0 failures: reachability, prerequisite
  rejection, each `when` by its own route, no re-fire after continuing,
  both routes into act 3, fallback offered only there). Needs a push.

- `Halcyon.json` — NPC schedules. Every NPC now carries `usualLocation` and
  a per-phase `schedule`, so the engine's WHO IS WHERE block runs on this
  Adventure (it emitted nothing before — no NPC had a routine, so the model
  placed people by feel). Location names verified against the JSON's
  `locations` list; presence block rendered headless from the starting
  location. Needs a push to go live. Calls: every contestant is at The Site
  for Build Block by format; Dorian is the one roaming (null) Evening slot,
  since his role is walking in on a flat scene; Renata is the only person
  scheduled into The Sunken Villa (After Dark — she holds the key); Cody's
  After Dark went to the villas, not The Site, so the overnight-fixing
  mystery isn't given away by a timetable.

## 24/08/2026

- All 6 `uniforms` entries shortened from a 73-word average (max 94) to 43
  (max 47). Length is the only thing this changes: the garments, colours,
  insignia, what each one bares and the tone words are preserved, and
  "dripping with sex appeal and unmistakably provocative" survives verbatim
  on every entry. Only the repeated restatements of "revealing" were cut. No
  engine change. - Same rule now applied to every Adventure. The uniform
  clause is the longest single clause in an image prompt and it is repeated
  once per character in a composite, so it is the cheapest thing to shorten
  and the most expensive thing to leave long. Ceiling is ~40 words plus
  whatever that Adventure's closing clause costs.

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

- Gained title-card art on the Adventure Selection screen.
  `Adventures/Halcyon/Card.webp` is the hosted copy registered as
  this Adventure's `coverUrl`; the full-size PNG beside it is the local
  master (see the project-root `Change Log.md` for the export convention).
  Engine feature, written up in full in `Generator/Steak and Bake
  Stories/Change Log.md`.

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
  URL), Adventures/Halcyon/Halcyon.txt (roster, twin-tell note, storyline list),
  and the lore files — Adventures/Halcyon/Lore/_superseded/npc-mara-quinn.txt is now
  npc-vela-quinn.txt, and npc-nova-quinn.txt's references to her sister
  were updated with it. The open item recording the pending rename is
  gone from the outline, and Hollowburn's cross-reference to it now states
  the rename as done. Still outstanding: the renamed lore file and the
  updated Halcyon.json need uploading to R2, where the old
  npc-mara-quinn.txt key is now orphaned.

- Gained the **tropic** UI skin (resort-and-building-site palette, hi-vis
  and hazard tape, Bebas Neue / Barlow). Engine feature, written up in full
  in `Generator/Steak and Bake Stories/Change Log.md`.
