# Perpetua (The Articles) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Perpetua.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Perpetua.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

## 23/08/2026

- Adventure created as canon only. `Adventures/Perpetua.txt` holds the full
  brief: premise, tone, the vote mechanic, fifteen NPCs across three groups,
  eight uniform categories, thirteen map locations, five watch phases, the
  vote-scale relationship ladder, three setup fields, and a three-act arc of
  ten milestones and six endings. No Story Definition JSON, no lore files,
  no map SVG and no UI skin exist; nothing is on R2 and the Adventure is not
  registered in the ADVENTURES array in `Code/Bottom Panel.txt`.
- The relationship ladder doubles as the vote count —
  `0 Would See You Marooned / 15 Votes Against You / 35 Signed The Same
  Paper / 50 Hears You Out / 65 Votes With You / 80 Speaks For You /
  95 Would Hang Beside You`. The signature mechanic therefore needs no new
  persisted field: a vote resolves by counting the standing tiers the engine
  already tracks and displays. `promptRules.setting` carries the rule that
  the narrator counts the room rather than inventing a result.
- Ship's constitution is public and adversarial by design. A vote to depose
  the Captain is called at the capstan, to her face, and she answers it
  there. Authored this way specifically so the Adventure cannot become an
  intrigue: there is no plot to uncover because the machinery for doing it
  openly already exists and is faster. The A-list precedent from Gallant
  applies, arrived at by a different route — Gallant removes the secret,
  this removes the need for one.
- `The Bone Shoals` fills the restricted-site slot held by Halcyon's Sunken
  Villa, Pemberton's Overflow and Gallant's Blackout Block, and carries no
  secret. The lore states plainly that the Absalom's company voted to try
  it, that the vote was properly called and counted, and that the majority
  were wrong. The slot is kept for map shape and to put the cost of the
  premise on the map in red, not for a mystery.
- `Will Cray` renamed **Fenwick Cray** at brief stage; his token is
  `Fenwick`. `Will` fires inside `William` and opens a sentence every few
  paragraphs. Recorded alongside a hazard specific to this Adventure: normal
  shipboard nouns — Watch, Deck, Mast, Sail, Port, Bell, Shot, Hold — are
  capitalised at sentence start constantly, so the programmatic sweep must
  cover the thirteen location names against narration as well as the cast
  against each other. `Aurelian Stack`'s token is `Aurelian` for the same
  reason.
- Content level set at Halcyon's in prose and deliberately **below**
  Gallant's in the portraits. The register is heat, salt and hard work
  rather than engineered display, and it is diegetic: no fresh water to
  wash in, clothing cut down from prizes, and no privacy anywhere on the
  ship. Both genders carry the same emphasis, per Gallant. `attractedTo` is
  omitted for Perrine Vaudray and Obadiah Finch only. Three authored costs
  are kept rather than written around: Adaeze Nwoye administers any
  punishment the player receives, Rasmus Kyd competes for the same votes
  without being made a villain, and Isaac Pell's desertion is saleable at
  Kingsreach by anyone aboard.
- `wetLocations` and `poolUniforms` are both present — first use of the
  wet-outfit swap outside Halcyon. Careening Beach and The Bone Shoals are
  the wet locations and the swap is the working state, hove down in the
  shallows. Gallant omitted both fields, which is inert; this is a
  deliberate opt-in and is untested against these categories.
- Loveday Ashe is authored as the standing argument against the Adventure's
  own premise: an autocracy that takes more, faster, with fewer people
  killed. Current position is that it is never visibly refuted, because a
  vote proved right by outcome turns the Adventure into propaganda for
  itself. Recorded in `Perpetua.txt` OPEN with its counter-argument.
- Open question with possible engine cost: whether the vote tally and the
  per-NPC tiers the narrator used should be written into the story export
  when a vote resolves. The mechanic is entirely narrator-side, so a tester
  who believes a vote resolved wrongly currently has nothing to send back.
