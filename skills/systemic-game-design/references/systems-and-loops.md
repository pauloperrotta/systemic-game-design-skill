# Systems and loops (chs. 2 and 7)

Read this to DESIGN or ANALYZE the dynamic structure of a game: parts (state, boundaries, behaviors), sources/stocks/sinks, reinforcing and balancing loops, patterns (fixes that fail, limits to growth, tragedy of the commons), emergence, hierarchy, the four principal loops, core loops, and the three kinds of gameplay loops (engines, economies, ecologies) with their typical failures and how to correct them. It includes the system document template and the questions for reviewing your loops.

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). Square brackets give the book section each block comes from.

## Index
- 2. CH. 2 - Defining systems
- 1. Review of loops [A Brief Review of Loops]
- 2. The four principal loops [The Four Principal Loops]
- 3. The three kinds of gameplay loops [Three Kinds of Gameplay Loops]
- 4. Examples of game systems [Examples of Game Systems]
- 5. How to define a system's loops and goals [Defining a System's Loops--And Goals]
- 6. Tools for designing game systems [Tools for Designing Game Systems]
- 7. How to document your systems [Documenting Your System Designs]
- 8. Questions to consider about your loops [Questions to Consider About Your Game Loops]
- 9. Failure catalog and diagnosis (operational synthesis for analyzing/balancing)
- 10. Heuristics and rules of thumb (flat list)
- 11. Index of game examples (one line each)
- 12. Key terms (quick glossary)
- Appendix: ways of thinking and real-world loop examples (ch. 1)

---

## 2. CH. 2 - Defining systems

### 2.1 Short and expanded definition [What We Mean by Systems / A Brief Definition]
Short definition: **a set of parts that together form interaction loops to create a persistent "whole"; the whole has properties and behaviors of its own that do not belong to any individual part.**

Expanded definition (the author's list):
1. Systems are made of **parts**. Each part has an **internal state** and external **boundaries**. Parts interact through **behaviors** that send information or (more often) resources to other parts in order to alter their internal state.
2. Behaviors form **loops**: local ones (A->B) and transitive ones (A->B->C->A).
3. Systems are organized into **hierarchical integrative levels** that arise from emergent properties of their loop structures. Each level shows organized state and behavior = being a part of a larger system.
4. At every level there is **persistence and adaptability**: the system does not fall apart quickly (it reinforces itself) and it tolerates/adapts to external conditions.
5. **Organized, decentralized yet coordinated** behavior: there is no central controller. The whole is in turn a part of a larger one.
Corollary: top-down and bottom-up are equivalent; the designer needs to be able to see the game bottom-up, top-down, or somewhere in between.
The author's quip: "This sentence is a system" (letters and words generate emergent meaning).

### 2.2 Parts: state, boundaries, behaviors [Defining Parts]

**State:** a combination of attributes, each with a value at every instant. A part's state = the aggregate of its current values; it changes only if other parts affect it.
- In the real world, state emerges from subsystems further down; in a game it sometimes does too (the "health of the forest" = an aggregate of trees), but **at some point you have to "hit bottom"** with simple attribute/value pairs (integers, strings). Examples: a chess piece = type + position; a monster = 10 HP, named Steve.
- **"Spreadsheet specific"** (level of specificity): you cannot build a game until every vague thing is brought down to spreadsheet-level values/attributes. But that floor is NOT a ceiling: you can build **second-order design** by grouping simple parts into richer subsystems so you do not depend on costly content creation. Heuristic: look for opportunities to group simple parts into larger systemic wholes.

**Boundaries:**
- A boundary is **emergent**, defined by the interaction neighborhood of the subparts: whatever is heavily interconnected (with loops) forms a subsystem = a higher-level part. There is no explicit "skin" (except in cases like the cell membrane); it is fuzzy.
- **Practical inside/outside rule:** if something can change the system's overall behavior, it is inside; if it communicates with a part but cannot alter the system's behavior, it is outside.
- The boundary is a form of **modularity** (emergent, or imposed in software): it makes parts understandable and reusable and avoids the temptation of centralized control ("small pieces loosely joined", Weinberger: the Web; if one page goes down the rest keeps working).

**Behaviors:**
- What a part does: typically create, change, or destroy a system resource, communicating a change of value to other parts. A part can affect itself (a monster that heals itself; compound interest).
- **Encapsulation:** one part can perturb another, but each part decides on its own how its state changes and whether it ignores the message. Nobody "reaches into" someone else's state. (Design/architecture implication: events/messages, not direct writes.)

### 2.3 Sources, stocks, and sinks; flows; resources [Sources, Stocks, and Sinks]
(There is no canonical notation; the author uses utilitarian terms.)
- **Source:** a part that increases the state of another. Typically assumed to be inexhaustible. Its internal state = a generation rate (e.g., 2 units/sec). It stores nothing; it generates and passes along.
- **Stock:** accumulates a resource; its state = the amount at a given moment. It can have a cap (the bathtub). Examples: a bathtub, a bank account, HP, the provinces of an empire.
- **Sink:** the outlet of the stock; it passes along an amount per unit of time; if the stock is empty nothing can pass (unlike the source).
- **Flow:** the connector between parts; it carries messages or, more commonly, a resource.
- **Resource:** anything countable, storable, or exchangeable, even if it is not physical (HP, provinces).
- **Converters:** transform one resource into another/a process. **Deciders:** measure and decide (too slow? too fast?) and feed back to speed up/slow down. Source->process->sink + deciders = the centrifugal governor; this is what makes the scheme "systemic" (it closes a loop).
- You have to **draw the design boundaries**: whatever is outside is modeled as an unlimited source/sink (e.g., assuming water and electricity come from outside). In games, you have to specify all the sources (faucets) and sinks (drains) and how they affect the game.

**Faucet/drain economy (Ultima Online, Fig. 2.3):** an early MMO modeled as faucets (spawns, NPCs that buy, payment in gold) -> stocks (natural resources, raw materials, goods, inventory, vendors) -> drains (decay, degradation, selling to an NPC, failed manufacturing).
- Problems: (a) player stocks are unlimited and the exit is not guaranteed (one player hoarded 10,000+ shirts; every object has to be tracked); (b) **inflation**: gold is created ex nihilo each time a monster is killed or something is sold to an NPC; if the money supply grows faster than what drains it, each unit is worth less to the player.
- Balance heuristic: for each resource, list faucets and drains with their rates; if faucets > drains in the steady state, there is inflation/accumulation; you need to add drains or caps on the stocks.

### 2.4 Complicated versus complex [Complicated Versus Complex]
- **Simple collection:** parts without behaviors that affect the state of the others (a bag of bricks, a fruit bowl). Not a system.
- **Complicated process:** many parts and interactions, but connected in a **linear sequence without loops**. Predictable and repeatable; when it fails it can usually be traced to one cause and the piece replaced (reductionist thinking can be applied). Examples: a simple pendulum, an assembly line, a rocket to the Moon (phases with no backward effect).
- **Complex system:** the parts form **loops**; a part's behavior feeds back to alter its own future state (A->B->C->A, with delay). You cannot "unroll" the loop without destroying its nature. Examples: the human body, an economy, hurricanes, termite mounds, a double pendulum, many games.
- **Implication for games:** games made of sequential levels are more complicated than complex: what happens in level 10 does not affect level 2; a played level loses its value and demands the creation of more content. (See 3.8 content vs. systems.)
- Diagnostic signal: if when something fails you can trace a single cause -> complicated. If the problem is distributed/circular -> complex, and you need to analyze the entire system.

### 2.5 Loops [Loops]
Loops are "the most important structures of systems and games". Two basic types:

**Reinforcing loop (positive feedback):** each part increases the output of the next. If a system does not have at least one primary reinforcing loop, it tends to die out (exception: stability through mutual opposition, like buttresses). In games: it rewards those who are winning, magnifies early success, **destabilizes**, and can produce a runaway winner if someone capitalizes just slightly better. Names: "snowball", "rich get richer", "vicious cycle" (if everything is going down it is still reinforcing, not balancing).
- Examples: bank interest (balance -> interest -> balance); **Monopoly** (more cash -> more properties -> more rent -> more cash).

**Balancing loop (negative feedback):** each part reduces the activity of the next; it maintains or restores equilibrium. In games: **it forgives whoever is behind, stabilizes, and prolongs the match**, and keeps the leader from pulling away for good.
- Examples: an oven thermostat; **XP in an RPG** (each new level raises the XP needed for the next -> slows down the speed of leveling); **the blue shell / spiny shell in Mario Kart** (a random item for whoever is not in first place that specifically attacks the leader and knocks them down).

Notation: in causal diagrams, an arrow with "+" = more of the origin -> more of the destination; "-" = more of the origin -> less of the destination. The nodes are stocks.

**Every system has both types.** The centrifugal governor reacts in both directions. But the output is almost always **nonlinear** with respect to the input, and that is what makes it interesting.

### 2.6 Nonlinearity: predator-prey [Combined, Linear, and Nonlinear Effects]
Lynx-hare example: hares reproduce (reinforcing, small loop) and lynx eat them (balancing, large loop). Emergent result: a **nonlinear, out-of-phase oscillation** (prey peaks, then predator peaks, then prey fall, then predators...). Predators are never as numerous as prey.
- Reason for the nonlinearity: killing one prey also removes all of its future offspring (a multiplicative effect, not an additive one).
- Rule: **do not extrapolate linearly** a growing quantity; "if we keep going like this..." almost never comes true.
- Not all nonlinearity is periodic; it can be chaotic (double pendulum).

**Lotka-Volterra equations (mathematical model):**
- Prey: dx/dt = a*x - b*x*y (they grow by a*x; they die by b*x*y, proportional to prey-predator encounters).
- Predators: dy/dt = d*x*y - g*y (they gain d*x*y depending on available food and conversion efficiency; they die by g*y).
- Parameters: a (alpha, prey birth rate), b (beta, successful predation rate), d (delta, efficiency of turning food into offspring), g (gamma, predator mortality).
- Real data (MacLulich 1937, Canada) show similar but noisier oscillations.

**Mathematical versus systemic modeling:**
- The mathematical model is concise but opaque: it treats parts as aggregate symbols and parameters as **knobs** on a black box, with non-obvious effects.
- In systemic design, those aggregate parameters should **emerge** from interactions among the parts' internal states (e.g., the predation rate comes from the lynx's attack vs. the hare's defense), which makes the model more understandable and nuanced.
- Even so, you have to decide the lowest level of detail and put parameters there (including random values) as a representation of what lies beneath.
- Every model is an approximation (scale model vs. real ship): its value is being useful, not exact. In games, "you are making a model of a part of the world".

### 2.7 Randomness vs. chaos [Chaos and Randomness]
- **Random effect:** an unpredictable value within a range (e.g., 1-10 with 10% each); the future state cannot be deduced from the current one. In games it is used to **simulate low-level systems that are not modeled** (variable damage instead of simulating 1,000 factors) and to give the higher-level system variability so it is not predictable and boring.
- **Chaotic effect:** **deterministic** (in principle predictable if you know the whole state) but hypersensitive to initial conditions (double pendulum). You cannot analyze it by taking it apart; you have to analyze the whole (subparts + relationships, or math).
- **Resonance events:** many small chaotic events combine into a reinforcing loop and produce an enormous nonlinear result.
  - Tacoma Narrows Bridge (1940): wind makes the bridge oscillate, the oscillation increases wind capture -> collapse (dominant reinforcing loop).
  - Albert Bridge (London): a sign asking troops to break step (synchronized steps -> resonance).
  - Synchronized fireflies: each one advances its flash slightly when it sees another; with no director, the population goes from chaos to resonance (patches -> waves -> unison). Also heart nerve cells. Lesson: emergent synchronized order from a single local rule.

### 2.8 Loop patterns (archetypes) [Examples of Loop Structures]

**a) Fixes that fail / unintended consequences loop:**
- Cobra effect: problem "too many cobras" -> solution "bounty for heads" (internal balancing loop) -> but an external, **delayed** reinforcing loop ("let's breed cobras!") brings the problem back worse (when the bounty was canceled, more cobras were released than before).
- Traits to detect it: a quick fix that works at first; a second, slow, hidden loop (delay marked with "\\" in the diagram) that reverses the effect; the problem ends up worse and time/energy was spent on an illusory solution. Examples: not maintaining the car to save money; the manager who makes quick fixes and gets promoted.
- In games: the strategy player who quickly builds a big army loses to the one who invests in upgrading troops; the choice **"build fast now" vs. "invest for the future"** is a structure called an **engine** (seen in ch. 7). For the designer: beware of rules/rewards that players can exploit with a loop you did not foresee (the equivalent of "breeding cobras"); and of balance patches that bring a delayed rebound effect.

**b) Limits to growth and subsequent collapses:**
- Two linked loops: one reinforcing (actions -> results -> more actions) and one balancing, fed by a **limiting condition** (a needed resource that the growth consumes: saturated market, soil minerals, ability to pay).
- Result: an **S-curve** (rises slowly, then fast, then flattens). Example: wheat yields flattening since the 90s. Rule: for all growth fed by reinforcement there is a balancing loop fed by a limiting condition; **always look for it**.
- Sometimes the limit appears **abruptly** and a reinforcing loop fires in the reverse direction ("vicious cycle"): the 1929 crash (buying on credit "on margin", 10-20% reserve; when prices fall you have to sell more to cover, which lowers prices further). A current example (2017): subprime loans; wealth concentration pushes investors toward risk and borrowers toward more debt; two unsustainable reinforcements.
- For games: every exponential growth mechanic (economy, character power) needs its limiting condition designed; if the limit is abrupt, the collapse can be a death spiral.

**c) Tragedy of the commons:**
- Each actor has its own reinforcing loop (more cattle -> more value); all consume a shared resource with a limit; total use forms an external balancing loop that exhausts the resource for everyone. Nobody wants it or feels responsible (garbage, pollution).
- Lesson: **systemic responsibility = distributed responsibility**; there is no "villain" and no single root cause.
- In games: any limited resource that several actors want to maximize (gold mine, animals). Example: players hunt rabbits for food -> the population collapses -> without rabbits the lynx die -> the plague they controlled is lost.

**d) Trophic cascade** (Yellowstone): a chain of reinforcing and balancing loops; the wolf reduces the elk (balancing) and therefore indirectly increases trees, bears, etc. (transitive reinforcement). Method for untangling it: identify the stocks/resources and the behavioral relationships (arrows) between them.

### 2.9 Emergence [Emergence]
- When reinforcing and balancing loops are in dynamic equilibrium, there is **metastability** and organized behaviors appear that exist in no single part (flock, molecule, synchronized fireflies).
- **Emergent effect:** properties qualitatively different from those of the parts, not a simple sum.
- **School of fish example:** the total weight of the school is NOT emergent (a sum); the **shape** (baitball) IS: it is in no fish, and no fish is in charge.
- **Emergence test** (three conditions; if they hold, there is a "new thing"): (1) no individual part determines it; (2) it is not the linear sum of the parts' attributes; (3) it is described more easily by the aggregate than by the detail of parts and relationships.
- There is no "central controller" ("no fish in charge"): even scientists assumed "founder cells/pacemakers" in aggregating slime molds; people had to learn to see distributed control. This applies to design: resist the temptation to add an omniscient director/controller when a local rule is enough.
- **Upward causality:** the parts' interactions cause the aggregate phenomenon (individual purchases -> the market rises).
- **Downward causality:** the aggregate affects the parts (a falling market makes everyone sell more; the size/shape of the school conditions each fish). This explains "irrational" bubbles/crashes. When you take a system apart you see the upward causality but lose the downward (it exists only while the system is running) -> reductionist analysis is not enough.
- Author's design note (ch. 3): the lack of an intrinsic theme/goal = absence of downward causality in the design (see No Man's Sky).

### 2.10 Hierarchy and levels of organization [Hierarchy and Levels of Organization]
- A metastable system creates a "new thing" at a **higher level**; its properties (state, boundaries, behaviors) emerge from the interactions of the lower levels. Quark -> proton -> atom -> molecule -> ... planet -> galaxy.
- Every system is part of a larger one, interacts with peers, and contains smaller systems. **In games you can choose the levels of abstraction**; making them deeper rather than shallower has rewards.
- Levels are emergent, not absolute.
- **Persistence** = "boundary through time": the system reinforces itself within its boundaries. **Adaptability:** it tolerates changing signals/inputs. In living things: **homeostasis** (keeping internal conditions within a narrow range despite external changes).
- **Structural coupling (Maturana):** two systems that interact recurrently shape each other until they form an integrated higher system (rider-horse, car-driver, flower-insect). **Game + player** form a structural coupling: if the game has a broad, diverse state space (second-order design), it adapts to the player while the player adapts to it; this generates engagement (it is hard to leave the loops).

### 2.11 Systemic depth and elegance [Systemic Depth and Elegance]
**Depth:** the system has parts at multiple levels of organization (parts that are subsystems). Self-similarity (fractals/romanesco) = a visual manifestation of depth.
Benefits of games with depth:
- The player builds multilevel mental models and is rewarded for learning each subsystem ("opening a gift and finding another inside").
- Great explorable variability because the designer defined a broad space (systemic design) rather than a narrow path of content.
- They can have **few rules** (Go: board + alternating stones + capture/surround + territory) and be very deep. **Bushnell's Law:** easy to learn, hard to master: few initial rules, each opening into subsystems as it is learned.

**Elegance** - when the following combine:
1. **Metastable** uniformity, not static: the game changes every match but keeps an overall familiarity (theme/experience).
2. High-level systems that are **simple to define but have great hierarchical depth**: the player discovers the depth gradually and builds a mental model; it gives rise to complex behaviors that in turn reveal systems and theme.
3. **Symmetry / self-similarity:** each lower system mirrors the structure of the one above; they need not be identical, but similar enough that the upper level serves as learning **scaffolding** -> a feeling of "I almost know this already".
4. **Few loose ends:** few exceptions and special cases (they break the mental symmetry and raise cognitive load).
5. After learning it, the player can reflect (metacognition) and appreciate the depth and symmetry; the game is enjoyed also by thinking about it.
- It is rare; it requires the designer to see everything at once and also linearly, as the player experiences it.

### 2.12 The whole of the design [Wholes]
- The whole the designer is after **is not the game alone, but the game+player system** (the game as experienced + the player acting). The game is the medium.

### 2.13 Operational summary of ch. 2 (final definition)
A system = an integrated whole of independent, interacting parts, with internal state, boundaries, and behaviors; the whole persists, adapts to external conditions, has coordinated emergent behaviors, contains lower-level systems, and is part of a higher one. Things and systems are the same (a marriage, a university, a conversation are real, metastable "things").
- A system is more than the sum of its parts when the parts connect into **loops**; this is where emergent behavior and interesting gameplay come from. [More Than the Sum of the Parts]
- "Systems design" = building effective loops out of interacting parts to obtain the desired total experience. It is not just "making the combat system": it is all the scaffolding that generates the experience.
- The designer's working hierarchy: **parts -> loops -> whole**. You have to oscillate between the three levels all the time.
- A game is almost always a combination of systems at different hierarchical levels; each system is a part of a larger system (systems of systems, loops within loops).
- What the designer does with this: (1) identify, (2) analyze, (3) create systems, breaking them down into their constituent loops. [Summary]

---

## 1. Review of loops [A Brief Review of Loops]

### 1.1 Kinds of collections of parts (ch. 2)
- Simple: parts that do not affect each other (fruit in a bowl).
- Complicated: linear connection (a process).
- Complex: parts with interactions that **feed back on themselves** (loops). Only loops give rise to emergence.

### 1.2 Reinforcing vs. balancing loops
- **Reinforcing loop ("positive feedback")**: the interaction reinforces the state of the parts. "Positive" does not mean good: it reinforces whatever quality is involved (compound interest = good; disease contagion = bad). Examples: bank interest, an epidemic, Monopoly.
- **Balancing loop ("negative feedback")**: one part's effect on another pushes everything toward an equilibrium point. Examples: thermostat/oven (the smaller the temperature gap, the less heat), predator-prey, the increase in XP required per level in RPGs (it evens out the time to level up).
- Almost all balance in games is **dynamic, not static**. A physical example: the centrifugal governor: throttle open -> engine faster -> weights spread -> throttle closes -> engine slower -> weights drop -> throttle opens... it oscillates within an acceptable range.

### 1.3 Uses in design
- **Reinforcing = rewards the winners / runaway / "rich get richer"**. Example: Monopoly (more money -> more properties -> more money). Commitment failure: the winner needs to pay less and less attention to keep winning; the loser has fewer and fewer options. The decision space collapses for both -> the game stops being psychologically engaging.
- **Balancing = reduces differences between players** ("forgive the loser, punish the winner", or both). Examples: turns where the advantage goes to whoever scored (possession in football/basketball); Power Grid (the best-positioned player plays last: a permanent balancing loop against the reinforcing loops of money/plants/cities).
- Rule of thumb: in most games reinforcing loops predominate (progression: the avatar becomes more powerful); balancing loops act as brakes/regulation. [Three Kinds of Gameplay Loops]

### 1.4 Parts as loop components (base vocabulary)
(Parts are detailed in ch. 8; here only the minimum needed to assemble loops.)
- **Resources**: objects passed between parts of the loop. Everything *countable* in the game (gold, mana, water in a bathtub, wood, troops), especially if it is created, destroyed, stored, or exchanged.
  - **Simple resources**: elemental and fungible (gold, wood, mana): one unit is worth as much as another.
  - **Complex resources**: assembled from others and with properties assigned by the game (a sword made of wood + metal; an army = conscripts + swords + armor).
  - **Production chains**: wood + metal -> swords/armor -> + recruits -> army. E.g., Terraria, Banished: systemic depth through long chains of combination.
- **Currencies**: a kind of resource that is **exchanged but not consumed** (the gold paid to a vendor does not "become" the weapon; the vendor reuses it). The key difference from ordinary resources (which are consumed in the conversion). In simulation it is assumed to be spent on something else outside the system; in many games the gold simply disappears into a sink.
- **Sources ("faucets")**: where resources come from; they can be a place (gold mine) or conceptual (killing monsters gives XP). They usually create resources *ex nihilo*; modeling buried gold adds cognitive load with no fun unless that is the point of the game.
- **Stocks ("pools")**: containers of resources. State = current amount; behavior = flow rate toward another part. Resources flow from the source (or another stock) into the stock at a certain rate up to a limit. Examples: money in the bank, HP, a town's population. Some have a maximum (bathtub), others do not (bank account).
- **Converters**: transform one resource into another (the original disappears, the new one is created). They are the basic "verb" of how something becomes something else. They can be a magic box (iron -> steel) or a process with multiple inputs/outputs (metal + wood + tools + skill + time -> sword + waste such as slag/heat). Design decision: more conversion detail gives more gameplay (how do I handle the accumulation of waste?) or is useless mental load.
- **Deciders (decision points)**: logic branches where the flow goes one way or another depending on internal logic, the amount of a resource, or external conditions. **Rule**: keep the decider's conditions as *local* as possible (at its own level of organization; at most one level up or down). Greater hierarchical distance = a more **brittle** system.
- **Sinks ("drains")**: the opposite of the source; resources flow outward. It does not matter where they go: whatever is beyond the sink is outside the system (a valid simplification for design).

### 1.5 Iconography (adopted from Joris Dormans / Machinations; not universal) [Iconography]
- Upward triangle = source.
- Circle = stock (quantity: individual tokens, shading for how full it is, etc.).
- Triangle with a line = converter.
- Diamond = decider.
- Downward triangle = sink.
- Arrows = flow between them. Loop diagrams are drawn with these symbols; you do not need to master all of Machinations to use the concepts.

---

## 2. The four principal loops [The Four Principal Loops]

Full list (the four the designer must keep in mind):
1. **Game's model loop**.
2. **Player's mental loop**.
3. **Interactive loop** (game-player).
4. **Designer's loop**.

### 2.1 The Game's Model Loop
- The game has an internal model of the world that is **dynamic and looping** (if it were static or linear there would be no interactivity or gameplay).
- That model creates the world the player sees and the gameplay space. Few viable paths = a narrow **probability space** = few meaningful decisions = no gameplay, no engagement, no fun.
- Designing the model through *second-order design* creates the player's space of exploration.
- The model = the combination of all the game's systems; types: **engines, economies, ecologies**. Familiar systems come out of this: progression, combat, inventory, skills, quests, etc.

### 2.2 The Player's Mental Loop
- The player's mental model is also dynamic and looping. It is built while playing (and the player must stay engaged while building it) and must **closely match** the internal model.
- If actions have unexpected or, worse, random effects, the player cannot build or verify their model -> a meaningless, unengaging experience.
- It includes **explicit** goals (set by the game) and **implicit** ones (set by the player). The sense of progress from achieving them usually comes from one or more progression systems.

### 2.3 The Interactive Loop
- The game<->player cycle: the player acts, the game gives feedback, the player learns. It subsumes both the game's model and the mental model (each is a subsystem of this loop).
- Player actions = input to the game's loop; the state change is communicated back = input to the player's model.
- **Until this loop exists, the game does not functionally exist.** Systems alone do not create the experience. "Closing the loop" (the player can decide, act, and receive feedback from the internal model) is the first sign that the intended experience might exist.
- It extends to multiplayer: each player must predict the game *and* the other players; the game is the referee of the magic circle. The game shows how others' plans are expressed through their structures, not the plans themselves.

### 2.4 Core Loops [Core Loops]
- **Core loop** = the game-player interactions that form the player's main focus / central attention. Sequence: forms an intention -> executes it -> changes the internal model -> feedback (often more skill or information) -> learning (updated mental model) -> new intention.
- At least **one** core loop; there can be several at **different time scales** (see the interactivity types from ch. 4: Action/Feedback, Short-Term Cognitive, Long-Term Cognitive, Social, Emotional, Cultural; Fig. 7.2). E.g., an RPG with fast combat (action/feedback + short-term cognitive) as the primary loop and long-term skill acquisition as an outer loop. The core loop changes when attention changes (from combat to choosing skills).
- **Inner / outer loops**: inner = short and fast; outer = long. "Core" does not mean the fastest or innermost, but **the most important to the player's experience at that moment** (sometimes: where the most time is spent, or the one the designer believes gives the most value; the term is not used consistently).
- Strategy: the player alternates building structures -> making units -> fighting -> researching; that core loop is made of shorter core loops.

**Examples of core loops (one line each):**
- *Clash of Clans*: three loops - collect (click on sources, store in stocks up to a limit), battle (high tension, deciding when/where to deploy troops; returns with gold/elixir/ranking), build & train (low tension, spend gold/elixir on structures that are sources - mines, collectors -, unit producers, or stocks). Limits: source rates, storage capacity, training slots; upgrading structures is limited by the Town Hall level. **F2P lever**: building and training take time; gems (earned or bought with real money) speed things up or buy resources = "money for time". Nested goals: "I upgrade the storage so I can upgrade the Town Hall so I can upgrade the barracks...". Outer social layer: clans. Each spending decision is part of a reinforcing loop (more/better units) and a balancing loop (spending blocks other decisions) -> meaningful decisions.
- *Marvel War of Heroes*: two selectable reinforcing loops, PvE (missions) and PvP (opponents), with different internal balancers (stamina in PvE, attack power in PvP) that limit how many rounds you can play without resting or paying for a refill. Outer loop: combining/upgrading heroes (flashy instant feedback + long-term strategic trade-offs) -> better performance -> more rewards -> more upgrades; it is the main commercial opportunity.
- *Boomshine*: a single click per level and watch the result; a short game, but the player creates their own outer loop (replaying to improve their model/skill).
- Recurring pattern: a **high-tension action loop** (battle, puzzle) + a **low-tension building/crafting/trading loop**. The first uses action/feedback and short-term cognitive; the second long-term cognitive, emotional, social. (The author's biological analogy: the sympathetic "fight or flight" system vs. the parasympathetic "rest and digest".)
- The same loop diagram can be drawn more abstractly or in more detail: **the level of detail should be chosen according to what is most informative for the audience** (devs, business, players).

**Summary**: if the core loops cover several durations of interactivity, the game hooks immediately and for a long time. Simple games = one core loop, a short experience.

### 2.5 Game Mechanics [Game Mechanics]
- Systemic definition: a **mechanic** is an identifiable interactive loop between player(s) and game, generally independent of the game's context (drawing a card, territory control, jumping on platforms, push your luck, rolling dice, resource management). It can be quick and simple with no subsystems, or long and composite.
- Without this definition, mechanics remain "fuzzy chunks of gameplay".
- **Core mechanic / core gameplay**: the mechanic the player encounters repeatedly (it incorporates the meaningful chunk + the idea of a core loop).
- **Genres** form when many games repeat similar mechanics (platformers: jump + double jump, moving platforms, wall jump; RPGs: combat, loot, gaining power). Familiarity helps the player build their mental model.
- The author does not make a list of mechanics; he prefers to look at the three kinds of loops (engines, economies, ecologies) and combine them.
- Existing pattern lists cited: Bjork & Holopainen (2004), Adams & Dormans (2012). Many designers find them of little use and prefer general patterns as hierarchical building blocks.

### 2.6 The Designer's Loop [The Designer's Loop]
- It is the outermost loop. The designer sees **game + player as a unified system from the outside**; both are necessary subsystems.
- It is a **balancing loop**: design -> experienced by the player -> feedback -> gap between the designer's intent and the player's experience -> the designer changes the design to reduce the gap -> repeat.
- Believing, testing, and adjusting the internal model is the essence of design. **Until you see players interacting with the game, the game "does not exist"**: a set of rules is not a game; not even a simulation (a model that runs by itself) is. Only with the game+player system operating does the designer's loop exist (detailed in ch. 12: prototypes and playtests).

### 2.7 Levels and hierarchy [Levels and Hierarchy]
- Systems contain systems. The interactive loop has the game and the player as parts; the interactive loop is part of the designer's loop (together with the designer's plans and goals).
- Critical skill: building systems of systems **knowing which level you are working at without losing sight of the total experience**.
- **Deer/wolves example (Fig. 7.6 and 7.7):**
  - Low level (Fig. 7.6): a deer system with a mainly reinforcing loop (more adult deer -> more births) with a balancing component (more deer -> less food -> fewer births). Food enters as an external source; death is a sink. The system's edges are marked with a dotted circle.
  - High level (Fig. 7.7): the entire deer system becomes **a stock** inside a larger system with wolves and plants. More deer -> more wolves (at the expense of deer: a mini balancing loop); deer vs. plants (another balancing loop); dead deer and wolves -> soil -> plants (**deer-soil-plant reinforcing loop**, which could run away, but is held in check by deer eating plants and wolves eating deer). The **different growth rates** of plants, deer, and wolves are what balance the whole. The deer system had an external source and sink; at the high level they become stocks that can be systems in their own right.
  - Lesson: what was "external" (a simple source/sink) at one level becomes part of the system at the level above. A diagram at a more abstract level encapsulates the previous one.

---

## 3. The three kinds of gameplay loops [Three Kinds of Gameplay Loops]

Every system is "a machine that does X" ("I want a machine that makes deer", "a deer-wolf ecology"). It does something because its parts (often systems themselves) interact in loop structures.

Systems mix reinforcing and balancing according to their purpose. In most games **reinforcing loops predominate** (they allow player gain/progression). The behavior of the parts is usually to increase, decrease, flow, convert, or exchange resources between parts; the loop can use the same resource or convert/exchange one for another.
- Reinforcing = "gaining" (resources grow over time); balancing = "maintaining" (resources fall to a predetermined level or to a dynamic balance).

**Taxonomy (two axes: reinforcing/balancing x same resource/exchanged resources):**
| Type | Nature |
|---|---|
| **Engines** | Reinforcing or balancing with the **same** resource |
| **Economies** | Reinforcing, **exchanging** resources |
| **Ecologies** | Balancing, **exchanging** resources |

### 3.1 ENGINES

Two variants: **boosting** (reinforces; adds resources to the game) and **braking** (balances; drains them).

#### 3.1.1 Boosting engine
- **What it is**: a system that adds resources to the game and lets the player choose between **using them now to act** or **investing them to have more flow in the future**. (Adams & Dormans call it a *dynamic engine*; a simple source is a *static engine*.)
- **Pieces**: source -> resource flows -> decider (player: do I build the engine or use the resource?) -> branch A: "increase the source's flow" (investment; closes the reinforcing loop) / branch B: "act in the game" (ends in a sink, with a short-term reward and a spent resource). Fig. 7.8.
- **Core decision**: when to invest vs. when to act. It tends toward long-term cognitive (strategic) when it is a core loop. If it is not played strategically you lose; if you invest too much and act too little, you can also lose.
- **Examples**:
  - *Monopoly*: $1,500 to start, $200 from the bank per lap (source); you invest in properties that generate more money; secondary engine: houses/hotels with a color monopoly. Reasons not to invest: waiting for a better property, having cash to pay rent/costs.
  - *Dominion, Power Grid, Splendor*: tabletop engine building. Splendor: cards bought with gems give "free" gems every turn (more flow) and also victory points; the decision is whether to spend only for future capacity or spend more to also score points.
  - PC strategy: spending on combat units vs. on facilities that build better units; outer loop: sending units to gather resources at the risk of losing them.
  - *Star Realms*: the individual core loop = engine building; combat between players is the brake.
- **How it fails (boosting engine problems)**:
  1. **Runaway (rich-get-richer)**: being reinforcing, without balancing loops it runs away. E.g., *Rampart* (1990) - after each round you rebuild the castle with more walls and cannons depending on performance; whoever started winning could not be caught; the only balancer was putting coins into the arcade machine (on coinless consoles the flaw became evident).
  2. **Stall from insufficient resources**: Monopoly with $500 starting money: few assets and a risk of quick bankruptcy. A fantasy where the only gold comes from a monster that can only be killed with a magic weapon bought with that gold = **deadlock** (the loop ends before it starts because the resource earned by running it is needed to start it).
  3. **Cost mismatch**: if units are cheap and do not die, the player accumulates enough of them and devotes everything to investment -> runaway or rapid escalation for everyone. Escalation can be exciting if players balance each other (typical in mobile strategy), but it ends in **content starvation** (units/content run out). Fixing with exponentially growing costs (balancing) **only delays, it does not prevent** content exhaustion (progression curves in ch. 10).
  4. **Dominant strategy**: when the balance between investing and acting is tuned too finely, players optimize and the space of paths collapses into a single optimal strategy (always preferable, highest probability of winning). E.g., a weapon+armor combination that beats all others; a unit that beats all others. Consequence: no meaningful decisions; players either rush toward the recipe or discover it and get frustrated because others already knew it -> the fun evaporates.
- **How to fix it / keep it healthy**: explicit balancing loops (production rate, how much the flow can grow, how much the player must spend on acting rather than investing, other counterweights), catch-up or brakes, rising costs, and making sure there is no single optimal option.

#### 3.1.2 Braking engine ("friction structure")
- **What it is**: balancing loops predominate; a source generates a resource but the loop's action **reduces it** and sometimes reduces the frequency/amount of future gain. Analogy: a car's brakes, the centrifugal governor. Adams & Dormans: *friction structures*.
- They appear as **parts inside other loops**, rarely alone. Function: regulator/brake on the player's progress.
- **Examples**: stamina and attack power in *Marvel War of Heroes* (without them you play with no restriction); the Chance card "make repairs" in Monopoly (pays depending on houses/hotels -> drains resources and also does *rubberbanding*, because it hits whoever has many properties far harder than whoever is behind). Other forms of friction: conditions the player must attend to that divert resources from progression (maintenance, repairs).
- **How it fails - "slowing to a stop"**: if the regulation is too severe and overwhelms the main reinforcing loop (of a boosting engine or economy), the player is left without resources to act and the game stops. It is like a car with dragging brakes: too much energy is taken out of the system. E.g., a repairs card that was more frequent or more expensive in Monopoly would leave the player with no action.
- **How to fix it**: calibrate the friction so it is smaller than the reinforcing engine; make it proportional (punish the leader more than the one who is behind).

### 3.2 ECONOMIES

- **Operational definition**: a system dominated by a reinforcing loop where the increase in resources or value comes **not from internally investing** a resource (that is a boosting engine) but from **exchanging or converting one resource into another with a nonlinear gain in value**. Quote from Brian Giaime (2015): a game economy = the dynamic exchange of resources, time, and power between systems and entities, exchanged because players perceive a gain in value.
- **Key difference between engine and economy**: engine = same resource, investment; economy = different resources, exchange/conversion. In an economy the player uses a resource for an action or exchanges it for another that gives more capability.

**The wood example (Fig. 7.9):**
- A worker needs 1 bread to cut 1 wood. If 1 wood is traded for 2 breads, the player gains the capacity to cut 2 more woods (after a delay, e.g., the next turn) = the core of the reinforcing economic loop. The delay prevents instant runaway.
- Outer investment loop: build a **sawmill**: 1 wood -> 1 plank (lumber), and 1 plank = 4 breads. A strongly **nonlinear** increase in capacity and value.
- **Costs of the leap** (timing and investment decisions = the heart of economic gameplay): (1) accumulate wood to build the sawmill (boosting-engine-style investment); (2) assign a worker (a scarce resource) to the sawmill -> less wood is cut; (3) extra conversion time; (4) repay the investment of time and wood that could have been traded directly for bread.

**Unfolding Complexity:**
- New objects, resources, and currencies can be introduced as the game advances: first only bread and wood; once that is mastered, the sawmill and the plank appear -> a new loop, an expanded mental model, more decisions (when to build it, how many workers).
- **Production chains** introduced over time (Fig. 7.10): ore mine -> ore -> smelter + chimney -> iron -> smithy -> steel -> weapons; each step requires a building, workers, and sometimes knowledge (an academy to turn workers into smiths). E.g., start by selling ore, then refine it into iron and see that it pays enough to justify the extra steps, up to multiple production routes.
- Benefits: exploration, mastery, and achievement as the mental model grows; multiple interlocking loops = a wide play space and long-term commitment. For those who enjoy building/managing chains.
- Specialized roles among players: each produces some resources and trades others (with another player or an NPC).

**Currencies in economies [Currencies]:**
- They act as a catalytic resource: they enable exchange without being consumed (like a chemical catalyst). Money that both the woodcutter and the baker use.
- In many game economies currencies are destroyed anyway via sinks when spent.
- Extra property: **near-universal use** (unlike resources with few uses). 1,000 coins -> training, weapons, information, or saving: many options + a feeling of valuable reward.
- Risk: inflation and stagnation. **The player has to perceive that the currency has exchange value**, otherwise it is a nuisance. Balancing it so it keeps its value without becoming too precious is a hard problem, to be viewed **at the level of the whole economy** and not per part; it requires a lot of iterative tuning (resource creation rates, prices, etc.) to reach a stable but dynamic economy.

**Economies with engines [Economies with Engines]:** it is common for an economy to have engines as subloops (selling wood for bread vs. investing it in the sawmill). Having sources whose resource can be used for internal investment or profitable exchange is the core of many good games: short-term vs. long-term gain trade-offs.

**Examples of economies [Examples of Economies]:**
- **Typical RPG**: "I kill a monster, get loot, buy things". The player exchanges **time** and **character health** (and weapon/armor wear) for loot (XP, skills, better weapons/armor, gold to buy or repair). Each encounter does not guarantee a reward -> a **variable schedule** of reward: rewards at unpredictable moments; it produces more engagement (persistent, focused behavior) and dopamine spikes per reward than a regular schedule; especially useful in action/feedback interactivity; it explains why we persist in games, gambling, the stock market. **Combat** is an ecology that is a subsystem of the larger economy.
- **Traditional trade economies**: barter or with currencies; every resource must have value to the buyer. In a healthy economy buyers satisfy needs or create value (the smith turns ingots into weapons). **That increase in value is what drives any economy** and keeps the reinforcing loop going.
- **Multi-resource, multiple buyers and sellers** (human or NPC): resources have different relative value depending on needs and budget. With many transactions prices settle into a narrow range; with few transactions they fluctuate widely (lack of history/precedent).
- **Supply and demand**: more interest or less availability (with persistent interest) -> price goes up; if it is easy to get -> it goes down. The economy happens when sellers and buyers agree. (The author stops at the edge of microeconomics: a recommended analytical complement.)
- **Critique of common practices**:
  - **Centrally set prices**: they give a consistent experience (lizard hides do not suddenly become useless) but take away the "life" and the decisions (no need to look for where to sell best). It reduces the economy to a mechanical exercise. It can be fine depending on the game. **Rule**: if you want economic decisions, allow price variability; if all that matters is being able to sell without thinking, variability only adds mental load and eats into the "interactivity budget".
  - **Vendors with infinite cash, stock, and appetite**: they buy the next 10, 100, 1,000 units at the same price; consistent but lifeless and without decisions.
  - **Player-to-player economies**: much more dynamic because players set prices; lots of economic gameplay, but with significant problems (runaway, inflation, see below).

**Economic issues [Economic Issues]:**
1. **Runaway / rich-get-richer**: one player takes advantage of the reinforcing loop and pulls ahead; they win by forcing others to lose, sometimes at the cost of their enjoyment or their presence. Monopoly and Risk are *zero-sum* with player elimination (all the value concentrates in one player). Unless you are after a hypercompetitive game, it does not make for a healthy design.
   - **Solutions**: **rubberbanding** (balancing loops that slow the leader or help whoever is behind; "forgive losers and punish winners"). They can be sudden, one-off corrections: Mario Kart's *blue shell* (the last-place player hits the first-place one and stops them for a few seconds); the thief in Catan (placed on the leaders' terrain to block their production until moved); built-in effects like Power Grid's turn order.
2. **Inflation** - "more faucets than drains": the reinforcing loop is too strong or the exchange/conversion too easy/profitable; the player accumulates too much and has nowhere to spend it meaningfully.
   - It can be used to advantage for a while: going from two coins to buying castles gives a feeling of power; **only as long as the quantities remain meaningful** (they can be used for something).
   - *Adventure Capitalist* (idle game): from lemonade to film studios, banks, and oil, with figures of 10^300 (novemnonagintillion). Few players get there: the gameplay becomes repetitive first. Partial solution: **prestige loop** - an external boosting engine: you accumulate a prestige resource (angel investors); when the current pace no longer pays off, you reset and keep only the prestige, which works as a **multiplier** on the main resource's rate -> you quickly pass the already-boring low levels and get further; you keep accumulating prestige, and there is an incentive to repeat. It turns inflation into part of the gameplay and lengthens the game's life.
   - *Diablo II*: every monster drops gold and items; plenty of gold with few uses (more faucets than drains) -> useless between players. Players adopted gems as an unofficial currency -> they were devalued too (amount of loot + "dupes" = cheating duplication of items). Then the *Stone of Jordan* (SOJ: small, expensive, useful) -> also devalued. Finally *high runes* (small, expensive, useful, with different stats = **denominations** of different value, like banknotes). Cause: a reinforcing loop too strong pouring out currency + not enough content to sustain meaningful decisions and goals. Every game with an economy faces this; it gets harder each time to add high-end content without repeating.
3. **Stagnation** - less common: the supply of resources/currency is too restricted, or the costs of staying in the game are too high. Players hoard out of fear of regretting a purchase, or must pay upkeep (a braking engine) until they run out of funds. It is rare because players simply leave when it stops being fun, and the economy fades.
   - Typical cause: designers so obsessed with balancing that they do not let the reinforcing loop grow. Shrinking the main loop prevents inflation but also removes the **economic gradient**: if nobody feels an exchange benefits them, there are no exchanges and no economy. Without exchange/conversion interaction between two resources there is no system; if it is a core loop, there is no game.

### 3.3 ECOLOGIES

- **Definition**: a system with predominant **balancing** loop(s) in which resources are exchanged (as in an economy) but in such a way that each part ends up balancing, not reinforcing, the others. Within the parts there are often reinforcing loops as subsystems, but they are not the main engine (Fig. 7.6 and 7.7).
- Goal = balance, not unchecked growth, but **it does not mean stagnation**: a healthy ecology is in **metastability** (internal equilibrium / dynamic balance). The parts change constantly, the whole stays balanced. Examples: deer/wolf; hare/lynx (Fig. 2.10); the trophic cascade from reintroducing wolves in Yellowstone (Fig. 2.22).
- Each part tries to maximize its growth, but together they are **braking engines for one another**: deer brake plants, wolves brake deer. The wolf (*apex predator*) is not limited by predators but by food scarcity (small population because of its metabolism and slow growth).

**Kinds of ecologies in games [Different Kinds of Ecologies]** (not only biological: any balancing system with resource exchange):
- **Inventory** (RPG): more things = less space; "things" and "space" balance each other. *Diablo II* takes it to the extreme: each piece competes for a configuration of space, not just a count.
- **Combat**: two or more sides that "balance" each other (try to kill each other). If the player wins, the rewards feed the larger economic loop.
- **Social ecologies**: *Dark Age of Camelot* - Realm vs. Realm with **three** factions (Albion, Hibernia, Midgard): if one dominates, the other two temporarily ally against the leader -> constant metastable balance. With **only two** factions, the balancing loop is overcome by a reinforcing one (everybody switches to the winner): runaway. This is what happened on early *World of Warcraft* PvP servers (Alliance dominated because it was more attractive, among other causes); class and incentive changes were needed and it never reached an organic balance like Camelot's.
- Derived design rule: **three or more factions** produce self-balancing through shifting alliances; two factions tend toward runaway.

**Ecological imbalances [Ecological Imbalances]:** the two main failures:
1. **Balance too static -> boring** (and, paradoxically, brittle).
2. **Balance that spins out of control -> destroys the system.**

- **Resilient vs. brittle**: within a certain range the ecosystem rebalances; past a **point of no return** it no longer can. Analogy: **homeostasis** - the body keeps its temperature within a narrow range; if the stress exceeds capacity, it goes from resilient to brittle and shuts down.
- **Practical difficulty**: it is hard to know when a system has become brittle. A sharp drop in hares can be a normal part of the cycle. With historical data you can build models: **statistical process control** - if a resource strays **more than 3 standard deviations from its historical mean**, the process is "out of control" and there is serious danger of brittleness. Problems: in dynamic systems it may be detected late, and in games there is almost never enough historical data.
- **Danger of over-controlling**:
  - **Oversteer** (overcorrection) -> another brittle failure.
  - **Forced stasis**: nailing everything down to ensure a consistent experience -> boring (no mental model to build, no decisions), and also brittle because the system does not self-balance and breaks under any outside influence. Analogy: if body temperature were pinned at 37 °C, a cold breeze or a ray of sun would drain the energy and the system would fail.
- **Dominant strategy in combat ecologies** (e.g., a unit too strong for its cost): it becomes an invasive species; everyone builds only that; the decision space collapses.
  - **"Counter-unit" anti-pattern**: creating a unit to counter the dominant one; if that one is OP (overpowered) it becomes the new only choice; the temptation to add yet another counter-unit is high and the game starts to resemble the song about the old lady who swallowed a fly. It is a non-systemic solution to a systemic problem (the author cites the DDT case in Vietnam: killing cats -> rats -> crops). **Fix the cost/balance at the source, don't pile up countermeasures.**

### 3.4 Combining loops [Combining Loops Together]
- Engines, economies, and ecologies are the primary types; many mechanics are built by combining them. It is rare for a game to have just one system.
- **RPG example (Fig. 7.11)**: the central reinforcing economy = character progression (exchanges time and HP for XP and loot -> more HP, skills, better tools). Inside it:
  - **Skill engine**: the player decides when and how to invest points (note: almost nobody lets you *spend* XP/skill points on an action instead of investing them; AD&D 3.5 does it with some spells; Deadlands and Torg come close. Design idea: seeing it as an engine reveals that possibility).
  - **Item economy**: crafting/trading.
  - **Inventory ecology**: space vs. things.
  - **Role economy**: party roles that reinforce each other (the tank absorbs, the ranged class damages, the healer keeps the tank up).
  - **Combat ecology** inside the larger economy.
  - **Braking engines** (stamina/energy that regenerates over time, typical F2P) that prevent progressing too fast.
- Net effect: the subsystems reinforce each other (more skills/items/party -> beat more monsters -> more XP/loot). Combat and inventory brake and force you to decide what to throw away, but **the predominant systemic effect is reinforcing the character's power**.
- **Benefits of a hierarchy of systems ("Bringing All the Systems Together")**:
  - The core loop changes as the player shifts focus between subsystems or to the highest level.
  - Parallel systems = more things to do = **breadth**.
  - Nested systems with mental zoom in/zoom out = **depth** with understandable complexity (Fig. 7.6, 7.7, 7.11).
  - This way second-order design creates play space: goals and decisions in every system and subsystem.
  - **Revealing complexity gradually** helps build the mental model: each new system brings knowledge, decisions, ways to act, and a sense of accomplishment.

---

## 4. Examples of game systems [Examples of Game Systems]
(Not an exhaustive list; we look at the primary loop, internal subsystems, and relationship to other systems.)

### 4.1 Progression Systems
- Almost all games give some progression (skill, power, resources, **knowledge**). The player's knowledge is a game resource: more knowledge -> doing more and better. Increasing the variety of things that can be done (more parallel systems and a deeper hierarchy) introduces concepts gradually and gives a growing sense of mastery.
- Very common and rewarding -> they are usually the **core loop**. They map to the interactive loop (action -> positive feedback -> new decisions). "What does the player do?" usually boils down to "how do they progress?". They are economies or engines, often with subsystems of both kinds.
- **From toy to game**: a *toy* (no explicit goals) is "nice, but what does the player do with it?". Adding explicit goals + progression turns a toy into a game and sustains engagement. A typical "toymaker" mistake (ch. 5).
- They are thought of as **reward/resource gain per unit of time**. For each dimension of progress (health, magic, knowledge, items, XP, troops...) you must specify a **rate of increase** (tokenizing, ch. 10). Sometimes it is hard to quantify (mental model and cognitive tools).
- **The rate itself must increase over time** (not just the amount) to keep it aspirational and avoid **habituation / hedonic fatigue (hedonic adaptation, satiation)**.

**Habituation and utility [Habituation and Utility]:**
- **Wanting > having** drives attention and behavior. A high goal, even a ridiculously distant one, sustains engagement. If the player feels they have achieved everything (killed the biggest boss, got the best treasure), engagement drops quickly.
- **Hedonic fatigue**: we get used to any reward; we evaluate it relatively, not objectively. In economics: **marginal utility** (diminishing marginal utility): the first bite of ice cream is great, the third is okay, the twentieth is unwanted; it can even become negative. 20 bites are not worth 20 times one.
  - Note (**network effects**): sometimes marginal utility rises (telephones, building blocks, networked computers) until saturation.
- Consequence: if the player does not feel meaningfully rewarded, they fall into the "boredom" at the lower edge of the flow channel (Fig. 4.11). **Rewards tend to grow over time -> an exponential reward curve**.
- **Fatal side effect**: if the rate rises over time, more resources enter the game. **If sinks don't grow as fast as sources -> inflation.**
- **Tactics against habituation/inflation** (full list):
  1. **Limiting sources**: fewer sources, a lower production rate per source, or a higher cost/difficulty of obtaining the resource. E.g., in an RPG: the difficulty of getting a better weapon, the last piece of a set with a nonlinear benefit, the XP for the next level with a nonlinear curve (ch. 9 and 10).
  2. **Limiting stock**: an inventory cap (WoW, Diablo) -> an ecology of "what I carry vs. the space I have left"; it postpones but does not eliminate inflation; it also gives another path of progress (learning to carry more).
  3. **Increasing sinks**: take resources out of the game. E.g., *Zelda: Breath of the Wild* (and others): weapons break and leave the game -> the player never sees a good sword as useless (it keeps its marginal utility) because they know others will break.
- Inflation and habituation are hard to avoid completely; that is a reason for the systemic approach with hierarchies of systems. **Games based only on content and progression end**: the content becomes ever more exaggerated to sustain exponential curves of challenge and reward and becomes more expensive to create and maintain. Games with a strong **ecological/balancing** component (e.g., Realm vs. Realm) can last much longer with no clear limit on engagement.

### 4.2 Combat Systems
- Typically **ecologies**: two or more opponents seeking to balance and eliminate each other. Time/interactivity: action/feedback + short-term cognitive. An important part of the core loop, but almost always accompanied by **reinforcing loops (progression)** to provide long-term goals and offset the balancing nature of combat.
- **Warning**: some games (especially mobile) have combat with no player decisions; the outer reinforcing loop keeps people playing, but the loss of fast action/feedback reduces engagement and longevity. **Even with a solid core loop, moment-to-moment decisions and interactivity remain vital.**
- Combat as a **balancing system that interacts with others**: *Star Realms* - the individual core loop is engine building; combat between players brakes/balances the rival's progress, raising the pressure on the engine decisions (build ships for immediate gain or long-term investment, knowing the rival will challenge you).

### 4.3 Construction Systems
- Crafting, farming, breeding, building/modifying vehicles, buildings, or the character (RPG). Typically **engines + economies** (with long production chains), depending on the emphasis: reinvesting (engine; e.g., deck-building as a core loop) or exchanging to gain value (economy).
- Interactivity: short-term and long-term cognitive; very detailed ones add action/feedback.
- They are often **supporting subsystems inside a larger progression loop**: in RPGs you build skills, weapons, armor, world knowledge, and a social network (party, guild); in strategy: research -> buildings -> stronger units -> fame and plunder (nested engines and economies).

### 4.4 Skill and Technological Systems
- Long-term goals of discovering skills/technologies: new abilities for a character/empire. They are **limited reinforcing engines**. They are usually organized as **trees** (one skill leads to 2-3 more); the player navigates them to customize a character or civilization.
- The player earns experience/research points and **invests** them in a skill. It is rarely possible to use the points on a non-investing action: an open area for design exploration.

### 4.5 Social and Political Systems
- These are **social ecologies**: cliques, rival gangs, political parties, factions; each balances the other while seeking its own reinforcing dominance. Social and long-term interactivity.
- They fail like any ecology: if one side reaches a self-reinforced position that can no longer be challenged, the system collapses and no gameplay is left.

---

## 5. How to define a system's loops and goals [Defining a System's Loops--And Goals]

### 5.1 Starting point: the system's design goals
Mother question: **what purpose does the system serve within your game?** To answer it:
1. Build the system's **loop shape** to sustain the desired gameplay and player experience.
2. Consciously and carefully consider the **player interactions, goals, and behaviors** it enables.
3. Clearly define the **parts and their interactions** you are counting on, and the other systems this one will interact with.

Goals are expressed in hierarchical levels:
- **Above**: the higher-level system it is part of; the highest is the **player experience** (arising from game+player): how they interact (fast/slow; perceptual, cognitive, emotional, social) and how their mental model corresponds to the systemic model.
- **Below / context**: if the system lives inside another (like Fig. 7.6/7.7), look at it in its context: which larger system it reinforces or balances and how it interacts with **peers** (other parts of the same higher system).

### 5.2 Defining the looping structure [Defining the Looping Structure]
Questions to resolve:
- What structure does it need? Options: a simple reinforcing loop, a simple balancing loop, an **engine**, an **economy**, an **ecology**, or a hybrid.
- Does it have internal subsystems?
- **Process**: sketch the primary loops (see Tools). It gives a quick understanding of the dynamic behavior, how it sustains the experience, which subsystems/resources form the loop, where the system fits and why it is necessary. **Do it several times**, redefining structure and relationships: it helps refine the system and the total experience and starts defining the **game objects that will be the parts**.
- **Pruning**: it may turn out the system isn't needed (it contributes little). Do not keep a system that does not fit with the rest, **even if you like it or worked hard on it** (e.g., a crafting system in a game about social relationships). Set it aside: it may be useful later or in another game.
- Also evaluate how the parts and their interactions sustain the system's goals -> this leads to **balance** and to whether the system allows meaningful decisions (parts: ch. 8; balance: chs. 9-10).
- Work on **parts, loops, and whole at once** (or alternating focus) to articulate goals as *dynamic machines* that create the action space, not as static content.

### 5.3 Linking player experience and system design [Linking the Player Experience and System Design]
- Every system is thought of in terms of how it supports the experience. **Combat example**: a large-scale battle of armies where you see the effects of your orders unfold over minutes, or intense personal combat with sub-second control of every move? Both are combat ecologies, but the player's interaction and the parts needed are entirely different. Defining the goals in terms of player interactions/experience, and of the parts, attributes, and behaviors that support them, clarifies the structure.
- **Progression example - pacing**:
  - How fast should it progress? How do you give a sense of early mastery in a fast loop to generate engagement while sustaining long-term interest?
  - Without early positive feedback the player does not build their mental model or get hooked. **Creating a "success experience" ("you did it!") in a core loop within the first minute** helps hook them.
  - But hedonic fatigue appears if you give the same reward at the same rate.
  - Rewarding too much/progressing too fast -> the game ends or gets boring quickly.
  - Progressing too slowly or with inherently unrewarding progression -> **grind**: the player persists only if they believe there is enough reward later; otherwise they quit.
  - (Footnote: the grind/leveling treadmill is accepted in RPGs/MMOs, but a systemic approach can aim for **systemic mastery** instead of mechanical repetition.)

---

## 6. Tools for designing game systems [Tools for Designing Game Systems]

- You do not need exotic tools: paper, whiteboard. The work is **highly iterative**: you redraw the loops over and over. Just trying to draw a loop diagram forces you to focus and clarify your thinking and shows how it works as part of the game.
- When the structures and diagrams solidify -> **build prototypes** to see whether the design works and meets the goals.

**List of tools:**
- **Whiteboards**: analog; draw/erase/redraw with colors; lots of time in front of one. Limit: your brain is the computer, and humans are terrible at maintaining an accurate understanding of the behavior of a dynamic system.
- **Loopy** (Nicky Case, 2017): free online, draws reinforcing/balancing loops and you watch them in action; limited functionality, clean aesthetics; does not support subsystems.
- **Machinations** (Joris Dormans): much more detailed; functional loop diagrams and even whole games (no presentation, just pure systems); includes operators with user input; aging and with no apparent maintenance; subsystems are not usably modular.
- **NetLogo** (Wilensky 1999): built for simulation; more powerful, can create complete systems for simple games; long learning curve and slower to iterate with.
- **Rapid-prototyping languages/environments**: JavaScript, Python, Unity, etc. **Fast and ugly** prototypes (art is not the emphasis). Key: use them as the means to go from conceptual diagrams to working prototypes as quickly as possible.
- **Spreadsheets**: a pillar of systems design; Excel the most popular (also Google Sheets, OpenOffice). You must master them to enter, visualize, and compare the data that defines the lowest-level parts and makes the loops run (ch. 8 and 10).

**Tool challenges (two axes):** how complex/complete the interactive system can be vs. how much it costs to learn and use the tool. Whiteboard: easy but no execution; Loopy/Machinations: easy to learn; NetLogo: more powerful, slower; general-purpose language: expressiveness vs. speed depending on style and willingness to learn. There is no single best tool: "the right one for the job".

---

## 7. How to document your systems [Documenting Your System Designs]

Anyone working on the game (**including yourself months later**) must understand:
- **Why** the systems are designed this way.
- **How** they support the game concept and the desired player experience.
- **How** they are embodied by the game objects as parts of the system.

Documentation is kept **alive**: it is updated and consulted with every iteration, not "write and forget". Not documenting leads to bad future decisions by losing the thread of why something was decided; systems have **subtle decisions with non-obvious effects** that the documentation must make explicit so the essence isn't lost.

### 7.1 System Design Document
Contents (full list):
1. System name and high-level description.
2. **System goals in terms of player experience**: how it helps create the gameplay; usually qualitative and experience-centered; words about how the player feels are valid.
3. **Graphic depiction** of the system: important subsystems, internal parts, and behaviors; typically the loop diagrams of this book (a high-level one would look like Fig. 7.11).
4. Player interactions enabled or required by the system.
5. A list (ideally live links) of the descriptions of subsystems, peer systems, and the containing system (the highest being game+player).
6. Any other detail needed to understand the purpose and implementation.
- **One short document per system**, clear and concise; **not a giant "design bible"** that ages fast. Separate but linked documents (web, Google Docs, wiki) so each can be edited without touching the rest.
- A *deliverable* is anything handed to a stakeholder (it can be your future self).

### 7.2 System Technical Design Document
- It focuses on **how it is implemented** (not the why). The design doc is for designers; the technical doc for programmers. They must be kept **in sync**. It is useful to separate them even if designer and programmer are the same person (two points of view).
- Contents: implementable descriptions of attributes and behaviors (code-like definitions); as it settles: **attributes by type** (string, integer, etc.), **valid ranges**, **formulas** for how behaviors alter attributes to produce the described effects, a **description of tests and results** to verify the system works; format and links to data files (spreadsheets); eventually software architecture elements (classes) depending on the level of detail needed (more in large teams/long projects).

### 7.3 Mockups and prototypes
- They help communicate the system's purpose and behavior and make sure you and others understand it. They give examples of how it works and what experience it creates. They do **not** exemplify the technical implementation (many shortcuts are taken that are not appropriate in the final game).
- **Mockup**: a non-functional diagram + supporting text; player-oriented drawings/storyboards/narrative descriptions ("more diagrams and less text is better"). E.g., a combat mockup: the player's choices as in the UI and a diagrammatic/narrative description of how a combat unfolds, showing the effect of the choices on the inner workings.
- **Prototype**: in digital games it has real, though limited, functionality, and leaves out whatever is unrelated to the system's function. Placeholder art as simple as possible. **"Fast and ugly" as a positive quality.** Any tool, from a spreadsheet to a full programming environment.
- **Strict rule**: the prototype is **forbidden from being transferred to the final game** (ideas only). Everything is rewritten in production; the temptation to copy-paste "just a little" costs more time and pain than resisting it.
- Having a working prototype referenced in the doc gives more certainty that the design meets the goals and makes it easier to understand the **function** (not just the structure).
- You don't need to prototype every system, but **the more important it is (core loops), the earlier you should prototype**, when it is quick and cheap. Discovering in production that the core loop or a major system doesn't work causes far more costly delays.

---

## 8. Questions to consider about your loops [Questions to Consider About Your Game Loops]
(Complete, paraphrased)
1. Is the system's purpose clear, especially to people who did not design it (team first, players after)? (Requires a working prototype and playtesting.)
2. Are the internal resources, currencies, and/or subsystems evident and well understood?
3. Is it clear where the system lives within the whole game? Is it part of a higher-level system? Does it have peer systems within that higher system? Does it form one of the player's core loops?
4. Does it have a primary loop of its own that is easy to define? Is there enough interaction and feedback among the parts (atomic ones or subsystems)? Does that loop act by reinforcing or balancing the resources in a way that sustains the intended gameplay?
5. Is the system resilient to internal and external changes? Do you understand (and can you predict) in what situations it becomes brittle and fails? Are there parts that override the effect of all the others, or **choke points** where, if one part or subsystem fails, everything fails?
6. Does it offer and even require meaningful decisions? Does it force a dominant strategy, or fail to give interactions at an appropriate frequency (for the type of interactivity sought)? Or, on the contrary, does it demand so many decisions that it overwhelms?
7. Does it give enough feedback about its inner workings for the player to build an effective mental model?
8. Can it **unfold progressively** as the player's understanding grows (a simple or high-level version to which detail and interaction are added as they learn)?
9. Does it create **emergent** gameplay? Do the parts and subsystems combine into new effects that reside in none of them and that surprise and delight?
10. Can you show how it works with a prototype instead of just talking about it?
11. Is it adequately documented, both design goals and specific implementation elements?

---

## 9. Failure catalog and diagnosis (operational synthesis for analyzing/balancing)

| Failure | Where it occurs | Structural cause | Signals | Fix |
|---|---|---|---|---|
| **Runaway / rich-get-richer** | Boosting engine, economy, social ecology with 2 sides | Reinforcing loop with no balancing loop; no catch-up | The leader wins with less and less attention; the one behind loses options; widening gap; few decisions | Rubberbanding (blue shell, Catan thief, Power Grid's reverse turn order); proportional friction (make repairs); 3+ factions |
| **Deadlock** | Boosting engine / economy | The resource earned in the loop is needed to enter the loop | Player cannot progress from the start | Provide an initial source independent of the loop |
| **Stall from insufficient resources** | Boosting engine (Monopoly with $500) | Poor start; high costs | Quick bankruptcy/elimination | Raise the initial stock/flow |
| **Content starvation / exhaustion** | Boosting engine with cheap, durable units; exponential progression | Investment with no consuming spend; rising costs only delay | Players with nothing new to unlock | More sinks, prestige loop, ecological systems that don't depend on content |
| **Dominant strategy** | Engines, combat ecologies | Balance too fine or one option mis-costed | Everyone builds/uses the same thing; "optimal recipe" known | Fix the cost at the source; avoid the counter-unit spiral |
| **Slowing to a stop** | Braking engine | Friction greater than the reinforcing loop | Player without resources to act | Reduce the brake; make it proportional |
| **Inflation** | Economy / progression | More faucets than drains; growing gain rate without proportional sinks | Unused, devalued currency; players switch currencies (Diablo II) | Limit sources, limit stock, increase sinks (breaking weapons), prestige loop, denominations |
| **Stagnation** | Economy | Resource supply too restricted or upkeep costs high | Hoarding; nobody feels an exchange benefits them; silent abandonment | Let the reinforcing loop grow; restore the economic gradient |
| **Habituation (hedonic fatigue)** | Progression | Constant reward | Engagement falls at the "boring bottom" of the flow channel | Rising reward rate + proportional sinks; aspirational goals |
| **Grind** | Progression | Progress too slow or not inherently rewarding | They persist only for a future promise | Inherently gratifying progression; systemic mastery |
| **Brittleness** | Ecologies | Passing the point of no return; or forced stasis | Values >3 deviations from the historical mean; system does not rebalance | No oversteer; leave dynamic balance; monitor with historical data |
| **Oversteer / counter-unit** | Combat ecologies | Non-systemic solution | A chain of OP units that counter each other | Fix at the source |
| **Stasis** | Ecologies | Pinning values for consistency | No mental model to build and no decisions | Allow variability |
| **Orphan system** | Any | A system that doesn't fit | Contributes nothing to the experience | Cut it (even if it hurts) |

---

## 10. Heuristics and rules of thumb (flat list)

- Draw the system as a loop diagram before balancing; redo the diagram several times.
- For each resource identify: source, stock (and whether it has a limit), converter, decider, sink. Count faucets vs. drains.
- Every time the reward rate goes up, increase the sinks in proportion.
- A reinforcing loop needs a balancing loop somewhere (limit, cost, friction, rubberband, delay).
- A **delay** between exchange and benefit prevents instant runaway in economies (e.g., the bread that feeds the woodcutter arrives the next turn).
- A decider's inputs must be local (same level of the hierarchy, at most one level away) so as not to make the system brittle.
- Don't leave vendors/prices completely fixed if you want economic decisions; if you aren't interested in the economic decision, variability is useless mental load.
- Keep the balance dynamic: neither too static (boring/brittle) nor free (collapses).
- To maintain a long-term balance between sides, prefer **three** or more (shifting alliances) to two.
- Currencies: they should keep their value without being too precious; review at the level of the whole economy, iteratively.
- When fixing a problem, be suspicious of non-systemic patches (counter-unit, counter-counter-unit).
- Give an early "success" (first minute) to start the mental model; then regulate the pace of rewards.
- Combat without meaningful decisions weakens longevity even if the outer progression loop works.
- A high-tension loop (action) + a low-tension loop (building) is a proven pattern.
- Visible long-range goals sustain *wanting*; if everything is achieved, engagement drops.
- Well-managed inflation can be part of the gameplay (feeling powerful) as long as the numbers are meaningful; if not, add a prestige loop or reset.
- Prototype the core loops first; the prototype is thrown away (not copied into the final code).
- One doc per system, short, with links; separate the *why* (design) from the *how* (technical).
- If the system doesn't contribute to the experience, cut it.
- Before deciding an ecosystem is broken, compare it with its historical variability (3 standard deviations as a statistical-control rule), although games often lack history -> use simulation/playtests to generate it.

---

## 11. Index of game examples (one line each)

- Monopoly: boosting engine ($200 per lap + investment in properties/houses), runaway, stall with little capital, braking with the repairs card (+ rubberbanding).
- Power Grid: turn order reverse to the leader = permanent balancing loop.
- Clash of Clans: collect/battle/build & train; gems exchange money for time (F2P).
- Marvel War of Heroes: PvE/PvP with stamina/attack power as brakes; outer loop of upgrading heroes.
- Boomshine: a one-click core loop; replaying as the player's own outer loop.
- Terraria, Banished: deep production chains.
- Rampart (1990): a rebuilding engine with no catch-up -> runaway.
- Dominion, Splendor: tabletop engine building (Splendor: cards give free gems + points).
- Star Realms: engine building with combat as the brake between players.
- Mario Kart (blue shell), Settlers of Catan (thief): one-off rubberbanding correctives.
- Risk: zero-sum with elimination.
- Adventure Capitalist: extreme inflation and the prestige loop.
- Diablo II: gold inflation -> gems -> SOJ -> high runes; inventory as a spatial ecology.
- WoW / Diablo: inventory cap as a brake on inflation; early WoW PvP with 2 factions = runaway.
- Dark Age of Camelot: 3-faction Realm vs. Realm = metastability.
- Zelda: Breath of the Wild: breaking weapons = a sink that preserves the value of what you have.
- AD&D 3.5, Deadlands, Torg: cases where XP is spent instead of invested (a skill engine with an alternative "use").
- Deer/wolf/plants: example of a hierarchical ecology (Fig. 7.6/7.7). Lynx/hare and Yellowstone wolves (ch. 2) referenced.

---

## 12. Key terms (quick glossary)

Reinforcing / balancing loop; core loop, inner/outer loop; game's model loop; player's mental loop; interactive loop; designer's loop; game mechanic / core mechanic; engine (boosting / braking, dynamic engine, friction structure); economy; ecology; resource (simple/complex); production chain; currency; source / faucet; sink / drain; stock / pool; converter; decider; dynamic balance / metastability / homeostasis; resilient vs. brittle; point of no return; statistical process control (3 sigma); rubberbanding; runaway / rich-get-richer; deadlock; dominant strategy; inflation (more faucets than drains); stagnation; prestige loop; variable schedule; habituation / hedonic fatigue / marginal utility; network effects; progression system; grind / leveling treadmill; toy vs. game; unfolding complexity; breadth vs. depth; system design document / technical design document; mockup / prototype ("fast and ugly").
## Appendix: ways of thinking and real-world loop examples (ch. 1)

### 1.1 Ways of thinking [Ways of Seeing and Thinking]
Metacognition: thinking about how we think. The designer must understand how the player thinks and how they themselves think.

Four modes of thinking, and which one to use:
1. **Phenomenological thinking:** the world as isolated events with no unifying principle. Consequence: you do not see the systems that affect you (e.g., the sea recedes quickly -> you don't see the tsunami; easy mortgages -> you don't see the crisis). For design: it is the designer/player who sees "X happened" without seeing the loop that produced it.
2. **Reductionist thinking:** take it apart into parts until the solution is obvious; it assumes determinism and a single root cause. Useful for complicated (linear) processes, dangerous in systems with loops. Typical failures:
   - Confusing correlation with causation (ice cream/drownings; night light/myopia; debt/growth with reversed causality).
   - "Greedy reductionism" (Dennett): believing the whole is just the sum of chemicals/parts.
   - Expecting linear effects: the "cobra effect" (see 2.7).
   - A simple pendulum = predictable (complicated); a **double pendulum = chaotic** (complex): a minimal change (one joint) makes the trajectory unpredictable.
3. **Holistic thinking:** seeing the whole; synthesizing. Advantage: you see macro-trends and avoid greedy reductionism. Risk: if everything is connected you find no causes; false positives (spurious correlations).
4. **Systemic thinking:** the "Goldilocks" middle ground: analyze the parts AND understand how they work together in their operating context; find the loops (A affects B, B affects C, C affects A). It is "both-and": reductionist + holistic. It is the designer's core skill.

Michigan Fish Test (Nisbett/Masuda): Westerners see the big fish (parts), Easterners see the scene and relationships. Moral: we tend to see the parts and not the relationships.

Examples of physical loops:
- Oven with a thermostat: the gap between desired and current temperature determines the heat applied; the heat reduces the gap (balancing loop).
- Centrifugal governor: valve opens -> engine speeds up -> weights spread -> lever closes the valve -> engine slows -> weights drop -> valve opens. It self-regulates. Lesson: to tune a system you must understand which interactions dominate; friction/"play" in the joints smooths oscillations (the equivalent of damping/delay in a game loop).
- Rabbits in Australia (24 rabbits, no predation, explosion): a small introduction can destabilize an entire ecosystem.
- Wolves in Yellowstone (14 wolves + 52 more, 1995): **trophic cascade**: a change at a high-level node propagates down through the whole ecosystem (wolves scare the elk, trees return, then bears, birds, fish, beavers, rivers change course). Diagram with +/- on the arrows; effects invert transitively (reducing what reduces = increasing).

### 1.2 Systems as the process of the world [Systems as the Process of the World]
- Systems have to be **experienced** (operating, in context); they are not understood by reading static rules. Example: **Reynolds' boids** (3 rules: don't collide, match direction/speed with neighbors, steer toward the visible center of mass) - reading them doesn't give you the flock; you have to run it.
- The author's thesis: **designing and modifying games is the best way to learn to see systems**. Example: the author's son understood house pricing through WoW's Auction House (a game economic system generalized to the real world).
- Growing interconnection: a fire at a plant (Sumitomo, 1993) drove memory prices from $33 to $95 per MB; coupled systems propagate shocks far.
- A skill for programmers/designers: think about the whole system (how my change affects everything else, what behavior to expect from users, what the final impact is).

### 1.3 What a "thing" is [A Strange Systemic Journey]
- Theseus' ship: is it still the same ship if you change all the pieces? Systemic answer: identity lies in the **relationships** among the parts, not in the parts. If you replace planks without breaking the relational structure, the system persists; if Helen builds another one from the old pieces, it is another system.
- "Things" (atoms, molecules, protons) are structures of relationships and energy; the parts are not "inside", they **are** the whole seen in more detail. The author's phrase: things are "less like a table, more like a tornado".
- **Metastability:** stable over time but always changing at a lower level (proton, flock, hurricane, water current). It is the basic property of a system.
- **Synergy (Buckminster Fuller):** behavior of the whole not predictable from the parts taken separately.
- **The "third thing" (D.H. Lawrence) / "quality without a name" (Alexander) / Aristotle's "cause":** what makes water water or a house more than a pile of bricks = the whole that arises from the relationships. Poincare: accumulated facts are not science just as piled-up bricks are not a house.
- Alexander (A Pattern Language): no pattern exists in isolation; it exists to the extent that it is supported by larger patterns, patterns of the same size, and smaller ones. Application: when building a thing you must "repair" the world around and inside it. Where he says "pattern", Sellers says "system".
- For the game designer: seeing "the tornado in the still table": static design (tables, skill trees) is a dynamic system; seeing at once the total experience (the game as played, each player's unique path) and being able to "zoom in" on each piece without collapsing it to a single path through the state space.
