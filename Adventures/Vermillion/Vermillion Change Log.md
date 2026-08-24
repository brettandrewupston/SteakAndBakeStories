# Vermillion (Nobody Calls the Police) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Vermillion.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Vermillion.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

## 24/08/2026

- Title card art added and wired in. `Assets/TitleCards/VermillionTitleCard.webp`,
  700x1050 WebP at quality 86 (199KB), exported from the 1023x1537 PNG per
  the standing export convention; the PNG master is in
  `AssetsNotHosted/Masters/`. Hosted in the assets repo and registered as
  `coverUrl` on the `vermillion` entry, which retires the "no coverUrl
  yet" hold in the registration entry below. Verified before registering:
  the hosted file returns 200 and is byte-identical to the local export,
  and `node --check` passes on the panel's script block.
- REGISTERED in the `ADVENTURES` array, which makes this Adventure playable
  and the skin reachable. Verified first: all 18 hosted files it references
  return 200, and the definition matches the registry entry. No `coverUrl`
  yet — the card renders as emoji + title + blurb until the title card
  exists. Written up in full in the engine log (24/08/2026).
- UI skin built and wired in — the seventh skin, oxblood and brass with a
  marquee. Engine change, so it is written up in full in the engine log at
  `Generator/Steak and Bake Stories/Change Log.md` (24/08/2026) and not
  repeated here.
- Hosting corrected: the 23/08 entry below says nothing is on R2. Every one
  of this Adventure's files — the Story Definition, the map SVG and all
  seventeen Lore files — is now live in the GitHub assets repo and returns
  200, and `Vermillion.json`'s own URLs were rewritten in the R2 to GitHub
  move. See the project-root `Change Log.md` (24/08/2026) for the move
  itself. What remains outstanding is the `ADVENTURES` registration, not the
  hosting.
- `Vermillion.txt` corrected in place for both of the above: the header, the
  OPEN item that said no skin was designed, and OUTSTANDING, which now lists
  the `ADVENTURES` registration and testing and nothing else. A new UI SKIN
  section records the look and points at the engine log for the mechanics.
  One internal contradiction fixed while there: the ENDINGS section said the
  nine accusation endings were authored in two halves and then listed three.
  They are three branches, which is what `Vermillion.json` carries.

## 23/08/2026

- Adventure created. `Adventures/Vermillion.txt` holds the full canon,
  `Story Definitions/Vermillion.json` the story definition, `Maps/Vermillion
  Map.svg` the map, and `Lore/Vermillion/` seventeen lore files. Nothing is
  on R2 and the Adventure is not registered in the ADVENTURES array in
  `Code/Bottom Panel.txt`. Untested — no Begin has been run.
- The killer is different on every playthrough. Three values carry the
  solution: `culprit` (who fired), `safecracker` (who opened the safe
  afterwards and took the book), and `wayOut` (which of three routes was
  used to leave a bolted room). Nine by nine by three.
- **The rotating solution needs no engine change.** It rides on existing
  behaviour: a `tiles` setup field the player leaves untouched is rolled at
  random at Begin. `culprit`, `safecracker` and `wayOut` are three ordinary
  tiles fields. Untouched they are rolled; touched, the player has pinned
  the answer deliberately, which is both the replay feature and the only
  way to test one configuration without rerolling. Three consequences,
  all accepted: the three values travel in the save and therefore in the
  export, so a tester's bug report carries the answer with it; the fields
  are visible on the setup screen, which advertises the mechanism and
  cannot be hidden without engine support; and the narration AI is handed
  the answer on turn one and has to keep it, which is the Adventure's
  single largest risk and is a prompt problem rather than an engine one.
- `safecracker` is rolled independently of `culprit` and is not prevented
  from landing on the same person. Same-person is a legitimate variant —
  one person did all of it — and excluding it would need engine support.
  Flagged in `Vermillion.txt` OPEN with the counter-argument.
- Two secrets rather than one, for a structural reason worth keeping: with a
  single secret, an innocent suspect cannot have a real trace in the crime
  scene without contradicting themselves, so the first piece of physical
  evidence found solves the case. A second person in that room after the
  death makes every trace ambiguous and turns "who opened the safe" into a
  mid-game answer that feels like the answer and is not.
- Symmetric clue authoring: all nine suspects carry a Lie, a Gap in the
  11:30-to-midnight window, a Trace and a Motive on every playthrough. Each
  innocent carries an authored true explanation for the first three; the
  guilty one carries a Tell instead. Every `npc-*.txt` lore file holds both
  versions, because a lore file that named the killer would be wrong on
  eight runs in nine.
- The verdict is engine-owned, deliberately the opposite call to Solmere's
  AI-decided duel outcomes. An AI narrator asked "was it Moretti?" agrees
  with whoever the player names, which would make the mystery decorative.
  Implemented without new engine capability: the `accused` milestone
  declares all nine tokens as outcomes, so the model reports only which name
  the player said — the one fact it cannot get wrong — and nine endings
  carry `when: "accused:<token>"` and fire deterministically. Each of those
  endings is authored in three branches (right and provable, right and
  unprovable, wrong) and the model picks by reading the culprit value rather
  than by forming a view.
- Twelve endings, the longest list of the eight: nine accusation endings
  plus Took It, Nobody Named, and Nobody Calls the Police (death, `anyTime`,
  `continuable: false` per the standing rule that a death ending never
  offers Continue). Flagged in `Vermillion.txt` OPEN as the first place to
  cut if the arc block gets unwieldy.
- Nine NPCs, all eligible as culprit and as safecracker including the
  player's own partner. The roster is deliberately smaller than Gallant's
  fifteen: every suspect has to be someone the player would seriously
  consider, and a suspect the narration treats as background plays badly one
  run in nine. Stated in `promptRules.setting` as "all nine are leads, there
  is no background tier".
- `npcSets`/`openingScenes` used for one NPC only — the partner is
  gender-mirrored to the player and the other eight are identical in both
  rosters. Keys are `male`/`female` matching the `playerGender` tiles values,
  and each key holds the roster for a player of that gender, following
  Meridian.
- The Cardinal never appears and never speaks, in flashback or otherwise. He
  is a shape nine people describe differently and every description is
  accurate.
- Four names changed at build for token-scan collisions, all four because
  the scan is a case-sensitive substring match with no word boundaries:
  `Sal` fires inside `Saloon`, `Fein` inside `Feint`, `Del` inside
  `Delivery`/`Delicate`/`Deliberately` at the start of a sentence, and
  `Marsh` inside `Marshal`. Tokens are `Moretti`, `Arturo`, `Rosetti` and
  `Joey`. Final set: Vivienne, Moretti, Arturo, Rosetti, Vasile, Serafina,
  Joey, Kilbane, Kaminski. `Kaminski` is the token in both rosters, so the
  partner scan is roster-independent. The sweep was run programmatically at
  build — all nine tokens against each other, against the fourteen location
  names, against the uniform/pose/expression strings, and against a list of
  common capitalised words — and is clean. Nicknames are not tokens, so "the
  Cardinal", "Handsome Sal", "the Deacon", "the Sparrow" and "Del" are free
  to use in narration.
- The funeral home is Carbone and Sons, not Rossi & Sons: `Rossi` is a
  near-miss against `Rosetti` for anyone maintaining this later, and an
  ampersand in a location name slugs to a run of hyphens under the map's
  `loc-<slug>` convention.
- Costume register set above Gallant's, which held the high mark for one
  day. Eleven categories, both genders written with equal exposure, and the
  register is 1949 formalwear taken to its limit rather than modern clothes
  in period trim — bias-cut silk, boning, gloves to the bicep, seamed
  stockings, garter straps, a great deal of bare back. It is diegetic twice
  over: the Adventure opens on the most dressed-up night of the year, and
  the building sells looking. `fully clothed, clearly an adult` plus
  `clothingStates` remain the guardrail on every category, `poolUniforms`
  and `wetLocations` are both declared so the wet swap is live, and the
  minor-safety layer is untouched.
- `floor-male` is declared with no NPC using it, so the waiters and dealers
  the narration invents have a category to land in instead of defaulting to
  a Family look.
- `attractedTo` is omitted for Marco Vasile only, which suppresses the
  per-NPC "Attracted to: ..." clause for him.
- Fourteen locations across two hubs — the Supper Club Floor for the sealed
  first night and the Alley for everything honest. The building is sealed
  until dawn and the city opens after it; the engine does not gate
  locations, so that is authored in `promptRules.setting` and in the phase
  guidance rather than enforced. The Cardinal's Office takes the
  restricted-site slot held by Halcyon's Sunken Villa, Pemberton's Overflow
  and Gallant's Blackout Block, and unlike Gallant's it does hold the
  secret, because this is the Adventure where that is the point.
- Relationship ladder written as what a suspect is currently prepared to do
  about the detective: `0 Wants You Gone / 15 Stonewalling / 35 Careful /
  50 Civil / 65 Talking / 80 Telling You Things / 95 On Your Side`. Bottom
  is not Nemesis and top is not Love, following Hollowburn, Pemberton and
  Gallant.
- Time phases are a club's night rather than a calendar day: Evening / The
  Countdown / Small Hours / Dawn / Afternoon, starting at The Countdown —
  five minutes after the shot, with the player already in the building.
- `imageStyle` is the proven `painted anime style, front on shot`.
  Hollowburn's departure from it is flagged in its own outline as the field
  most likely to need reverting, so this Adventure does not repeat the
  experiment.
