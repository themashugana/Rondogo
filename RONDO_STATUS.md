# Rondo — Project Status Document  
Read this at the start of every conversation. Update this document at the end of every conversation.

---

## What Is This Game?  
**Working Title:** Rondo (previously: Pitch)  
**Elevator Pitch:** Digital Subbuteo meets Chess meets Abalone — a turn-based tactical football (soccer) strategy game played on a grid pitch with 11 player-pieces per side, each with unique attributes, movement rules, and special abilities.

---

## Decisions Made (Do Not Re-Litigate)

| Decision | Detail |  
|---|---|  
| Game type | Turn-based, grid-based tactical strategy |  
| Players per side | 11 |  
| Inspirations | Subbuteo (feel), Chess (piece logic), Abalone (spatial pressure/blocking) |  
| Probability system | Attribute-linked probability for contested actions — skill builds odds, luck decides the moment |  
| Player pieces | Unique pieces with attributes: movement range, pass range/direction, shot power/accuracy, defensive strength |  
| Base archetypes | GK, CB, Full Back, Midfielder, Winger, Striker |  
| Variant system | Exceptions to base types (e.g. Sweeper Keeper, Wing Back) unlocked over time |  
| Squad building | Pick formation pre-game with limits on player types — squad identity is part of the strategy |  
| Deck building | Players ARE the pieces/cards — each with their own attribute values within a type/variant |  
| Platforms | Eventually: face-to-face (board game feel), online PvP, single player vs AI |  
| Depth | To be determined through playtesting — start simple, layer complexity |  
| Grid dimensions | 15 wide x 20 tall |  
| Grid zones | Two end zones (rows 1-3, 18-20), defensive/attacking thirds (rows 4-7, 14-17), middle third (rows 8-13), penalty boxes (3x5 in each end zone) |  
| Grid type | Square grid with 8-direction movement (including diagonals) |  
| Turn structure | Fixed 3 actions per turn; all 11 players eligible each turn; each action must use a different player; every action must be active (no holding) |  
| Action vocabulary | Move, Dribble, Pass, Shoot, Tackle/Press |  
| Dribbling | One action; player moves with ball across multiple squares; dribble range = same as movement range per archetype |  
| Ball states | Possessed, Loose, Dead ball — ball only moves when acted on by a player |  
| Movement rules type | Hard rules — restrictions are absolute, not cost-based |  
| Movement rules — GK | Range: 2 / Cannot leave own penalty box |  
| Movement rules — CB | Range: 3 / Cannot cross halfway line (cannot enter rows 8-20) |  
| Movement rules — Full Back | Range: 4 / Cannot enter central 5 columns (cols 6-10) / Cannot enter opposition attacking third (rows 14-20) / Cannot move more than 2 squares horizontally in a single action (Move or Dribble) |  
| Movement rules — Midfielder | Range: 4 / No restrictions — full pitch access |  
| Movement rules — Winger | Range: 5 / Cannot enter central 5 columns (cols 6-10) / Cannot enter own defensive third (rows 1-7) |  
| Movement rules — Striker | Range: 4 / Cannot enter own defensive third (rows 1-7) |  
| Movement freedom | All archetypes use free roam within range bubble (Chebyshev distance) — can reach any square within range including diagonal combinations |  
| Midfielder variants | Kept as single archetype for now — Defensive Mid, Attacking Mid etc. to be handled via variant system later |  
| Pass mechanics — philosophy | Hybrid: positioning and attributes determine the odds, moment of execution has an element of chance |  
| Pass range — GK | 10 squares |  
| Pass range — CB | 7 squares |  
| Pass range — Full Back | 5 squares |  
| Pass range — Midfielder | 9 squares |  
| Pass range — Winger | 5 squares |  
| Pass range — Striker | 4 squares |  
| Pass range — modifiers | Fixed per archetype; special abilities can extend or modify range |  
| Passing lanes | Option C — defender adjacent to passer creates hard block; defender further along lane reduces probability but doesn't prevent attempt |  
| Passing lanes — abilities | Special abilities (e.g. through ball) can allow certain players to thread passes through lanes under specific conditions |  
| Pass difficulty factors | Distance, defender proximity to passer (pressing), defender in the lane, passer's pass attribute, receiver's control attribute, defender proximity to receiver |  
| Shoot mechanics — philosophy | Same hybrid probability system as passing — skill builds odds, luck decides the moment |  
| Shot range — Striker | 5 squares |  
| Shot range — Winger | 4 squares |  
| Shot range — Midfielder | 6 squares (long-range specialist) |  
| Shot range — Full Back | 3 squares |  
| Shot range — CB | 2 squares (tap-ins / headers only) |  
| Shot range — GK | Cannot shoot |  
| Shot difficulty — zone probability | Inside box central: High / Inside box wide: Medium / Just outside box central: Medium / Just outside box wide: Low / Middle third central: Low / Middle third wide or own half: Very Low |  
| Shot difficulty — modifiers | Defender proximity (adjacent = odds down); GK position (well-positioned = odds down, out of position = odds up); shooter's attribute (higher = odds up) |  
| Shot difficulty — zone mapping | Zone position uses existing grid zones; central = cols 6-10, wide = cols 1-5 and 11-15 |  
| GK interaction | Passive — GK positioning and attribute modify shot probability automatically; no separate save action or reaction mechanic |  
| Shot edge cases | Post/crossbar handled via near-miss probability band (see rebound system) |  
| Curl ability | Shared ability — Winger, Striker, and Midfielder pools; position-specific behaviour (see ability definitions) |  
| Probability system type | Option C — hybrid: fixed base probability modified by attributes and situational factors; % based (not dice); luck is the moment, skill builds the odds |  
| Probability — base pass | 65% |  
| Probability — base shoot | 50% |  
| Probability — base tackle | 45% |  
| Probability — attribute modifier range | +/-25% for acting player's primary attribute |  
| Probability — receiver attribute modifier range | +/-15% for receiver's control attribute |  
| Pass modifiers — distance | Short (up to 1/3 max range): +10% / Medium (1/3-2/3): 0% / Long (2/3-max): -10% |  
| Pass modifiers — defensive pressure on passer | Defender adjacent to passer: -15% / Defender in passing lane: -10% / Both combined: -25% |  
| Pass modifiers — receiver | Receiver control attribute: +/-15% / Defender adjacent to receiver: -10% |  
| Pass modifiers — defender in lane distance | Defender in passing or shooting lane only triggers lane penalty if within 3 squares of the passer/shooter; beyond 3 squares = too far to intercept, penalty does not apply |  
| Shoot modifiers — zone | Zone determines base probability — no separate distance modifier on top |  
| Shoot modifiers — defensive pressure | Defender adjacent to shooter: -15% / Defender in shooting lane: -10% (only if within 3 squares) |  
| Shoot modifiers — GK positioning | GK well-positioned: -15% / GK out of position: +15% |  
| Shoot modifiers — shooter attribute | +/-25% — consistent with rest of probability system |  
| Tackle modifiers — tackler attribute | +/-25% — consistent with rest of probability system |  
| Tackle modifiers — ball carrier attribute | +/-15% — mirrors receiver control in passing |  
| Tackle modifiers — positional modifier | None — no facing/direction modifier; kept simple |  
| Tackle modifiers — supporting defender | Supporting defender adjacent to ball carrier: +10% |  
| Defensive zone mechanic — Pressured Squares | Any square adjacent to a defender is a Pressured Square; relevant probability penalties apply automatically; formalises existing adjacency modifiers as a named spatial mechanic |  
| Defensive zone mechanic — Partial Pressure | 3+ defenders adjacent to ball carrier: movement restricted to squares away from defenders only |  
| Defensive zone mechanic — Fully Trapped | All escape squares blocked (by defenders + pitch boundary): automatic turnover; loose ball placed in nearest open square toward trapping team's goal |  
| Formation system | Fixed presets — players choose from a curated list of 10 formations pre-game |  
| Formation — two-layer system | Layer 1: Formation (shape / numbers per line); Layer 2: Role (archetype assigned to each slot, constrained by a role menu) |  
| Formation — role flexibility | Constrained — each slot has a defined menu of valid archetypes; prevents nonsense combinations while allowing tactical variety |  
| Master role menu — Goalkeeper | GK only |  
| Master role menu — Centre Back | CB only |  
| Master role menu — Wide Defender | Full Back or Wing Back |  
| Master role menu — Defensive Midfield | Midfielder only |  
| Master role menu — Central Midfield | Midfielder only |  
| Master role menu — Wide Midfield | Winger or Midfielder |  
| Master role menu — Wide Forward | Winger or Striker |  
| Master role menu — Attacking Midfield | Midfielder or Striker |  
| Master role menu — Striker | Striker only |  
| Formation 1 — 4-4-2 | GK / CB / CB / Wide Def (L) / Wide Def (R) / Wide Mid (L) / Wide Mid (R) / CM / CM / ST / ST |  
| Formation 2 — 4-3-3 | GK / CB / CB / Wide Def (L) / Wide Def (R) / CM / CM / CM / Wide Fwd (L) / Wide Fwd (R) / ST |  
| Formation 3 — 4-2-3-1 | GK / CB / CB / Wide Def (L) / Wide Def (R) / DM / DM / Wide Fwd (L) / AM (Midfielder or Striker) / Wide Fwd (R) / ST |  
| Formation 4 — 4-5-1 | GK / CB / CB / Wide Def (L) / Wide Def (R) / Wide Mid (L) / CM / CM / CM / Wide Mid (R) / ST |  
| Formation 5 — 4-1-4-1 | GK / CB / CB / Wide Def (L) / Wide Def (R) / DM / Wide Mid (L) / CM / CM / Wide Mid (R) / ST |  
| Formation 6 — 4-2-4 | GK / CB / CB / Wide Def (L) / Wide Def (R) / CM / CM / Wide Fwd (L) / ST / ST / Wide Fwd (R) |  
| Formation 7 — 3-4-3 | GK / CB / CB / CB / Wide Mid (L) (Winger, Midfielder or Wing Back) / CM / CM / Wide Mid (R) (Winger, Midfielder or Wing Back) / Wide Fwd (L) / ST / Wide Fwd (R) |  
| Formation 8 — 3-5-2 | GK / CB / CB / CB / Wide Mid (L) (Winger, Midfielder or Wing Back) / CM / CM / DM / Wide Mid (R) (Winger, Midfielder or Wing Back) / ST / ST |  
| Formation 9 — 5-3-2 | GK / CB / CB / CB / Wide Def (L) / Wide Def (R) / CM / CM / CM / ST / ST |  
| Formation 10 — 5-4-1 | GK / CB / CB / CB / Wide Def (L) / Wide Def (R) / Wide Mid (L) / CM / CM / Wide Mid (R) / ST |  
| Squad size | 14 players total — 11 starters + 3 substitutes |  
| Substitution moments | 3 per game — one substitute per moment |  
| Substitution timing | Start of your turn, before your 3 actions |  
| Substitution rules | Subbed-off players cannot return |  
| Archetype limits — GK | Min 1 / Max 1 |  
| Archetype limits — CB | Min 1 / Max 4 |  
| Archetype limits — Full Back | Min 0 / Max 4 |  
| Archetype limits — Midfielder | Min 0 / Max 6 |  
| Archetype limits — Winger | Min 0 / Max 4 |  
| Archetype limits — Striker | Min 1 / Max 4 |  
| Starting positions | Fixed per formation — exact grid coordinates deferred to Phase 2 / prototype build |  
| Kick-off | Ball starts centre square; coin toss decides who kicks off; kicking-off team must have at least one player in centre zone |  
| Special abilities — design approach | Football logic first — mechanics serve the ability, not the other way around |  
| Special abilities — scope | Abilities can modify existing mechanics OR introduce new actions |  
| Special abilities — count | Variable — tied to player rarity/quality tier |  
| Special abilities — passive vs active | Both — determined ability by ability |  
| Special abilities — archetype exclusivity | Loose — primary home archetype, but football-logical crossovers allowed |  
| Curved ball path mechanic | Players with Curl or Whipped Cross ability can deliver a curved L-shaped path; player nominates destination only; ball travels laterally first then forward (or vice versa); +2 range boost when using curved path; defenders on the straight line but off both segments of the L are not in the lane |  
| Burst ability | Shared — all archetypes including GK; Active (once per turn): player gains +2 to movement range for this action only |  
| GK ability — Sweeper Keeper | Active (once per turn): GK can move outside penalty box up to 2 squares beyond box boundary |  
| GK ability — Long Throw | Active (once per turn): Pass that bypasses passing lane penalties entirely; normal pass attribute modifiers still apply |  
| GK ability — Penalty Specialist | Passive: Significant probability bonus when defending shots from central box zone |  
| GK ability — Command of the Box | Passive: All attackers inside the box take -10% on pass/shoot while GK is inside own penalty box |  
| CB ability — Aerial Presence | Passive: All attackers attempting to receive a pass inside the CB's adjacent squares take an additional -10% on top of existing adjacency penalties |  
| CB ability — Last Ditch Tackle | Active (once per turn): CB can attempt a tackle on a ball carrier up to 2 squares away rather than needing to be adjacent; base probability -10% |  
| CB ability — Step Up | Active (once per turn): CB can temporarily cross the halfway line to pressure a ball carrier; must return to own half at start of next turn |  
| CB ability — Sweeper | Passive: If a loose ball lands in the CB's defensive third, the CB may immediately move 1 square toward the ball as a free action |  
| CB ability — Clearance | Active (once per turn): When the ball is loose or possessed by a teammate in adjacent squares, launch a long clearance up to full pass range ignoring passing lane penalties; ball lands as a loose ball in nominated square |  
| CB ability — Intercept | Passive: When a defender block results in clean possession for this CB, they may immediately move up to 2 squares as a free action |  
| Full Back ability — Overlap Run | Active (once per turn): Full Back can temporarily ignore the no-central-columns restriction when moving forward in the same wide channel as the ball |  
| Full Back ability — Underlap Run | Active (once per turn): Full Back can cut inside toward central columns — temporarily ignoring the no-central-columns restriction — when moving forward in the same wide channel as the ball |  
| Full Back ability — Tracking Run | Passive: When an opposition Winger moves, if the Full Back is within 3 squares they may immediately move 1 square toward the Winger as a free action |  
| Full Back ability — Whipped Cross | Active (once per turn): Pass into the opposition penalty box from a wide position; bypasses receiver adjacency penalty; ignores one defender-in-lane penalty; curved path available (+2 range boost). Shared: Full Back and Winger |  
| Full Back ability — Last Ditch Tackle | Active (once per turn): Full Back can attempt a tackle on a ball carrier up to 2 squares away rather than needing to be adjacent; base probability -10% |  
| Full Back ability — Recover | Active (once per turn): When this Full Back gains possession from a defender block or loose ball in their own half, they may immediately attempt a pass as a free action |  
| Midfielder ability — Through Ball | Active (once per turn): Pass that bypasses passing lane penalties entirely; base probability -10%; ignores defender-in-lane modifier |  
| Midfielder ability — Press Trigger | Active (once per turn): Midfielder moves toward ball carrier and nearest friendly player within 3 squares also moves 1 square toward ball carrier as a free action |  
| Midfielder ability — Dictate | Passive: When this Midfielder completes a pass, the receiving player's next action this turn gains +10% probability |  
| Midfielder ability — Long Shot | Passive: Shot probability from outside the box upgraded one band (e.g. Low becomes Medium) |  
| Midfielder ability — Recycle | Active (once per turn): After a failed pass or tackle in this Midfielder's zone, may immediately attempt to recover a loose ball without using one of the 3 turn actions |  
| Midfielder ability — Skill | Active (once per turn): When dribbling, attempt to bypass a single opposition player; probability check made (base tackle probability, modified by both players' attributes); success = opposition player's Pressured Square penalties ignored for this dribble and Midfielder can move through or past them freely; fail = loose ball. Shared: Midfielder, Winger, Striker |  
| Midfielder ability — Clearance | Active (once per turn): When the ball is loose or possessed by a teammate in adjacent squares, launch a long clearance up to full pass range ignoring passing lane penalties; ball lands as a loose ball in nominated square |  
| Midfielder ability — One-Two | Active (once per turn): Player passes to an adjacent teammate, then immediately moves up to their full movement range as a free action. Shared: Midfielder and Winger |  
| Midfielder ability — Dummy Run | Active (once per turn): This Midfielder moves without the ball; any defender within 2 squares may be moved 1 square toward this Midfielder as a free action by the opponent, but the opponent must choose before seeing the next action |  
| Midfielder ability — Curl | Active (once per turn): Crossover ability. Ignores one defender-in-lane penalty on any pass regardless of position or zone; curved path available (+2 range boost). When combined with Through Ball in a single action, the pass takes a curved L-shaped path AND bypasses all lane penalties; both ability charges consumed. |  
| Winger ability — Curl | Active (once per turn): When shooting from a wide position, the shot is treated as central zone for probability purposes. Also ignores one defender-in-lane penalty on the shot. Curved path available (+2 range boost). Shared: Winger and Striker |  
| Winger ability — Whipped Cross | Active (once per turn): Pass into the opposition penalty box from a wide position; bypasses receiver adjacency penalty; ignores one defender-in-lane penalty; curved path available (+2 range boost). Shared: Full Back and Winger |  
| Winger ability — Run In Behind | Active (once per turn): The Winger can move through squares occupied by opposition players when moving forward (toward opposition goal); no tackle attempt is triggered; cannot end movement on an occupied square |  
| Winger ability — Cutback | Active (once per turn): When the Winger is inside the opposition penalty box, they can pass backward to a player outside the box; bypasses receiver adjacency penalty and ignores defender-in-lane modifier |  
| Winger ability — Dribble Magnet | Passive: When the Winger successfully completes a dribble, one opposition player adjacent to the Winger's destination square is displaced 1 square away from the Winger (owner's choice of direction, cannot be placed off the pitch) |  
| Winger ability — Pin Point Cross | Active (once per turn): When crossing into the opposition penalty box from a wide position, the pass bypasses the receiver adjacency penalty, ignores one defender-in-lane penalty, curved path available (+2 range boost), AND the receiving player gains +10% on any shot attempted from that ball this turn |  
| Winger ability — Sweet Strike | Active (once per turn): When the Winger moves from a wide column (cols 1-5 or 11-15) into a central column (cols 6-10) and shoots in the same action, the shot is treated one probability band higher than the zone would normally allow |  
| Winger ability — Press High | Active (once per turn): When the opposition has possession in their defensive third, this Winger can move up to their full movement range toward the ball carrier as a free action, ignoring the no-own-defensive-third restriction for this action only |  
| Striker ability — Curl | Active (once per turn): Ignores one defender-in-lane penalty on any shot, regardless of position or zone. Curved path available (+2 range boost). Shared: Winger and Striker |  
| Striker ability — Clinical | Passive: When the Striker shoots from inside the penalty box, their shot attribute modifier is treated as maximum (+25%) regardless of actual attribute value |  
| Striker ability — Movement | Active (once per turn): The Striker can move without using one of the 3 turn actions, but only into the opposition penalty box; cannot carry the ball |  
| Striker ability — Poacher | Passive: If a loose ball lands inside the opposition penalty box, the Striker may immediately move 1 square toward it as a free action |  
| Striker ability — Hold Up | Active (once per turn): When a defender attempts a tackle on this Striker, the tackle probability is reduced by 15% |  
| Striker ability — Overhead Kick | Active (once per turn): The Striker can attempt a shot from a loose ball in the box without needing to control it first; base probability -15% |  
| Striker ability — Aerial Threat | Active (once per turn): When receiving a pass into the opposition penalty box, the Striker can immediately attempt a shot without using a separate action; base probability -10% |  
| Striker ability — Drop Deep | Active (once per turn): This Striker can move into the middle third to receive a pass; upon receiving, they may immediately pass to any teammate in the opposition half as a free action, bypassing the no-own-defensive-third restriction for that pass only |  
| Through Ball + Curl combination | When a Midfielder has both Through Ball and Curl abilities, they can activate both in a single action; the pass takes a curved L-shaped path (+2 range boost) AND bypasses all lane penalties; both ability charges are consumed |  
| Set pieces | REMOVED — no corners, free kicks, throw-ins, goal kicks; replaced by board rebound system |  
| Fouls | REMOVED — no foul system; failed tackles produce loose balls only |  
| Ball out of play | REMOVED — replaced by board rebound system; ball never goes out of play |  
| Deflection system — type | Hybrid: deterministic for physics-based deflections (boundary, post/crossbar); probabilistic for human-body deflections (GK save, defender block, failed tackle) |  
| Deflection system — boundary rebound | Ball reflects off boundary (horizontal flips off side boards, vertical flips off end boards, both flip off corners); travels remaining momentum in new direction; lands as loose ball; hits second boundary = stops dead as loose ball; cannot score directly off a rebound |  
| Deflection system — post/crossbar | Same reflection rule as boundary rebound; ball travels remaining momentum in reflected direction; lands as loose ball; vertical shot rebounds straight back; diagonal shot reflects at opposite diagonal angle |  
| Deflection system — GK save | Second probability check: hold vs parry; Hold = GK gains possession (treated like receiving a pass); Parry = ball lands in one of 3 adjacent squares facing shot direction, equal probability across 3 squares; Factors for check: GK attribute (+), shooter power attribute (-), shot distance (close range -) |  
| Deflection system — defender block | Second check: clean possession vs deflection; Clean possession = only if pass failed by large margin; Deflection = ball lands in one of 2 squares on far side of defender (left or right), equal probability between the two; exact probability margins for clean possession threshold to be defined in probability tuning session |  
| Deflection system — failed tackle | Ball carrier maintains possession; no deflection, no loose ball |  
| Board rebound system | Ball hitting any pitch boundary rebounds and stays live; governed by unified deflection system reflection rules |  
| Rebound scoring | A ball that rebounds off a boundary board cannot directly score — a player must touch it first |  
| Post / crossbar mechanic | Near-miss probability band on shots — if a shot probability check fails within a defined band just below the success threshold, the result is a post or crossbar hit; ball rebounds using same reflection rule as boundary rebound; exact band width to be defined during probability tuning |  
| Goal definition | Cols 6-10 on row 1 (and row 20 for opposite end); ball must cross end line within these columns without being a rebound to count as a goal |  
| Only restart | Kick-off after a goal is scored — the only dead ball situation in the game |  
| Variant — Wing Back | Full Back variant; same rules as Full Back except: CAN enter opposition attacking third (rows 14-20); all other Full Back restrictions remain (no central columns, max 2 horizontal squares per action, range 4) |  
| Variant — Sweeper Keeper | Ability only — not a movement variant; Sweeper Keeper is a GK ability, not a separate archetype with different movement rules |  
| Attribute system — universal | Every player has the same 6 attributes; values differ per player; no archetype-exclusive attributes; edge cases allowed (e.g. a CB with high Shooting) |  
| Attribute list | Pace / Passing / Control / Shooting / Defending / Goalkeeping |  
| Attribute scale | 1 to 10 |  
| Attribute to probability mapping | Rating 1 = -25% / Rating 5-6 = 0% (average) / Rating 10 = +25% / Linear scale (~5% per point) |  
| Attribute ranges — GK | Pace 2-5 / Passing 4-8 / Control 3-6 / Shooting 1-3 / Defending 3-6 / Goalkeeping 7-10 |  
| Attribute ranges — CB | Pace 3-6 / Passing 4-7 / Control 4-7 / Shooting 1-4 / Defending 7-10 / Goalkeeping 1-3 |  
| Attribute ranges — Full Back | Pace 5-8 / Passing 4-7 / Control 4-7 / Shooting 2-5 / Defending 6-9 / Goalkeeping 1-3 |  
| Attribute ranges — Midfielder | Pace 5-8 / Passing 6-9 / Control 6-9 / Shooting 4-8 / Defending 5-8 / Goalkeeping 1-3 |  
| Attribute ranges — Winger | Pace 7-10 / Passing 4-7 / Control 5-8 / Shooting 5-8 / Defending 2-5 / Goalkeeping 1-3 |  
| Attribute ranges — Striker | Pace 6-9 / Passing 4-7 / Control 6-9 / Shooting 7-10 / Defending 1-4 / Goalkeeping 1-3 |  
| Attribute ranges — soft guardrails | Ranges are typical, not hard caps — rare players can exceed or fall below typical range for their archetype |  
| Win condition | Most goals after fixed number of turns wins |  
| Turn count | Exact number parked for playtesting — to be decided once prototype exists |  
| Tiebreaker | Penalty shootout if scores level after all turns completed |  
| Forfeit rule | Forfeit at any point (including during shootout) = 3-0 defeat on record |  
| Penalty shootout — format | 3 kicks per side; then sudden death if still tied; sudden death continues indefinitely until a winner is found |  
| Penalty shootout — taker selection | Randomly selected from the 10 outfield players still on the pitch; GK excluded; no player selected twice until all 10 have taken a kick; substituted-off players removed from pool |  
| Penalty shootout — goal grid | 4 zones (2 wide x 2 high: left/right x top/bottom) |  
| Penalty shootout — decision mechanic | Simultaneous hidden selection — both players secretly pick their zone, then reveal together |  
| Penalty shootout — GK wrong zone | Base probability 85%; modified by Shooter Shooting (+/-25%) and Shooter Control (+/-15%) |  
| Penalty shootout — GK correct zone | Base probability 50%; modified by Shooter Shooting (+/-25%) and GK Goalkeeping (+/-15%) |  
| Penalty shootout — composure | Composure folds into existing attributes — Goalkeeping for GK, Control for shooter; no separate composure attribute needed |  
| Player identity | Fictional names, real football archetypes — winking tributes to real players, not legal copies |  
| Squad building model | Model 1 — fixed budget, pick from full player pool |  
| In-world currency | Rondos (R) |  
| Budget cap | R100m for 14 players |  
| Player tiers | 3 tiers — Standard (1 ability), Elite (2 abilities), Icon (3 abilities) |  
| Tier price bands | Standard: R3m–R7m / Elite: R8m–R14m / Icon: R15m–R25m |  
| Pricing within tiers | Attribute-driven — better attributes = higher price within tier band |  
| Abilities & price | More/better abilities = higher cost, reflected in tier and price band |  
| Positional requirements | Existing archetype limits only — no additional squad composition constraints |  
| Sub pricing | Same as starters — no discount |  
| Dribbling past a defender | Automatic tackle check triggered when dribbling player moves adjacent to or through a defender's square; success = loose ball; failure = dribbling player continues |  
| Skill ability interaction with dribbling | Skill ability bypasses the automatic tackle check entirely for one defender — no check triggered, dribbling player moves past freely |  
| Tackle range — standard | Adjacency only — tackling player must be adjacent to ball carrier; extended range exclusively via Last Ditch Tackle ability (CB and Full Back) |  
| Tackle outcome — Step 1 | Success = proceed to Step 2; Failure = ball carrier keeps possession, no loose ball |  
| Tackle outcome — Step 2 | Second probability check: Clean possession vs loose ball; Clean possession = tackling player gains ball immediately; Loose ball = ball lands in one of 2 squares on far side of tackling player, equal probability between the two |  
| Tackle outcome — Step 2 probability | Base 50%; tackling player's Defending attribute +/-25% |  
| Crossing mechanic | A cross is mechanically a pass into the box — no separate crossing action required; crossing flavour handled entirely by Whipped Cross and Pin Point Cross abilities |  
| Prototype approach | Digital from day one — browser-based web app (HTML/CSS/JavaScript) |  
| Tech stack | Claude writes code → VSCode (workbench) → GitHub (version control) → open in browser |  
| Prototype format | Interactive board — two human players (or solo both sides); no AI opponent in Milestone 1 |  
| Milestone 1 scope | 15x20 grid / both teams in 4-4-2 / click to move / movement rules enforced / pass + shoot + tackle with probability checks / turn tracker (3 actions) / score tracker / ball states |  
| Milestone 1 excludes | Special abilities / squad builder / player cards / AI opponent — all deferred to later milestones |  
| First build | index.html — working prototype; pitch renders, pieces placed, actions functional, probability checks live, score + turn tracking working |  
| GitHub repository | https://github.com/themashugana/Rondogo |  
| Formation starting positions — 4-4-2 | GK: col 8 row 2 / CBs: cols 5+11 row 5 / FBs: cols 2+14 row 5 / MFs: cols 3+6+10+13 row 8 / STs: cols 5+11 row 9 — Team B mirrors row only (row = 21 - row); columns unchanged |  

---

## Build Phases

### Phase 1 — Concept Bible (COMPLETE ✅)  
Fully document every game system before building anything.

- [x] Core concept defined  
- [x] Player archetypes outlined  
- [x] Variant system established  
- [x] Grid & board design  
- [x] Turn structure & actions  
- [x] Movement rules per archetype  
- [x] Dribble range  
- [x] Movement freedom (free roam / Chebyshev) & directional restrictions  
- [x] Pass mechanics (range, lanes, difficulty factors)  
- [x] Shoot mechanics (range, zone probability, difficulty factors, GK interaction)  
- [x] Contested action / probability system — base numbers, attribute modifiers, pass situational modifiers  
- [x] Shoot probability modifiers (situational)  
- [x] Tackle probability modifiers (situational)  
- [x] Defensive zone / blocking rules (Abalone influence)  
- [x] Formation & squad building rules — formations, squad size, substitutes, archetype limits, starting positions  
- [x] Special abilities per archetype (COMPLETE — all 6 pools locked)  
- [x] Replacement abilities for Set Piece Threat slots (COMPLETE)  
- [x] Dead ball & rebound system (COMPLETE)  
- [x] Unified deflection system (COMPLETE)  
- [x] Variant definitions (COMPLETE — Wing Back locked; Sweeper Keeper ability only)  
- [x] Attribute system (COMPLETE — 6 universal attributes, 1-10 scale, archetype ranges, probability mapping)  
- [x] Win conditions & edge cases (COMPLETE — fixed turns, penalty shootout, forfeit rule)  
- [x] Player identity & fantasy squad building (COMPLETE — fictional players, Model 1 budget system, Rondos currency, 3 tiers)  
- [x] Tackle & dispossession system (COMPLETE — two-step outcome chain, dribbling past defenders, clean possession probability)  
- [x] Crossing, curl & curved ball path mechanics (COMPLETE — crossing = pass into box; Curl/Whipped Cross/Pin Point Cross updated; curved L-path mechanic; lofted ball rule; Through Ball + Curl combination)  

### Phase 2 — Build Strategy (IN PROGRESS 🔄)  
Claude + Google tools build plan for a non-technical founder.  
- [x] Prototype approach chosen — digital, browser-based
- [x] Tech stack decided — HTML/CSS/JS via Claude + VSCode + GitHub
- [x] First playable milestone defined — Milestone 1 scoped
- [x] First build delivered — index.html working in browser
- [x] GitHub repository created and connected — https://github.com/themashugana/Rondogo
- [x] Formation positions corrected — teams now in correct halves, mirror formula fixed
- [x] Player highlight on select fixed — cell highlights immediately on click
- [ ] Formation positions visually confirmed in browser
- [ ] Guided turn walkthrough completed
- [ ] Milestone 1 fully playable and testable

### Phase 3 — Prototype  
- [ ] Not started

---

## Current Session Focus  
**Session 18 — Phase 2: Prototype Fixes**

Fixed two known bugs: formation starting positions (row orientation + mirror formula) and player highlight on click. GitHub repository created and first commit pushed.

**Next Session Should Start With:**  
- Confirm formation fix looks correct in browser (screenshot)
- Do guided walkthrough of a full turn to identify any further bugs
- Begin structured playtesting once fixes confirmed

---

## Open Questions (Parking Lot)  
- All movement ranges and probability numbers subject to playtesting — may need tuning once prototype exists.  
- **Ability limit mechanics** — active once per turn is current default; discuss whether recharge mechanics, per-game limits, or other systems should exist alongside or instead. Decide before closing abilities session.  
- **Five-a-side variant** — a smaller, faster format for quick games. Revisit when core 11v11 game is fully designed and in prototype.  
- **Puzzle mode** — situational chess-puzzle-style challenges built from real game positions. Revisit when core mechanics and prototype are established.  
- **AI difficulty levels** — tiered AI opponents (e.g. Beginner / Semi-Pro / Professional) for single player mode. Revisit in Build Strategy / Phase 2 session.  
- **Post/crossbar near-miss band** — exact probability width to be defined during playtesting / probability tuning session.  
- **Defender block clean possession threshold** — exact probability margin to be defined during probability tuning session.  
- **GK hold/parry probability base number and modifiers** — to be defined during probability tuning session.  
- **Turn count per game** — exact number to be decided during playtesting; informed by both 11v11 and five-a-side feel.  
- **Exact pricing formula within tiers** — attribute weighting for price calculation to be defined during prototype tuning.  
- **Model 2 / collectible layer** — budget system (Model 1) is the starting point; collectible card layer to be revisited once prototype exists and commercial direction is clearer.  
- **Prototype look and feel** — aesthetic decisions (colours, pitch markings, piece design) deliberately deferred; get it working first, pretty second.  

---

## Session Log

| Session | Date | What Was Covered | Key Decisions |  
|---|---|---|---|  
| 1 | 2026-04-20 | Core concept, archetypes, variants, probability system, inspirations | All decisions in table rows 1-12 |  
| 2 | 2026-04-20 | Grid & board design | Grid 15x20, zone structure, square grid 8-direction movement |  
| 3 | 2026-04-20 | Turn structure & actions | 3 actions/turn, different player per action, action vocabulary, ball states |  
| 4 | 2026-04-20 | Movement rules per archetype | Hard rules, range + directional restrictions for all 6 archetypes |  
| 5 | 2026-04-20 | Dribble range, movement freedom & Full Back restriction | Dribble range = move range; free roam (Chebyshev); Full Back max 2 horizontal per action; Burst ability concept confirmed |  
| 6 | 2026-04-20 | Pass mechanics | Hybrid probability philosophy; pass ranges per archetype; Option C passing lanes; pass difficulty factors; through ball ability concept |  
| 7 | 2026-04-20 | Shoot mechanics | Shot ranges per archetype (real football logic); zone-based probability bands; shot difficulty modifiers; passive GK interaction; curl ability concept noted; edge cases parked |  
| 8 | 2026-04-20 | Contested action / probability system | Option C % system confirmed; base probabilities set (pass 65%, shoot 50%, tackle 45%); attribute modifier ranges set (+/-25% / +/-15% receiver); full passing modifier stack completed |  
| 9 | 2026-04-20 | Shoot & tackle modifiers + defensive zone / blocking rules | Full shoot modifier stack completed; full tackle modifier stack completed; Pressured Squares named mechanic defined; Partial Pressure and Fully Trapped states defined |  
| 10 | 2026-04-20 | Formation & squad building rules (complete) | Fixed preset formations confirmed; two-layer system locked; master role menu locked; all 10 formations mapped; squad size 14 (11+3); 3 sub moments; archetype limits set; starting positions fixed per formation |  
| 11 | 2026-04-20 | Special abilities — all six pools complete | Philosophy locked; all 6 archetype pools designed and locked; Burst universal across all archetypes; Skill shared across Midfielder/Winger/Striker; One-Two shared across Midfielder/Winger; Curl shared across Winger/Striker; ability limit mechanics added to parking lot; Set Pieces added as dedicated Concept Bible session |  
| 12 | 2026-04-20 | Dead ball & rebound system | Set pieces removed entirely; fouls removed; ball never goes out of play; board rebound system adopted; goal defined as cols 6-10; post/crossbar near-miss probability band mechanic defined; only restart is kick-off after goal; Set Piece Threat ability slots marked for replacement |  
| 13 | 2026-04-20 | Unified deflection system & replacement abilities | Hybrid deflection system designed and locked (deterministic: boundary/post/crossbar; probabilistic: GK save, defender block, failed tackle); all 5 replacement abilities locked (CB: Intercept, Full Back: Recover, Midfielder: Dummy Run, Winger: Press High, Striker: Drop Deep) |  
| 14 | 2026-04-20 | Variants, attributes, win conditions & edge cases | Wing Back variant locked; Sweeper Keeper confirmed as ability only; 6 universal attributes defined (Pace, Passing, Control, Shooting, Defending, Goalkeeping); 1-10 scale; archetype ranges set; probability mapping locked; win condition = fixed turns; penalty shootout tiebreaker fully designed; forfeit = 3-0 defeat; Phase 1 COMPLETE |  
| 15 | 2026-04-20 | Player identity & fantasy squad building | Fictional-but-inspired player identity locked; Model 1 budget system designed; currency = Rondos (R); budget cap R100m; 3 tiers (Standard/Elite/Icon); tier price bands set; attribute-driven pricing within tiers; GK limit updated to max 1; all Phase 1 parking lot items resolved |  
| 16 | 2026-04-20 | Tackle & dispossession, crossing, curl & curved ball path | Tackle two-step outcome chain locked; dribbling past defenders locked; tackle range locked; crossing confirmed as pass into box (no separate mechanic); Curl updated for Winger/Striker/Midfielder; Whipped Cross shared Full Back + Winger; curved L-path mechanic locked (+2 range boost); lofted ball rule locked (3 square threshold); Through Ball + Curl combination locked; Phase 1 fully complete |  
| 17 | 2026-04-20 | Phase 2: Build Strategy + First Prototype Build | Prototype approach locked (digital, browser-based); tech stack locked (Claude + VSCode + GitHub); Milestone 1 scoped; first working build delivered (index.html); formations and usability fixes identified for next session |  
| 18 | 2026-04-21 | Phase 2: Prototype fixes — formation positions + highlight bug | Formation mirror formula fixed (row-only mirror, columns unchanged); 4-4-2 starting positions corrected; player highlight-on-click fixed; GitHub repo created (themashugana/Rondogo) and first commit pushed; formation fix pending visual confirmation |  

*Last updated: Session 18 — 2026-04-21*
