# Marque — Change Log

Content and data changes for this Adventure: cast, lore, locations, maps,
Story Definition JSON (`Marque.json`), the town files, contentApproach,
outfit and location data, hosted asset paths, and the outline in `Marque.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

## 30/08/2026

- `Card.webp` cut from `AssetsNotHosted/Masters/MarqueCard.png` — 1024x1536
  master down to the 700x1050 the registry expects, WebP q86, 214 KB, which
  sits inside the 102-283 KB range the other seven occupy. `coverUrl` added
  to the registry entry, so Marque renders as a poster card rather than an
  emoji beside them. The art matches the authored `crew-female` uniform,
  cloth tied across the front over short leather shorts.

- Port casts brought to ten a port — thirty-six new characters across
  Tortuga, Port Royal, Curacao and Santo Domingo, written to the brief's
  register for port people: one want, one angle, memorable in two scenes,
  with the crew carrying the depth. Gender runs 20/20 across the four.
  Loaded roster is eighteen at any port, the scale Pemberton already runs at.
  Verified: token sweep clean across both crew rosters against every town,
  every required NPC field present on all fifty-six, no schedule naming a
  location its town does not declare, and no uncovered wardrobe category.

- Four cast lore files added, one per port, so the ten in a town are
  retrievable as a unit rather than only through their own NPC records.
  Twenty lore files total, none dangling.

- Lore authored: sixteen files. Four topics on the ship file (the 1660
  Caribbean, the commission, the Recompense, what a crossing is), eight crew,
  and one per port declared on that port's town file so it loads and unloads
  with it.
  Crew files are written by SURNAME and never use a first name.
  `loreEntries` is not gender-keyed, so a file naming Ezekiel would be wrong
  in half of all playthroughs — but both rosters share surnames by
  construction, which makes one file correct for either and needs no engine
  change. Verified that no first name from either roster appears anywhere in
  the lore, and that every declared URL resolves to a real file.

- Skin authored — the commission nailed to the wood. Oak is the ground, every
  panel is sailcloth or laid paper on top of it, and the wax seal is reserved
  for what the paper authorises: Send, Begin, the selected tile, the current
  location. Full writeup in the engine log, including its verification.

- Curacao and Santo Domingo authored, completing the four ports and the four
  upgrade axes. Curacao sells hulls through Griet van Doorn's dry dock, the
  literal Dutch advantage of the period; Santo Domingo sells sails through
  Rodrigo Nieves, who knows what kind of captain buys them in a Spanish port
  and has never said so to a soldier. Token sweep clean across both rosters
  against all four towns.

- `crossingTurns` differs by port, which gives the map real distance — Santo
  Domingo four, Tortuga and Port Royal six, Curacao nine. That is what makes
  a route a decision rather than a menu: the hulls cost the most sea to
  reach, and the sails sit a short hop away in the one port that would hang
  the captain on sight.

- Crossings lengthened from three beats to six, and ten sea encounters
  authored: squall, calm, waterspout, a sail astern, whales, water gone bad,
  a hand overboard, wreckage with a survivor on it, a King's ship, and the
  thing under the hull. Weighted so weather is common and the kraken is rare,
  capped at one to a passage with `encounterChance` at 0.25, which measures
  out at six to ten beats a crossing with about one in five quiet. All are things the sea does —
  nothing supernatural, per the grounding rule. The King's ship is the one
  that makes the false commission cost something.

- Crossings set at three beats between Tortuga and Port Royal, carried as
  `crossingTurns` on each town entry so distance can differ by route once the
  other two ports exist. The engine side of sailing — the Travel control, the
  commitment warning, and a passage during which no port is loaded — is in
  the engine log. The empty stretch at sea is deliberate: it is the room the
  encounter table needs, and it is what the Sails upgrade shortens.

- Two-port skeleton authored and registered. `Marque.json` carries the eight
  crew as gender-mirrored `npcSets`, six ship locations, the crew and captain
  wardrobe, clothing states, the vote-free relationship ladder, a three-
  milestone arc and both opening scenes; `Towns/Tortuga.json` and
  `Towns/PortRoyal.json` carry three locations and one shipwright each.
  Tortuga sells the cabin through Margaux Vaudray's plunder market, Port Royal
  the rudder through Hollis Crake. Built small on purpose: it exists to run
  the town-file path against real data before fifty NPCs are written against
  an untested pipeline. Needs a push.

- Token collision sweep run and clean. Both crew rosters checked against each
  other, against each town's cast, against all nine locations in each
  combination, and against a common-capitalised-word list. Ship's name is
  the Recompense; no token is a working noun. Location names are not scanned
  in narration — the `[[LOCATION]]` tag is validated against the list rather
  than matched inside prose — so the shipboard-vocabulary hazard applies to
  tokens only.

- Town files are in the engine — see the engine log — so the ship-file and
  four-town-file split this Adventure is designed around is now the shape the
  engine actually loads. Random encounters is the last outstanding
  dependency.

- Dependency list narrowed to two: town files and random encounters. The
  presence-tiered plan-pass roster is in the engine — see `planPassScope()`
  in the engine log — and it thins an absent NPC to a name and token rather
  than dropping one, so a four-port cast still pays a line per character on
  every beat. Town files stay the load-bearing blocker: only holding one
  port in memory at a time keeps the roster inside the model's context.

## 29/08/2026

- Adventure created as canon only. `Adventures/Marque/Marque.txt` holds the
  brief: the 1660s buccaneer Caribbean, a captain holding a commission taken
  out under false pretence, and a voyage between Tortuga, Port Royal,
  Curacao and Santo Domingo rather than a single location. Deliberately
  loose — no central question and no conspiracy. Nothing else exists.

- Four ports, four shipwrights, one upgrade each, on four separate axes so
  the choice is real: Curacao hull (fewer encounters), Santo Domingo sails
  (shorter crossings), Port Royal rudder (the choice to run), Tortuga cabin
  (a locationScenery swap). Only the cabin reaches the prompt. Santo Domingo
  has to be entered by a captain who preys on Spain, which is its reason to
  exist beyond the map.

- Two classes of relationship, authored differently. The crew travel the
  whole voyage and carry the depth; port people get roughly two scenes each
  and are written sharp and single-note. Returning to a port with what was
  done there still standing is what the persisted relationship number is
  for.

- Encounters are grounded on one line: these are things the sea does.
  Krakens and sea monsters cost no cosmology because sailors in 1660
  believed in them. Ghost ships and skeleton crews are parked rather than
  rejected, and are recorded in `Marque.txt` OPEN with what settling them
  would change.

- Crew set at eight, mirrored Meridian-style: one crew written twice, same
  roles and personalities with names and identity lines regendered, rather
  than two separate casts. Eight is a context budget — the crew are present
  in every scene and every port, so they are the permanent full-line load,
  and eight beside a port's ten is the scale Pemberton already runs at.
  Roles are quartermaster, navigator, bosun, gunner, surgeon, carpenter,
  cook and topman, each carrying a hook rather than only a job. The
  navigator is mechanically load-bearing, since their skill weights the
  encounter roll.

- The Quartermaster knows the commission is false. True from turn one, with
  no reveal and nothing to uncover — the pressure is that one person aboard
  could end the captain in any port by saying so, and has not. Authored this
  way so it costs no machinery and cannot pull the Adventure into an
  intrigue.

- Content level set high, at Gallant's in the portraits rather than below
  it. The register is loose and minimal — sleeves gone, shirts open or
  knotted, bare midriffs, legs and feet — and it is diegetic: tropical heat,
  no fresh water to wash in, and prize clothes cut down to fit a body they
  were not made for. Nothing anachronistic is named. A shirt with the
  sleeves hacked off is the tank top and slops cut short are the short
  shorts, which gives the same silhouette without breaking 1660. Both
  genders carry the same emphasis.

- The commission can be lost, and losing it is a mid-story turn rather than
  an ending. It changes the standing of every port at once — a captain
  without the paper is a pirate everywhere, including where it was issued —
  while the ports, shipwrights and encounter weights stay where they were.

- Arc set: three acts, ten milestones, five endings, turning on the
  commission rather than on a plot. A loose Adventure has no question to
  answer, so it ends on a choice — where the captain stops and who with —
  which the four ports already supply. `commission_lost` closes Act I and
  `the_price` closes Act II, both deliberately without prerequisites: the
  world does them TO the captain, so a cautious player cannot be locked out
  of the back half. Endings are Commissioned, Ashore, Still Sailing, Taken
  and The Ship, the last two reachable at any point.

- Crew baseline authored. `crew-female` is a length of loose cloth tied and
  knotted across the front over short leather shorts belted low; `crew-male`
  is a linen shirt with the sleeves torn away and the front open over short
  leather breeches. Bare arms, midriffs, legs and feet in both, everything
  salt-stiff and hand-cut to fit. The leather is the most historically
  literal thing in the brief rather than a concession to the look —
  buccaneers hunted cattle on Hispaniola and wore the hide, which is where
  the word comes from.

- Blocked on three Features.txt entries — town files, the presence-tiered
  NPC roster, and random encounters. The first two are what make a four-port
  cast fit the model's context at all.
