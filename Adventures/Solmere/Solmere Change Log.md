# Solmere (Solmere) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Solmere.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Solmere.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

Entries from 16/08/2026 to 22/08/2026 predate this split and are in the
project-root `Change Log Archive.md`.

## 26/08/2026

- Solmere.json — **`titleImageUrl` and `narrationBackdropUrl` removed
  (again).** The engine log of 25/08 records them removed, but the file
  on disk this morning still carried both, so today's rewrite (modest
  costume sets) carried them forward and the push brought the old
  storyboard background and title art back over the heraldry skin.
  Both keys deleted; nothing else touched. Re-push required.

- Solmere.json — **`uniformsModest` and `poolUniformsModest` added** (6 + 6
  entries, one per existing category). The engine's Fan service toggle
  (Off by default) draws from these; On uses the original `uniforms` /
  `poolUniforms`, which are unchanged. Same garments worn normally —
  buttoned, knee-length, one-piece, no innuendo — style anchors kept.
  Engine change in Code/Bottom Panel.txt, same day.

## 24/08/2026

- Ysolde's `identity` opened `"a attractive"`, and `asSentence()` capitalises
  the first character of every fragment it is handed, so every image prompt
  she appeared in began the sentence "A attractive and sexy sophisticated 21
  year old female". Corrected to `"an attractive"`. The article is the only
  thing changed — no other NPC record differs.
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
- All six `uniforms` entries shortened from a 73-word average (max 88) to
  43 (max 46). **Length is the only thing this pass changes.** The
  garments, colours, crests, what each one bares, the tone adjectives and
  the closing "dripping with sex appeal..." clause are all preserved word
  for word; `imageStyle`, `poolUniforms`, `clothingStates` and every NPC
  `identity` are untouched. Only the two or three redundant restatements
  of "revealing" per entry were cut. No engine change.
  - It is deliberately a controlled change. Meridian's outfits were
    rewritten the same day and came back visibly better across the whole
    image, not just the clothing — but three things changed there at once
    (length, a new `imageStyle` anchor, and the closer being dropped), so
    the cause was not isolated. Solmere-before and Solmere-after differ in
    nothing but uniform length, so comparing renders actually tests it.
    Verified by asserting every non-`uniforms` field is byte-identical to
    the previous file before writing.
  - **A two-character composite was running past the point where the
    backend truncates.** `IMAGE_PROMPT_WARN_CHARS` is 1700; Ysolde and
    Kael in the Courtyard built a 1975-char prompt, so the tail — the
    second character's outfit, pose and expression — was being dropped.
    The same prompt is now 1556. This is the mechanical reason multi-
    character images were worse than solo ones, and it is fixed for two.
  - **Three or more characters is still over and cannot be fixed by
    trimming.** The same trio now builds 2559 chars, and capping every
    `identity` at 40 words as well only reaches 2095. The composite
    builder repeats the character's name as the subject of four separate
    clauses by design (it is the documented mitigation for attribute
    bleed), so the floor is structural. Getting 3+ under the threshold
    needs a change to the composite builder in `Code/Bottom Panel.txt`,
    not more editing here — engine work, so it belongs in the engine log
    if it happens.
  - Word budget recorded in `Solmere.txt` STANDARD UNIFORMS. If it holds
    up across Adventures it is a cross-project rule and moves to the root
    `Change Log.md`; it is written here for now because only Meridian and
    Solmere have been trimmed.
  - `Solmere.json` needs re-uploading to the GitHub assets repo before
    any of this is live.
- **Dining Hall** added as Solmere's twelfth location — the Academy's
  second social hub, sitting alongside the Courtyard. Added to
  `Solmere.json` `locations`, to both lore files, to `Solmere.txt`, and
  drawn on the map.
  - It is the one location exempt from the two-NPCs-per-phase authoring
    convention. A refectory that isn't crowded isn't a refectory, and
    Midday was the emptiest phase on the roster — eight of the twelve NPCs
    were either roaming or unscheduled there, so a player crossing the
    Academy at lunch could reliably meet nobody.
  - Placements: Finn at Morning; Kael, Elowen and Toren at Midday;
    Thaddeus and Junia at Evening. Deliberately empty in the Afternoon and
    at Night, so the room after hours is somewhere to meet unobserved
    rather than another crowd.
  - Junia's Evening moved out of the Commoner Dormitory Wing to get her
    there, leaving Rook alone in the wing that phase. Finn's Morning and
    Kael's, Elowen's, Toren's and Thaddeus's previously-unplaced phases
    cost nothing to fill.
  - Added to every NPC's `roamLocations` except Instructor Voss's. His is
    a duty roster, not a social one, and that is what keeps him reading as
    staff rather than as another student.

- **The Restricted Wing is no longer drawn on the map.** Hidden locations
  stay off it. The Wing's existence is the discovery the `wing_found`
  milestone turns on, and the journal already flags that milestone hidden
  for exactly that reason — a map the player can open on turn one was
  quietly undoing it, in dashed red, labelled. It remains a real location
  in `locations`, in the lore and in Ysolde's Night routine; it simply has
  no element on the map, so the "you are here" marker doesn't appear while
  the player is in it. `positionPlayerMapMarker()` already tolerates that.

- Map redrawn accordingly: the Dining Hall takes the lower-left slot the
  Restricted Wing occupied, with its own spoke off the Courtyard hub.
  Rendered under both the dark and parchment palettes before delivery.

- **The map is now illustrated art**, replacing the hand-drawn schematic the
  same day. `Maps/Solmere Map.svg` is a wrapper: a single `<image>` pointing
  at the hosted `Maps/Solmere Map.webp`, plus eleven invisible circular
  anchors carrying the `loc-<slug>` ids. The room names are drawn into the
  art, so the SVG holds no text of its own.
  - Generated from a layout spec written to match the schematic room for
    room, kept at `Maps/Solmere Map Art Prompt.md` so a re-run or a later
    Adventure can reuse it.
  - Export: 1536x1024 WebP at quality 86, 554KB, no downscale — the map
    renders at about 832px inside an 880px modal, so the native size is
    already just under the 2x target. Crop-compared against the PNG master
    at 1:1; a 1280-wide variant was visibly softer and was rejected. Master
    at `AssetsNotHosted/Masters/Solmere Map.png`.
  - **No engine change.** An anchor keeps `class="sg-map-building"` so
    `updateMapHighlight()` can clear it, and never draws: `fill-opacity="0"`
    and `stroke-opacity="0"` as presentation attributes, which the skins'
    `fill` rules and `.sg-map-current-loc`'s `stroke` rule cannot reach.
  - **The player-portrait marker is the sole "you are here" indicator.** The
    room-outline highlight is a schematic-map device — over illustrated art
    it draws a second ring around the portrait's own and reads as clutter.
    Dropping it costs the one thing it covered: open the map before the
    baseline portrait has finished generating and nothing marks the current
    room. Accepted, since that window is short and the portrait is the
    indicator the feature was designed around.
  - Anchor radius 88 sets the marker size: `positionPlayerMapMarker()` takes
    0.22 of the shorter bounding-box side, giving a portrait about 75 units
    across — roughly 41px at the width the map renders at. Verified in a
    headless render with the parchment palette and a stand-in portrait.

- One stale clause in the engine's parchment-skin CSS comment, which cited
  Solmere's "dashed red Restricted Wing" as its worked example of a room
  kept off-palette, now describes the palette rather than the room —
  written up in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

## 23/08/2026

- Setup fields gained `nameSets` (male and female first-name pools) and
  lost the now-dead `default`/`required` flags, as part of the
  skip-the-setup-screen change —
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

- The tournament now has a structure. It is a standing **ranking ladder**,
  not a knockout bracket: every student holds a rank, duels are frequent
  and can be sought out or forced on the player, and a loss costs rank
  rather than ending a season. This closes the "exact tournament
  structure/rules — not designed yet" item that had been open in
  `Solmere.txt` since 17/08/2026, and `Solmere.txt` now carries the full
  readable version under THE LADDER.
  - Chosen over a bracket on two grounds. The premise already describes
    duels earning "standing, resources and reputation," which describes a
    ladder and not a bracket. And a bracket yields only about four duels
    across a whole playthrough, with an early loser stranded for most of
    the story with nothing left to pursue — where on a ladder there is
    always a next duel. A ladder-into-bracket hybrid was considered and
    rejected: two systems to author and explain for a marginal gain.
  - Bands, each crossed once: `ranked` → `contender` → `challenge`
    (earned/denied) → `title` (won/lost), plus `washed_out` as the other
    way out of contention. Duels between bands are unlimited and emergent;
    only the crossings are tracked.
  - Side thread off the ladder: `wing_found` → `faction_faced`
    (exposed/buried). This finally gives the previously unnamed shadowy
    faction a job — it is arranging the rankings from outside the Academy.
    Exposing that ends the story; burying it doesn't, and leaves the player
    inside a system they now know is rigged. `Solmere.txt`'s NPC list no
    longer describes the faction as only a loose hook.
  - Acts: I until `ranked`, II until `challenge` or `washed_out`, III
    after — so the final act is reachable by winning through *or* by
    washing out, and a player who never gets a challenge still gets an
    ending.
- Six endings authored in `Story Definitions/Solmere.json`: Killed at
  Solmere and Expelled from Solmere (both reachable from the first turn,
  neither continuable), What the Ladder Was For, Champion of Solmere,
  Broken on the Arena Floor, and One of the Many. One primary ending per
  playthrough. Romance has no ending of its own by design — the ending
  beat closes out whoever the player ended on strong or bad terms with,
  whichever ending it was.
- `Solmere.json` gained the `arc` block holding all of the above, placed
  after `relationshipLabels` so the narrative-state blocks sit together.
  The engine mechanic behind it is written up in full in the engine log,
  23/08/2026.
- Journal content for the arc, for the Codex tab added the same day (engine
  mechanic written up in full in the engine log, 23/08/2026):
  - A player-facing `journal` line on every milestone, second person and
    forward-looking, kept separate from the AI-facing `description` — the
    descriptions here are written as instructions to the narration AI
    ("Resolve it 'earned' if...") and would read as nonsense, and as a
    spoiler, if shown to a player.
  - Every `label` reworded from a past-tense verb to a noun phrase — "A
    place on the ladder" rather than "Placed on the ladder" — because the
    journal shows the same label under "Done", "In front of you" and
    "Later", and only the first of those reads correctly in past tense.
  - `wing_found` and `washed_out` flagged `hidden`, so neither is listed
    until it has actually happened. The Restricted Wing's existence is
    itself the discovery, and listing "out of contention" as something in
    front of the player would read as an instruction rather than a risk.
    `faction_faced` needs no flag — concealment is inherited from
    `wing_found`.
  - The four ladder bands stay visible from turn one on purpose: the
    ladder is public knowledge in-world, and a first-year should know a
    title exists. `Solmere.txt` records the visibility policy.
- **Needs re-uploading to R2.** Without the re-upload the arc simply is
  not in the hosted file, and the Adventure plays as though it was never
  added. The journal content above is in the same file, so it rides on the
  same upload. (The `jsonUrl` carried a `?v=3` cache-buster when this was
  written. It was removed later the same day, along with the unconfirmed
  caching theory behind it — see the engine log, 23/08/2026.)
- Still open: how many students are on the ladder, and whether reaching a
  band gives anything material — the premise promises "resources," which
  means nothing mechanically yet. Authored flavour for now. House/Cohort
  sorting is now optional rather than a prerequisite; the ladder works
  without it.

## 22/08/2026
- NPC routines authored: every one of the twelve carries a `schedule`
  (phase-keyed), most a `usualLocation` fallback, and all a
  `roamLocations` list. Engine mechanic written up in full in the engine
  log, 22/08/2026. Needs re-uploading to R2.
  - Occupancy is held to two NPCs per location per phase, as an authoring
    convention rather than anything the engine enforces — it keeps the
    Scene Image side to a workable number of subjects per room. Roaming
    NPCs can still push a beat past it, and the plan prompt's existing
    "at most 3-4 NPCs acting per beat" cap is what actually guards that.
  - 18 of the 60 cells are deliberately left unplaced, weighted toward
    Morning through Afternoon; Evening and Night are routine-heavy, which
    is how those hours actually read. Every NPC has at least one free
    phase.
  - Sable is the deliberate outlier — one fixed cell (Midday, Library) and
    no `usualLocation` at all, so she is unplaceable by default. It suits
    a character written as hiding more than she shows, and it gives the
    engine someone it can put anywhere without reading as a violation.
  - The Enrollment Hall is empty in every phase. It's an arrivals hall;
    the opening scene puts people there on Day 1 and nobody has a reason
    to loiter afterwards, so walking in later should feel quiet.
  - The Restricted Wing has exactly one entry — Ysolde, Night. A player
    who wanders in after dark finds the aloof royal somewhere she has no
    business being, which is the strongest hook the table carries.
  - The Showers are scheduled once (Seraphine, Midday, after duels) and
    sit in eleven of the twelve `roamLocations` lists instead. Anyone
    might be in there and nobody reliably is: a scheduled slot in a
    high-interest room would be a repeatable, farmable beat, which is the
    one place the schedule's determinism works against the Adventure
    rather than for it.
- Time phases authored: `timePhases` `Morning / Midday / Afternoon / Evening
  / Night`, `startingPhase` `Morning` — the first day begins on arrival at
  the Enrollment Hall. Engine mechanic in the engine log, 22/08/2026.
- Gained title-card art on the Adventure Selection screen. `Assets/TitleCards/SolmereCard.webp`
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
- The Appearance/uniform section names Story Definitions/Solmere.json as
  the authoritative wording, replacing the note that this outline was
  being edited in parallel and might not match what's live.
- Removed the parenthetical recording that Healer Maren was once an
  unnamed placeholder excluded from Stage A detection; she has a name and
  the operative entry now just says so.
