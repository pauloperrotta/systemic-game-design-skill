# Balance: Methods and Practice (Ch. 9 and 10)

Read this to BALANCE with numbers: the four methods (designer, players, analytics, math), probability (1-(1-p)^n, distributions, perceived fairness), cyclical rock-paper-scissors relationships vs. cost-benefit, curves (linear, polynomial, exponential, logistic, piecewise, NAP), a procedure to value and cost items (Mod Value), pacing and time per level, economy (inflation, stagnation, arbitrage, import/export channel) and metrics (funnels, cohorts, retention).

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). The book section each block comes from is given in brackets.

## Index
- PART A — CH. 9: BALANCING METHODS
- A1. What "balance" is [sec: Finding Balance in Your Game]
- A2. The four families of methods [sec: Overview of Methods and Tools]
- A3. Probability in balancing [sec: Using Probability in Game Balancing]
- A4. Transitive and intransitive systems [sec: Transitive and Intransitive Systems]
- PART B — CH. 10: BALANCING IN PRACTICE
- B1. Progression and power curves: fundamentals [sec: Creating Progression and Power Curves]
- B2. Types of curves: cost-benefit [sec: Defining Cost-Benefit Curves]
- B3. Balancing parts (weapons) [sec: Balancing Parts, Progression, and Systems → Balancing Parts]
- B4. Balancing progression [sec: Balancing for Progression]
- B5. Economic system balance [sec: Economic System Balance]
- B6. Analytical balance and metrics [sec: Analytical Balance]
- B7. Chapter summary and closing messages [sec: Summary]
- PART C — SYNTHESIS FOR PRACTICAL USE (derived from the above)
- C1. Recommended balancing workflow (combined from the two chapters)
- C2. Common mistakes and how to detect them
- C3. Formulas at a glance
- C4. Games cited (one line each)

---

---------------------------------------------------------------------
# PART A — CH. 9: BALANCING METHODS
---------------------------------------------------------------------

## A1. What "balance" is [sec: Finding Balance in Your Game]

- **Game balance**: how well the game plays; it results from the relationships between parts (attributes, values, behaviors that affect one another). At bottom it is numbers (attribute values), but it is a property of the player+game system (including the player's mental model, psychology, systems and math).
- It includes the pace of individual and overall progression (does the player advance too easily/quickly or hit too many obstacles? do all players advance at a similar pace without feeling "on rails"?).
- **Balanced game** =
  - There is no single dominant path/strategy and no player with an inherent, insurmountable advantage.
  - There is an **explorable possibility space** with meaningful decisions and several viable directions.
  - The space does not narrow until how to win is obvious; in hindsight there is no "easiest way to win".
- An unbalanced game (dominant strategy) **reduces engagement and replayability**: once you know the trick, why keep playing? If everyone has similar opportunities, it feels fair; the loser feels they could have won and tries again (especially if they did not see another player exploit a flaw).
- From the player's side: they can take risks and recover; they do not feel the ending was decided long before. They stay in the **flow channel** (skill vs. challenge dynamically matched, neither bored nor frustrated).
- **Bicycle metaphor**: balance is dynamic, not static. If the player falls into an unrecoverable failure state, or the game is balanced at the start but not later on, "the bike falls over".
- Almost no game is born balanced: it is achieved in the **designer's loop** (iterate + test). Building the game from **nested hierarchical systems** lets you balance each system on its own and then as part of the one above it, instead of the whole game at once.
- Approach: think of balance as manipulating the system's **parts and loops**.

## A2. The four families of methods [sec: Overview of Methods and Tools]

Two broad categories: qualitative/heuristic (intuition) and quantitative (math). They are **complementary**, not mutually exclusive.

### 1) Designer-Based Balancing
- Use intuition ("does it feel right?"). You need a set of design heuristics. Essential at the start.
- Careful: hard does not mean unbalanced (Dark Souls, Super Meat Boy: hard, not for everyone, but not badly made).
- **Cautions**: intuition also leads you astray; no designer gets a larger system right the first time. Do not get discouraged if a "beautiful" game turns out unplayable. Worse: **hours- or days-long arguments based on intuition** about something a quick prototype would settle. Rule: cut those arguments short with other tools (prototype and measure). Heuristics help you see which relationship between attributes produces the intended experience and decide when to continue or cut your losses, but no wise designer trusts them completely.

### 2) Player-Based Balancing
- Playtesting: players play and report; it is the designer's loop in action. Use it liberally.
- **Caution**: players give *feedback*, not solutions. They tell you what they dislike, rarely how to fix it; finding the solution is the designer's job (they are not designers, just as a moviegoer is not a director).

### 3) Analytical Methods (backward-looking)
- They analyze real data on how the game is played. They need enough players (hundreds/thousands) and a playable game.
- Look at behavior, not just user counts: which paths they follow, which quests they repeat or avoid, **every important decision point** (record the choice and how long they take to decide).
- Examples of what to measure: in strategy, which faction wins how many battles (if one wins far more, that is a problem); in RPGs, which characters they pick on entry, whether they read descriptions, whether they finish the tutorial; time for each class to reach a given level.
- **Beware of correlations**: if thieves level faster, it may be an inherent class advantage OR veterans may be the ones playing them. Cross-check against other factors (player tenure, session length, number of characters played) before concluding.
- It requires instrumenting the game: log and send data (with permission when offline). In analog games: measure game length, turn length, pieces/strategies used in playtests.

### 4) Mathematical Methods (forward-looking)
- Models of how the game will work; most useful when creating a new game and in competitive games with heavy progression. They require some probability/statistics.
- They rely on **spreadsheets** (rows = objects, columns = shared attributes, cells = values; color formatting and comments to keep things tidy). They help visualize relationships and build formulas that compute values.
- They ensure: (a) object costs and benefits are in balance; (b) no object is "the one that beats everything" or "the one everything beats"; (c) objects, costs and rewards progress at roughly the same pace, consistent with the sense of fairness/engagement and with the desired speed.

### Cautions about analytical methods [sec: Cautions About Analytical Methods]
- **Analytics-driven vs. analytics-informed**: do not let the data (or testers, or your own taste) override everything; interpret it in context. Trying to build a "guaranteed" game from preference data (genre, mechanics, art) fails because it ignores systemic/emergent effects and what players cannot ask for because they cannot conceive of it (a quote attributed to Ford: "faster horses").
- **Sample size and distortion**: if a large % of ALL players never build X or never play Y, that is strong data. Relying on friends / a small focus group / a small community is risky (worst case: changes made because "the boss's nephew doesn't like it").
- **Vocal minority**: the most committed fans are the loudest and the most resistant to change. The author's case: a game with ~100,000 players/day, big changes, forums exploded; analysis showed the key metrics were rising and the complainers were a few dozen people (<0.05%). The change stayed; people got used to it. Caveat: sometimes the vocal ones are "opinion leaders" who anticipate the rest; tell the difference by looking at the data.
- Footnote: "learn to play" is not a valid designer response to perceived difficulty.

### Case: Tumbleseed (progression analysis) [sec: An Example: Tumbleseed]
- Postmortem with progression-funnel data: 41% reached the Jungle; 8.3% the Desert; 1.8% the Snow; 0.8% the Summit; 0.2% finished the game. 59% did not get past the first checkpoint and each of the next two lost ~80% of the remaining players. It should have set off alarms about the difficulty ramp.
- Cause: the player had to master all at once: new controls, new rules, new terrain (random every time), new enemies (sometimes several), new powers (some dangerous) → it exceeded the **interactivity budget** (action/feedback + short-term cognitive + long-term cognitive at the same time). There was also a mismatch between casual/colorful graphics and hard difficulty (it hurt sales).
- Lesson: it is not fixed by "tweaking a class or a level"; it is a problem caught early through playtesting. The good part: they instrumented progression and could find out why it was perceived as so hard.
- **Usage heuristic**: measure the funnel by checkpoints; ~80% drops in consecutive steps = alarm. Mind the pace at which novelties are introduced (do not stack several at once).

### Cautions about mathematical models [sec: Cautions About Mathematical Modeling]
- They are a means, not an end; the illusion of "leaving the balance perfect" is a time-consuming trap. Models find **the most unbalanced parts**; they do not reach arbitrary precision.
- They do not make aesthetic decisions: if you want a faster or flashier vehicle without it costing more, you have to compensate with other costs (high maintenance, poor handling) using existing or new attributes or systems.
- No method replaces the designer's judgment.

---------------------------------------------------------------------
## A3. Probability in balancing [sec: Using Probability in Game Balancing]
---------------------------------------------------------------------

### Basic primer [sec: A Quick Primer on Probability in Games]
- Probability as a number between 0 and 1 (100% = 1.0; 50% = 0.5): this lets you manipulate them mathematically.
- It is used to **simulate systems you do not implement**: the point where the system hierarchy "cuts off" and you assign a probability (a sword that hits, seducing with wit) instead of modeling physics/psychology. You set a success probability, generate a random value and see what happens.
- **Randomness**: dice, cards, counters, RNG. **Apparent/functional randomness** is enough (the deck is not rigged, the RNG's period is undetectable).

### Separate vs. linked events [sec: Separate and Linked Events]
- The probabilities of all possible outcomes sum to exactly 1.0.
- **Separate (independent) events**: the coin has no memory; after 100 heads, the next flip is still 0.5.
- **Linked events**: if you require several to happen (3 heads in a row, or 3 coins at once), you **multiply** probabilities: 0.5×0.5×0.5 = 1/8 = 12.5% (each additional coin halves it).
- Die: rolling a 6 = 1/6 ≈ 0.167; two 6s at once = 1/36 ≈ 2.8%.
- Practical formula: P(A and B independent) = P(A)×P(B).

### Probability distributions [sec: Probability Distributions]
- With several dice added together NOT all totals are equally likely. Probability of a total = (combinations that produce it) / 6^n (with n dice; 2d6 → 36).
- 2d6: total 5 → 1+4, 2+3, 3+2, 4+1 = 4/36 ≈ 11.1%. Full 2d6 distribution (2..12): 2.7%; 5.6%; 8.3%; 11.1%; 13.9%; 16.7%; 13.9%; 11.1%; 8.3%; 5.6%; 2.7% → "bell curve" (normal/Gaussian distribution). It appears when combining several independent events.
- Definitions:
  - **Mean**: add up and divide by the count.
  - **Mode**: the most likely value (the peak).
  - **Median**: the middle one (as many above as below).
  - **Range**: the difference between the extremes (2d6: 2-12).
- In symmetric distributions mean, mode and median coincide; in asymmetric ones they differ (if mode and median are above the mean, the "hump" shifts to the right). Example: the strength of RPG characters (1-100 scale) tends to have a mean >50 because players like characters stronger than the population average.
- **Use in design**: adding more dice = results more concentrated at the center and less volatility; a single die = everything equally likely (more "swingy"). Use this to choose how much variance you want in an outcome.

### Changing probabilities [sec: Changing Probabilities]
- Drawing cards without replacement: the probability of the sought card rises with each miss (1/52 → after 32 cards without seeing it, 1/20 → 1/1 at the end).
- Used to give a sense of "getting closer" (pity timers / growing probabilities). E.g., loot boxes with a 1% rare-prize probability, independent vs. linked (rises a bit after each miss). Since those games have thousands of possible items, the probability of getting one specific item is still small and takes a huge number of attempts/purchases.

### Cognitive biases and the three-door problem [sec: Cognitive Biases and the Three-Door Problem]
- People estimate probabilities poorly (e.g., more lottery tickets are bought the bigger the prize, even though the chance is tiny).
- **Monty Hall**: 3 doors; after your pick, the host (who KNOWS where the prize is) opens a door with a goat. Staying = 1/3; switching = 2/3. Key: the opening was not random, so it does not change the 1/3 of your original choice; the entire remaining 2/3 concentrates on the other door. 100-door version: he opens 98, switching = 99%.
- Relevance: the player's mental model of probabilities is often wrong, and that is part of the design.

### Perceived fairness and the Bernoulli formula [sec: Fairness]
- Players perceive pure probabilities as "unfair" if the outcome takes a long time (especially in digital games).
- **Probability of at least 1 success in n attempts** (Bernoulli process):
  - P(≥1 success in n) = 1 − (1 − p)^n
  - Example p=0.33: n=3 → 1−0.67³ = 1−0.30 = 0.70 (70%). After 5 failed attempts the chance of that happening was ≈13.5% (people already suspect cheating). After 10 attempts there is still ~2% of not having won.
- Rarity example: p=1/100,000 (0.00001): 100 attempts → ~1%; for 50% you need almost 70,000 attempts (≈69,300; n = ln0.5/ln(1−p)).
- **Design rule**: you design for engagement/enjoyment, not statistical rigor. You can tilt probabilities in the player's favor (or against) creatively without ruining the experience.
- A super-rare item with social value (MMO): you can make it impossible for the first hours/days to build tension, or raise the odds sharply **just once** to trigger the incentive (others see it and want one) and readjust immediately so as not to flood the game (it loses social value).

### Unlikely events with a large population [sec: The Likely Occurrence of Unlikely Events]
- With many people, the rare happens by itself. 1M players/day, 100,000 attempts a day with p=0.00001 → 1−(1−0.00001)^100,000 ≈ 63% that the item shows up in a day. "Lottery logic": someone wins even though each person's chance is minimal.
- Decision: either you tilt the probabilities to encourage players, or you let the scale of the player base do the work.
- **Social casino games** (no real-money payout, not subject to gambling regulation): they allow tricks like the **near miss** (the game has already decided you lose and animates an "almost" win: 3 of 4 ships lined up, the fourth overshoots/falls short). Fallacy: believing that "almost winning" or failing several times makes the next attempt more likely ("I'm due one"). Two sequential events are independent, but the mind does not see it that way.
- **Ethical use**: (a) *silent assist*: quietly raising the success probability after failures (virtual basketball, hitting monsters) to avoid frustration; (b) manipulative uses (pushing spending). If overdone, the player finds out and quits feeling they "never had a chance". It is an ethical decision for the designer.

### List of probability procedures (to apply)
1. Define whether events are independent or linked; multiply for linked ones.
2. Chance of achieving something in n attempts: 1−(1−p)^n; attempts needed to reach a target chance q: n = ln(1−q)/ln(1−p).
3. To see whether the reward pace is perceived as fair, calculate at which n the player "should already have won" (e.g., ≥90%) and see how many players exceed it without a reward.
4. Decide whether a "protected bad luck" mechanism (growing probability) is needed, depending on tolerance for perceived unfairness.
5. Choose the number of dice/events to control variance (more terms = more bell-shaped).

---------------------------------------------------------------------
## A4. Transitive and intransitive systems [sec: Transitive and Intransitive Systems]
---------------------------------------------------------------------
> **Watch the terminology.** Sellers calls the rock-paper-scissors cycle "transitive" and the cost-benefit ladder "intransitive". Most of the literature (Schreiber, Adams, Ernest) uses the terms the **other way around**: there, "intransitive" = rock-paper-scissors and "transitive" = A better than B better than C, offset by cost. This reference keeps the book's terms inside this section, but when talking to the user it is best to use unambiguous names: **cyclical balance** (rock-paper-scissors-style counters) and **cost-benefit balance** (a power ladder paid for with cost), and to point out the inversion if the user uses either of the two terms.

### Cyclical balance ("transitive" per Sellers; rock-paper-scissors, RPS) [sec: Transitive Balance]
- **Author's definition**: each part is better than one and inferior to another; none dominates all the others. RPS is the example; there are variants with more parts (up to 101; Rock-Paper-Scissors-Lizard-Spock: each beats two and loses to two).
- Examples: Wu Xing (5 phases: wood, fire, earth, metal, water; generating cycle and overcoming cycle); lizards with three male colors (orange>blue>yellow>orange; each color "invades" another when it is rare and can be invaded when it is common → dynamic balance); **Dark Age of Camelot** (RvR with three realms, each dominating another; if one grows too much, the other two ally: self-balancing); 1975 US military doctrine (units as RPS). Many wargames use it because it is easy to understand and to balance at the system level; it tends toward dynamic balance and avoids "rich-get-richer".

### Requirements for transitive balance [sec: Requirements for Transitive Balance]
- **Odd number of parts** at the same organizational level: each must dominate exactly half of the others and be dominated by the other half. With 5 parts: beats 2, loses to 2.
- Dominance can be **probabilistic** (a significant advantage, not a guaranteed win), but must be clear.
- **Even number → no stable transitive balance**: an uneven advantage/disadvantage can always emerge. Case: Horde vs. Alliance in WoW (only 2 factions) → continuous ecological collapse that the designers had to correct.
- Each type can have **several instances/subtypes** if they aggregate into a group with the same transitive characteristics (several infantries, cavalries, archers, as long as infantry as a group beats cavalry, etc.).
- More than 3 main types is possible but **hard to define with attribute values**; even 3 is complicated. That is why almost all games stay at 3 main types + many subtypes.

### How to achieve transitive balance (procedure) [sec: Achieving Transitive Balance]
1. Choose attributes shared by all the parts (e.g., Attack, Defense, Range, Speed).
2. Give each part the **same total of points** ("+") to equalize overall capability (first level of balance).
3. **Distribute those points differently** so each excels at one attribute.
4. Verify that each winning pair meets the rule.

Table 9.1 (reconstructed): 
| Unit | Attack | Defense | Range | Speed |
|---|---|---|---|---|
| Infantry | +++ | ++ | + | + |
| Cavalry | ++ | + | + | +++ |
| Archers | + | + | +++ | ++ |
(each row sums to 7 "+"; the exact distribution is inferred from the text.)
- Infantry beats cavalry (Attack +++ vs. Defense +; cavalry runs, but if the infantry closes the distance, it loses).
- Cavalry beats archers (Attack ++ vs. Defense +; Speed +++ vs. ++ prevents fleeing).
- Archers beat infantry (Range +++ vs. Defense +; infantry has more attack but archers keep their distance).
- **Caution**: the transitive system exists inside a larger one (terrain, weather, styles). If it is too rigid and insensitive to outside influences, nobody gains an advantage and the game stagnates. If players discover that "rocky terrain makes archers invincible", the decision space collapses into a single strategy. **Playtest under different conditions** so that it is resilient but neither static nor reducible to one strategy, and remains perturbable by the player.

### Cost-benefit balance ("intransitive" per Sellers) [sec: Intransitive Balance]
- Author's definition: in a given pair, one part is simply better than the other (always or probabilistically). Taken alone, each transitive pair is intransitive.
- Another way to balance: it does not equalize all parts at the system level, but **balances them by cost-benefit**: more benefit ↔ proportionally more cost. It appears in any game with **progression** (character, items, armies, crops that grow in power).
- Intuitive: a rusty dagger costs less than a great adamantium sword; the hard question is **how much more**. It requires defining the mathematical relationship between types of parts + a lot of iteration.
- To balance intransitive systems you must define the **progression/power curve**, which means defining costs and benefits (Ch. 10).

### Summary of the golden rule
- Transitive: same point "budget", different distribution, dominance cycle (odd). Intransitive: cost proportional to benefit, power curve.

---------------------------------------------------------------------
# PART B — CH. 10: BALANCING IN PRACTICE
---------------------------------------------------------------------

## B1. Progression and power curves: fundamentals [sec: Creating Progression and Power Curves]

Two base ideas:
1. **Every benefit has a cost**; as cost rises benefit rises and vice versa, tied together. The delay in being able to pay higher costs is what regulates the game's pace while the player keeps feeling improvement.
2. Both the player's representative and the objects they use (or that oppose them) advance by improving attribute values. Curves regulate that **player and challenge** grow at the pace you want.

### Defining costs and benefits [sec: Defining Costs and Benefits]
- The cost/benefit relationship is **economic** (the player trades costs for benefits). If the player feels worse off after advancing (leveling up, adding units), resources lose value and engagement drops.
- Costs and benefits are expressed in relevant attributes = resources. Costs: XP, currency, commodities, battles won, animals raised. Benefits: more health, magic power, cards, provinces, action points.

### Core resources [sec: Core Resources]
- One or a few resources that the player maximizes and/or cannot lose in order to keep playing (score and lives in an arcade game). They are tied to the core loops. E.g.: health and XP in an RPG; money in a tycoon; controlled area in strategy.
- **Procedure to find them**: review the parts sheet (Ch. 8: attributes in columns, parts in rows); look for the attributes the player depends on most and without which they cannot continue. There may be several if there are several loops (focus on one at a time).
- If there are several candidates: check whether one **encompasses** the others (it may be the one that emerges from the synergy of the others), or whether they are **sequential** (health → wealth → social status by phases).
- **Shadow resource**: a resource not visible in the game that encompasses several resources, to base costs/power curves on.
- If they are truly incommensurable → one progression curve per resource, taking care with the **handoff** from one to another without losing momentum.
- Goal: have ONE core resource as the pillar of the cost or benefit of the primary progression/power curve (it may require reorganizing attributes; worth it).

### Subsidiary resources [sec: Subsidiary Resources]
- Those that sustain/improve/repair the core ones; their benefits are indirect to the core resource. E.g.: in strategy with "controlled area" as core, armies/fortifications/technology are subsidiary; in romance, the relationship with one person is core and friends/money/information are subsidiary.
- Core resource curves first, then the derived secondary ones.

### Special cases [sec: Special Cases]
- Resources that affect others and have limited or periodic effects. Spaceship example: ore = core; speed and armor = subsidiary; an occasional **turbo** that slightly damages the ship is a special case (it does not matter until it matters a lot). More complicated: spending ore to increase the turbo's duration or reduce its recharge.
- Reducing everything to a single equation (shadow resource) can be a receding goal, or flatten the game's **dimensionality** by making the trade-offs too obvious.
- Part of the cost-benefit correlation will have to be done **heuristically** + iterative playtesting; costs/benefits end up near a curve you perhaps could not have predicted.

---------------------------------------------------------------------
## B2. Types of curves: cost-benefit [sec: Defining Cost-Benefit Curves]
---------------------------------------------------------------------

### Comparison summary

| Curve | Formula | Rate of change | Key feature | Use / risk |
|---|---|---|---|---|
| Linear | y = A·x + B | constant | fixed slope | simple; relative change shrinks (hedonic fatigue) |
| Polynomial | y = x^n (with multipliers) | grows, but its proportion relative to y tends toward linear | relatively "flattens out" | power that rises quadratically; same problem as linear at the high end |
| Exponential | y = A^x or y = B·A^x | ALWAYS grows | constant proportion between steps | the most used in progression; gigantic numbers at the top |
| Logistic/sigmoid | y = L / (1 + e^(−k(x−x0))) | slow-fast-slow | ceiling L | power with diminishing returns; economy of stacked resources |
| Piecewise linear | linear segments | constant per segment | hand-made | milestones, intermediate goals |
| NAP | no equation | irregular | round/hand-set numbers | "surprise and delight", adding variety |

### Linear curves [sec: Linear Curves]
- y = A·x + B. A = slope (how much y changes per unit of x); B = offset (often 0).
- In progression A>0 (more power as you advance). Example: A=2, B=0 → x=1→y=2; x=3→y=6.
- **Problem**: the same absolute change is proportionally smaller and smaller. y=2x: going from x=8→10 (y 16→20) is +25%; from x=98→100 (y 196→200) is +2%, the same absolute sum but "so what?". This feeds **hedonic fatigue**. That is why the linear curve is almost never used alone for power/progression.

### Polynomial curves [sec: Polynomial Curves]
- y = x^n (with multipliers: e.g., 5x²). x=1..5 with x²: y = 1, 4, 9, 16, 25; differences 3, 5, 7, 9 (the **second difference** is linear → a property of polynomials).
- **Basic progression ratio** (Bateman 2006): the difference in y between consecutive steps. In linear it is constant; in polynomial it grows. **Total progression ratio**: that difference as a proportion of the total value of y; in polynomials it tends to 1.0 as x grows (the curve "flattens", resembling linear). Consequence: in play, the top of the curve feels like a similar amount of change (it loses impact), but there are also no astronomical jumps as in exponentials.
- **Useful property**: a quadratic polynomial is the **product of two linear progressions** (Achterman 2011). Example: monsters per level 1,2,3,4,5 (linear) × gold per monster 10,20,30,40,50 (linear) = gold per level 10, 40, 90, 160, 250 (quadratic). Two simple systems that interact give faster growth than the sum of the parts. Careful: multiplying two linear curves by accident produces an accelerating curve.

### Exponential curves [sec: Exponential Curves]
- y = A^x (or y = B·A^x). The rate of change keeps growing without flattening. If the **base A is small**, it does not rise too fast.
- RuneScape: a complex XP equation with an exponential component of base 1.1^x → steps that grow slowly at first: early levels are reachable and quick (sense of achievement), late levels seem superhuman, but by the time you get there you already earn huge amounts of XP.
- **Perceptual property**: the *total progression ratio* stays low relative to the current value: the far end looks like an impossible mountain, but the next step looks reachable compared with what you have already covered → it helps you keep going and avoids hedonic fatigue.
- It is probably the **most used** curve in progression/power: easy to tune and to fit to objects. Risk: absurd numbers (billions, trillions...; Adventure Capitalist reaches 10^300 = "1 novemnonagintillion"): since they cannot be imagined they lose meaning (hedonic fatigue again). The pleasure of "numbers going up" (A Dark Room: "people who like numbers going up" + "exploring the unknown") exists but wears out if overdone.

#### Use for levels/thresholds (procedure)
1. Each level/milestone = value x; the points it requires = y of the exponential function.
2. If the player earns more points from ever-harder challenges, the thresholds must spread further apart or the player will reach them faster and faster.
3. **The base is the heuristic for how much each step grows**: y = 1.4^x → each level asks for 1.4× the previous; after 4 levels it has doubled (1.4⁴ ≈ 3.84 ≈ almost 4×; "more than double" per the text is an understatement: in 2 levels it is already 1.96 ≈ 2). Move the base (1.2; 1.3; 1.5...) to adjust the rise and **doubling time**.
   - Shortcut (derived, not in the book): levels to double = ln2 / ln(base): base 1.1 → 7.3; 1.2 → 3.8; 1.4 → 2.06; 1.5 → 1.71.
4. Decide according to time/battles per milestone, challenge hardness and reward size, and then **balance challenges, power and rewards against one another**.

**Table 10.1: XP = 1,000 × 1.4^level** (rounded to hundreds; level 1 arbitrarily set to 0): 
| Level | XP | Level | XP |
|---|---|---|---|
| 1 | 0 | 10 | 28,900 |
| 2 | 2,000 | 15 | 155,600 |
| 3 | 2,700 | 20 | 836,700 |
| 4 | 3,800 | 25 | 4,499,900 |
| 5 | 5,400 | 30 | 24,201,400 |
- Ratio between consecutive levels ≈ 1.4: acceptable; but the absolute numbers become enormous.

#### Key mistake: poorly coupled challenge and reward curves
- Book example: if challenges rise ×3 per level and the core-resource reward (health, attack) rises only ×1.25, the game quickly becomes unplayable (challenges grow much faster than the ability to face them). Rule: **the bases of the challenge and power curves must be similar** (or the power one slightly larger if you want a power fantasy; slightly smaller if you want rising tension).
- How many quests/monsters per level remains the designer's decision and a matter for playtests; the math only warns you if players "burn through" the game too fast or get frustrated.

### Logistic / sigmoid curves [sec: Logistic Curves]
- Less used for balance, but useful. They model real processes (learning, ecology: slow initial growth → rapid expansion → slowdown as resources are consumed). Widely used in simulation and AI.
- **Formula**: y = L / (1 + e^(−k(x − x0)))
  - L = maximum value (the ceiling)
  - e ≈ 2.718
  - k = steepness (how fast it rises in the middle)
  - x0 = x of the midpoint (below x0 it is low, above it is high; at x0, y = L/2)
- Shape: slow – fast – slow – tends to stop changing. In play: power that at first demands a long investment, pays off a lot in the middle stretch, and at the top has **diminishing returns**. Figure 10.1: L=6, k=1.0.
- Advantage over the exponential: it lacks the runaway change in y.
- **Stacked logistics**: one per resource; the player must decide when to switch resources once the first reaches diminishing returns (Fig. 10.2: 4 resources with different curves). It widens the range of values of an economy without unbalancing it and spreads the "fast rise effect" of an exponential across several logistics. Balancing each object on its own curve is simpler than covering the whole range with a single curve.

### Piecewise linear curves [sec: Piecewise Linear Curves]
- Motivation: the smoothness of an equation becomes boring; the player knows the rate (a +n sword is always a given improvement over n−1) and decides nothing. It is made by hand, approximating an exponential with linear segments (by summation or by linear interpolation).
- **Summation method (known rates)**: RPG HP: level 1 base = 12 (≠0 so the graph is clear); +2/level in levels 1-10 (→30 at level 10); +5/level in 11-20 (→80 at 20); +10/level in 21-30 (→180 at 30).
- **Interpolation method (known endpoints)**: you want 2 HP at level 1, 20 at level 10, 100 at level 20. 
  - Segment slope = (y1 − y0) / (x1 − x0).
  - Segment 1: (20−2)/(10−1) = 18/9 = 2 HP/level. Segment 2: (100−20)/(20−10) = 80/10 = 8 HP/level.
  - In a spreadsheet you play by changing the endpoint y values until you reach the desired numbers and slopes.
- Each segment is linear but the whole looks curved/exponential. It is simpler than mapping to an exponential if your math is rusty and it also **gives milestones**: knowing that at level 11 the HP per level jumps from 2 to 8 is an intermediate goal for the player.

### Near-Arithmetic Progression, NAP [sec: Near-Arithmetic Progression Curves]
- Term from Bateman (2006): hand-made curves, similar to arithmetic (linear) ones but with no equation; typical of RPGs, made "by eye" or to keep round numbers.
- Example WoW early levels: 1→2 asks for 400 XP; then +500 for 2→3 and 3→4; +700 for 4→5 and 5→6; etc. (the pattern does not hold at every level).
- Benefit: "irregular" curves with zones of fast or slow acceleration to **surprise and delight** (Pecorella 2015), avoid boredom from predictability, and coordinate power curves so that **one type of object/resource yields more for its cost than another in certain stretches**, so that the player explores the space of curves by deciding how to spend.

### General principle: "make it work for the game, not for the math" [sec: Making It Work for Gameplay, Not Math]
- The math is never perfect, but the better balanced the curve, the less iteration time. After that you go back to playtesting and intuition to find the balance points. It may start exponential and end up hand-made, and that is fine.

### When to use each curve (derived guide)
- **Linear**: rarely alone; useful for short stretches or as a component of a product (quantity × value).
- **Polynomial / quadratic**: when you want moderate accelerated growth without explosion; note that it appears on its own when multiplying two linear curves.
- **Exponential**: the parent curve for XP per level, item tiers, rarity; tune it with the base.
- **Logistic**: for resources/items with a ceiling and diminishing returns; to force decisions about switching resources; as a comparison guide for cost-benefit (the book uses it that way in Fig. 10.7 with k=0.95 and x0=3.5).
- **Piecewise / NAP**: start with one of the above and hand-craft milestones, reward peaks and attractive opening stretches.

---------------------------------------------------------------------
## B3. Balancing parts (weapons) [sec: Balancing Parts, Progression, and Systems → Balancing Parts]
---------------------------------------------------------------------

### Context
- A frequent task: getting a system's parts balanced against one another. They are **intransitive** objects: some better than others but proportional to cost. Example: RPG weapons (attributes Attack, Damage, Speed; the scales do not match each other, which is normal).
- Criterion for balanced (it does not mean "equal"): each part has **a valid place** (a situation in which to choose it), they are **different** enough, and to the player it seems that **benefits and costs offset each other**. If costs were equal, nobody would use anything but the most powerful.

### Step-by-step procedure (the book's example)
0. **Initial table** (spreadsheet; reconstruction of Fig. 10.5: columns Attack/Damage/Speed; in short: the dagger with the lowest Attack and Damage, the great sword with 8/8 but speed 0-2 "by far the slowest"; dagger/short sword/rapier share the highest speed). Line chart (Fig. 10.6) to see the clustering: most values in a narrow middle range, only the dagger and great sword stand apart → more variety is needed.
   - Note: a line is not technically right for categorical data (bars would be), but it helps to see how they relate; explore visualizations.
1. **Choose the core resource** to balance: in an RPG, health (HP). An enemy at 0 = victory and loot; the player at 0 = death/setback.
2. **Order attributes by their causal chain toward the core resource**: damage reduces health, but first you have to hit (Attack) and before that be able to attack (Speed): Speed is the first "gate", then Attack, then Damage.
3. **Initial cost hypothesis**: summing Attack+Damage+Speed gives unconvincing costs (short sword and cutlass both 10; dagger 7; broad sword 11).
4. **Weights/coefficients per attribute**: Damage = 1.0 (the one most tied to the core resource); Speed = 2 (more speed = more chances to hit); Attack = 1.5 (important, but hard to know how much). Try it in the sheet. Result: a range from ~10 (dagger) to ~20 (great sword) → somewhat narrow (the most expensive only 2× the cheapest) but fine; problem: the cutlass ends up cheaper than the short sword (it loses value due to low Speed).
5. **Move the attribute values**, not just the weights (if you can; if not, you are left with manipulating multipliers or **situational factors** such as how hard it is to obtain; careful: they can block the player, e.g., they cannot afford another weapon and cannot find where the one they want is, or going there means dying).
   - Choose a **base object / midline**: the broad sword with everything at 5. Raise the dagger a little in Attack (0→1). Raise the great sword from 8/8 to 10/10. This "uncorks" the middle.
   - Watch the attribute chart to avoid crowding and absurdities (cutlass faster than rapier).
   - Iterate weights and values together (they affect each other).
6. **Decouple cost from value** (decoupling): call the weighted sum **Mod Value** and set the in-game **Cost** by hand, independently. Plot Mod Value vs. Cost together with a **guide logistic curve** (k=0.95, x0=3.5 in Fig. 10.7) as confirmation that it still follows the desired type of relationship.
7. **Final result** (Fig. 10.8; Mod Value = 1.3·Attack + 1.0·Damage + 1.75·Speed). Table reconstructed and checked against the formula:

| Weapon | Attack | Damage | Speed | Mod Value | Cost |
|---|---|---|---|---|---|
| Dagger | 1 | 1 | 6 | 13 | 10 |
| Short sword | 2 | 1 | 6 | 14 | 12 |
| Cutlass | 4 | 7 | 3 | 17 | 15 |
| Broad sword | 5 | 5 | 5 | 20 | 20 |
| Rapier | 5 | 3 | 8 | 24 | 25 |
| Long sword | 7 | 6 | 6 | 26 | 28 |
| Great sword | 10 | 10 | 3 | 28 | 30 |
(Check: dagger 1.3+1+10.5 = 12.8≈13; broad sword 6.5+5+8.75 = 20.25≈20; great sword 13+10+5.25 = 28.25≈28.)

8. **Cost set by hand, with intent** (reading of Fig. 10.7):
   - Weak weapons cost **a little less** than their Mod Value (an advantage to new/poor players).
   - Top-end weapons cost **a little more** (aspirational premium: seeing a great sword = the character paid a lot).
   - The cost/benefit lines **cross at the broad sword** (a fixed point of the mental model, in the middle).
9. **Verify**: in the attributes, each weapon has different strengths and weaknesses; wide ranges; following the ascending cost-benefit curve means the relationship is proportional and the player grasps it intuitively.
10. **Playtest**: do players quickly and happily build a mental model of relative effectiveness/cost? Surely more iteration.

### Practical rules from this procedure
- Assign weight 1.0 to the attribute most directly tied to the core resource; scale the others according to their position in the causal chain (frequency gates).
- Test weights with a spreadsheet and look at relative ranges (max/min cost ratio).
- Avoid the "congested center": widen the range of attributes; pick an anchor piece in the middle.
- In-game cost ≠ calculated value; use the difference as a design lever (accessible/aspirational).
- Balance signal: the Mod Value order matches the cost order; no weapon with better Mod Value AND lower cost than another (dominated/dominant).
- Once the weights are set, **any variant can be valued**: e.g., how much more benefit a dagger with +2 Speed gives vs. a broad sword with +1 Damage (delta × weight comparison).

---------------------------------------------------------------------
## B4. Balancing progression [sec: Balancing for Progression]
---------------------------------------------------------------------

- Types of progression: (1) the player representative's (character, army, farm) in attributes; (2) economic progression: coins, availability and improvement of items.
- Steps to design player progression:
  1. Choose the **carrier attributes** of the improvement (the core attributes).
  2. Those attributes lead to the **resources that are the cost** of advancing.
- Standard example: leveling up = accumulating XP and "spending" it automatically on crossing the threshold (more health, powers, access to content). The next threshold is higher than the current total (XP is not reset to zero): this allows exponential curves of points per level and the feeling of numbers that always go up. "Access to content" is a special attribute that is hard to quantify.
- **More than one progression resource**: more work (you must evaluate difficulty and time for each) but if different resources pay off differently at different stages, the player chooses their path strategically → more meaningful decisions. Example: progressing through combat/health at the start, then through wealth, then through friends, as health and wealth give less return (the step to the next level grows exponentially while the points earned do not). Careful: not everyone wants a multifaceted system; someone who starts with one resource must be able to **continue** with it. Optimizers will want the optimal route, so offering a change of focus can raise engagement.
- **Sacred rule**: the player must always feel they are advancing. If progress stops or the next advance is "infinitely far" given the reward at their challenge level, engagement evaporates. (Idle games: the external *prestige* loop provides another way out when the primary one becomes slow.) Even with several dimensions, they must always see meaningful ways to progress in at least one.

### Pacing [sec: Pacing]
- Progression is usually **punctuated (discrete)**, not continuous: improvements at milestones, more rewarding (something to look forward to) and easier to balance (you choose where the level-ups fall). A continuous curve is possible but hard to balance.
- Decide the **pace** in game units (monsters, provinces, flowers).
- The **shape of the cost-benefit curve** defines the pace: if you want them to give more and more points but take longer to advance, exponential. Hybrids too: a hand-made initial stretch (piecewise) to hook, then stacked logistics with different cost resources that together approximate an exponential. There is no single formula.

### Time and attention [sec: Time and Attention]
- The ultimate resources are **attention and time** (similar but not identical: attention = actively playing; time = can be passive).
- **Procedure for estimating time to advance** (activity calculation):
  - Points per activity × number of times needed × time per activity. E.g., zoo: 10 points per animal fed, 100 to level up → 10 animals; 2 min each → 20 min of full attention.
  - With randomness and failures: gem example: 1,000 points to level up; 50-200 points per successfully cut gem → 5 to 20 gems; with 80% success → ~7 to 25 gems including failures (actually 5/0.8 = 6.25 and 20/0.8 = 25); 1-3 min per gem → minimum ~7 to 75 min (the book's values); a very wide range → reconsider the system so it does not feel uneven.
  - Example remedies: the longer you spend cutting (up to a maximum), the lower the chance of failure; a bonus for cutting very well.
  - Summary formula: min_time ≈ (level_points / max_points_per_action) / p_success × t_min; max_time analogously with the maxima. What matters is the **range**, not just the average.
- **Clock time (timers)**: if part of the progression is regulated by clock time (crops, armies), you control with certainty how fast they advance, but engagement drops: the player starts the process and leaves (little to do, less chance of coming back). You have to respect the player's time.

### Secondary progression [sec: Secondary Progression]
- In complex games, short-term secondary paths keep engagement up when the primary milestones are far away.
- WoW example: **inventory** is limited at first (hard decisions about what to keep); with level and wealth you buy bigger bags; with trade skills you craft them. It is not rigidly tied (e.g., "2 more slots at level 10"), but to level, wealth and secondary skills → **almost self-balancing** because the player addresses the need when it becomes a problem. Keep these progressions decoupled but make sure they do not overwhelm the overall progression.

---------------------------------------------------------------------
## B5. Economic system balance [sec: Economic System Balance]
---------------------------------------------------------------------

- Economy = resources that enter through **sources**, are exchanged and leave through **sinks**, in reinforcing loops. Resources and objects are a secondary progression (wealth and possessions as markers of achievement and status). Balancing economies is still an "inexact art".

### Inflation, stagnation, arbitrage [sec: Inflation, Stagnation, and Arbitrage]
- **Inflation**: too many sources and too few sinks → the resource accumulates and is worth less and less. It happens to almost every game with an economy (not all the principles to prevent it are known yet).
- **Stagnation**: too few sources → low **economic velocity** (how fast resources flow, like a river). If it drops, the economy dies. It usually happens from overcorrecting against inflation (resources too precious → frustration).
- **Arbitrage**: buying cheap in one place and selling dear in another; if not managed, it produces massive inflation.

### Case: Habitat, dolls and crystal balls [sec: The Lesson Learned from Dolls and Crystal Balls]
- Habitat (1987): players start with 2,000 tokens (source). Vendroids = sinks (they sell items), Pawn Machines = buy back (token sources). Two Vendroids far apart had low prices on certain items: dolls at 75 tokens that a Pawn Machine bought back at 100 (+25 per doll); crystal balls at 18,000 that another Pawn Machine bought back at 30,000 (+12,000 each). So much money accumulated that the supply quintupled in one night, with no bug and no reports.
- Cause: each buyback created tokens out of nothing; inconsistent prices between machines = arbitrage loop. Luckily the players spent the money on treasure hunts instead of flooding the market; the prices were corrected.
- **Lessons**: (1) consistency: an NPC's sell price must never be lower than another NPC's buy price for the same item; (2) **monitor** the total money supply and per-player balances daily (the Habitat admins did and caught it); (3) every buyback is a source: it counts as one.

### Sources that must grow, sinks that keep pace
- Rewards that are too stingy → stagnation and abandonment; if they equal the previous one → hedonic fatigue. That is why most games with an economy inject more and more currency as the player progresses and then **struggle to find sinks**. WoW: the monetary value per monster rises more than 750× from level 1 to 60. If it is not accompanied by enormous sinks, the currency loses meaning as a reward.

### Building an economy with tiers and rarity (Albion Online) [sec: Constructing a Game Economy]
- Objects grouped into **tiers** (rarity + power/utility). Tiers 1-3 = training (little economic effect); tiers 4-8 = core of the economy. World zones with different tiers; value/power scales with danger/difficulty of obtaining.
- **Item power**: exponential **1.2^tier** → each tier is 20% more advanced; tier 8 ≈ 1.2⁴ ≈ 2.07× the utility of tier 4 (sense of progress without the distance between top and bottom becoming impossible). It was obtained **empirically** with a great deal of playtesting; once found, it saves time when adding content (it does not have to be derived again). For more difference: more tiers and/or a larger base.
- **Rarity** (probability of finding the item): exponential **3^tier** → each tier is 3× rarer; tier 8 is 3⁴ = 81× rarer than tier 4. The two highest tiers are extremely rare and valuable.
- **Decoupling the two curves** (power vs. rarity): keeps power "creep" in check, because rarity (and hence cost) per unit of power is high and grows nonlinearly (different bases). It enables a player-driven economy.
- Crafting in Albion: transmuting up to higher tiers and salvaging high tiers down to lower ones + money (a currency source).

### Price boundaries / market channel [sec: Price Boundaries / Creating the Market Channel]
- **Price boundaries**: give players room to form fluctuating prices (strategic and social interactivity) without excluding others or allowing inflationary prices.
- **Mechanism**: a virtual **import/export** market (sources and sinks independent of the player). If you cannot find a buyer, you sell to the **export** (pays little but always buys). If you cannot find a seller, you buy from the **import** (almost anything, at a high price). Exceptions: unique items reserved by the designer.
- Effect: every item can be bought and sold; nobody is left out (if they have the money); the designer sets the price **floor and ceiling**. As long as there is distance between floor and ceiling, the player market self-balances and is, in the long run, immune to excessive currency injections (little inflation). Temporary fluctuations do not change the structure.
- A player selling a horse: lists it at a price > export and < import. If they sell below the export, the buyer resells to the export for an instant profit (unlikely); if > import, nobody buys.
- **Procedure to build the channel**:
  1. Define a rarity (or power) curve per tier, e.g., rarity = 1.5^tier.
  2. **Export (floor)** = a fraction of that value (e.g., 50%) — or a fraction of the average time value (in currency) of obtaining an item of that rarity; it must not be 0.
  3. **Import (ceiling)** = a multiple of that value (e.g., 200%).
  4. The multipliers (50%, 200%) are tuned in playtest.
  5. New items that follow the same rarity scheme enter the channel automatically.
  6. The channel **widens with tier** (because it is exponential): stable and almost fixed at low tiers, open and volatile at high ones. Raising the base even slightly widens the channel and the potential volatility.
  - Example Fig. 10.10: tiers 1-10, rarity 1.5^tier; export = 50%, import = 200% → tier 1: 0.75 / 3; tier 10: 1.5¹⁰ ≈ 57.7 → export ≈ 29 / import ≈ 115 (derived calculation).
- If there is crafting: ingredient costs and rarities somewhat below and proportional to the cost of the product; derive them from the products' minimum/maximum prices.

### Putting it all together [sec: Putting It All Together]
1. Base weapons (table 10.8) with core-resource costs = lowest tier/least rare = price lower bounds.
2. Calculate the cost/benefit of each successive item with the same weights (e.g., compare +2 Speed on a dagger vs. +1 Damage on a broad sword).
3. Assign each item to a tier according to pace and cost-benefit clustering (ideally on an exponential curve of total benefit).
4. Build the market channel if you want trade between players.
- It is much more work with dozens/hundreds of items; start from the design of parts/attributes → core resources → diverse, balanced intransitive objects → an economic progression curve applied to each object.
- Balancing an economy is among the hardest tasks; it mixes math, analytics and heuristics; there is no substitute for building, playtesting and finding your own balance points.

---------------------------------------------------------------------
## B6. Analytical balance and metrics [sec: Analytical Balance]
---------------------------------------------------------------------

- Analytics is the partner of mathematical modeling. It focuses on the **overall experience**: is it engaging, does it feel balanced, and for how long?
- **Three types of metrics/data**:
  1. **Development process data** (are we on track?; Ch. 12).
  2. **Performance data** (fps, memory; profiling).
  3. **User behavior data** (what players do in aggregate → game health and success). This is the one relevant to balance; it does not build structure, it **records what they do**. It is only useful with many players (almost commercial launch) and regular data, ideally near real time.

### How to collect [sec: Collecting Player Information]
- Mostly useful in games with an online component; F2P requires much more information. Offline and analog: difficult/of little use.
- Calls in the software that record: player ID, where they are in the game, additional information (time in the session). They are sent as short strings to a server.
- **Do not instrument everything**: collect only **KPIs** (key performance indicators); if it is not a KPI, do not collect it (it is data you have to analyze for no benefit).
- **Freshness**: >1 hour behind is usually stale; >1 day can lead to bad decisions (except for retrospective use or comparison with the same day the previous week). Ideal: continuous/near real time; in practice, every few minutes is enough.

### Cohorts [sec: Grouping Players Together]
- Individual data is almost never useful (it can even mislead); it is aggregated into **cohorts** (groups). The typical method: by the day or week they started playing. You follow the cohort over time and **compare cohorts** (e.g., started week of 7/9 vs. 7/16) in progression time, session length, purchase behavior → to see whether the game is getting better or worse.

### Behavior categories [sec: Analyzing Player Behavior]
Full list: (1) Acquisition and first experience, (2) Retention, (3) Conversion, (4) Usage, (5) Community.

**1. Acquisition / FTUE [sec: Acquisition]**
- **FTUE** (first-time user experience): first impression; if it is confusing/frustrating the player leaves.
- Measure: how many start the game, how far they get in the first session; go back to downloads/installs/web clicks.
- **Heuristic**: you lose ~**50% of players for every click/tap** from when they launch until they are playing. 3 clicks (choose nation, character, gender) → 50%×50%×50% = 12.5% remain (≈87% lost). Moral: get the player into the game as quickly as possible.
- **Acquisition funnel**: a drop of ~**10×** per stage: for 1 regular player you need 10 who start the game, 100 who install it, 1,000 who look it up, 10,000 who know about it (do not count on better).
- Once inside: record what they do; Tumbleseed as an example (most did not reach the first checkpoint and ~80% of those who did did not get to the next one).
- Tutorial: measure the player's response in the first minutes; tutorials frustrate or their absence confuses → balance that part with data.

**2. Retention [sec: Retention]**
- Measured in days: D0 (first day), D1, D7, D30; cohorts by start → % who return on D1, D7, D30. Improve with the FTUE and return incentives (bonus for coming back the next day, celebrating the return). A game that does not bring the player back the next day has a very hard time.
- **DAU** (daily active users): the "heartbeat"; watch variations by day of the week (Tuesday is usually the weakest: a dip there is not relevant; a 50% drop on Saturday vs. the previous Saturday is an alarm).
- **MAU** (monthly active users): players in the last 30 days (retrospective).
- **Stickiness = DAU / MAU**: if it rises over time the game is healthy; if it falls, a bad sign, act quickly.
- **Player lifetime**: most play <1 day. Improve FTUE and early balance; conversely, measure how long regulars play (weeks/months) and **why they stop** (e.g., they run out of content, more common in content games than in systemic ones).

**3. Conversion (F2P) [sec: Conversion]**
- 98-99% of F2P players never buy (players ≠ customers). **Conversion** = going from player to customer.
- Measure per cohort: when they make their first purchase, average daily spend, probability of a second purchase. Better FTUE ⇒ they buy sooner and more; someone who buys once is much more likely to buy again.
- **ARPU** (average revenue per user) = revenue / all users. **ARPDAU** (per daily active user). **LTV** (lifetime value) = average revenue per player over their whole lifetime; "the most important metric" for experience balance and commercial success.
- **Iron equation of F2P**: LTV > eCPU + Ops (eCPU = effective cost of acquiring a user; Ops = operating cost per player over their lifetime). Example: a player lasts 1 year, operating costs $1/month, acquiring costs $3 → you need LTV > 3 + 1×12 = $15; if each player pays $10 on average over their lifetime, you go bankrupt.
- Monetization is part of the design: build the experience so the player does not feel they *must* buy but chooses to do so often enough.

**4. Usage [sec: Usage]**
- Quests: are they all completed at a similar rate? One that is repeated a lot may be unbalanced in the player's favor; one almost nobody completes may be too hard or tedious.
- **How they die / lose**: seeing what causes defeat reveals unbalanced parts.
- Economic measures (Habitat): variation in total money supply and daily per-player balance. Anything that affects usage, sources/sinks and accumulation of core resources deserves to be measured.
- Tip on where to start: instrument **every event that triggers a sound/audio feedback**; if it generates too much useless data, filter it.

**5. Community [sec: Community]**
- Time in general chat and with specific people, number of persistent groups (guilds) and their activity → a rough model of social contact (who connects with whom), to detect **influencers and early adopters**. If a group of influencers cuts back its play time, it can be an early signal (they ran out of content).
- Number and type of **complaints** about parts of the game: they reveal bugs and areas perceived as unbalanced, difficult, tedious or not engaging.

---------------------------------------------------------------------
## B7. Chapter summary and closing messages [sec: Summary]
---------------------------------------------------------------------
- Balancing is a **continuous** exercise; it is never perfect or finished. If the game seems basically fair to you and to the players, you are on track. Each player can unbalance the game in new ways → building **resilient** systems reduces the chance of breakage and loss of engagement.

---------------------------------------------------------------------
# PART C — SYNTHESIS FOR PRACTICAL USE (derived from the above)
---------------------------------------------------------------------

## C1. Recommended balancing workflow (combined from the two chapters)
1. Define the type of relationship between parts: cyclical ("transitive" in Sellers: counter cycle, odd number of types, same point budget) or cost-benefit ("intransitive" in Sellers: cost proportional to benefit).
2. Identify the core resource (and subsidiary ones, and special cases). Look for a shadow resource if there are several.
3. Tabulate parts × attributes in a spreadsheet; order attributes by causal chain toward the core resource; assign weights (1.0 to the most direct).
4. Calculate Mod Value (weighted sum) → set in-game cost by hand (cheap at the bottom, premium at the top, crossover at the central piece).
5. Choose a parent curve (exponential for thresholds/tiers; logistic for ceilings/diminishing returns; piecewise/NAP for milestones and variety); adjust the base and check doubling time.
6. Couple the challenge ↔ power ↔ reward ↔ cost curves (approximately the same base).
7. Estimate time/attention per milestone (activities × success × duration) and watch the **range**, not just the average.
8. Economy: balance sources and sinks, avoid arbitrage (consistent prices), set a floor/ceiling (import/export) tied to the rarity curve.
9. Playtest to validate the player's mental model; instrument KPIs and look at cohorts; compare with intuition.
10. Iterate; accept that perfection is never reached.

## C2. Common mistakes and how to detect them
- **Dominant strategy / collapsed space**: an object/weapon/class with better Mod Value and lower cost than others; a faction that wins far more (analytics of win rates by faction/class); a terrain or condition that makes one type invincible (playtest under different conditions).
- **Parts clustered in the middle** (little variety): plot the attributes and look for crowding.
- **Decoupled curves**: challenges ×3 vs. power ×1.25 → unjustifiable; review the base of each curve.
- **Linear/polynomial curve at high scale**: the "+n" no longer feels like anything; hedonic fatigue.
- **Exponential with unimaginable numbers**: it loses meaning; limit levels/tiers or move to stacked logistics/prestige.
- **Multiplying two linear progressions without realizing it**: unexpected quadratic growth.
- **Inflation**: sources > sinks; **stagnation**: overcorrection; **arbitrage**: inconsistent prices (Habitat). Detection: monitor money supply and daily balances.
- **Progression time range too wide** (e.g., 7 to 75 min per level): uneven players.
- **Progress that feels stalled** or the next milestone infinitely far away: engagement evaporates.
- **Transitive system with an even number of types**: unstable ecology (WoW Horde/Alliance).
- **Stacking too many novelties at once** (Tumbleseed): breaks the interactivity budget; detect with the progression funnel.
- **Relying only on intuition or only on vocal players**: use data from the majority, not the noisy minority; unrepresentative samples.
- **Stale data or over-instrumentation**: without clear KPIs, time is wasted.
- **Perceived unfairness with pure randomness**: people miscalculate streaks; use 1−(1−p)^n and consider bad-luck protection.

## C3. Formulas at a glance
- Linear: y = A·x + B
- Polynomial: y = x^n (or a·x^n); quadratic = product of two linear ones
- Exponential: y = A^x or y = B·A^x; levels to double ≈ ln2 / ln A
- Logistic: y = L / (1 + e^(−k(x − x0))); at x0, y = L/2
- Segment slope: (y1 − y0) / (x1 − x0)
- Linked probability: P = p1 × p2 × ...
- Success in n attempts: P = 1 − (1 − p)^n
- Combinations in nd6: number of combos / 6^n
- Mod Value (weapons example): 1.3·Attack + 1.0·Damage + 1.75·Speed (initial weights tried 1.5 / 1 / 2)
- XP per level (example): 1,000 × 1.4^level
- Power per tier (Albion): 1.2^tier; rarity: 3^tier; market channel: rarity×0.5 (export) to rarity×2 (import)
- Funnel: ~50% loss per click; ~10× per acquisition stage
- Stickiness = DAU / MAU
- Iron equation F2P: LTV > eCPU + Ops

## C4. Games cited (one line each)
- Dark Souls / Super Meat Boy: hard without being unbalanced (taste vs. balance).
- Tumbleseed: very steep progression funnel; novelty overload; casual aesthetics / difficulty mismatch.
- Rock-Paper-Scissors / RPSLS: basic transitive balance (each beats half).
- Wu Xing, three-color lizards: natural/cultural examples of transitive cycles.
- Dark Age of Camelot (RvR): three realms with cyclical dominance and alliance against the strongest.
- Horde vs Alliance (WoW): two factions (even) → unstable.
- RuneScape: exponential with base 1.1 for XP.
- Adventure Capitalist: exponential reaching ~10^300 (meaningless numbers).
- A Dark Room: pleasure of "numbers going up" + exploring the unknown.
- WoW early levels: NAP curve with round numbers (400, 500, 500, 700, 700...).
- WoW inventory/bags: self-balancing secondary progression.
- WoW money per monster: ×750 from level 1 to 60; example of massive currency injection.
- Habitat: dolls/crystal balls arbitrage; money-supply monitoring.
- Albion Online: power 1.2^tier vs. rarity 3^tier; market with import/export.
- Loot box / social casino games: linked probabilities and near-miss.
- Let's Make a Deal (Monty Hall): cognitive biases in probability.
