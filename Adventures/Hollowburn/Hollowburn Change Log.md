# Hollowburn (The Quiet Hour) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Hollowburn.json`), contentApproach,
outfit and location data, hosted file paths, and the canon doc in
`Hollowburn.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

Entries from 16/08/2026 to 22/08/2026 predate this split and are in the
project-root `Change Log Archive.md`.

## 25/08/2026

- `Hollowburn.json` — NPC schedules. Every NPC now carries `usualLocation` and a per-phase `schedule`, so the engine's WHO IS WHERE block runs on this Adventure (it emitted nothing before — no NPC had a routine, so the model placed people by feel). Location names verified against the JSON's `locations` list; presence block rendered headless from the starting location. Needs a push to go live. Same routine on both rosters (Jonah/Mara). Calls: Peter is null at Small Hours and Night — he works nights but not every night, and where he is at three a.m. is the mystery; Kirsty, Yasmin and Denny take nulls where they'd otherwise be wrongly placed at the cul-de-sac or the pub overnight (no home locations exist for them). **The Marra has no schedule and `omitFromPresence: true`** — engine flag added the same day (engine log), because an NPC with no routine is otherwise listed every turn as "may be anywhere, including right where the player is", which is the opposite of "appears rarely, never casually".

## 24/08/2026

- `locationScenery` authored for all 13 locations, ~20 words each — the room,
  two or three fixed physical features and its light. These now carry the
  image prompt's setting line, which until today was the bare location name.
  The engine mechanism is generic and is written up in full in the engine log
  at `Generator/Steak and Bake Stories/Change Log.md`.
- `imageStyle` gained `professional photo`, placed with the other style
  tokens and ahead of the framing instruction:
  `painted illustration, muted desaturated palette, overcast north-east English light, professional photo, front on shot`
  A photographic quality token paired with a painted style token lifts
  detail, lighting and coherence without the render losing the style.
- THE PLAYER CHOOSES WHICH BLYTHE CHILD THEY ARE. Female puts them in Mara at
  21 with Jonah as the 19-year-old brother; male puts them in Jonah at 21 with
  Mara as the 19-year-old sister. The haunted role never moves — only the name
  and sex of whoever holds it, and the sibling beside them.
  WHY, since the manuscript is female-only: Evelyn was fifteen in 1989 when her
  brother Duncan stopped sleeping and the honest answer is she gave him to it.
  Playing Mara makes the player Evelyn's echo, the sister who may do the same.
  Playing Jonah makes them Duncan's echo, the one it came for, with Evelyn
  watching a boy stop sleeping in her house for the second time in her life.
  The rhyme rotates rather than breaking, and the male reading is arguably the
  crueller one. `being-believed.txt` already reverses the roles mid-story, so
  the mechanic needs nothing.
- ALL DATA, NO ENGINE WORK. `npcs` became `npcSets` and `openingScene` became
  `openingScenes`, both existing gender-keyed fields that Meridian and
  Vermillion already use. `nameSets` carries exactly one name per gender, so
  the Character name field fills itself as Mara or Jonah and the player never
  types. Hollowburn is the first Adventure to change WHO is in the cast rather
  than only how they regard the player — the other two keep the same roster
  across both sets.
- The Mara NPC is not a gender-swapped Jonah. Jonah's sleep signal is snoring;
  hers is a podcast she falls asleep to and never turns off. That makes her
  accidentally warded — sound that keeps time is the one thing the Marra cannot
  hold a room against, the same mechanism as Ivy Ogle's radio, which nobody in
  the house has worked out. It also makes the silence when it stops worse.
- `npc-jonah-blythe.txt` rewritten as "The Blythe Children", covering both
  siblings and stating which one the player is under each gender. `loreEntries`
  is a flat list with no gender keying — unlike npcSets and openingScenes — so
  one file covering both is the only option. The filename was deliberately NOT
  changed: an overwrite is one commit, while a rename on GitHub's web uploader
  is a delete and an add with a window between them where the live app 404s.
- Two lore lines that gendered the player neutralised: `the-marra.txt` rule 3
  and the VOICE paragraph in `npc-the-marra.txt` both said "your brother's
  voice", now "the one you grew up beside". Evelyn's own "her brother Duncan"
  is untouched — that is her history, not the player's.
- Appearance defaults changed from shoulder-length straight black to short
  straight dark brown, which read as female-specific once a male player was
  possible. Matches Jonah's canon look, stays plausible for Mara, and no lore
  describes the player's appearance so nothing constrains it.
- The setup screen is back; `skipSetup` removed. See the engine log for why it
  had to come off the ADVENTURES registry entry as well as the hosted JSON.
- VERIFIED in the real engine headless, both genders: correct name, correct
  sibling in `currentStory.npcs`, correct opening scene, `playerCategory`
  resolving to family-female / family-male, Hush skin still applied, no page
  errors.

## 23/08/2026

- No character-creation screen. The JSON declares `skipSetup: true`, so the
  card opens straight into the story. There was nothing on that screen to
  decide: the manuscript already names the protagonist, fixes her as the
  Blythe daughter, and sets her appearance. Age's default moves 18 -> 21 to
  match the canon in this file.
  How Long Since You Slept and What You Believe now roll at random on every
  new story rather than being asked — they stay real story levers and each
  playthrough opens somewhere different.
  The engine change is written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.
  Needs re-uploading to R2 before it takes effect live.

- Character name no longer rolls a random name. The field declares
  `default: "Mara"` with "Mara" as its placeholder, so leaving it blank gives
  the manuscript's own protagonist and typing over it still wins. `nameSets`
  is removed with it — nothing reads it now, and this Adventure's gender
  field offers one option, so no pool it held could ever have applied.
  The engine change that makes a text `default` an auto-fill source is
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.
  Needs re-uploading to R2 before it takes effect live.

- The Quiet Hour has its own UI skin now (**hush**, a lighting skin built
  on this Adventure's title-card palette). It is an engine change and is
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

- Setup fields gained `nameSets` (male and female first-name pools) and
  lost the now-dead `default`/`required` flags, as part of the
  skip-the-setup-screen change —
  written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md`.

## 22/08/2026
- Title-card art registered: `coverUrl` now points at
  `Assets/TitleCards/QuietCard.webp`, so this Adventure shows a poster on
  the selection screen instead of the emoji-plus-text fallback. Exported
  from the 1024x1536 PNG to 700x1050 WebP at 141 KB, matching the other
  cards; the PNG moved to `Assets/Masters/QuietCard.png` per the export
  convention. The registry comment recording that no art existed yet is
  removed rather than left standing.
- The long-blurb card-stretch bug this Adventure surfaced is an engine
  fix — written up in `Generator/Steak and Bake Stories/Change Log.md`.
- Registered in `ADVENTURES` and live. The story definition, map and Lore
  had all been authored and uploaded; only the registry entry was missing,
  so nothing in the app could reach any of it. Registered as **The Quiet
  Hour** (the in-world name, following Halcyon being registered as
  "Paradise Rebuilt" rather than by its folder name), cover `🕰️`, pointing
  at the R2 copy of `Hollowburn.json`.
  No `coverUrl`: no title-card art exists for this Adventure yet, so it
  renders as the emoji-plus-text card beside three posters. That is the
  documented fallback working rather than a defect, and the carousel
  stretches it to the posters' height so it doesn't read as broken — but
  it is the odd one out until art is exported and uploaded.
- Time phases authored: `timePhases` `Small Hours / Dawn / Morning /
  Afternoon / Dusk / Night`, `startingPhase` `Small Hours` — six rather
  than five, and the day is ordered to begin in the hours the player
  character can't sleep through rather than to end in them, so Day 1
  covers a whole village day instead of a single phase. Engine mechanic
  in the engine log, 22/08/2026.
- Built. `Story Definitions/Hollowburn.json` (12 NPCs, 13 locations, 5
  uniform categories), `Maps/Hollowburn Map.svg`, `Lore/Hollowburn/*.txt`
  (19 files), and the canon doc `Hollowburn.txt`, which replaces the
  outline sketch — the sketch file was moved to the project-root
  `_to_delete/` folder rather than left beside it.
- The player is female by design and the cast bios say "sister" and
  "daughter" outright. The `playerGender` setup field is nonetheless kept
  rather than removed, as a `tiles` field with a single Female option,
  defaulted. `playerState.gender` reads straight from
  `rawSetup.playerGender`, and both `playerIdentityWithAge()` and
  `playerGenderPhrase()` return an empty string without it — the two
  functions that fix the wrong-sex baseline portrait, since the player's
  identity text comes from the Appearance dropdowns and never states sex.
  Expressing "female only" by dropping the field would silently
  reintroduce that bug. Keeping it also lets `playerCategoryTemplate`
  stay in the standard `family-{playerGender}` form.
- SFW is enforced in the data, not only by instruction. Three optional
  fields are omitted entirely, each verified against the engine to
  degrade gracefully: `clothingStates` (the prompt's CLOTHING STATES
  block is built only when declared, `extractClothingTags()` drops tags,
  `rollRandomClothingState()` returns undefined — the AI is never told
  undress states exist); `wetLocations`/`poolUniforms` (the wet-outfit
  swap is guarded on both being present, so every portrait comes from the
  four ordinary categories); and `attractedTo` (the "Attracted to:"
  clause is appended per NPC only when the field exists — no NPC here has
  one, so nothing nudges toward romance). `likes`/`dislikes` still drive
  affinity.
- `promptRules.contentApproach` does not follow the player's lead. Solmere
  and Meridian share a string ending "if the player's own input clearly
  steers a scene that direction, follow their lead" and Halcyon is
  deliberately permissive; this Adventure refuses outright and instructs
  the AI to turn the scene back into the dark rather than refuse coldly.
  The Bathroom is deliberately not a wet location despite the source
  manuscript opening with a bath.
- The map is two hubs (The Landing, The Cul-de-sac) joined by one solid
  line for the front door, not the hub-and-spoke the other three use.
  The Old Pit Head gets Halcyon's danger treatment: red, dashed, path
  drawn severed.
- MAP AUTHORING RULE, generalise this: a raw `&` in an SVG label is
  invalid XML and kills the entire render silently. "Mam & Dad's" did
  exactly that and was only caught by rendering the file in a browser and
  looking at it. Escape label text, and render every future map before
  delivering it — the id/overlap/viewBox checks all passed on the broken
  file.
- Four names changed during authoring for the substring-token scan:
  Iris -> Ivy (fires inside "Irish"), Frank -> Sheila (fires inside
  "Frankly"), Ray -> Barry (fires inside "Rays"), and Cathal -> Nell for
  gender balance rather than collision. Jonah's room is "The Box Room"
  rather than "Jonah's Room" so the location name does not carry his
  token and pull him into every scene set there. One residual: "Peter"
  fires inside "Peterlee" and "Peterhead", real towns on this coast,
  mitigated in fiction by a `promptRules.setting` rule that no
  neighbouring town, city or county is ever named.
- Canon is fixed rather than left open, departing from Halcyon's Sunken
  Villa precedent: the entity, its five rules, the 1947 fall, the
  eleventh name and the 1968 cap under the cul-de-sac are all pinned
  down, because five branching endings need a fixed thing to end.
- `relationshipLabels` runs Written Off -> Believes You rather than the
  Despised -> Love / Nemesis -> Devoted scales the other three use.
  Being believed is the story's actual mechanic, so it is the top of the
  track.
- `imageStyle` is "painted illustration, muted desaturated palette,
  overcast north-east English light, front on shot" rather than the
  "painted anime style, front on shot" shared by the other three. This is
  the only field here that departs from a setting proven against the live
  image pipeline, and the first candidate for reverting if portraits come
  out wrong.
- The player is female by design. The cast section previously stated a
  gender-neutral bio convention ("sibling", "their child") that the bios
  beneath it did not follow; the convention is dropped and the bios stand
  as written.
- Closed two OPEN items that the outline already treated as canon
  elsewhere: Evelyn's price was her brother Duncan (1989), not her body —
  the crutches are arthritis; and the Durham coast stays, since the sea
  workings, the Beach location and the uniform rules all depend on it.
