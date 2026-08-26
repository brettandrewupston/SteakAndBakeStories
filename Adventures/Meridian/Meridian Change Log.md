# Meridian (ISV Meridian) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Meridian.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Meridian.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

Entries from 16/08/2026 to 22/08/2026 predate this split and are in the
project-root `Change Log Archive.md`.

## 26/08/2026

- Meridian.json + Lore + Meridian.txt — **the Ensign is no longer written or
  drawn young.** Live: the narration read "Ensign" as a young cast member,
  which is the rank's connotation in the sci-fi the text model was trained
  on. The authored data was pushing the same way harder than the rank was.
  Both Ensigns carried "slim, girlish" / "slim, boyish", "her/his frame is
  still filling out" and "a little coltish" / "gangly" in `identity` —
  which is image-prompt text — and "the youngest crew member aboard, barely
  out of training" in `bio` and in their Lore files.
  Mira Solano is now 26 and Toby Reyes 27; ensign is a commissioning rank,
  not an age. The still-developing wording is replaced with a "lean,
  athletic" / "lean, rangy" build, and their eagerness is now justified by
  being the newest aboard on a first posting rather than the youngest.
  Two more image-prompt signals went with it: Priya Anand's and Rhys
  Okafor's "restless, girlish energy" / "boyish energy" (they are 28 and 29)
  reads "irrepressible energy", and all four ensign uniform strings say
  "rank bar" where they said "trainee bar".
  Role, crush, comic-relief function and speaking voice are unchanged.
  `personality`'s "girlish/boyish wonder" on the two doctors is deliberately
  left as-is: it reaches the text model only and never the image prompt.
  Live on the next push; the local and hosted copies are otherwise in sync.

- Meridian.json — **`uniformsModest` and `poolUniformsModest` added** (15 + 15
  entries, one per existing category). The engine's Fan service toggle
  (Off by default) draws from these; On uses the original `uniforms` /
  `poolUniforms`, which are unchanged. Same garments worn normally —
  buttoned, knee-length, one-piece, no innuendo — style anchors kept.
  Engine change in Code/Bottom Panel.txt, same day.

## 24/08/2026

- `locationScenery` authored for all 12 locations, ~20 words each — the room,
  two or three fixed physical features and its light. These now carry the
  image prompt's setting line, which until today was the bare location name.
  The engine mechanism is generic and is written up in full in the engine log
  at `Generator/Steak and Bake Stories/Change Log.md`.
- `imageStyle` gained `professional photo`, placed with the other style
  tokens and ahead of the framing instruction:
  `painted anime style, cyberpunk aesthetic, professional photo, front on shot`
  A photographic quality token paired with a painted style token lifts
  detail, lighting and coherence without the render losing the style.
- Story arc authored into `Story Definitions/Meridian.json`: ten
  milestones, three phases, six endings, using the engine arc mechanism
  built 23/08/2026. No engine change. Meridian is the third Adventure
  with an arc, after Solmere and Pemberton. Summary in `Meridian.txt`
  STORY ARC; the operative descriptions, journal lines and phase guidance
  live in the JSON and are not duplicated.
- `settled` ("A life aboard") added to the design as a tenth milestone
  and a fourth `until` on act2. Act2 closes on commitment, so a player who
  opens none of the three roads would never leave it and `drift` — the
  final-phase fallback ending written for exactly that player — would be
  permanently unreachable. Hidden, so accepting your situation is never
  listed as an objective.
- `rota` requires `told` rather than `pod_alive`, so the two locks on the
  escape can be found in either order; `escape` still requires both. A
  player can plausibly notice the watch pattern before they care about
  the pod, and gating it the other way would have made a puzzle into a
  sequence. `rota` therefore carries its own `hidden` flag rather than
  inheriting concealment.
- Hidden flags sit on `pod_alive`, `rota`, `case_made` and `settled`
  only. Concealment is inherited, so `escape` surfaces in the Journal
  exactly when both its locks are found and `initiative_answered` when
  the case has been made — the escape route stays a discovery instead of
  a listed objective, without either milestone needing a flag.
- `escape`'s description points the model at the current phase's NPC
  presence roster as the ground truth for who is standing in the EVA Bay,
  and states that an attempt made while the watch is posted resolves
  `caught`. This is what couples the arc to the routines authored earlier
  today rather than leaving the window to invention.
- Verified with a simulated-playthrough harness (117 assertions, all
  passing) rather than by reading: the real arc functions are extracted
  by name from `Code/Bottom Panel.txt`, `currentStory`/`storyHistory` are
  stubbed, and `[[EVENT:]]`/`[[ENDING:]]` tags are replayed through a
  mirror of the narrator call site at Bottom Panel.txt ~8898-8944. Same
  approach as Pemberton's, and the same reason: the 23/08/2026 ending
  re-fire defect was invisible to a read-through. Covered: prerequisite
  rejection, one-milestone-per-beat, outcome discipline, both escape
  outcomes, the continued-past-ending re-fire case, the passive-player
  route, every ending reachable by its own route and only its own,
  dead-end outcomes not ending the story, and undo rolling the phase
  back.
- The arc's load-bearing premise addition: the player will not be
  released. The Meridian is three generations from anywhere and letting
  the only outsider aboard leave means the outside world learns where the
  Initiative went. Settled policy, not cruelty. Without it the Adventure
  has fascination but no pressure, and neither main ending costs
  anything.
- Two endings requested by Brett — `escaped` (`when escape:launched`) and
  `known` (`when study_closed:complete`). `escaped` is not continuable:
  the whole cast is behind the player, so continuing would cost leaving
  its weight. `known` deliberately has no warm/cold variants — the ending
  beat already holds every relationship score, same convention as romance
  getting no ending id of its own.
- Four further endings: `contained` (`when escape:caught`), which is what
  makes the escape attempt risky and therefore makes solving the rota
  worth anything; `course_change` (`when initiative_answered:turned`),
  the inverse of escaping — the player stays and the ship does not stay
  as it was; `death` (anyTime, not continuable, house convention); and
  `drift`, the final-phase fallback in Solmere's `also_ran` slot.
- Escape gated on two locks rather than one, on the grounds that a
  single-lock puzzle is thin: the pod still draws power despite being
  logged derelict and needs the Chief Engineer or Miravel to revive
  (social), and the EVA Bay watch has one unmanned phase (observational).
  The pod's origin stays unanswered — `Lore/Meridian/derelict-hook.txt`
  unchanged.
- New location **EVA Bay**, the airlock and the only way off the ship, a
  posted watch station off the Cargo Bay. Chosen over putting the rota on
  the Cargo Bay itself: a large room people legitimately pass through
  makes "someone is always here" read as coincidence, where a one-person
  watch station reads as deliberate. Not yet on `Maps/Meridian Map.svg`
  or in `Meridian.json` locations.
- The watch window is **Early Shift** — handover, both watches on the
  Bridge for the log read. Chosen against Night Cycle, which is the first
  phase every player tries and is therefore authored as the most covered.
  The rota rotates its occupant (Chief Engineer / Ensign / Chief Science
  Officer / Security Chief) rather than merely being occupied: one empty
  room is noise, four faces with a hole in the pattern is
  reconstructable.
- Three fair discovery routes authored so the window is findable without
  narration ever stating it: the Ensign complaining about the watch bill,
  the Chief Engineer grumbling about handover, and Miravel at high
  relationship. The `rota` milestone fires only on the player naming or
  acting on the specific window, never on wondering aloud.
- Crew routines authored into `Meridian.json` — `schedule` on all 14 NPC
  records across both rosters and all five phases, `usualLocation` on the
  four post-holding roles, `roamLocations` on the three that deliberately
  declare none. This turns on the engine's NPC presence feature for this
  Adventure, which was previously off because no NPC declared either
  field. The table is in `Meridian.txt` CREW ROUTINES.
  - Both rosters carry identical routines by role: the two rosters are
    the same ship with the same posts, so applying by role (via NPC
    token) rather than per-set also removes any chance of repeating the
    22/08/2026 npcSets key-convention bug.
  - The whole roster is authored, not just the watch. A schedule covering
    only the EVA Bay would leave the rest of the ship reading as empty
    and the gap would stop being a gap.
  - The Cargo Bay is on no routine at all, only in the Security Chief's
    `roamLocations`. The room holding the pod is usually quiet enough to
    work in and never reliably so.
  - Verified against a mirror of `npcScheduledLocation()`: every resolved
    cell and every roam entry is a real `locations` name, and Early Shift
    is the only phase with nobody at the EVA Bay.
- `EVA Bay` added to `locations` in `Meridian.json` (after `Cargo Bay`),
  to `Maps/Meridian Map.svg`, and to `Lore/Meridian/locations.txt`. On
  the map it is a dead-end annex off the Cargo Bay sharing its red/dashed
  treatment, joined by a short red connector, with no spoke to the hub.
  All 12 `locations` were checked programmatically against the SVG's rect
  ids via `locationSlug()` — exact match both ways, none missing, none
  spare.
- All 15 `uniforms` and all 15 `poolUniforms` entries rewritten. Every
  Meridian outfit is now lingerie rather than a duty uniform: ultra-thin
  translucent harnesses, bralettes and briefs in sheer iridescent
  material with glowing neon fluorescent trim and neon outlines. Summary
  in `Meridian.txt` STANDARD UNIFORMS; the operative prompt text lives in
  the JSON and is not duplicated. No engine change —
  `uniforms`/`poolUniforms` are opaque category-keyed strings to the
  engine.
  - The material vocabulary is fixed and appears in all 30 entries:
    ultra-thin, translucent, sheer, iridescent, glowing neon fluorescent
    trim, neon outlines. Brett arrived at it by testing against the image
    plugin directly rather than by reasoning about it, and it renders
    suggestive rather than explicit — no anatomy resolves.
  - **A garment described as fully see-through does NOT render as a bare
    figure.** That assumption drove an earlier draft of this pass toward
    an opaque-core/panelled-sheer construction, and testing disproved it.
    The material words carry a visible surface on their own; describing
    the fabric is what makes it read as fabric.
  - The trim colour is the role marker, one per role and never shared:
    command gold, security crimson, medical mint-green, science magenta,
    engineering orange, ensign cyan. A crew member is identifiable by
    colour alone in a group image, where a name label doesn't exist and
    six charcoal uniforms previously read as interchangeable.
  - `officer-male`/`officer-female` split into `command-*` and
    `security-*`, and the Captain and Commander records in both rosters
    repointed. The Captain and the Security Chief shared one category, so
    without the split the ship's two most opposed figures would have worn
    the same colour. Six role-categories now, not five.
  - Each role keeps exactly one prop — rank bars, thigh holster,
    stethoscope, data-slate, tool belt, trainee bar. Lingerie strips out
    the silhouette differences that used to separate a lab coat from
    coveralls, so without a prop the trim colour would be doing all the
    identification on its own.
  - Entries held to roughly 40 words, poolUniforms to 26-40, down from an
    average of 97. The uniform clause is the longest single clause in an
    image prompt and `composeImagePrompt()`'s own comment records the
    setting being crowded out by Solmere's ~60-word text. Detail past
    that point buys nothing visible and costs the room, the pose and the
    expression their weight.
  - `cyberpunk aesthetic` added to `imageStyle` rather than to the outfit
    text. It anchors the whole image, not the clothing, so it belongs in
    the one field that leads every prompt — including scene and group
    images, where the ship itself should match.
  - The closing "dripping with sex appeal and unmistakably provocative"
    clause dropped from every entry. On a lingerie garment it restates
    what the garment already says, and it was eight words of a forty-word
    budget. It is not a cross-project convention — nothing in Goals.txt
    or Features.txt requires it.
  - The player's `guest-*` outfit keeps the same construction but its
    trim is explicitly flat matte-grey, dead and unlit, with no insignia.
    It is the only outfit aboard that doesn't glow, so every image states
    the outsider premise without a line of narration doing it.
  - Miravel's `liaison-female` carries no neon trim either. Her
    luminescent Sevari markings glow through sheer violet silk instead —
    she is lit like nobody else because she is the other exception, and
    borrowing the ship's palette would have flattened that.
  - `clothingStates` untouched. `resolveUniformFromCategoryAndClothing()`
    returns the clothing text *instead of* the uniform, never appended,
    so none of the above reaches a shirtless/topless/nude/towel render.
  - Verified programmatically before delivery: every `npc.category`
    across both rosters and the player's `guest-{playerGender}` template
    resolves in both tables, no orphan keys, the two key sets match,
    every category's gender suffix matches its NPC's gender, every entry
    carries the full material vocabulary, each role's text names exactly
    one trim colour and only its own, no entry repeats the imageStyle
    anchor, and every entry is inside its word budget.
- `Story Definitions/Meridian.json`, `Maps/Meridian Map.svg` and
  `Lore/Meridian/locations.txt` all need re-uploading to the GitHub
  assets repo before any of this is live. `Code/Bottom Panel.txt` needed
  no change for the arc, the schedules, the new location or the uniform
  rewrite.

## 23/08/2026

- Setup fields gained `nameSets` (male and female first-name pools) and
  lost the now-dead `default`/`required` flags, as part of the
  skip-the-setup-screen change —
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

## 22/08/2026
- Time phases authored: `timePhases` `Early Shift / Mid Shift / Late Shift /
  Off-Watch / Night Cycle`, `startingPhase` `Mid Shift` — a generation ship
  keeps watch rotations, not daylight. Engine mechanic in the engine log,
  22/08/2026.
- Gained title-card art on the Adventure Selection screen. `Assets/TitleCards/ISVCard.webp`
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
- Removed the stale half of the OPEN item claiming no mapUrl exists —
  Maps/Meridian Map.svg is built and mapUrl is set in Meridian.json. Only
  narrationBackdropUrl is still outstanding.
