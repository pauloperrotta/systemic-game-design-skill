# Parts, Attributes, and Behaviors (ch. 8)

Read this to take a design down to the spreadsheet level: choosing the minimum set of attributes, attribute orders (amount/rate/rate of the rate), ranges, local and generic behaviors that generate emergence, feedback rules (100-250 ms, consistent, no noise), closing loops between parts, and documenting in text plus data-driven spreadsheets.

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). Square brackets give the book section each block comes from.

## Index
- 1. Getting Down to Parts (intro)
- 2. Defining Parts
- 3. Determining Attributes (rules for choosing attributes)
- 4. Attribute Ranges
- 5. A Nautical Example (example: age-of-sail naval battles)
- 6. Specifying Behaviors for Parts
- 7. Back to the Nautical Example (the ship's behaviors)
- 8. Creating Looping Systems (loops built from parts)
- 9. Don't Get Lost in the Weeds or the Clouds
- 10. Documenting Your Detailed Design
- 11. Spreadsheet Details (spreadsheet structure)
- 12. Questions to Consider About Your Detailed Design (complete, paraphrased)
- 13. The Author's Summary (Summary)
- 14. Extracted Operational Checklists (for designing / analyzing / balancing)
- 15. Cited Example References (quick index)

---

---

## 1. Getting Down to Parts (intro)

- **Parts**: the components of a system; they create loops through their actions. In games, this is where you define the numbers and logical functions that make the game work.
- A part can be a **subsystem** of another level. At some point you have to reach **simple/atomic parts**: indivisible ones. There you stop thinking in loops and move on to internal structures and behaviors.
- **The game's nouns and verbs**:
  - Attributes = nouns = determine **state**; they have values and define **resources**.
  - Behaviors = verbs = define **function**; they specify interactions with other parts and resource flows. Behaviors are what let you create loops, and therefore systems.
- Parts specify the interactions and their effects, including **feedback to the player**, which makes meaningful decisions possible. The experience comes out of the player-game loop.
- Implication: you must be able to shift focus between the atomic part, the systemic loop, and the overall experience.

## 2. Defining Parts

- Goal: make every part "spreadsheet specific": its internal state specified without ambiguity. Every part ends up decomposed into **structural tokens** (ch. 3 and 7, "Parts as Loop Components") plus the behaviors that act on them.

### Types of Parts
Three families; all have state and behavior via attributes and values:
1. **Physical**: character, army, tree.
2. **Nonphysical (concepts)**: area of control, emotion, time.
3. **Representational / rules-based**: maximum cards in hand, UI displays/controls, current turn order.
- **Decorative background parts** (UI decoration) with no state or behavior: they go on the art/UI list, they are NOT system parts.

### Your Game's Parts (how to find them)
- Start from the loops you have already sketched (internal model + interactive loop): resources, currencies, and values show up there = core parts.
- A few parts hold the player's attention and sit in the core loops: in an RPG, characters and opponents; in strategy, armies and controlled territory.
- Each primary part drags in others contained hierarchically (character -> weapons, armor, spells, loot, pet/horse; army -> unit types; area -> adjacency, resource production).
- List everything to see the count and the hierarchy; the systems defined in your loops show which parts are atomic and which need more specification.
- Consider physical, nonphysical, and representational parts: anything with internal state data, with behaviors that affect other parts, or that the player interacts with (e.g., character -> weapons -> inventory UI).
- **The parts list is a proxy for scope**: how much art, animation, and programming work there is. It grows fast.
- Separate parts by type, typically on **different sheets** of the spreadsheet, grouping those that share attributes (don't mix environment objects with enemy NPCs or with UI objects such as cards in hand). This helps you spot missing parts; parts of the same type share many attributes/behaviors.

### Internal State
- A part's state = the current value of each attribute/variable (hitPoints = 5, gold = 10, class = Ranger, secretName = "Steve"). It includes numbers, types, strings, any trait with a name and a value.
- Attributes are **stand-ins for real systems**: instead of modeling metabolism, you use a "5 hit points" attribute.
- **Name-value pairs** (attribute-value / key-value): the classic structure in programming and databases. If the datum is numeric of a certain kind (units, dollars), it is a **stock** in systems terms.
- Mapping to programming: a part = a class instance (data members = attributes; methods = behaviors). OOP and component-based architectures fit well.

## 3. Determining Attributes (rules for choosing attributes)

Practical rules, in order:
1. **As few as possible**: every attribute adds complexity to rules and code and is **a new way to unbalance** the game. Start with few and add by iteration.
2. **Combine similar attributes across parts**: don't create two attributes for two parts if one will do.
3. **Prioritize attributes the player interacts with most or that yield the most meaningful decisions.**
4. **Communication test**: if you can't quickly tell the player how two attributes differ and why both matter, drop one or merge them. Example: slash vs pierce attack; unless the game is about fine-grained melee combat, a single attack attribute is enough (add a second later if needed).
5. **Broad applicability**: avoid attributes used by only 1 or 2 parts. E.g., "visibility" on a camouflageable part: can other parts hide? If it's the only one, is it worth it, or should it be generalized? Many single-use attributes complicate things without adding engagement and make behaviors harder to program.
   - **Exception**: the player's representation (character, nation) can have several unique attributes because of its special relationship with the rest of the game.
6. **Consider the amount and the rate of a resource**: e.g., an account with gold = 100 (amount) and attributes income = 10, debt = 3 (rate) -> +7 per period. The period can be an attribute of the account or, more likely, a global game attribute (per turn, per minute).

### Attribute order (first/second/third-order attributes)
- **First-order**: describe an amount (current gold, XP).
- **Second-order**: affect the resource's rate of change (income, XP rate in idle games).
- **Third-order and higher**: the rate itself changes (income that slowly grows; the XP needed for the next level and the new rate at that level: both are third-order).
- **Design decision**: attribute or function? If the purpose can be represented simply by a number -> numeric attribute. If it takes logic to determine -> it is the output of a behavior (and the part goes from simple to a system of its own).

## 4. Attribute Ranges

For each numeric attribute, define the valid range. Requirements for the range:
- You understand it intuitively **and** can communicate it to the player.
- It works well across all the parts that use the attribute.
- It gives **enough discrimination** between values (can you tell 5 from 6? do you need a 5.5?).
- It isn't so large that the "feel" is lost (556 vs 557 are indistinguishable).

Rules/heuristics:
- Example: attack 0-10; if 5 vs 6 is indistinguishable or granularity is lacking, move to 0-100; 0-1000 is almost always excessive.
- Byte ranges (0-128, 0-255) are useful for programming but get translated to 0-100 or 0-10 for the player (people don't think in binary/hex).
- **Integers** by default: easy to understand and faster than floats.
- For combined probabilities, 0.0-1.0 is used (easier math), but people tell 0.5 from 0.05 poorly. Trick: define a large integer range (0-10,000) and divide when operating (**normalization** to 0.0-1.0).
- The player can be shown the number however works best: an integer, or **text labels** mapped to the number ("terrible" ... "awesome").
- **Shape of the range (linear vs differential probability)**: percentile 1-100 = every value equally likely (99 as likely as 37 or 2). Two d6 summed: range 2-12 but not equiprobable (2 and 12 ~3% each; 6 ~17% because it can be rolled 5 ways: 5+1, 4+2, 3+3, 2+4, 1+5). A 10 on a linear 1-10 scale means something very different from a 10 on a 2-12 bell curve. You have to understand how the attribute is determined, not just its range. (Developed in ch. 9, Fig. 9.1.)

## 5. A Nautical Example (example: age-of-sail naval battles)

An extended example of how to find parts and attributes; summarized:
- **Concept**: naval combat between ships of the line, more strategic/tactical than fast action (there is downtime). It defines how the **interactivity budget** is spent. Sea elves/dragons are ruled out (scope control). The player builds their navy and fights an enemy fleet controlled by the game.
- **Derived systems**: primary progression with an **economic loop** (defend ports/trade -> money to build/repair ships and hire crew); a merchant-trade economic subsystem inside the model (the player doesn't touch it directly, but you have to think through its parts).
- **Risk detected: rich-get-richer / snowball**: if the enemy sinks merchant ships or takes a port, the player loses funds and can't recover. Suggested solution: a **balancing loop** (e.g., a one-time sum from the king to retake the port).
- **Core loop**: the player directs battles between their fleet and the enemy's. **Outer loop**: uses income to build/repair and hire (perhaps intelligence).
- **Core parts**: ships (primary, in the core loop and progression). It needs a navigation system (including orientation relative to the wind) and a combat system (a balancing-loop ecology among several ships). Each ship needs to know which navy it belongs to (so it doesn't fire on allies).
- **Granularity decision**: is crew a single name-value pair ("crew = 100") or a subsystem (training, morale)? There's no single answer: it depends on the experience, the interactivity budget, and the number of units. With 2-3 ships detail is welcome; with 200 it's a burden. More detail = more decisions, but it's easy to overdo. Design initially -> playtest.
- **Attributes defined**: crewNumber, crewTraining, crewMorale (integers, inputs to the ship's behaviors; they can become a subsystem later); shipNation, shipName (non-numeric, identifiers); maxSpeed, turn rate, maximum sails, currently deployed sails (integers, each could become a subsystem); number of operational cannons (determines attack strength; firing speed and quality depend on the crew).
- **Captain as a part of its own**: separated from the crew to add texture (heroes like Nelson, Cochrane, Aubrey); some sail/fight better -> a meaningful choice of whom to assign to each ship. The ship has a "captain" attribute that is a part with its own attributes and behaviors.
- **Gaps found on review**: the **wind** is missing (attributes: direction, intensity, maybe how often it changes; it can be a complex part with a subsystem that interacts with the ship). A better-trained crew should sail faster: since "training" already exists as an attribute, adding that costs little.

### The Detail Design Process
- You have to define **every part and every attribute**; some atomic, others with systems of their own; all have behaviors and almost all contribute to player decisions.
- **Limit** attributes/parts/systems that exist only for the internal loop and barely interact with the player (e.g., the trade system that provides the reward for protecting merchant ships). There should be few of them; make them as simple as possible: if it doesn't generate interaction or decisions, don't spend effort on it (balancing them is complex and iterative, ch. 9-10).
- **Iterative process (part of the designer's loop)**, in order:
  1. Define the parts and attributes clearly needed for the core loops and the desired experience.
  2. Define the parts' behaviors to link them into loops.
  3. Iterate with mockups and prototypes (ch. 12). An ugly prototype with a complete core loop already tells you a lot about whether the game is worth making.
- Define recursively (parts within parts); you don't have to finish everything at once.

## 6. Specifying Behaviors for Parts

- Behaviors = the functional complement of attributes: through them, parts form loops (engines, economies, escapements, ecologies) and give feedback to the player.
- Base questions: what resources does each part create, consume, or exchange? Physical resources (health, money, ore) and nonphysical ones (movement, time, experience, sanity, combos).
- The player also accumulates some resources and minimizes others; some parts help them and others oppose them ("push back" against their goals). The player decides in their mental loop -> interacts.
- **Rule**: for every change of a resource, or interaction between two parts or between player and game, a behavior must exist.
- Each behavior ends up being an iterable **formula or logic** = the rules of the game (human-run in tabletop, code in digital).

### Principles for Creating Behaviors

**a) Local action**
- A behavior interacts with parts at a **similar level of organization** and in the **same operational context**. Cannons affect crew (fatigue) and other ships (damage): fine. Cannons affecting a port's trade: **not local** (different level, no reasonable operational connection).
- The acting part **contributes an effect** (a resource change) but **does not decide how the other part responds**. "20 damage" to the other ship; the receiving ship decides whether it loses crew, cannons, or sails, or sinks. In systems language: a part can **perturb** another's state but not **determine** it. In OOP: **encapsulation** (you don't "reach in" to set another object's attributes).

**b) Generic, modular behaviors (generic, modular, context-free)**
- As simple as possible, with no more context than necessary, generic enough for many situations. Cannons fire -> inflict damage; they don't know whether the target is an enemy or how much damage it already has (another behavior decides that: the player or an NPC captain deciding to fire).
- Common mistake: context creeps into elaborate scripts -> less reuse. Example: an NPC with a generic "open the door" (it doesn't know why it is going to another room, nor how to unlock or force it; "unlock door" only unlocks). Counterexample: "move the NPC from their room to the command room" = complex, contextual, usable only once, no emergence.
- Warning sign: narrow, scripted scenes/behaviors that are **brittle** and don't apply to the NPC's general function.

**c) Creating Emergence**
- Local behaviors + single-level + modular/generic = a source of emergent effects: endless variety, sustained attention and engagement with **less content and lower cost** than highly contextual scripting.
- Examples of emergence (one line each):
  - **Flocking (boids)**: 3 local rules per bird (same direction/speed as neighbors; don't collide; steer toward the nearby center of mass) -> dynamic, unpredictable flocks.
  - **Conway's Game of Life** (Gardner 1970): on/off cells with 4 rules based on the 8 neighbors (fewer than 2 neighbors on -> off; on with 2-3 -> stays on; more than 3 -> off; off with exactly 3 -> on). Only local context, only affecting the cell itself -> fascinating patterns.
  - **Parable of the Polygons** (Nicky Case 2014, based on Schelling 1969): triangles and squares with a "happiness" attribute based on like neighbors (happy if exactly 2 like neighbors; "meh" if all are alike; unhappy if only 1; only the unhappy ones can move; the movement is done by the player, not the polygons). Emergent result: segregation even though nobody wants it.
  - **Slime Rancher** (2016): slimes stack when close together (no purpose): this lets them escape from a corral to reach food (stacking + food seeking); **tabby slimes** move food they can't eat toward where food already is: it reads as theft or a gift, redistributes food, and triggers unpredictable cascades that delight.

**d) Providing Feedback**
- Closes the **interactive loop**: the player perturbs the state; the game acts with behaviors and responds. **Every verb in the game must give feedback to the player.** If a part has no behavior, or the behavior has no feedback, rigorously question whether it is needed.
- Feedback builds the **mental model**: learning, confirming or recreating predictions, seeing what works, evaluating one's own improvement. It sustains engagement.

**Feedback and Player Expectations (three cases)**
1. Feedback matches the expectation -> positive experience, reinforces the model.
2. Feedback is surprising but the player adjusts the model quickly -> valid learning, also positive.
3. Feedback is absent, distorted, or incompatible with the model and can't be reconciled quickly -> negative, lowers engagement.
- It reports the effects of recent actions and ongoing processes (analogy: turning on the stove burner = knowing at once that it heats; boiling water = gradual temperature feedback).

**Kinds of Feedback**
- Mostly **visual and auditory**, plus text/symbols. Visual: changes in color, size, animation, special effects (glow, fireworks). Auditory: tones, notes, music changes, SFX. Visual is used more (it tells you which part changed better than sound does), but sound is underused and used with little imagination.
- **Every state change, every behavior action, must have feedback.** If a change doesn't merit feedback, examine whether it is needed in the game at all: does the player need to know that state to improve their model?
- Proportional intensity: a subtle change = a thermometer bar that fills slowly; a **complete state change** (building finished and usable) = an emphatic notification. If the player misses "army ready" or "water boiling", they get frustrated and end up watching the UI instead of playing.

**Amount, Timing, and Comprehension**
- **Amount**: relate it to the interactivity budget. A fast-action game with only action/feedback interactivity can bombard the senses (part of its appeal). In strategy, relationships, or socializing: if there is visual/auditory chaos, **reduce parts and behaviors** to leave the focus where it belongs.
- **Timing**: **immediate** feedback = no more than **100 to 250 ms** after the change (ch. 4). Between ~0.25 and ~1 s it feels annoyingly laggy. Beyond ~1 s the player may not associate it with the change.
- **Instant comprehension**: the connection to the state must be obvious, with no reasoning through obscure symbols. Bad example: a blue flame in the upper left = boiling water (blue=water + flame=heat). The player plays the game, not the UI or the rules.
- It is enough for the feedback to say "this part's state changed" and be recognizable as such.
- **Text = a bad medium**: "people don't read" (a useful exaggeration). Even floating damage numbers: color and motion matter more than the figure. For feedback that requires reasoning: break it out (separate dialog/window) and **pause the game** if possible until it sinks in.
- **Avoid misleading or meaningless feedback**: fireworks must mean something; don't fire them at random or for different states depending on the situation. Anything is valid if it is obvious, immediate, and **consistent**.
- "Ambient" animations/sounds not tied to a state change (even a trivial one) are a risk: the player interprets almost all feedback as meaningful and builds it into their model; if it means nothing, it is **noise** that distracts and lowers engagement.

## 7. Back to the Nautical Example (the ship's behaviors)

- Ships: move, attack, take damage from the enemy; ask yourself whether anything is missing that the ship should do. Decide in the initial design and revisit in playtesting.
- Captain and crew contribute to sailing and fighting: the basis of their behaviors (interaction functions with the ship = the navigation and combat systems).
- **Ship Attack** = the operational-cannons attribute modified by the crew. The captain does NOT modify attack directly (to interlock systems and keep the captain's behavior local): their behavior adds a bonus (or penalty) to the crew's **morale** according to their **Leadership** attribute.
- The "fight" behavior inside the crew: combines the number of crew members, morale (affected by the captain), and training (affected by money the player spent) to produce a **modifier** on the ship's attack (Fig. 8.2: Captain.Leadership -> Crew.Morale; Crew.Number/Training -> "Fight!" -> Ship.Attack with Cannon; -> enemy ships; tentative return connection to improve Leadership).
- **Weighted function**: few crew with many cannons = low attack (without crew they don't fire); many crew with poor morale/training = low; great captain + good crew + few cannons = low; strong captain + large crew + many cannons = high. This suggests a formula/logic that determines the effect of each factor, how the player interacts with each, and the range of possible values of the attack modifier.
- It can generate **subsidiary attributes**: weighting coefficients (how much cannons, crew, and captain weigh) tuned by iterating in playtest (balance, ch. 9).
- Sailing is similar, but with the external variable **wind** (direction/intensity): is that level of detail enough? It depends on the play experience.
- Tokenize the concept; test and adjust in prototypes as early as possible: you won't get the parts, attributes, or behaviors right the first time. Document the parts design.

## 8. Creating Looping Systems (loops built from parts)

- Behaviors should be local, generic, with plenty of feedback, **and form feedback loops**, not just linear chains. **Every part should affect and be affected by** others.
- Example: ships fighting: attack depends on operational cannons, crew quality/quantity, and leadership. When damaged they lose crew and/or cannons, and morale drops -> less ability to counterattack. The two ships form an **ecological balancing loop** (exchange of the "damage" resource, each one reducing its own crew and cannons).
- The captain's contribution is a **one-way connection**: it works but doesn't create a dynamic system. To close it: have the crew affect the captain in return. Options:
  - A short **reinforcing economic loop**: if morale stays high at the end of combat, the captain gains Leadership (Morale is exchanged for Leadership).
  - A long **progression loop**: the captain gains Leadership only after winning a certain number of battles; success improves the leadership that improves success.
- You need to make sure the parts affect each other forming loops **and** that they form interactive loops with the player. The key parts must drive the core loops through their interactions.
- Player decisions that feed the loops: moment-to-moment in battle (immediate effect on captain, crew, ship) and long-term decisions (which captain on each ship, how much crew, how much to spend on cannons and maintenance).
- **Check**: go through the parts list and confirm that each one affects some parts and is affected by others. Every part does NOT need to affect all the others (the mental model would be impossible); it is enough for it to affect a few, locally and at similar levels of organization.
- Use the ch. 7 templates (engines, economies, ecologies) to map the loops. Each part can be atomic or have internal loops: this is how you build hierarchy and depth (= more engagement).

## 9. Don't Get Lost in the Weeds or the Clouds

- Designer types (**storytellers, inventors, toymakers**) are comfortable at different stages; you have to move through all levels of organization without losing the overall vision.
- High-level storyteller: dropping down to attributes/behaviors can feel tedious, but it's the only way the design becomes real. Detail-oriented designer: the concept may feel nebulous, but you have to let go of precision and check that the details add up to something enjoyable.
- **Warning sign**: a game that is "a pile of parts lying around waiting to be fun" (no cohesive concept). Nor do you need total realism or great variety: one catapult class in a strategy game may be enough, not five; three types of flowers/hairstyles/banners may be enough. If you enjoy defining parts, don't overindulge as a route to a coherent experience.
- Every game needs fully defined parts/attributes/behaviors, but they **exist to build loops and support the perceptual, cognitive, social, emotional, and cultural interactivity** that generates the experience. The game is not the parts: it emerges from their interactions with each other and with the player. Having the parts isn't enough.
- See the whole and the parts at once; move up and down in abstraction: a clear concept, the systems that support it, the parts that enable meaningful interactions and progression.

## 10. Documenting Your Detailed Design

- In the detailed design, specificity is critical: it defines what the game is, why, and how it is implemented.

### Getting Started and Overall Structure
- At first: a whiteboard or a text doc. Then move to **text design documents + spreadsheets**.
- **Text**: preserves the intent of each part with implementable precision (code or analog rules).
- **Spreadsheets**: the home of all the specific information, especially numerical (attributes and values). They also let you test and iterate fast.

### Detailed Design Documents (contents)
- A set of documents that specifies everything: **design rationale** (why each part matters) + a **specific behavior description** convertible into code or game rules.
- Use images, diagrams, flow models, mockups; link to external mockups and prototypes.

### Being Assertive and Precise (writing rules)
- Treat them as **blueprints for a building**.
- **Present** tense ("the game behaves like this", not "will behave"); no hedging words ("might").
- Avoid qualitative terms except at a high level: not "this enemy moves fast", "big explosion", "this turret turns left and right". Ask: how fast? how big? how far?
- Wherever there is a quantity (number of skills/levels, damage): give a **number, a defined range, or a reference to an equation/factor** in the doc or the spreadsheet. If the decision hasn't been made yet, **say so and mark it as an open issue to resolve**.
- Being precise forces you to eliminate the vagueness of the design in your head; it's easier to find gaps in a proposal than in an idea.

### Avoiding Overdoing It
- Documenting too much harms as much as documenting too little.
- If you know the detail: document it (diagrams, mockups, text). If not: document what you are looking for, your best ideas, and **discarded paths**, and **prototype** (paper or electronic). Don't document or debate many options: **locate the zone of uncertainty and prototype it**; once the path is clear, document that and why.
- Documents online, shareable, linkable, commentable, editable with **change control** (who, when, rollback). Linked to each other and to the systems and concept docs.
- One-page diagrams, big and visible, per system, so the team internalizes them.
- Avoid the monolithic, impenetrable **"design bible"**; prefer small, understandable references for artists, programmers, etc.

### Keeping Your Documentation Up-to-Date
- "Living" documents: plan from the start to update them. If neglected, the implemented game drifts away from the designed one and the documentation becomes outdated, misleading, and "worse than useless".

## 11. Spreadsheet Details (spreadsheet structure)

- **Basic structure**: one **row per part**, one **column per attribute**. The part's state = the values in its row.
- Example (Fig. 8.3, melee weapons): columns Name / Attack / Damage / Speed; rows: Dagger, Short sword, Cutlass, Broad sword, Rapier, Long sword, Great sword (values like Attack 0-5, Damage 2-6, Speed 1-5; the extracted text has the table misaligned, don't trust the exact numbers).
- Parts of very different types (weapons, flowers, cars, teams) -> **groups or, more commonly, separate sheets**; parts of the same type together. Ranged weapons or spells can go on the same sheet if they share nearly all attributes; if not, a sheet of their own with their attributes.
- There can be cells with the **effect of each behavior in mathematical form** (formulas).
- Include **pointers** to external descriptions (text and diagrams) of parts, attributes, and behaviors.

### Beyond Attributes and Values
- **Names**: a part can have an on-screen name, an internal reference name, and a filename/directory name for its content (art, sound). List them all in the spreadsheet: it helps with **localization** (replacing the on-screen name with its equivalent in another language) and with maintaining the file-naming scheme the program reads.
- A **single file-naming standard**, followed to the letter and reflected in the spreadsheet, saves "immense headaches"; letting everyone name things as they please is a recipe for disaster (you can't reconstruct why a file is named the way it is). You don't have to settle it on day 1.
- **Color formatting** for readability: distinguish part names, **global coefficients**, numbers that must not change, etc.
- **Cell comments**: record the why of a name or value, and whether it is **temporary/under test** or **thoroughly tested and must not change**. Keep them up to date or they become misleading.

### Data-Driven Design
- The most valuable thing about the spreadsheet: using the data **directly in the game** (if digital). It's worth automating the **export to CSV, JSON, or XML** that the game reads.
- Code objects have **default initialization values** that the data file overrides -> data and code structures stay separate.
- If the spreadsheet/docs match the parts and attributes in the code, designers try new values **without touching code** -> much faster iteration.
- A recommended extra step: have the game check the exported file's **timestamp** and **reload it if it changed**, allowing data changes **while the game is running** (hot reload) and trying many more attribute values, shortening the design-test cycle even further.
- Footnote: it works just as well in analog games: prepopulating card values and importing them into a layout program greatly reduces testing and iteration time.

## 12. Questions to Consider About Your Detailed Design (complete, paraphrased)

1. Are enough parts defined to build the core loop? Does each have attributes, values, value ranges, and behaviors?
2. Do all the parts have meaningful interactions with each other and with the player? Do they all affect others while also being affected?
3. Have you defined different types of parts: physical, nonphysical, and representational game parts?
4. What is the smallest number of states and behaviors with which the loops can be built and the intended effects achieved? Do they support the desired interactions and progression paths?
5. Are the main parts specified well enough to implement ("spreadsheet specific")?
6. Do the behaviors give enough feedback for the player to understand when state changes occur and to build their mental model?
7. Does the player have enough interaction? Do the parts enable meaningful decisions and enough "knobs and dials" to perturb the game's internal model?
8. Are the effects of the behaviors local in scope and general in applicability? Are there parts with global effects, single-use or brittle behaviors, or ones that overshadow all the others?
9. Are parts, attributes, and behaviors documented? Are there text docs and diagrams linked to spreadsheets with the part-attribute data? Can those spreadsheets be read in the game during development to speed up iterative testing?

## 13. The Author's Summary (Summary)

- You have reached the most detailed and most "grounded" level of design. Designing the parts well builds the systems and supports the desired experience; documenting them in text and numerically in spreadsheets ensures they are implementable and that the numbers support the overall goals. Ch. 9 shows how to make the parts' values and effects deliver a balanced experience.

---

## 14. Extracted Operational Checklists (for designing / analyzing / balancing)

**Designing a new part**
1. What type is it (physical / nonphysical / representational)? Is it atomic or a subsystem?
2. Minimum attributes: does an equivalent one already exist on another part? Does the player see it and decide with it? Can I explain it in one sentence that differs from the similar attribute?
3. For each attribute: order (amount / rate / rate-of-the-rate), range, type (integer, normalized, label, string), distribution shape (linear vs bell curve), scale communicable to the player.
4. If the value needs logic -> it becomes a behavior (and the part is a system).
5. Behaviors: what resource does it create/consume/exchange? Is it local (same level and context)? Does it only perturb, not determine? Is it generic/context-free? What feedback does it produce?
6. Does it close a loop (affects and is affected)? If the connection is one-way, look for the return (short reinforcing, long progression, or balancing).

**Analyzing an existing design (warning signs)**
- Single-use attributes, or two attributes the player can't tell apart.
- Ranges that are too large (imperceptible differences) or too small (no discrimination); 0-1.0 without normalization; ranges read as linear when the generation is a bell curve.
- Behaviors that affect parts of another level or context (not local); parts that "determine" the state of others (they break encapsulation).
- Scripted, contextual, single-use behaviors (brittle); lack of emergence.
- Verbs without feedback; late feedback (>250 ms laggy, >1 s disassociated), obscure, text-only, inconsistent, or decorative with no state behind it (noise).
- Parts with linear chains and no return; parts with global effects that overshadow the others.
- Internal systems the player neither sees nor decides on but that get a lot of effort (e.g., merchant trade).
- Granularity out of balance with the interactivity budget (per-unit detail with hundreds of units).
- Possible rich-get-richer: losing reduces the resources needed to recover -> add a balancing loop.
- A concept with no cohesion (a pile of parts), an excess of irrelevant part variety, a monolithic "design bible", outdated documentation, unmarked open decisions, qualitative adjectives without a number.

**Balancing (hooks into ch. 9)**
- Weighting coefficients as attributes of their own (the weight of cannons/crew/captain in the attack) to tune by iteration.
- Every extra attribute = a new route to imbalance; hence minimize.
- A data-driven spreadsheet with timestamp-based hot reload to try values without recompiling; comment cells with a "temporary / tested" status.
- Understand each attribute's probability distribution (percentile vs 2d6) before comparing values.
- A prototype with a complete core loop (even an ugly one) before fine-tuning numbers.

## 15. Cited Example References (quick index)
- Nautical age-of-sail game (hypothetical): the guiding example for parts, attributes, behaviors, loops, and rich-get-richer.
- Flocking (boids): emergence from 3 local rules.
- Conway's Game of Life (Gardner 1970): emergence from neighborhood rules.
- Parable of the Polygons (Nicky Case 2014) / Schelling 1969: emergence of segregation from local happiness.
- Slime Rancher (2016): stacking + food seeking; tabby slimes moving food -> emergent cascades.
- Two d6 (ch. 9, Fig. 9.1): non-uniform distribution (2 and 12 ~3%, 6 ~17%).
- Idle games / RPG XP: second- and third-order attributes.
- Melee weapons (Fig. 8.3): a spreadsheet example with part=row, attribute=column.
