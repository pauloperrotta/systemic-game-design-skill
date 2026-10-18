# The systems model of a game, vision and analysis (chs. 3, 5 and 6)

Read this to ANALYZE an existing game (7-step checklist: whole → loops → parts), to understand the systems model of a game (tokens and rules, meaningful decisions, sources of opposition, types of goals, content vs. systems, theme), the five qualities of a good system, and to work on the desired experience and the concept document (fantasy, key moments, One Question, audience and motivations).

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). The book section each block comes from is given in brackets.

## Index
- 3. CH. 3 - Game fundamentals and game design
- 4. DERIVED DESIGN / ANALYSIS / BALANCE CHECKLISTS
- 5. QUICK GLOSSARY (English -> idea)
- CHAPTER 5 — Working as a systems designer
- 1. How to start ("How Do You Even Start?")
- 2. Know your strengths, work on your weaknesses ("Know Your Strengths, Work to Your Weaknesses")
- 3. Qualities of game systems ("Qualities of Game Systems", Achterman 2011)
- 4. Tabletop vs. digital games ("Tabletop and Digital Games")
- 5. The process of designing games as systems ("The Process of Designing Games as Systems")
- 6. METHOD: analyzing games from a systems view ("Analyzing Games from a Systems View")
- 7. Prototyping and playtesting ("Prototyping and Playtesting")
- 8. Chapter 5 summary
- CHAPTER 6 — Designing the total experience
- 9. The big idea ("What's the Big Idea?")
- 10. The desired experience ("The Desired Experience")
- 11. The concept document ("The Concept Document")
- 12. Designing the game+player system ("Designing the Game+Player System")
- 13. Questions to consider about your design vision ("Questions to Consider About Your Design Vision")
- 14. Chapter 6 summary
- APPENDIX: Quick-use lists (for designing / analyzing / balancing)
- A. Design checklist by level
- B. Problem signals (detection)
- C. Games cited (one line each)
- D. Key terms (EN) for quick lookup

---

## 3. CH. 3 - Game fundamentals and game design

### 3.1 Definitions of "game" [What's a Game?]
| Author | Key idea |
|---|---|
| Huizinga (Homo Ludens, 1938) | Play is absorbing, "not serious", outside ordinary life, with no material interest, within its own limits of time/space and with fixed rules -> **magic circle**. |
| Caillois (Man, Play, and Games, 1961) | Separate from reality, neither obligatory nor profitable, governed by internal rules, with **uncertainty** (the course depends on choices). **Four types:** **agon** (competition), **alea** (chance), **mimicry** (role-playing), **ilinx** (altered perception/vertigo). Spectrum from **ludus** (rule-bound, sport-like) <-> **paidia** (spontaneous, childlike play). |
| Crawford (1984) | Four factors: **representation, interaction, conflict, safety**. A game = a closed formal system that subjectively represents a subset of reality; explicit rules; the player "creates their story" by choosing; goals and obstacles; conflict and danger without physical consequences. |
| Dewey | Play keeps its "freedom from subordination to an end imposed by external necessity"; if it is tied too closely to an external need, it stops being experienced as play. |
| Sid Meier | "A series of interesting choices" (useful because it demands meaningful, informed decisions; caveat: education and relationships are also that, and they are not games). |
| Costikyan (1994) | An art form in which participants make **decisions to manage resources through tokens in pursuit of a goal**. It is not a puzzle (static), nor a toy (no goal), nor a story (linear); art is passive, a game demands active participation. |
| McGonigal (2011) | Four traits: **goal, rules, feedback system, voluntary participation**. |
| Salen & Zimmerman (2003) | "A system in which players engage in an artificial conflict, defined by rules, that results in a quantifiable outcome." |
| Juul | Component: **valorization of outcome** (some outcomes are better than others, encoded in the rules). |
| Wittgenstein | Don't look for a definition common to all games: there is a "network of overlapping similarities" (family resemblance). |

Common elements (Summing Up Game Definitions):
- An experience in its own context, separate from the rest (magic circle).
- Its own rules (formal = ludus; tacit/dynamic = paidia).
- Voluntary, participatory interaction (not just watching).
- Meaningful goals, choices and conflict.
- Ends with a recognizable (valorized) outcome.
- As a design product: concrete parts implemented in some technology, loops arising from the interaction of behaviors, and all of it experiential (dynamic/dramatic) when played with the player.
- Exceptions: real-money poker (porous circle); endless MMOs; not all games have conflict. These are typical characteristics, not prescriptive ones.

### 3.2 Game frameworks [Game Frameworks]
**MDA (Mechanics-Dynamics-Aesthetics, Hunicke et al. 2004):**
- **Mechanics:** the game's components at the level of data and algorithms.
- **Dynamics:** the run-time behavior of the mechanics acting on each other's inputs and outputs over time.
- **Aesthetics:** the emotional responses desired in the player.
- Reading: the **player** sees aesthetics first -> dynamics -> mechanics; the **designer** sees mechanics -> dynamics -> aesthetics. The aim is for the designer to think about aesthetics first (in practice each designer starts wherever they want).
- Key point: **only the mechanics are under the designer's direct control**; the dynamics are prepared indirectly (this anticipates second-order design).
- Criticisms: "mechanics" is used elastically (from "jump"/"play a card" to loops like the blue shell: a matter of "chunk size"); "aesthetics" gets confused with the visual and distracts toward look & feel instead of the total experience.

**FBS (Function-Behavior-Structure, Gero 1990):** Function (purpose/why it was designed), Behavior (attributes and actions derived from the structure that achieve the function; can change over time), Structure (physical parts and relationships; topology/geometry/material; does not change). **SBF** (Goel et al.) inverts it, bottom-up: components and actions -> states and transitions -> functional schemas. A bridge between MDA and the systems view; little used in games.
- The author's message: other ad hoc frameworks are valid if they work for you; the systems approach complements them.

### 3.3 Systems model of games [A Systemic Model of Games] - THE CORE MODEL
Descriptive, not prescriptive; "a scaffold, not a straitjacket".

**Top level:** the game-as-played = a **game + player(s)** system, two subsystems (Fig. 3.1). Without a human player the game has no utility and no gameplay.

Three levels of components in the game subsystem (mapping directly to parts -> loops -> whole):
1. **Structural (Parts):** **tokens and rules** = "nouns and verbs".
2. **Functional (Loops):** "sentences" built from nouns and verbs; what we call "the game's systems"; internal model of reality, play space, uncertainty, mental model, meaningful decisions, opposition, goals.
3. **Architectural and thematic (Whole):** the internal (developers) and external (player) faces of the same whole.

Gameplay = the game's overall purpose and action, communicated as an emergent effect of the four kinds of elements (structural, functional, architectural, thematic).

**The player as part of the larger system:** can have an explicit avatar, an aggregate avatar (a ship with captain, crew, cannons) or be invisible (the "invisible hand" of a village/empire). Point: both (player and game) model each other: the game represents the player in its model; the player builds a mental model of the game (co-representation).

### 3.4 Structural parts: tokens [Structural Parts of a Game / Tokens]
- Tokens = representative objects that denote aspects of game state; they have no meaning by themselves outside the game; they communicate state and changes between game and player.
- Degrees of representation: highly conceptual (Go stones), semi-representational (chess pieces of nobility), detailed (RPG weapons/armor).
- No game represents the whole world: "a 1:1 scale map is useless"; total verisimilitude takes you out of the magic circle.
- Tokens are the **nouns**: (1) the representation of the player; (2) independent units that act on their own or are used by the player; (3) the world (divisions with state: chess squares, terrain); (4) resources (money in Monopoly; wheat, sheep and wood in Catan); (5) non-material objects (the **turn**, how many cards are in hand, how many items are carried, how many dice).
- **Rule:** everything that has state and behavior in the game must be represented by a token or an aggregate of tokens.
- Tokens are symbolic but **precise**: state and behavior are always defined (the piece is on one and only one square). Every concept (does it fly? are there mountains?) must be specified in tokens and rules.

### 3.5 Structural parts: rules [Rules]
- Rules = specification of processes; **the verbs**: they define the behavior of tokens.
- Functions of rules (the author's list):
  1. **Specify acceptable actions within the game:** they create the play space where you act differently (lying in The Resistance, stealing in EVE Online); we accept being inefficient (not grabbing the king in chess, not checking the deck).
  2. **Specify how the world works:** allowed states, how they change, how you progress, obstacles, conflict resolution, endings (win/lose), topology (grid, sphere, impossible worlds like Monument Valley, Antichamber), structure of pieces (cards in hand, starting workers), universal rules ("infinite fall without damage", "gravity changes every 30 s").
  3. **Preserve player agency:** rules must allow different paths/goals/styles; if they restrict too much, the decision space collapses to a few options or just one and the player goes from participant to observer.
- **Heuristic for the number of rules:** the minimum number of rules that defines the game space well. Too few -> ambiguity, the player cannot build/navigate a mental model. Too many -> constrained agency, engagement evaporates.
- **Avoid exceptions to the rules:** arbitrary rules or rules with exceptions overload the mental model (the opposite of elegance). Examples: a six-sided die that is normally a "good result" except in cases where it is bad; in digital, one click = jump and double click = drop everything you carry (actions that are cognitively and physically similar should have similar results).
- **Game mechanics:** **semantically viable** combinations of tokens and rules (short sentences: "when you pass Go you collect $200"); complex ones are combinations of simple ones. A precise definition is not the goal; the author anchors them in systems terms.

### 3.6 Games and metagames [Games and Metagames]
- The magic circle is defined by tokens and rules; in general what happens in one match does not carry over to the next (Monopoly).
- **Metagaming:** applying tokens or rules across matches: house rules (Free Parking), advantages for newcomers, **legacy** games (the events of one match alter the next), tit-for-tat based on earlier matches. It crosses the magic circle.
- Game theory has almost nothing to do with design; it is economics/mathematics. **Repeated games** (e.g. repeated rock-paper-scissors) do show that the metagame can end up subsumed into the game.

### 3.7 Functional aspects [Functional Aspects of a Game]
- These are the assemblies with loops (economies, characters, empires). Criterion: anything that completes the sentence **"in this game, the player is a..."** (pirate, pilot, florist, emperor) or that is an important part of reaching a goal.
- Everything must reduce to tokens and rules, but the designer spends a lot of time organizing parts into **operating subsystems** that support the experience.
- **Creating possibilities for play:** the economy/character/empire is not coded directly, only its *possibilities*; the game must offer scaffolding for those structures to emerge and change during play.
- **Nested "machines" (Ellenor):** a functional component is "a machine that does X" (weather, an email on completing a quest); simple machines inside more complex ones, hierarchically down to tokens and rules; this avoids monolithic machines.

**Internal model of reality:**
- Every game is a "pocket universe" with its own laws; abstract (Chess/Go) or detailed (RPG/strategy). Koster: games are abstract and iconic and exclude distracting details.
- **Endogenous meaning (Costikyan):** tokens and rules mean something only through their function within the game ($1,000 in Monopoly).
- **Warning:** more realism/complexity does not make a better game. If the model is so complex, variable or unpredictable that the player cannot form an effective mental model, it is an interesting simulation but not a fun game.

**Second-order design (Salen & Zimmerman):** two meanings:
1. Tokens and rules specify a **state-space** with many paths, not a single path (first order = the same experience for everyone). A single path = narration (book/movie); the player stays passive. The player knows there were other paths even if not all are equally good.
2. Designing tokens and rules to form dynamic systems is **enabling emergence**: the mechanics are designed directly; the dynamics arise in play. The player's experience cannot be mapped to a part or sum of parts, and may be unpredictable to the designer.

**Dwarf Fortress - the cat deaths:** cats die of intoxication: they hunt rats in the tavern, wine spilled by dwarves sticks to them, they groom themselves (only cats and red pandas do), and the alcohol's effect scales with body size -> they die. Nobody designed this; it emerges from several systems (drinking, splashing, size, self-grooming). It illustrates procedural play, extreme systemic play and unplanned emergence (and incidentally that systems interact in ways the designer doesn't foresee: you have to test, not just specify).

**Uncertainty and chance:** every game presents uncertainty; not all use randomness. Chess/Go: the uncertainty comes from not knowing what the other will do. Most have randomness, seen as a counterweight to developed skill. Types of randomness: uniform (1-100 with equal probability) or weighted (bell curve).
- **Rule:** the more deterministic the world, the more is known in advance; the more is known, the more the space collapses to a single path and the player loses decisions. E.g. memorized chess openings; the game stays interesting because players recombine "chunks" (subsystems of pieces and positions) in new ways.

**Player's mental model:**
- The player builds it by interacting with tokens, rules and functional elements. It is not part of the game, but the game must support building it.
- Easier to build and more consistent with the designer's model -> more engagement. Incomplete or inconsistent rules -> the game fails or demands a lot of cognitive resources (limits the audience).
- "Easy to build" is not "simple": Tic-Tac-Toe has a simple model but gets tiring fast (no chance, no systemic depth, no mutual uncertainty). Go or Stellaris require effort, but being systemic they have few inconsistencies and reward you with more capability as the model grows = an **exploration reinforcing loop** (learning -> power -> more exploration).

### 3.8 Meaningful decisions, opposition and goals

**Meaningful decisions:**
- They require **uncertainty** (in the player's mental model and normally in the world). Without it there is no decision.
- Three situations: **no decisions** (passive player, the play experience collapses), **ineffective/illusory decisions** (two doors that lead to the same place = the same as not choosing), and **decisions that lead to change**.
- Practical definition: a decision is meaningful if it affects the state of the player or the world in a discernible way and **opens or closes** opportunities for later exploration and decisions. For the player: if they believe the outcome brings them closer to or further from what they want.

**Opposition and conflict:** without opposition the goal is reached effortlessly (pick up the king and say "I won"). Four sources of opposition:
1. **The rules** (movement limits, limits on actions per resource, impassable terrain). They must feel like a natural part of the world; the more arbitrary they are, the more the player thinks about how to play instead of playing.
2. **Active opponents** (agents with agency: from anonymous goblins to an elaborate nemesis).
3. **Other players** (directly or indirectly: winning, score).
4. **The player themselves** (limited resources: troops now vs. upgrading barracks for later; trade-offs because you can't do everything at once).

**Player goals:** without a goal no choice is better than another: there is no intent or meaning; the player "drifts".
- **Explicit goals:** provided by the designer (win, "finish the level"); they answer "how do you win?". They serve as training wheels for building the mental model.
- **Implicit goals:** created by the player once their mental model is sufficient ("finish without killing anyone"). They can be combined with optional achievements (e.g. "pacifist") that encourage self-set goals and improve retention.
- **Games with only explicit goals:** shorter lifespan and lower replayability; they bound the possible goals; they reduce state space, decisions and engagement (the illusion of agency remains until it is seen through).
- Goals arise from endogenous meaning + mental model; without them the player wanders.

**Types of goals (by duration/frequency and motivation):**
1. **Instant:** actions with immediate timing (jumping at the right moment, grabbing the rope, blocking a shot).
2. **Short term:** a puzzle, killing a monster, using a tactic, leveling up; cognitive, they include several instant goals.
3. **Long term:** strategic (defeating a strong opponent, a complete set, a skill tree, an empire); the backbone of long-term engagement; they contain short-term goals, which contain instant ones. This **goal hierarchy** should be evident and is a source of satisfaction.
4. **Social:** relationships with other players (inclusion, status, cooperation, competition); they leak outside the game (porous circle).
5. **Emotional:** the designer usually doesn't think about them explicitly but they "should be among the first considered"; emotional resolution (Gone Home, Road Not Taken, Undertale); they matter more for enjoyment than cognitive ones even though the player doesn't consciously think about them.

### 3.9 Architecture and theme [Architecture and Thematic Elements]
Architecture and theme = two faces of the same whole: **architecture = inward-facing (developers)**, **theme = outward-facing (player)**.

**Architectural** elements:
- Balance of content and systems.
- Mechanical/technical components of the narrative structure.
- Interface organization (UX, the technical side of how the player interacts).
- Technology platform (digital or tabletop).

**Thematic** elements:
- How content and systems support the player's interactivity and goals, particularly the **autotelic** ones.
- Narrative content (if any).
- Look and feel of the interface ("juiciness"): the pleasure of seeing/operating it in itself.

**Content vs. systems [Content and Systems]:** all games have both; the question is which one the core gameplay depends on mainly. (Complicated = sequence without loops; complex = loops.)

**Content-driven games:**
- Content = locations, objects and events that the designer develops and assembles (levels/missions with exact placement and timing).
- Linear game; explicit goals, clear opposition along the way, decisions predetermined in opportunity and outcome. Replaying doesn't change the essentials (only implicit goals like "best time").
- **Little emergence**: designers avoid it because it is unpredictable, untestable and risky.
- **Content treadmill:** players consume content faster than it is created; each new piece is more expensive; huge teams; risk of little innovation. Pro: more predictable development.
- If the new content doesn't change tokens/rules (parts, states, possible behaviors), the player notices there is nothing new to learn or master and gets bored. Example: **reskins** (changing the context/art from medieval to sci-fi) excite at first and wear out fast.

**Systemic games:**
- They use complex interactions (loops) between parts to create world, opposition, decisions and goals; the designer doesn't author the experience but the conditions; the path changes in every match -> freshness and replayability.
- Example by Daniel Cook, Steambirds: Survival: when it wasn't engaging they added **systems** (downed planes drop power-ups) instead of scenarios with triggers: "do I go for the heal or turn toward the Dart at 6 o'clock?" is a meaningful decision driven by systems, not an "authored cheap thrill".
- Even with an overall explicit goal (Civilization: conquer the world; FTL: destroy the mothership), the player creates their route; uncertainty and combinations keep the space from collapsing into a single optimal path. It's not all random: it's systemic (a desert with random cacti, but no polar bears).
- **Balance:** they are not mutually exclusive; systemic games need some content and explicit goals; linear ones have subsystems (economy, combat) in a linear context. The book bets on designing systemic games using linear elements when appropriate. Trend: games becoming more *complex* and not just more *complicated*.

**Autotelic experience:** an experience with purpose in itself, not dependent on an external goal or need. The player creates implicit goals out of their own motivation and the actions have intrinsic value.
- Play is separate, inconsequential and voluntary but has to be satisfying in itself (Dewey).
- **"Gamification" fails** when the experience is subordinated to an external end: it looks like a game but isn't one.
- Explicit goals serve for learning; chaining them indefinitely produces **"the grind"** (quest after quest for an external reward, like a job; it also depends on expensive, ephemeral content rather than "evergreen" systems).
- Long-lived games (Chess, Go, Civilization) allow intrinsic implicit goals; the support is the thematic and systemic elements.

**Narrative [Narrative]:** an account of individuals living through a series of connected events with meaning; both (events and individuals) matter. A bridge between architecture (how it is assembled from the functional) and theme (how it informs the player what it's about).
- It can be the focus or just the **premise** (why the world is the way it is and what the goals are). It also works as a reward (expository cut-scenes).
- **Story-driven games:** more care with content than with systems; opposition, goals and decision points defined by the designer; low replayability. **Central tension:** steering toward the story (narrows the space to a single path; passive player) vs. leaving it free (the story and the expensive content may be missed, and the theme may not be communicated).
- Example: Knights of the Old Republic (light/dark side; few endings because multiple endings are very expensive -> narrowing of paths).
- **Systemic game with a premise:** the designer sets forms of opposition; the player's decisions and chance determine when/how they are faced; Terraria (minimal premise), Sid Meier's Pirates! (basic narrative, optional goals). The narrative is not written, it is lived.

**Theme, experience and meaning [Theme, Experience, and Meaning]:**
- Theme = what the game is about; the player's side of the whole; context for their mental model, decisions and goals. The player interprets tokens and rules in light of the theme.
- If everything (structure, function, architecture, theme) combines as a system, game + player create **meaning** (a property of the player+game system).
- The theme doesn't need to be deep, but it must be **consistent** with structure and function and must drive the player (Minecraft: open exploration and crafting, enough).
- Examples of failure:
  - **No Man's Sky:** a technically deep world but with no explicit goals and no possibility of implicit goals; without a theme -> no meaningful decisions or intrinsic goals -> it falls flat (it lacks top-down design causality and no theme emerges through bottom-up causality).
  - **Splendor:** beautiful with appealing mechanics, but the theme (gem merchant) barely connects to the abstract tokens and rules; anyone who doesn't fall in love with the mechanics themselves loses interest.
- Future: games with a wide, deep play space, with strong narratives that don't steer too much nor leave the player stranded in a themeless space.

### 3.10 Evolution of design [The Evolution of Game Design] (only the useful part)
- Senet (~5,000 years). Design as a recognized discipline since ~the 1980s (Crawford, The Art of Computer Game Design, 1984; Journal of Computer Game Design; first conference in 1988).
- Designers historically came from other fields or were players; the best way to learn is still to **design, develop, test and ship** (learning by practice); game design theory has only been accumulating since ~2010. **Game theory ≠ game design theory.**

### 3.11 Chapter 3 summary (from the author)
- Games happen in a separate, consequence-free context (magic circle) expressed by tokens and rules; play is voluntary and requires participation; they provide a defined world, meaningful decisions, opposition, interaction and different types of goals.
- Systems view: **Structures** (tokens and rules), **Functional elements** (the loops/"sentences" that give the second-order world model, mental model, decisions and goals), **Architecture and theme** (the whole: balance of content/systems, narrative, experience).


## 4. DERIVED DESIGN / ANALYSIS / BALANCE CHECKLISTS

### 4.1 Questions for analyzing a game or a system (derived from chs. 2-3)
Parts
- What are the parts? For each one: what attributes/state does it have (with "spreadsheet" values), what limits it/what interacts with it, what behaviors does it have and what resource do they move?
- Does each part decide its own state (encapsulation) or are there "outside hands" modifying it?
- Where are the sources, stocks, sinks? What caps do the stocks have? What converters/deciders are there?
Loops
- What reinforcing loops are there (which is the main one?) and what balancing loops contain them? For each reinforcing loop: what is its limiting condition (S-curve)?
- Are there delays between actions and consequences (possible fixes that fail)?
- Are there shared resources with multiple consumers (tragedy of the commons)?
- Is there a snowball for whoever is winning? Is there a catch-up mechanism (blue-shell type)? Which one dominates? Is there a risk of a death spiral (negative reinforcement)?
- Which effects are nonlinear? Would you expect oscillation (predator-prey)?
- Is there a risk of resonance (many small events that reinforce each other)?
Emergence and levels
- What emerges that is not in any single part? Test: is it not determined by one part? Is it not a linear sum? Is it better described in aggregate?
- What levels of organization are there (parts that are subsystems)? Are they self-similar (a learning scaffold)?
- Is there downward causality (global state affecting local decisions)?
Game
- Is it content or systems that sustains the gameplay? How much of the replay value depends on new content?
- Is there a state space with multiple paths (second order) or a single path?
- For each decision: is there uncertainty? Does it open/close options? Or is it illusory?
- What sources of opposition are there (rules, opponents, other players, the player themselves/trade-offs)?
- What goals are there by type (instant, short, long, social, emotional; explicit and implicit)? Are they nested in a hierarchy?
- Does it rely on autotelic goals or on grind with external reward?
- Is the theme consistent with structure and function?

### 4.2 Problem signals (and how to detect them)
- **Rules with exceptions / arbitrary rules** -> the player thinks about the rules instead of playing; high cognitive load. Detect: tables of "special cases", the same input with different meanings.
- **Too many rules** -> constrained agency. **Too few** -> ambiguity; no mental model gets built.
- **Illusory decisions** (all lead to the same outcome) -> equivalent to not choosing.
- **A single optimal path** (state space collapsed by known determinism) -> no decisions.
- **New content that doesn't change tokens/rules** (reskin) -> fast burnout.
- **Content treadmill:** consumption outpaces production; the cost per hour of play grows.
- **Inflation / accumulation** in faucet/drain economies without enough sinks or without caps on stocks.
- **Snowball without catch-up** -> matches decided early; **excessive catch-up** -> effort is not rewarded (an inference from the reinforcing/balancing pair).
- **Expected linear growth** of something that has a limiting condition -> false predictions.
- **Reward exploit** (cobra effect): players optimize the reward metric in a way that breaks the objective.
- **Excessive realistic complexity:** more simulation is not more fun; if the player cannot model it mentally, it fails.
- **Theme disconnected from the mechanics** (Splendor) or **without goals** (No Man's Sky).
- **Gamification/grind:** external goals that turn the game into work.
- **Untested emergence:** effects like the Dwarf Fortress cats; the interaction of subsystems produces unforeseen situations -> you need simulation/telemetry, not just specification.
- **Unnecessary central controller:** if something "steers" the system, emergence is probably being lost.

### 4.3 Practical rules / heuristics (pocket summary)
1. Design rules and parts, not linear experiences (second order): only the mechanics are directly under your control; the dynamics emerge.
2. Every system has a reinforcing loop and a balancing loop; if there is only reinforcement, look for when it blows up; if there is only balance, look for why it doesn't advance.
3. For each reinforcing loop, explicitly design its limit (S-curve) or prepare for collapse.
4. For each resource: list sources and sinks and set caps. Check for inflation.
5. Prefer parameters that emerge from internal states (attack vs. defense) instead of opaque global knobs; but you bottom out in spreadsheet values.
6. Use randomness as a stand-in for what you don't model and for variability, not as a replacement for decisions.
7. Keep the mental model buildable: few special cases, consistency between similar actions.
8. Depth through hierarchy and self-similarity (Go): few rules, subsystems that resemble the ones above them.
9. Goals: explicit to teach; enable implicit/autotelic ones for longevity; hierarchy instant->short->long; don't forget the emotional ones.
10. Content and systems are balanced: systems give replayability; content gives polish; avoid depending only on the latter.
11. A theme that is coherent and consistent with the mechanics (even if simple) so that meaning is generated.
12. Test the system in operation: systems are understood by experiencing them (simulating/playing), not by reading rules.

---------------------------------------------------------------------
## 5. QUICK GLOSSARY (English -> idea)
- Metacognition: thinking about thinking.
- Phenomenological / reductionist / holistic / systemic thinking: four modes of thinking.
- Greedy reductionism: believing the whole is just the sum of its parts.
- Metastability: stable at one level, changing inside.
- Synergy: the whole is not predictable from the parts.
- Part = state + boundaries + behaviors.
- Spreadsheet-specific: the level of detail that can be implemented.
- Encapsulation: each part controls its own state.
- Source / stock / sink / flow / resource / converter / decider.
- Faucet/drain economy.
- Simple collection / complicated process / complex system.
- Reinforcing (positive) vs balancing (negative) loop; snowball; vicious cycle.
- Nonlinearity; Lotka-Volterra; knobs.
- Random vs chaotic; resonance event.
- Fixes that fail / unintended consequences loop; limits to growth (S-curve); tragedy of the commons; trophic cascade; engine (build now vs invest).
- Emergence; upward / downward causality.
- Levels of organization / integrative levels; persistence; adaptability; homeostasis; structural coupling.
- Depth; self-similarity; elegance; Bushnell's Law.
- Game+player system; magic circle; ludus/paidia; agon/alea/mimicry/ilinx.
- MDA; FBS/SBF.
- Tokens (nouns) / rules (verbs) / mechanics (viable token+rule combos).
- Metagame; legacy game.
- Internal model of reality; endogenous meaning; second-order design; state-space.
- Mental model; meaningful decisions; opposition (rules, opponents, other players, self).
- Explicit vs implicit goals; instant/short/long/social/emotional goals.
- Architecture (inward) vs theme (outward); content-driven vs systemic; content treadmill; reskin.
- Autotelic experience; the grind; gamification.
- Narrative; story-driven games; premise.

---

# CHAPTER 5 — Working as a systems designer

## 1. How to start ("How Do You Even Start?")

- Starting is hard because the problem seems to offer no handholds. Designers have historically "jumped into the pool". Failing a lot is normal (example: Rovio made 51 attempts before Angry Birds). Seeing the game as a system of systems reduces the number and length of failures.
- **Wholes to Parts or Parts to Wholes**: there is no single correct starting point. Three schools coexist:
  - "Nouns and verbs" (the parts that form the systems). E.g. Will Wright.
  - Desired experience / holistic feel (the author).
  - "A machine that does x" (Ellenor 2014): imagine a machine, deduce its parts and see what game emerges.
- Practical implication: you have to end up with parts, loops AND whole defined. Move fluently between organizational levels; start with the one that makes sense and bounce back and forth. Differences of school cause misunderstandings within the team (the author took a while to understand Wright, and vice versa).

## 2. Know your strengths, work on your weaknesses ("Know Your Strengths, Work to Your Weaknesses")

Every designer has a "home place" they return to when the design gets hard. You need to identify it, not stay there, and know how to work with people who start from somewhere else. Three archetypes:

| Archetype | Starts from | Strength | Trap / risk | What to develop |
|---|---|---|---|---|
| **Storytellers** | The whole: the player's journey and feelings, the world | Painting the experience, the theme | "Games are not stories"; telling the game as a tale is not enough | Functional systems with tokens, rules and dynamic elements; collaborating with someone who provides structure |
| **Inventors** | Complex mechanisms (clocks, ecological/economic simulations). E.g. Spore prototypes with star-system formation simulation | Fascinating dynamic systems | Mechanism at the center, no human player ("watch it go"); the player gets thrown crumbs | Including the human as an integral part; long-term goals and reasons to play (the whole) |
| **Toymakers** | Appealing pieces/mechanisms even if they don't "do" anything; or domain knowledge (the cadence of a Sopwith Camel, medieval swords, corals) | Prototyping fast from tokens/rules | They don't think about what the player does or why it is fun | Building interactive systems and finding goals for the player |

- Rule: every starting point is valid **as long as it isn't where you end up**. Teams with different styles are harder to coordinate but produce better games.
- "Find the fun" requires all three layers (parts, loops, whole) **plus** engaging interactivity.
- Core skill: communicating ideas, listening to others', working with strengths different from your own.

## 3. Qualities of game systems ("Qualities of Game Systems", Achterman 2011)

Five marks of an effective game system:

1. **Comprehensible**: the designer must understand the game and its internal systems, and the player must be able to build a mental model. That is why design documentation matters (for you) and so does presenting the game in a way that can be mentally modeled (for the player).
2. **Consistent**: rules and content work the same in all areas. Temptation: adding an exception/special case to fix a problem → lowers the system's resilience (future problems) and makes it harder to learn.
3. **Predictable**: same inputs → predictable outputs. It helps the mental model, and is somewhat in tension with emergence. It doesn't mean mechanical/boring; but neither very different results for similar inputs nor a system that is fragile in the face of the unexpected. Minimum: having considered the edge cases that damage the experience or leave an exploitable crack.
4. **Extensible**: building systemically lets you reuse content or generate it procedurally instead of depending on hand-made "set pieces". Prefer **loops to arcs**: quote from Daniel Cook, an arc is "a broken loop that you leave immediately". A general system ("building construction") lets you add a new class of buildings without hand-making it. A system built from loops can be relocated as part of another game. Minimum necessary parts + enough loops between them.
5. **Elegant**: it sums up the previous ones and goes beyond consistency. Examples of elegance: a diverse explorable space with few rules (archetype: Go); systemic rules with few exceptions, easy to learn, with predictable and emergent behavior; a system usable in multiple contexts or with new parts that can be added.

Derived problem signals: accumulated exceptions; hand-made content that can't be reused; single-use "arcs"; fractured/separated systems.

## 4. Tabletop vs. digital games ("Tabletop and Digital Games")

- Design has a lot in common between the two. Studying tabletop games teaches even if you never design one: the only "computing power" is in people's heads, and interaction is only with physical tokens → it exposes the relationship between tokens/rules, loops and experience. Digital games can hide design laziness behind graphics and cinematics; tabletop games can't.
- Analogy (Terrence Mann): "film makes you famous, TV makes you rich, theater makes you good". Tabletop is to digital what theater is to film: closer to the audience, with less to hide behind.
- That is why the book uses many tabletop examples. Designing tabletop games is not mandatory, but it is good practice.

## 5. The process of designing games as systems ("The Process of Designing Games as Systems")

- An **iterative** process across parts, loops and whole: first in your head/on whiteboards/papers/documents/spreadsheets; then, once it has shape, a prototype + playtest cycle (ch. 12). It's better to prototype fast and test early than to wait for the idea to come out complete.
- **Game designer's loop** (Fig. 5.1 = Fig. 4.3): Designer → designs Game; Player ↔ Game exchange input/feedback; the designer receives feedback from the player/game and adjusts. Design is a designer-player-game feedback loop.
- You can start at any level; what matters is that the three later support each other. The book goes through them in the order whole → loops → parts.

### 5.1 WHOLE level: thematic architecture ("The Whole Experience: Thematic Architecture")
It answers "what is the point of the game (or of a system within it)?". It splits into **architectural** (technical aspects of the experience: how it looks and feels) and **thematic** (tacit qualities: what it is about).
- Example: For Honor, Jason VandenBerghe: "combat is an art form" → melee combat as a lethal dance. It isn't enough on its own, but it is a guiding star from which interactions and details derive.
- Common mistake: teams that launch into production without clarifying the "total experience"; a shared, coherent vision is the best predictor of team success (ch. 11).
- Aspects of the vision to articulate:
  - **World and History**: what is the world and the player's point of view? (the same world of spies: a spy on the rise / a boss pulling strings / a veteran on a revenge mission → three different designs). History: only the events that apply to the player. At the start, one or two pages; don't write 100 pages of lore unless you have the time, money and experience. Don't write more than the design needs.
  - **Narrative, Progression, Key Moments**: history is the past; narrative is present/future. Questions: is there a predefined story? Are there major events around the player that leave room for decision? Or is the past just a starting point? From there come major events, goals, progression and **key moments** (short accounts of significant climactic points).
  - **Art, Monetization and other whole-experience concerns**: art style (2D/3D, painterly, cel-shaded, hyperrealistic) and how it reflects the heart/theme; UI/UX; monetization (decided at this stage).
- It doesn't matter whether you start with a blue-sky vision or arrive after defining parts and loops: you iterate between the two; before developing you must have the whole clearly articulated and shared.

### 5.2 LOOPS level: systems and play space ("Systemic Loops and Creating a Space for Play")
- The loops: the dynamic model of the game world, the player's mental model and player-game interactions. Designing them is the core of the "systems designer" (detail in ch. 7).
- Goal: create a **space** that the player explores and inhabits, not a single path. The systems must support the theme and the experience, and work interactively between game and player. You must specify (via prototype + playtest) the **core loops**, the explicit goals and the progression.
- Difficulty: it is the hardest part of design, because the experience they produce can't be seen well in advance. Example: resources, crafting, wealth production and combat each have their own workings and interrelate with each other and with the player. It takes skill, patience and resilience in the face of failed attempts.
- **Balancing Game Systems**: all defined parts must be used and balanced against each other, and every system must have a clear purpose. Example: if you add a quest system and players ignore it, understand why and decide whether to remove or fix it (detail in chs. 9-10).

### 5.3 PARTS level: tokens, values and rules ("The Structural Parts: Tokens, Values, and Rules")
- Before it is a game, you have to place the functional loops in the context of the whole and create the structural parts. Moving from vague description ("hand-waving") to something implementable is mandatory.
- This is the **detailed design** or the "spreadsheet-specific" part: does the sword weigh 3 or 4? Does it cost 10 or 12? How many types of troops/horses/petals, and what difference do they make? It is what makes the game real and lets you **balance the tokens against each other** so the systems don't "fly off" separately.
- How to think about tokens (game objects: player, other people, nations, creatures, ships): give each one enough attributes, values and behaviors. **Guiding question**: what is the smallest number of attributes, states and behaviors that supports the systems and the desired experience?
- Make it evident to the player what the tokens are, what they do and how they affect them → this feeds UI/UX. The UI can't be specified until you know what information is needed; asking what information the player needs to know helps clarify the tokenization.
- Preview of ch. 8: complex objects with a few general attributes that interact (subsystems); inter-object behaviors; how to avoid "easy win" tokens or ones that break the game.

### 5.4 Revisiting the process ("Revisiting the Systemic Design Process")
- The designer's cycle: alternating between seeing the game as a whole, as systems/loops and as individual parts (Fig. 5.2), seeing them at once and being able to drop into the detail of any of them.
- **Unsticking heuristic**: if you push on one level without effect, change your point of view. Not achieving the experience? Explore the tokens and how they inform the experience. Have the experience clear but can't specify tokens? Look at what the systems say about how they should work.
- **Anti-pattern**: avoiding tokenizing, ensuring interesting interactions or thematic cohesion just because it isn't your comfort zone. All three are necessary.

## 6. METHOD: analyzing games from a systems view ("Analyzing Games from a Systems View")

It follows the same structure as design: whole → loops → parts (and how you build your mental model). Goal: understand what makes other games work (or fail), learn from the designer's decisions and improve your own designs.

**Step by step (analysis checklist):**

1. **Your own mental model at the start (first contact)**
   - Do you understand the setting and the theme?
   - What surprises you?
   - Which concepts were important, incomplete or hard to understand while learning?
   - How could the game have increased your engagement at the start?
2. **The whole (experience)** — during and after playing
   - What experience and feelings was the designer trying to evoke?
   - Which aspects supported or detracted from your experience?
   - Which visual and interactive elements support the theme and the desired experience?
   - What can you infer about the designer's intent from the art style and the interactive aspects?
3. **Systems** — identify which specific systems exist
   - Are there systems that operate independently of the player, or do all of them depend on the player doing something first?
   - Example: Power Grid (tabletop) has systems almost outside the players' control; a supply/demand economy: the more fuel players buy, the higher the price goes until supply is replenished the following turn; supply is replenished every turn and lowers prices if unused.
4. **Progress loops**
   - How do you progress? Which **reinforcing loops** do you identify?
   - Which **balancing loops** push against advancement, or keep a player who gets ahead early from simply winning?
5. **Interactivity**
   - What are the primary forms of interactivity?
   - How does the game allocate its **interactivity budget**? Strategy and socializing, or quick thinking and action?
   - Do the ways of interacting help establish the theme or go against it?
6. **Parts: tokens and rules** (the atomic parts with values and behaviors)
   - Do they support the experience or get in its way?
   - Having learned a system, can you transfer that to another part of the game, or are there many rules with their own exceptions that force you to think hard about how to play? (consistency/elegance test)
   - Look at how the art is expressed in the tokens, sometimes in surprising ways. Example: Splendor (tabletop, gem merchant): the chips weigh like poker chips; the weight subtly adds to the experience even though it isn't functional.
7. **Compare and synthesize**: when analyzing many games, commonalities and unique traits appear; this helps avoid others' mistakes, take good ideas and keep your design fresh.

## 7. Prototyping and playtesting ("Prototyping and Playtesting")

- Design is testing and refining ideas repeatedly in service of a vision; almost everything changes during development except the unifying vision.
- Example: Ed Catmull (Pixar): "all our movies suck at first". Up started with a kingdom in the sky, two princes and a giant bird called Kevin; in the end only the bird and the word "up" remained.
- Practical rules:
  - Be willing to do many iterations and to **throw work away** (drawings, animations, code, documents). Don't cling to something because of the time invested: you end up with the "okay" or mediocre when with more work it would be great.
  - **Prototype**: an early version to play and test the idea; it can be whiteboard drawings, paper and coins. Almost always ugly or incomplete, they converge on the polished product. The point is to get the idea out of the realm of ideas and make it playable **as fast and as often as possible**.
  - **Playtesting**: validation of prototypes, or more often, how you discover where the design is broken. The designer's intuition never replaces testing with players who have never seen it. Quote from Cook: without implementation and playtesting, a design is an "ineffective paper fantasy".
  - Test early and often; the brilliant idea in your head does not survive contact with reality unchanged (probably with many changes).
  - Humility and creative flexibility to change based on what others think.

## 8. Chapter 5 summary
By dividing the game into parts, loops and whole (not necessarily in that order) you have a handhold for defining it at each level. Ch. 6 = the whole; ch. 7 = loops; ch. 8 = parts.

---

# CHAPTER 6 — Designing the total experience

Purpose: arrive at the "big idea" and record it in a **concept document**, which is the unified whole and the touchstone during development.

## 9. The big idea ("What's the Big Idea?")

- Every game has a single driving idea (concept / vision). It must be clarified **early** and be explainable succinctly. If postponed, you wander around nibbling at possibilities without finding the heart, and nobody understands what you're doing or why it's worth it.
- Sharing a clear and compelling vision is the practice that correlates most with successful games (ch. 11).
- The vision doesn't have to be grand: the smaller and more focused, the better. Examples: Angry Birds (not an epic idea at all, enjoyed by millions); For Honor ("combat as dance": one evocative phrase communicates and excites).

### 9.1 Blue-sky design ("Blue-Sky Design")
- **Ideation** = generating and communicating new ideas. **Blue-sky design** = a very open form, with no limits, rules or business realities. Seductive, especially for young designers.
- **Methods**: you can do it alone, but it is far more effective with others (bouncing ideas around). Typically: a room with empty whiteboards and a small team → "be creative, NOW".
- **Brainstorming-ish** (with modifications):
  - Quantity first, not quality: get ideas out.
  - Seed it with a prompt or a joke (Ron Gilbert: every good session starts with 15 minutes about Star Trek). Loosen the group up mentally.
  - Keep the flow going with a light hand: heavy moderation cuts off creativity. Take turns so everyone contributes; even games (the first letter of your idea is the last letter of the previous idea).
- **Getting Past the Easy Ideas**: the first ideas are almost always stereotypes and clichés or copies of something recent (whatever is on the surface of the mind). They can't be avoided, but you mustn't stop there, nor let ego ("how clever I am") slow you down. With others, build on what they said.
- **Twisting Ideas**: take an idea on the table and subvert it. Example: "warrior who kills the dragon to save the village" → what if you save the dragon? What if you convince the villagers to ally with it? What if you are the dragon?
  - **"Yes, and..."** (an improv technique): instead of a "no" that kills the flow, each person accepts and adds their twist; the idea mutates by addition. It removes ego: the ideas matter, not who said them.
- **Curation**:
  - There is a limit to "there are no bad ideas". Past the initial flow you must **turn the tap down**: look at the written ideas, see which have the most passion/creativity (the ones people keep discussing on their own) and discard the "dry wells".
  - Not all popular ones work: some exceed the means, require nonexistent technology or don't fit the direction.
  - Analogy: a museum director who chooses what to exhibit without saying the rest has no value.
  - Usually decided by a senior profile (creative director, lead designer, sometimes an executive producer): from circulating ideas on a whiteboard to asking for a few written treatments to be developed. It means leaving the rest behind.
  - Quote from Steve Jobs (paraphrased): focus means saying "no" to a thousand good ideas.
- **Limits to Blue-Sky Design**: without limits it usually goes nowhere or in opposite directions with no winner. Many designers freeze up; or retreat to the safety of a known game; without a time limit, they tinker endlessly and never finish.
- **Constraints Are Your Friend**:
  - You almost always already have constraints: time, money, platform, programming and art skills; licenses; required type of game. They limit the blue sky but not the creativity within.
  - It's also worth setting limits on **genre** (type of gameplay) and on the **experience** sought. Even in the session, ground rules such as "no virtual reality" or "no killing". They eliminate millions of ideas, and that is the point.
- **Cautions (for brainstorming)**:
  1. **Dominant voices**: whoever speaks first or most is heard most; extroverts and men tend to drive and other perspectives get lost.
  2. **Groupthink**: if everyone agrees it's assumed to be good, but a homogeneous group (all men, fans of the same genre, etc.) considers a narrow range and is the worst equipped to see it (we can't see our own blind spots). Bring in diverse people (gender, ethnicity, life experience, interests, experience level).
  3. **Forcing the vision or feature in a single sitting** (all day if necessary): a poor way to create; the quiet ones get left out and it wears out fast. When the flow drops, rest: everyone leaves for an hour or more with some ideas, and then regroups to see where the thinking has gone (no need to restart or pick up exactly where you left off).

## 10. The desired experience ("The Desired Experience")

- The most important question of ideation: **what experience do you want the player to have?** That is: what they do, how they progress and, above all, **what they feel**.
- It is hard, especially for inventors and toymakers, and may seem secondary next to tokens/rules. Sooner or later you have to face it; it doesn't resolve itself. Designing without intentionally designing the experience gives a more chaotic mental model, harder to learn and to get hooked on.
- If you're a storyteller: you reach the emotional essence quickly but need to get down to earth with others. If there is already a narrative: make sure you design a game, not a movie. Question: does the desired experience support **second-order design** (a play space to explore, not just a tale to walk through as a spectator)?
- Specific decisions to make about the experience (list):
  1. Who are your players? What are their motivations?
  2. What is the genre (the most-used type of gameplay)?
  3. Combining both: what is the **player's fantasy** (a role that gives reason and space to explore: hero, pirate, emperor, dung beetle, child…)?
  4. What kind of decisions does the player make and how do they progress?
  5. What type of interactivity does it rely on most? How do you spend the **interactivity budget**: a game of reflexes, careful planning or emotional response? What are the visual and sound aesthetics?

## 11. The concept document ("The Concept Document")

- Articulating the vision in order to communicate it; skipping it is tempting on small teams, but it clarifies thinking, aligns the team and helps sell the design (new members, funders, executives).
- It is informative **and** persuasive: convey the idea quickly and clearly and show why it is worth making. It is similar to the structure of the **pitch**, though they differ by audience (ch. 12). Template in the book's online resources.
- Format: on paper, or better **online** (wiki/web): it stays current instead of becoming obsolete, and details are added in an organized way without bloating the document.
- Rules for the document:
  - Always **high level**; "the tip of the iceberg"; the hub of all design documentation; keep it up to date.
  - Brief, clear, highlighting the vision; the more images and diagrams, the better.
  - It gives brief conceptual descriptions (art style, world history, progression) and **points** to more detailed specific documents → this lets several designers work on different parts and documents be added, keeping the concept doc as the overall expression. It is the touchstone of the agreed vision and an active organizing principle.
- **Three main sections**: (1) High-level concept, (2) Product description, (3) Detailed design.

### 11.1 Section 1: High-level concept ("Capturing the Concept")
Subsections (full list): **Working title, Concept statement, Genre(s), Target audience, Unique selling points**.

- **Working Title**: the handle name for talking about the game. Evocative of the game; some teams search for domains and competing titles; others pick an unrelated name (codename, for confidentiality). Both work and it probably doesn't matter: the final title is almost never the initial one. Capture the game and move on; the name search is for later.
- **Concept Statement**: one or two sentences that capture all the important aspects, above all the **player's experience**; it answers "what is your game about?" and is the first impression. It should be brief, incisive and understandable; it should give an exact (not detailed) idea of the main points, why it isn't like the thousands of other games and why it is fun. Trick: fit it into a 140-character tweet (going a bit over doesn't matter; it helps you choose each word).
- **The One Question (Booth 2011)**: a single question about the game used to **resolve design issues** (not strictly part of the doc but may derive from the concept statement). It applies literally or figuratively to everything, from small features to UI.
  - Examples: historical simulation → "is it authentic?"; ninja game → "is it stealthy?".
  - Guitar Hero: "Does it rock?" If a feature doesn't contribute to that, it's out; between two features, the one that rocks more. Applied to characters: create your own character or pick a pre-made one? → whichever makes you feel more that you're the one rocking (hence the customization down to the eyeliner).
  - Rock Band: fixing the vision was hard because of the love for Guitar Hero; the question became "is it an authentic experience of being in a rock band?". Once it was fixed, many feature arguments disappeared because everyone could see the dividing line between the two projects.
  - Use: it gives you the concise vision and evaluates later ideas/features to see whether they belong.
- **Genre(s)**: a heuristic label (no official designations; they mutate and subdivide) based on gameplay conventions, types of challenges and decisions, and often aesthetics/technology. It indicates the type of prevalent interactions: fast action, reflective strategy, emotional/narrative, social, or a combination.
  - Shooter example: an action subgenre, lots of fast action/feedback and short-term cognition in a kill-or-be-killed setting; endless subtypes ("2D top-down space shooter" like Gratuitous Space Battles; "massive cooperative bullet-hell shooter" like Realm of the Mad God). Portal: it's a shooter because you shoot, but you don't kill anything and you shoot to solve puzzles → an example of rethinking tacit assumptions.
  - **Danger**: using the genre name without considering which aspects of that genre you include → lazy design. ("Strategy": does it mean a top-down/isometric camera, commanding many units, or something else?). **Best practice**: say which aspects of which genres you want (e.g. "multi-unit control from strategy + the pacing of action + juicy, easy-to-learn interactions from casual"). That informs others and helps you see whether you're covering too many genres.
  - The book's list of genres with their interactivity profile (useful for analysis):
    - **Action**: fast action/feedback loops; story as a backdrop, little narrative in the gameplay.
    - **Adventure**: fast action/feedback loops within an adventure story that provides long-term goals.
    - **Casual**: easy to learn, few loops and short-term goals, short sessions; "juicy" interactions: bright graphics, clear actions (big, colorful buttons), lots of visual/sound feedback; aimed at people who don't consider themselves "gamers" (they may play for hours, but as a pastime).
    - **Idle**: the player decides little, the game "plays itself"; focus on action/feedback (clicker variant), little short-term cognition and some long-term planning. Shallow interactivity = a trait; low cognitive load. It progresses even while the player is absent and gives positive feedback about how much progress was made on return. A Dark Room (Michael Townsend): audience = people who like "numbers going up" + people who like exploring the unknown. Risk: when the promise fades, you see there is no more point than watching numbers go up.
    - **MMO**: hundreds/thousands of players; avatar and world persist without the player. Action/feedback (combat), short- and long-term cognition (character progression); social interaction is crucial (grouping, informal communities).
    - **Platformer**: an avatar that jumps between platforms; fast action/feedback (knowing when and how to jump); easy to pick up, rewarding to master (comes from the 80s arcades).
    - **Rhythm**: gameplay based on a sense of rhythm/musicality/dance; replicating musical/dance sequences with fast action/feedback within a song.
    - **Roguelike**: procedurally generated maps, often permadeath (if you die, you start over); dying often is expected, and that "deadly precariousness" (Pearson 2013) is part of the appeal. Named after the game Rogue. Since the levels change, it can be replayed without repetition. Today the term is also applied to space exploration, simulation, etc. Interactivity: a mix of action/feedback (real-time combat) and long-term cognition to improve the avatar (skills, gear) and face growing challenges.
    - **Role-playing**: a specific role, usually heroic adventures; combat (action/feedback), skill improvement (short-term cognition) and sometimes crafting (long term).
    - **Sports and simulation**: they simulate real activities with greater or lesser verisimilitude; sports use action/feedback + short- and long-term cognition; simulations (farm, airplane, city) rely mostly on short- and long-term cognition.
    - **Strategy**: almost exclusively short- and (above all) long-term interaction for planning and commanding; it can look visually dull because the cognitive/interactive budget is spent on long-term cognition.
    - **Tower defense**: protect a base/objects from growing waves while the defenses ("towers") are built up; you can build anywhere to "herd" enemies along a path; there is a feedback loop: you earn points/currency for creating or upgrading towers based on enemies eliminated. A mix of short/long-term cognition with some action/feedback.
  - There are combinations (e.g. World of Tanks: action-strategy MMO).
  - **Genre heuristics**: look for similar games to define yours. Beware of: (a) fitting an established genre too well (for example, a 2D action platformer copied from thousands) → less interesting and lazy design that leans on the label; (b) confusing or gimmicky mashups ("narrative bullet-hell with strategy and shooter": hard for people to understand).
- **Target Audience**: described along three axes: **psychographics, demographics and technological/environmental context**.
  - *Psychographics and Motivations*: the easy way: "whoever likes game X will like mine". The more sophisticated way: primary gameplay motivations.
    - **Quantic Foundry model (Matsalla 2016; survey of ~300,000 gamers): 6 motivations**:
      1. Action: destruction and exciting, fast-paced gameplay.
      2. Social: community and competition (not mutually exclusive).
      3. Mastery: hard challenges and long-term strategies.
      4. Achievement: completing quests and becoming powerful.
      5. Immersion: being someone else and living an elaborate story.
      6. Creativity: expressing yourself through crafting/customization, tinkering and exploration.
    - **Three clusters**: Action-social (excitement, competition, destruction → community); Mastery-achievement (completion, strategy, challenge → power); Immersion-creativity (story, customization, design, fantasy → discovery). "Power" and "Discovery" are "bridge" motivations between clusters. Axes: cerebral vs. kinetic; action "on the world" vs. "on other players".
    - **Bartle (1996)**: axes "acting on" vs. "interacting with" and "players" vs. "world" → achievers (act on the world), explorers (interact with the world), socializers (interact with players), killers (act on players). It doesn't withstand quantitative scrutiny but retains intuitive usefulness (Box's aphorism: all models are wrong, some are useful).
    - The clusters correlate with the **Big Five / Five Factor Model**: neuroticism, extraversion, agreeableness, conscientiousness, openness to experience. Action-social ~ extraversion; mastery-achievement ~ conscientiousness; immersion-creativity ~ openness. Players choose games that match their personality: "not to be who they are not but more who they are" (Yee).
    - **Use**: list the likely motivations of your players based on the gameplay and interactivity; as with the interactivity budget, spot unlikely combinations (someone who wants emotional immersion in an elegant story probably doesn't want to spend time blowing things up).
  - *Demographics*: age, gender, life context. Some create personas ("Lisa, a divorced 45-year-old…"), useful for taking the focus off yourself but can distract from real motivations; don't elaborate unless the detail matters to the game.
    - Relevant trends (Yee 2017): the "excitement" motivation falls linearly with age and becomes an "anti-motivation" at 50+ (which would explain why League of Legends is more popular among the young). "Competition" falls faster, high in adolescence and minimal by the 40s; men are more motivated than women until ~45, then the difference disappears. "Completion" stays stable across age and is always among the top 3 motivations of men and women.
  - *Environmental Context*: platform (console, PC, mobile…), available time/environmental factors ("commuters with 10 minutes on the bus" vs. "dedicated players with a whole day"), level of technical or gaming sophistication, other relevant factors.
  - *Summing up*: put together a short descriptive statement (e.g. high-action players with meaningful competition supported by predefined missions that satisfy completion; interrupted by life, they value 10-minute sessions and an easy learning ramp, with the ability to show off skills and completed missions). It should be clear but not restrictive, neither excessively broad nor narrow.
  - **Hard rule**: if the answer to "who is your target player?" is "everyone", you haven't thought enough about the concept or its appeal. No game is universally appealing; within the general appeal there is a "bull's-eye" audience. Defining it helps you decide.
- **Unique Selling Points (USPs)**: a short list (**3 to 5**) of brief, meaningful statements of what makes the game unique/appealing. If it's hard to write meaningful USPs, you probably need to **redo the concept**.
  - Test question: why would someone leave a game they already know they like to play yours?
  - **Traps**: believing that because it seems great to you it will seem great to everyone; believing that because it was hard to make it must be good / that the team's passion shows (it never does). Players don't care about your love or effort; you first have to capture visual and gameplay attention.
  - You can settle for "fresh": not 100% new, but not seen over and over, with a new twist. E.g. zombies; trivial changes ("fast zombies", "purple zombies") aren't enough; something like rescuing zombies and re-infecting them to turn them human again could be.
  - You can also **subvert a genre** (Portal with shooters; Undertale with RPGs): take the dominant trope ("in shooters everything is about destroying") and change it ("you shoot to navigate and solve puzzles"). Harder than using aspects of the genre and taking it in new directions (e.g. a narrative game with action elements; an idle game that escapes pointless clicking).
  - Balance: the new and unique differentiates, but the game must still be **recognizable**; otherwise people dismiss it as unintelligible as quickly as they would for being conventional.
  - Thinking about USPs is another reason to design the concept patiently: if you stick with the first idea, it is probably not meaningfully unique. You need something more than "it sounds cool to me".
  - **X-statements**: two definitions. (1) the "x-factor": what makes it special/different/appealing (≈ list of USPs). (2) the structure "A x B" ("A crossed with B" / "A meets B"): e.g. "The Division x Overwatch", "GTA meets Undertale": a blend of existing games for a fresh version.
  - **Caveats**: using USPs/x-statements as a crutch for lazy design (combining USPs from other games hoping for a wonderful hybrid "almost never works"). USPs must support a **coherent vision**, not form a monstrous agglomeration of unrelated points. Despite the "selling", they serve above all to understand and communicate the concept: the emphasis goes on what makes it appealing and engaging in new ways, not on what will sell. Design a good game that sells, not a game that sells "and hopefully is good".

### 11.2 Section 2: Product description ("Product Description")
Subsections (full list): **Player experience, Visual and audio style, Game world fiction, Monetization, Technology/tools/platform, Scope**. With pointers (links) to detail documents (chs. 7 and 8).

- **Player Experience**: a few short paragraphs; includes the player's fantasy, **key moments** as gameplay examples and a brief discussion of what the game comes to mean to the player. It should reflect (and be reflected in) the concept statement and USPs. The main output of the blue-sky process.
  - **What Is the Fantasy?**: make clear the player's point of view and what fantasy it gives (heroic knight, stealthy thief, star captain, single mother supporting her family, single-celled organism, disembodied leader of a galactic empire). Each one = a different experience.
    - Fantasies are usually **aspirational** (captain, mayor, brave fighter, wise wizard); sometimes it's being in a difficult situation and bringing out your best (The Last of Us); sometimes putting yourself in someone else's shoes (Gone Home: a girl investigating what happened in her home; The Sims: a family of your own invention).
    - Each game creates its own **magic circle**: a novel experience, separate and without consequences within its limits.
    - **Entrance (Daniel Cook, Spry Fox)**: the player must understand at the start what they do and why it's interesting. Validation test: give a potential player the concept statement and ask them to tell you how they imagine the game: what they would do, where they would start, how it would end, whether it would be worth it. If they can't build a mental model they can relate to you, or it doesn't match your concept, there is a lot of work to do. If they immediately understand the fantasy and take it in the same direction as your design, good start. Keep it informal: it's a test of the concept, not a way for players to design for you.
    - You arrive at the fantasy from the storyteller side (total experience first) or the toymaker side (unifying mechanics under one experience).
  - **Key Moments**: tell a few brief anecdotes: when they happen, how they hold the player, how they make them feel. They illustrate the experience at different stages: **learning, being habitual, having mastered**; and from the points of view of players with different motivations.
    - Create **personas** (archetypes): the experienced player, the hurried one, the insecure one, etc. (depends on the game). For each, identify important situations: first victory and first defeat; how the game opens up in a new way (level 50, second castle, first motorcycle); what happens when they play online with someone; etc.
    - Don't neglect the **opening**: many believe the **first 300 seconds (5 minutes)** decide whether the player gets hooked. You don't need to map them all, only the key moments that you believe (and will test) hook players and motivate them to continue.
    - Narrate in text and quick drawings. They help understand the concept from different players' perspectives, remember why decisions were made, and **test new options against the personas and key moments**.
    - Put a few in the concept doc and point to a separate document with more.
  - **Emotions and Meaning**: the total experience is how it makes them feel. If it doesn't generate an emotional response, it doesn't hook. It doesn't need to tug at heartstrings or change a worldview, but you must be able to identify an overall emotional component: achievement, escaping a disaster gasping for air, or (as in Tetris) "I died but better than last time" / "worse but I know I can improve".
    - Some games aim for subtle emotions (loss, hope, gratitude, inclusion, revulsion…). If you depend on emotional interactivity, you have to carefully design the experience, key moments and systems that support it: it doesn't happen on its own; you create the space and the player, if they want, approaches.
    - **Meaning**: does the game leave a lasting meaning? Even Monopoly teaches a model of how to get rich and what success is. What does a shooter teach about war vs. This War of Mine? What meaning about relationships do Firewatch, Gone Home, The Sims convey? You can choose a light game without meaning (Candy Crush), but it's best to decide that. Example (Will Wright): the original "meaning" of The Sims was that time is the only non-renewable resource: the more things you buy, the more time the Sims spend maintaining them → "possessed by their possessions".
- **Visual and Audio Style**: describe the intent of the art and how it supports the concept and experience. Qualitative in words ("light, airy, bright desaturated colors"; "dark tone, grays and hard shadows in low-poly scenes") **accompanied by images** of concept art or **reference art** (art from other sources not used in the game; acceptable use as reference, never include others' material in the game without permission). **Mood boards**: public panels with reference/concept art so the team captures tone and mood.
  - Audio (music and effects) is at least as important as the visuals: it complements and unifies. It is described qualitatively ("simple, evocative theme on solo violin"; "electronic distortion themes throughout the game, fitting the dark visual tone and creating an ominous atmosphere"); use reference audio and links in online docs.
  - The detail goes in the **style guide**, not in the concept doc (but it is referenced); it can be completed almost upon entering production.
- **Game World Fiction**: a brief description of the backstory and the world; not pages of detail, but an idea of the world contemplated ("you are an amoeba looking for its home"; "star pilot stranded in a world where magic works and technology doesn't"). A few sentences on what happened up to the beginning, possibly a map of the territory and a brief description of main NPCs. The basis for detailed design.
- **Monetization**: every commercial game must recover costs plus profit. Think about at least one of these models:
  - **Premium pricing**: a single price upon acquisition; the classic model, today with no guarantee (players reluctant to pay even $1); few games with this model recover costs outside large budgets (tens of millions).
  - **Free to play (F2P)**: dominant today, especially on mobile; free forever but designed to incentivize purchases (some aggressively); sometimes watching an ad video replaces a purchase. **It must be integrated into the design from the start; it is not added at the last moment.**
  - **Limited-play pricing**: play free up to a point (first levels) and buy to continue; less common since F2P.
  - **DLC**: paid additional content; key question: could it have been included in the original game, or do players feel it was withheld to charge for it later?
  - **Ad supported**: free with ads; attractive because you don't have to design F2P, but income is meager unless there are millions of regular players.
  - There are other models (even ones not yet invented); if the game is commissioned/subsidized and there is no monetization, note it in the doc to avoid questions.
- **Technology, Tools, and Platforms** (list of what to define): hardware and operating system (Windows/Mac, mobile iOS/Android, VR/AR/mixed: big consequences); development tools (Unity, Unreal or others: they save work but require knowing them and have costs and drawbacks); server and network (even if single player, define it from the outset); monetization and advertising (integration with ad/payment servers; at least know whether it is part of the product); **localization** (decide from the beginning: it is very hard to retrofit once development is advanced). If you don't know all the answers, answer most and list the rest as questions to resolve quickly.
- **Scope**: from the concept and product you deduce how many people, what skills and how much time. More art/content, more systems to create and balance, more monetization and localization items → greater scope. **Rule**: limit the scope of any project, especially the first; even producers of 100+ person teams try to; if there is a time/money limit, be ruthless in prioritizing.

### 11.3 Section 3: Detailed design ("Detailed Design")
It is a prediction (it isn't built yet): it will be somewhat wrong, but it is important. Subsections (full list): **Core loops; Objectives and progression; Narrative and main systems; Interactivity**.

- **Core Loops**: what activities the player will do, especially the most repeated moment to moment (combat, building, gathering petals…) and **why that set of loops is engaging and supports the objectives and goals**.
- **Objectives and Progression**:
  - The player's journey from tutorial to mastery and spatial route (if one exists, e.g. crossing a map).
  - **Progression vectors**: dimensions in which the player grows (money, skill, reputation, magic power, provinces, crew size…).
  - Build **immediate, short-term and long-term goals**, supported by core loops, narrative and main systems.
  - The goals must support the fantasy and the experience of the concept (e.g. assassin game → raising hedgehogs is a bad objective; empire-building game → describe what the player does moment to moment to keep interest).
  - If the game supports **implicit** player goals (in addition to explicit ones), note how (e.g. being able to become a master craftsman in a combat-centered game).
- **Narrative and Main Systems**: narrative (what happens during the game, which the player takes part in or which happens to them; distinct from the backstory, which looks to the past) briefly and with a pointer to a detailed document. Describe the **main systems** (physical/magical combat, economy, ecology, political systems…), often related to the core loops; indicate which ones the player touches directly and which live only in the world model (e.g. background political machinations the player can't affect).
- **Interactivity**: primary forms of interaction: mouse only, keyboard+mouse, controller, touch, gaze, etc. Comment on how the game spends its **interactivity budget** (fast or "juicy" action/feedback; short- or long-term cognition; emotional, social, cultural) and how it achieves it visually and sonically. It is not the detailed UI, but it is how the primary methods support the experience and give **enough verbs and feedback** for actions to affect the systems. Include at least one screen mockup and a list of non-visible interactions (typed, gestures, mouse).

## 12. Designing the game+player system ("Designing the Game+Player System")

- This whole process is the design of the larger system of which game and player are parts: the **game+player system**. It only exists if the player keeps playing → the game must be comprehensible, enjoyable, and the experience engaging and fun.
- At the conceptual level: the idea must be clear and consistent; if others don't understand the vision, it becomes confusing for players too (if you ever get to develop it).

### 12.1 Keeping to the theme ("Keeping to the Theme")
- Vision/concept = framework, constraint and "connective tissue". The thematic elements (the "whole") **must touch the entire game**.
- **Pruning rule**: if a system or token doesn't derive its meaning from the theme or doesn't support it, it is **removed or altered** so that it fits. A consistent theme throughout → parts, loops and whole aligned and unified → a game+player system that captivates in the good sense (engagement).

### 12.2 Elegance, depth and breadth ("Elegance, Depth, and Breadth")
- **Elegance**: a clear and consistent vision running through systems, tokens and rules (from whole to loops and parts), with few exceptions and special cases. It satisfies **Bushnell's Law** (easy to learn, hard to master): the player builds a good mental model early that serves them without major readjustments; learning is almost effortless subjectively, each thing learned adds to progression and the sense of mastery, and they should never have to mentally step out of the game to remember an exception or a contradictory rule.
- **Depth (systemic depth)**: how long mastery takes depends on systemic depth and the breadth of features. With elegance, there are typically **systems within systems**, organized so that early learning applies to later mastery (rather than being undone). Even with few simple systems, the navigable space can be enormous → it is perceived as great depth. Players motivated by exploring rules and mastery will keep going as long as they can expand their mental model within their budget of cognition, emotion and interactions.
- **Breadth**: more features = more ways to interact with the same content/systems. Sometimes it **substitutes** for systemic depth (mountains of content to retain the player instead of deep systems that don't require so much content) — a warning sign. Other times the scope requires a wide palette (multiple classes, vehicles, combat systems, interacting resource/economy/politics/combat systems; typical of "grand strategy").
- Broad games can also be deep and keep some elegance, but adding breadth and depth almost always adds exceptions and special rules that make learning harder; just the number of features to attend to complicates the mental model. That limits elegance in large, broad, deep games, which is **not necessarily a defect**: it depends on the desired experience and the audience (whoever seeks that doesn't ask for effortless elegance).

## 13. Questions to consider about your design vision ("Questions to Consider About Your Design Vision")

Use them to check that the concept is clear and complete before defining loops and parts, and **come back to them often** so the design doesn't drift. Full list (paraphrased):

1. What is your concept statement in one or two sentences? Does it capture all the important elements? Do you have a "One Question" test for features based on the concept?
2. Who is your game for? What motivations does the audience have? What other games does whoever plays yours enjoy? Are there external/environmental factors that affect how it is played (for example, during the commute, or requiring a whole day to be set aside)?
3. What traits or aspects of gameplay distinguish it from all the others? Why would a target player (who already enjoys this type of game) leave an existing one to play yours? What will attract initial interest and what in the design will keep them hooked over time?
4. What are the hallmarks of the experience of playing it? How do you characterize it in motivations and emotions?
5. Does the experience seem intentional to the player? Is it a cohesive whole or a badly stitched patchwork of concepts and systems?
6. Do players come to feel mastery, or at least greater competence? How do they know they are progressing in their skill?
7. How do the art (visual and sound) support the concept and the gameplay? Does the art differentiate the game from similar ones?
8. Which game systems directly support the concept and the experience?
9. What forms of interactivity support the experience? Are there superfluous or obscure interactions that tax the player's cognitive resources?
10. Does the game mean something to the player? Does it have heart, does it generate emotions? Not every game needs deep meaning, but it's worth considering and **asking about it in playtests** to see whether the perceived meaning matches the intended one.

## 14. Chapter 6 summary
Create the game's concept and devise an intentional, consistent and clear whole: blue-sky → refined vision of the experience → concept doc with three sections, as a pointer to detailed design and a unifying force. Starting from the concept is not mandatory, but you cannot design or develop without it; if you're an inventor or toymaker and it doesn't come naturally, do it anyway before developing. Without understanding the framework of what you are building, you wander.

---

# APPENDIX: Quick-use lists (for designing / analyzing / balancing)

## A. Design checklist by level
- **Whole**: concept statement, One Question, fantasy, key moments (learning/habitual/mastery), emotion and meaning, art/audio style, world, constraints. Verify that every system/token derives from the theme; if not, prune.
- **Loops**: core loops, immediate/short/long-term goals, progression vectors, reinforcing and balancing loops, interactivity budget, systems that operate with and without the player.
- **Parts**: tokens with the minimum of attributes/states/behaviors; concrete values (spreadsheet); balance between tokens; what info the player needs (→ UI).
- Bounce: if you get stuck on one level, switch levels.

## B. Problem signals (detection)
- A system players ignore (e.g. quests) → understand why; remove or fix.
- Accumulated exceptions and special cases → loss of consistency/resilience.
- Single-arc or hand-made content that isn't reused; breadth used to cover for a lack of depth.
- Fractured systems that "fly off separately" for lack of balance between tokens.
- A mechanism with no place for the human (inventor); a tale with no play space (storyteller); pieces with no objective (toymaker).
- A player who cannot describe the game from the concept statement (failure of "entrance").
- Target audience "everyone"; USPs impossible to write; USPs that are a sum of others' ideas; genre used as a vague label or a confusing mashup.
- Incompatible combinations of motivations in the same design (refined narrative immersion + only explosions).
- Superfluous or obscure interactions that spend cognitive load.
- Monetization, localization or scope considered at the end.
- Attachment to work done because of the time invested; not testing with new players.
- A brainstorm dominated by strong voices, a homogeneous group, a single marathon session.

## C. Games cited (one line each)
- Angry Birds: Rovio's 51 attempts; a simple, focused idea that millions like.
- For Honor: one-sentence vision ("combat as dance/art").
- Spore: prototypes with fascinating simulations (star formation) → example of an "inventor".
- Power Grid: a supply/demand system that operates outside the player's direct control.
- Splendor: chips heavy as non-functional art that reinforces the experience.
- Go: few rules, enormous space (archetype of elegance).
- Up (Pixar): a movie that changed almost everything except the bird and "up" → iteration.
- Guitar Hero / Rock Band: the "One Question" ("does it rock?" / "is it an authentic experience of being in a band?").
- Portal: a shooter that doesn't kill and shoots to solve puzzles → genre subversion.
- Undertale: subverts the RPG.
- Gratuitous Space Battles / Realm of the Mad God: shooter subgenres (2D top-down space / massive cooperative bullet-hell).
- World of Tanks: action-strategy MMO (combined genre).
- A Dark Room: idle with narrative elements; "numbers going up" + exploring the unknown.
- Rogue: origin of the roguelike (procedural levels, permadeath).
- League of Legends: example of excitement/competition that appeals more to the young.
- The Last of Us: fantasy of doing your best in a difficult situation.
- Gone Home / The Sims: fantasy of putting yourself in someone else's shoes; Firewatch, This War of Mine: meaning.
- Tetris: the emotion of "I died but better than before".
- Monopoly: teaches a model of how to get rich (meaning even in a light game).
- Candy Crush: a game with almost no meaning beyond sensory/puzzle pleasure.
- The Sims (Wright): meaning "time is the only non-renewable resource"; more possessions → more time maintaining them.
- The Division x Overwatch, GTA meets Undertale: examples of x-statements.

## D. Key terms (EN) for quick lookup
Qualities of Game Systems (comprehensible, consistent, predictable, extensible, elegant) · game designer's loop · storytellers/inventors/toymakers · thematic architecture · detailed design / spreadsheet-specific · interactivity budget · blue-sky design / ideation · yes, and... · curation · groupthink · concept document (high-level concept, product description, detailed design) · working title · concept statement · The One Question · genre · target audience (psychographics, demographics, environmental context) · Quantic Foundry motivations · Bartle · Big Five · unique selling points · x-statement · player fantasy · entrance · key moments · personas · magic circle · mood board / reference art · style guide · monetization models · scope · core loops · progression vectors · game+player system · Bushnell's Law · elegance/depth/breadth.
