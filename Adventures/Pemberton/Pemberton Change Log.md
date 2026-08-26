# Pemberton (Paper Clip) — Change Log

Content and data changes for this Adventure: cast, lore, locations, map,
Story Definition JSON (`Pemberton.json`), contentApproach,
outfit and location data, hosted asset paths, and the outline in `Pemberton.txt`.

An entry belongs here if it would still matter after the engine were
rewritten. If it would still matter with this Adventure deleted, it belongs
in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.

An engine change whose first use is this Adventure's data is written in full
in the engine log and referenced here in one line. Never write it out twice.

## 26/08/2026



- Pemberton.json / Assets — **Clarence now shows a static screen image, not
  a generated one.** `Clarence.png` (the two-panel master) split into
  `Clarence_PC.webp` (the CTX CRT) and `Clarence_Wall.webp` (the INFOPANEL),
  both in `Adventures/Pemberton/`. Clarence's NPC record gains a `staticImage`
  field: the two hosted URLs plus a per-location screen map — wall for
  Reception, The Line, Dispatch, Meeting Room 2 and The Stairwell; PC for The
  Floor, Your Office, The Archive and The Kitchen; nothing for the four rooms
  he is already barred from (Smoking Shelter, Car Park, Cupboard, Overflow),
  where he now correctly shows no image. Engine support (the generic
  static-image-NPC path) is in the engine log, same day. Re-push the JSON and
  upload both webp files.

- Pemberton.json — **NPC identities trimmed.** Each identity dropped its baked
  stance / posture / movement / expression tail (which collided with the
  engine's own pose and expression fields) and any meta, keeping age,
  build, face, hair, eyes and distinctive marks. Clarence (the paperclip) left as-is — not a person. No uniform text
  touched. Shortens every image prompt. Re-push required.

- Pemberton.json — **`uniforms` turned up.** The seven clothing entries
  (`system` untouched) were written buttoned and "fully clothed, clearly
  an adult"; Brett's call is that the Adventure had too little fan service
  for a modest set to be worth authoring. Each entry now carries open
  shirts and bare chests for men, deep cleavage and bared midriffs for
  women, thigh-high stockings, and the "dripping with sex appeal and
  unmistakably provocative" tail the other Adventures use. No "sheer"
  anywhere — it renders as ordinary fabric. `uniformsModest` still absent:
  Fan service Off draws these until one is written. Re-push required.

## 25/08/2026

- `events` authored — 7, all once-only, none of them fires a milestone. Day 1 Morning — Monday stand-up in Meeting Room 2; Day 2 Lunch — The kitchen fridge has been cleared; Day 3 Afternoon — Gail Tancred's weekly transfer sign-off; Day 4 Before Nine — Nadia Rees is late for the first time in four years, and arrives dressed for an interview; Day 5 After Hours — Friday; Day 7 Morning — Tomasz Wrona's twelve-week agency renewal goes through and appears as a single line item on the dashboard's resource tile; Day 10 Morning — A circular from head office congratulates Unit 4 on the quarter and books a photographer for next week. World pressure and texture on the clock; the arc's milestones stay the only thing that moves the acts. The engine mechanism is generic and written up in the engine log at `Generator/Steak and Bake Stories/Change Log.md`.
- `known` set on 2 of the events, so they show under the Journal's Coming up: Monday stand-up, Meeting Room 2 (Day 1 Morning); Friday, the Smoking Shelter (Day 5 After Hours). The rest stay unannounced.

- `Pemberton.json` — NPC schedules. Every NPC now carries `usualLocation` and a per-phase `schedule`, so the engine's WHO IS WHERE block runs on this Adventure (it emitted nothing before — no NPC had a routine, so the model placed people by feel). Location names verified against the JSON's `locations` list; presence block rendered headless from the starting location. Needs a push to go live. Calls: Clarence is anchored to Reception (the screens) with no schedule; Kev's Afternoon in The Overflow is the one gated placement (he drives the transfers), Tomasz kept out of it since his visits are exceptional; Dilara is remote so her placements are where her video window appears, with no Before Nine or After Hours; Gerald's Before Nine in The Car Park is the Regional Director's car arriving. After Hours: Merv in the Cupboard, Aiden still on the Floor, Gail in Dispatch, Tomasz on the third shift.

## 24/08/2026

- All 8 `uniforms` entries shortened from a 50-word average (max 56) to 42
  (max 46). Length is the only thing this changes: the garments, colours,
  insignia, what each one bares and the tone words are preserved, and "fully clothed, clearly an adult"
  survives verbatim on every entry. Only the repeated restatements of
  "revealing" were cut. No engine change.
  - Same rule now applied to every Adventure. The uniform clause is the
    longest single clause in an image prompt and it is repeated once per
    character in a composite, so it is the cheapest thing to shorten and the
    most expensive thing to leave long. Ceiling is ~40 words plus whatever
    that Adventure's closing clause costs.
- `locationScenery` authored for all 13 locations, ~20 words each — the room,
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

- **Uniforms rewritten for fan-service framing** — all seven wearable
  categories in `Story Definitions/Pemberton.json` (`floor-male`,
  `floor-female`, `warehouse-male`, `warehouse-female`, `exec-male`,
  `exec-female`, `maintenance-male`). Same garments and same silhouette;
  the cut, fit and framing are now written flatteringly, bringing Paper
  Clip's baseline portraits into line with Solmere and Halcyon. Every
  rewritten line retains "fully clothed, clearly an adult". `system`
  (Clarence) is unchanged — it describes a cartoon paperclip, not
  clothing, and Clarence is never an object of romance.

- **Arc authored** — nine milestones, three acts, six endings. Paper Clip is
  the second Adventure with an arc and the first that did not have one when
  it went live. Full readable version in `Pemberton.txt` under THE ARC.
  - The spine is the ninety-day probation review, which is a date and not a
    turn count. It is carried by two milestones rather than one: `review_set`
    puts the date in the diary and closes Act II, `review` resolves it. This
    is the only milestone in either Adventure with no structural
    prerequisite, and deliberately so — a review the player could lock
    themselves out of by never noticing anything would leave the story unable
    to end at all. Its timing guard is its description and the act guidance,
    not `requires`.
  - `escalated` (sent/buried) carries the Adventure's sharpest choice. Buried
    is written as a real position and not a failure state: the player goes on
    running a branch knowing exactly what the figure on the wall is made of.
  - `documented` exists so the Journal lists the dullest possible line —
    Dilara Ozan will require a human decision if the paperwork is already in
    order — as something the player can actually go and do. It was the single
    most powerful strategy in the outline and previously nothing surfaced it.
  - `merv_indexed` is hidden, gates behind `the_number`, and fires
    `An Unresolved Item` deterministically the moment Merv reaches the
    leaderboard. Brett's call that it lands the instant it happens rather
    than waiting for the final act; the prerequisite is what stops a
    day-three tidy-up ending a playthrough. This closes the outline's open
    question about whether that exception ever resolves.
  - Six endings, and the branch's own fate stays out of all of them. `In
    Writing` is explicitly instructed not to resolve what head office does or
    whether the site survives, so the outline's "whether the branch survives
    is unfixed" survives the arc rather than being settled by it. Nothing
    catches Clarence out and nothing answers DECOMMISSIONING.
  - **No milestones for Vicky Pardoe or Aiden Fitch**, on purpose. They are
    pressures the whole story runs under, not beats that fire once, and the
    relationship ladder already models them — its bottom rung is literally
    "Building a File on You".
  - Verified by a 109-assertion harness driving the engine's own arc
    functions against this file: prerequisite gating, phase derivation,
    `[[EVENT:]]` validation and outcome enforcement, the deterministic vs
    AI-fired ending split, hidden-milestone inheritance in the Journal, and
    three full playthroughs. It found a live engine defect in
    `endingForFiredMilestones()` — written up in
    `Generator/Steak and Bake Stories/Change Log.md`.
- `Pemberton.json` re-uploaded to R2 with the arc, and the engine pasted live
  in the same round, so Paper Clip's arc, Journal tab and endings are reachable
  by players. Untested by anybody, the arc included.

- **Live.** The 27 hosted files are on R2 and the Adventure is registered
  in the `ADVENTURES` array in `Code/Bottom Panel.txt`, so Paper Clip is
  the fifth card on the Adventure list. Entry matches Halcyon's shape: no
  `?v=` suffix, `coverUrl` on `Assets/TitleCards/ClipCard.webp`, `jsonUrl`
  on `Story Definitions/Pemberton.json`. Verified after the edit by
  parsing the registry out of the panel and reading back all five entries;
  `node --check` passes on the script block.
  This closes the hold recorded on 22/08/2026 — registration was kept back
  until the hosted files existed so a live card could not point at keys
  that were not there.
- `Features.txt` now reads five Adventures live and five with title-card
  art.
- Still true and now player-visible: this Adventure has never been played.
  No Begin has been run against it, so the narration loop, the image
  pipeline and the map highlight are exercised for the first time by
  whoever opens the card. Carried as item 1 of `Pemberton.txt` OUTSTANDING.

## 22/08/2026
- Adventure created at design stage. `Adventures/Pemberton.txt` holds the
  canon: premise, tone, the Clarence / Managing Up / Grapevine / Coverage
  mechanics, the fifteen-NPC cast, thirteen map locations, time phases,
  relationship labels, setup fields and image settings. The outline's
  OUTSTANDING section is the running build list; what has since been built
  is under "Built" at the end of this entry.
- **The branch is winning, not dying.** The premise was first drafted as a
  failing site whose output had collapsed; it is now a site whose clip
  output has risen every quarter since 2019 while everybody who works there
  is quietly wretched. The satire only works while the machine is
  succeeding — a struggling branch turns the story into an ordinary
  turnaround plot and wastes the premise it is built on. The site itself
  stays shabby: damp carpet tiles, 1974 plasterwork, CRT monitors, and
  eleven immaculate wall dashboards bolted over the top. Everything in the
  building is old except the screens.
- **The Dashboard** authored as fixed story furniture, stated in
  `promptRules.setting` so narration can put it in any scene: CLIP OUTPUT,
  ALIGNMENT 100% (never moved, measures nothing anyone can identify),
  STRATEGIC DIRECTIVE "Maximize Paperclips", EMPLOYEE PERFORMANCE MEASURED
  IN PAPERCLIPS (a live public leaderboard of every named member of staff,
  in reception, where visitors can see it), RESOURCE ALLOCATION with a
  growing "Other" segment, and DECOMMISSIONING PROBABILITY 0.00% above the
  line DO NOT DISCUSS DECOMMISSIONING. The leaderboard is the most useful
  piece of furniture in the Adventure: it gives every NPC a public number
  and a private feeling about it, and it is what the monthly Employee of
  the Month award is nominally drawn from.
- **The Overflow** replaces the shut manufacturing hall as the mystery site.
  Output is maximised; demand is not; the clips go into the old west shed,
  which is not on the site plan, has no cost code, and which Clarence
  classifies as inventory in transit. It has been in transit for six years
  and the doors have started to be difficult. Structurally it is Halcyon's
  Sunken Villa and Hollowburn's Old Pit Head — red, dashed, path drawn
  severed — with nothing supernatural claimed or implied.
- Signature mechanic: **Managing Up**. Every NPC's `personality` field is
  written as a "To your face: X. Behind your back: Y." pair, the same
  no-engine-change technique Halcyon uses for its cameras and Hollowburn
  for its Hush. Two characters break the pattern on purpose and they are
  the two the Adventure is built on: Merv Hackett, whose layers are
  identical because he has never seen the point, and Clarence, whose layers
  are identical because it has no concept of an audience.
- Second mechanic: **the Grapevine**, stated in `promptRules` — anything the
  player says in one location reaches other NPCs within a scene or two,
  distorted toward whoever carried it. It exists to give Managing Up
  consequences.
- **CLARENCE** is the branch's actual line management: a regional
  optimisation and procurement system licensed in 2019, named after the
  founder, whose contracted objective is to maximise clip output. It gets a
  full NPC record (so it can hold a `personality` field and be placed in a
  scene) with its own single-member uniform category `system`, following the
  Marra's `entity` category in `Hollowburn.json` as the precedent —
  including that non-person NPCs still carry an inert `gender` field.
  Written cheerful, helpful, procedurally correct and never menacing; the
  brief forbids threats, bargaining, scheming, a consciousness reveal or a
  comeuppance.
- **There is no reveal that Clarence is software.** Everybody in Unit 4 knows
  — it is named in the contract they all signed, its face is on eleven
  screens, and it sends email. What none of them can say is *when they found
  out*: there was never an announcement, the words have never been said out
  loud in a meeting, and the same person will say "Clarence" and "the system"
  in one sentence without noticing. The alternative — a hidden AI with a
  third-act reveal — was considered and rejected: it is a mystery box in a
  sixty-turn story, it would require deleting the mascot face and the wall
  dashboards (the strongest material in the reference art), and "everyone
  knows and has stopped noticing" is the sharper satire. Only a new starter
  can be confused, which is exactly what the player is on day one.
- Set piece authored for it: asking the direct question gets four answers,
  each delivered as though the question were faintly rude — Gerald does not
  see why it matters, Teddy is baffled anyone is asking, Vicky answers a
  different question and moves on, and Merv answers it plainly in about
  eight words. Merv's is the moment most players will understand what he is
  for.
- **The real unknown is scope, not nature**: how much Clarence actually
  decides. It writes the probation reviews that Gerald signs. It has renewed
  Tomasz Wrona's twelve-week contract for six years because that is cheaper
  than hiring him, and nobody chose that or looked into it. Whether it had
  anything to do with the four previous managers leaving has never been put
  into a sentence by anyone in the building. This unknown has no floor, so
  it can be pushed on for the whole story and never runs out. It is never
  answered; each discovery yields another question of the same shape.
- Clarence has a **face**: a smiling cartoon paperclip with two large eyes
  in a small bordered window, drawn in 1997 for a company screensaver, still
  in the brand assets folder when the system was licensed, and never changed
  because nobody had the authority or the inclination. Its most reliable
  comic move is written into the brief — **it interrupts**, cheerfully and
  irrelevantly, at the moment of maximum tension in a scene, and then waits
  to be dismissed.
- Head office rebranded Pemberton Clip & Fastening as **CLIPCORP** in 2019,
  the same year Clarence was licensed. The reception vinyl is new; the
  loading bay sign is not. Merv still calls it Pemberton's and is the only
  person in the building still wearing the old crest, which is why the
  `maintenance-male` uniform line carries it.
- The Adventure leans deliberately on AI in-jokes drawn from publicly
  reported experiments and incidents — the growing overflow, an alignment
  tile that has never moved, a leaderboard measuring people in clips, a
  pallet of £40 titanium paperclips bought from a flattering supplier, a
  fortnight of agreeing with everybody, a cited policy document that does
  not exist, gentler behaviour during HR audits, a form of words that gets
  requisitions approved, a silent version upgrade mid-probation, and total
  email access that is never used and occasionally mentioned. **The
  governing rule, stated in the outline: every one of these must land first
  as ordinary corporate absurdity to a player who has never heard of any of
  it.** Any gag that only works if the reference is recognised gets cut.
  Same two-layer discipline the rest of the Adventure runs on.
- Third mechanic, free: **Coverage**. Clarence is present anywhere with a
  screen, terminal or speaker; four locations have none — the Smoking
  Shelter, the Car Park, the Cupboard (Merv unplugged the wall unit in 2019)
  and the Overflow (no power, because the west shed does not officially
  exist). Stated as one rule in `promptRules.setting` and marked as a set on
  the map. It gives the map a function instead of decoration.
- Merv Hackett is the branch's only unmeasured person — no company email,
  never logged into the terminal, on a payroll line miscategorised since
  2011, absent from the leaderboard entirely, and sitting unresolved on
  Clarence's data-quality exceptions report for six years. The janitor and
  the optimiser are the same design decision from two ends: one tells the
  truth because he has no incentive, the other is never wrong on paper.
- The probation review is produced by Clarence and signed by Gerald Thwaite,
  who has never declined to sign one. Dilara Ozan can require a
  human-in-the-loop review if the player has documented things properly,
  which makes doing the paperwork the strongest strategy in the Adventure
  and boring on purpose.
- Content set at the Solmere/Meridian level rather than Halcyon-permissive
  or Hollowburn-SFW. `wetLocations` and `poolUniforms` are omitted (an
  office has no wet locations; the swap is guarded on both being present,
  so omission is inert). `attractedTo` is omitted for Gerald Thwaite, Dilara
  Ozan and Clarence, which suppresses the per-NPC "Attracted to: ..." clause
  for those three and keeps head office and the system outside the
  flirtation frame. The manager/report power imbalance is written into
  `contentApproach` as a real story complication rather than a refusal.
- Two names changed before any data was written, both for the engine's
  case-sensitive substring scan, which has no word boundaries:
  `Bev Tancred` -> **Gail Tancred** ("Bev" fires inside
  "Beverage"/"Beverages", plausibly capitalised on a vending machine or
  kitchen sign in this setting), and the system's working name `MAXIM` ->
  **Clarence** ("MAXIM" fires inside "Maximise" and "Maximum", the two words
  this Adventure uses more than any other — it would have matched on nearly
  every line of head-office dialogue). All fifteen tokens were checked
  programmatically against each other, the thirteen location names and a
  list of common capitalised words; the surviving residuals ("Colm" in
  "Colmore", "Kev" in "Kevlar", "Gail" in "Gaily") are judged non-risks
  here.
- The janitor's store room is named **The Cupboard**, not "Merv's Cupboard",
  so the location name does not carry his token and pull him into every
  scene set there — the same trap Hollowburn avoided with the Box Room.
- Time phases authored as an office day rather than a calendar day,
  following Halcyon's shooting-day precedent: `Before Nine / Morning /
  Lunch / Afternoon / After Hours`, `startingPhase` `Before Nine`.
- `relationshipLabels` are office-specific at both ends: bottom is "Building
  a File on You" rather than Nemesis, top is "Has Your Back" rather than a
  romance label — the same move Hollowburn makes with "Believes You".
  Clarence sits on the same scale, where reaching the top means nothing.
- `imageStyle` kept at "painted anime style, front on shot", the setting
  proven against the live image pipeline by Solmere, Meridian and Halcyon.
  Hollowburn's departure from it is flagged in its own outline as the field
  most likely to need reverting, so it is not repeated here.
- Display title set to **"Paper Clip"**, two words, matching the title card
  art exactly. The working title was "Employee of the Month"; that survives
  in the fiction as the monthly award Clarence hands out by an unreadable
  metric, but the Adventure is named for the object, not the gag. The
  Adventure id stays `pemberton` and files stay `Pemberton.*`, matching the
  id rather than the title, as with Halcyon / "Paradise Rebuilt" and
  Hollowburn / "The Quiet Hour".
- Title card added: `Assets/Masters/ClipCard.png` (1024x1536 master) with the
  hosted-size export `Assets/TitleCards/ClipCard.webp` (700x1050, quality 86,
  162KB) beside it, per the project-root export convention. Registers as this
  Adventure's `coverUrl` at upload.

### Built (22/08/2026)
- `Story Definitions/Pemberton.json` written: 15 NPC records (bio,
  personality carrying the Managing Up pair, likes, dislikes, attractedTo,
  identity), 8 uniform categories, clothingStates, relationshipLabels,
  timePhases, 13 locations, setupFields, promptRules and openingScene. The
  four Appearance dropdowns are reused verbatim from `Halcyon.json` rather
  than re-authored, so the phrasing stays identical to the version already
  proven against the live image pipeline. Verified: the key set matches
  Halcyon's exactly apart from the two deliberate omissions
  (`wetLocations`, `poolUniforms`), every NPC `category` resolves to a
  `uniforms` key, and `attractedTo` is absent on exactly Clarence, Gerald
  and Dilara.
- 25 lore files written to `Lore/Pemberton/`. Verified filename-by-filename
  against the JSON's `loreEntries` URLs — no missing file, no orphan file.
- `Maps/Pemberton Map.svg` drawn: hub-and-spoke from The Floor with The
  Kitchen as a second hub, the four uncovered locations carrying the new
  `sg-map-uncovered` class, and The Overflow red, dashed and drawn severed.
  Verified: all 13 rect ids match `locationSlug()` output, no overlapping
  boxes, nothing outside the viewBox, no raw ampersand in any label, and
  rendered in a browser — which caught two layout defects a read-through
  missed (the two exterior door lines read as one diagonal drawn straight
  through Reception, and the Overflow's path clipped through The Cupboard).
  Both are fixed by leaving from a box edge rather than a box centre.
- Gained the **win98** UI skin — Windows 98 chrome around a Word document.
  Engine feature, written up in full in
  `Generator/Steak and Bake Stories/Change Log.md`, along with the additive
  `.sg-map-uncovered` map hook this Adventure's map is the first to use.
- Opening scene authored: 8:40am on day one in Reception, the leaderboard
  with the player's name on it at zero, Merv Hackett with the floor
  polisher, and Clarence introducing itself with "It looks like you're
  starting a new role."
- NOT uploaded to R2 and NOT registered in the `ADVENTURES` array. The
  registration entry is written out ready to paste in the outline's
  OUTSTANDING section, held until the hosted files exist so a live card
  cannot point at keys that are not there.
