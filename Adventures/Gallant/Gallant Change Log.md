# Gallant (Property Damage) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Gallant.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in
`Gallant.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

## 24/08/2026

- Title card art added and wired in. `Assets/TitleCards/PropertyDamageTitleCard.webp`,
  700x1050 WebP at quality 86 (283KB), exported from the 1024x1536 PNG per
  the standing export convention; the PNG master is in
  `AssetsNotHosted/Masters/`. Hosted in the assets repo and registered as
  `coverUrl` on the `gallant` entry, so the Adventure Selection card now
  renders as a poster instead of emoji + title + blurb. Verified before
  registering: the hosted file returns 200 and is byte-identical to the
  local export, and `node --check` passes on the panel's script block.
- REGISTERED and live. The Adventure's entry is in the `ADVENTURES` array in
  `Code/Bottom Panel.txt` — id `gallant`, title `Property Damage`, cover `⭐`,
  no `coverUrl` (no title card exists, so the card renders as emoji + title +
  blurb), `jsonUrl` pointing at the committed Story Definition. Registration
  was held until the hosted files were confirmed present, per the standing
  rule in the array's own preamble. Verified before writing: all 24
  `Lore/Gallant/` files are in the assets repo, the Story Definition fetches
  and parses with id `gallant` and 15 NPCs, and `node --check` passes on the
  extracted script block.
- Gained the **newsprint** UI skin — printed-comic palette, Ben-Day dots,
  caption-box narration, Archivo Black. Engine feature, written up in full in
  `Generator/Steak and Bake Stories/Change Log.md`.
- Hosting is the GitHub assets repo, not R2. This Adventure's data was
  authored against `pub-d948...r2.dev` URLs and was swept to
  `raw.githubusercontent.com/brettandrewupston/SteakAndBakeStories/main/`
  with the other six Story Definitions in the project-wide move — the
  hosting decision is in the project-root `Change Log.md` (24/08/2026) and
  the URL rewrite in the engine log.

- Adventure created and built. `Adventures/Gallant.txt` holds the brief;
  `Story Definitions/Gallant.json`, 24 files in `Lore/Gallant/` and
  `Maps/Gallant Map.svg` are the data. Fifteen NPCs across four groups, nine
  uniform categories, thirteen map locations, five time phases, the
  star-scale relationship ladder, ten setup fields, and a three-act arc of
  ten milestones and six endings. No UI skin, no title card and no
  `coverUrl`.
- Build-time verification run against the generated data: all 13 rect ids in
  the map SVG match `locationSlug()` output, no boxes overlap and none falls
  outside the viewBox; the map was rendered in a headless browser before
  delivery. All 15 tokens were swept against each other, the 13 location
  names, every setup-field option label and a common-capitalised-word list —
  no collisions. Every NPC category resolves to a uniform, both
  `playerCategoryTemplate` expansions exist, and every arc `requires`, phase
  `until` and ending `when` resolves to a real milestone and outcome.
- The relationship ladder doubles as the VANTAGE app's public star rating —
  `0 Reported You / 15 One Star / 35 Unrated / 50 Three Stars / 65 Four
  Stars / 80 Five Stars / 95 Would Call Again`. The signature mechanic
  therefore needs no engine support and no new persisted field: the number
  the engine already tracks and displays is the number the fiction is about.
- The A-list openly cause the incidents they respond to, and the city knows.
  Authored this way specifically so the Adventure cannot become an
  investigation — there is nothing to expose, so the antagonists can be
  present and petty in every scene instead of withheld. An earlier version
  of the brief had it as a hidden conspiracy with a discoverable
  declined-call trail; that structure is not the one built.
- `The Blackout Block` fills the restricted-site slot held by Halcyon's
  Sunken Villa and Pemberton's Overflow, but carries no secret by design —
  six blocks zoned out of insurance coverage, stated plainly in the lore.
  The slot is kept for map shape and for Elodie Sarr's storyline, not for a
  mystery.
- `Wen Zhao` renamed **Bricky Zhao** at brief stage; his token is the
  nickname. `Wen` fires inside `When` at the start of a sentence, which
  would have matched on a large share of every scene's narration. Four
  residual collisions are recorded in `Gallant.txt` TOKENS and still need a
  programmatic sweep at build time.
- Content level set to Halcyon's rather than Solmere's, with two authored
  costs: Kell Brannigan's Cardinal brand-alignment clause, and Marguerite
  Delph being the player's landlord. `attractedTo` is omitted for Pilar
  Anastas and Yolanda Pesch only.
- Costume register set above every previous Adventure — this is the most
  overtly sexualised uniform set of the six, applied to all eight
  categories and to both genders equally rather than to the female
  categories alone. It is diegetic: Category D holders are paid on a
  public star rating, so dressing to be looked at is what the job pays
  for. Identity lines carry an explicit adult figure description to
  compose with it, `poseVocabulary` and `expressionVocabulary` are written
  to the same register, and `fully clothed, clearly an adult` plus
  `clothingStates` remain the guardrail on every category. The minor-safety
  layer is untouched.
