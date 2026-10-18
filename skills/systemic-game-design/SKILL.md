---
name: systemic-game-design
description: 'Systems-based game design, built on Michael Sellers'' "Advanced Game Design: A Systems Approach". Use it to DESIGN game systems (core loop, reinforcing and balancing loops, engines, economies, ecologies, progression, parts with attributes and behaviors, emergence), to ANALYZE or CRITIQUE a design (why something is boring, doesn''t hook players, turns into a checklist or a grind, has a dominant strategy, inflation, snowballing, decisions that don''t matter, too much mental load) and to BALANCE with numbers (XP curves, power and cost, value and price of weapons, items or units, probability and drops, rock-paper-scissors counters, sources and sinks of an economy, retention metrics). Use it ALWAYS when the user talks about game design, mechanics, loops, balance, progression, economy or difficulty, or brings playtester feedback about how fun a game is, even if they don''t say "systems" or name the book. Works for video games and board games.'
---

# Systemic game design (Sellers)

This skill applies the method of *Advanced Game Design: A Systems Approach* (Michael Sellers, 2018) to concrete games. The book's central idea: a game is a **system**, and the experience isn't written by the designer but **emerges** from parts that interact in loops, together with the player. The designer directly controls only the parts and the rules. The experience is reached indirectly, by building the space where it happens (what the book calls second-order design).

Use it to think through **the user's** game with them, not to give a lecture. Theory is worth using only if it changes a design decision.

## The lens: whole, loops, parts

Every game is viewed at three levels. Walk through all three and move between them:

| Level | What it is | Questions |
|---|---|---|
| **Whole** | The experience of the game+player system: fantasy, theme, what the player feels and decides | What experience are we after? What does the player do at each moment and why do they care? |
| **Loops** | The systems: parts connected in reinforcing or balancing cycles (engines, economies, ecologies) | What grows, what slows it down, what gets exchanged? Where are the decisions? |
| **Parts** | Tokens with state (attributes and values), limits and behaviors, specified "at spreadsheet level" | What is the minimum set of attributes and behaviors that sustains the loops? With what numbers? |

**To get unstuck:** if one level isn't moving, switch levels. If the experience won't come together, look at what the parts allow. If the experience is clear but the numbers won't work, look at what the loops demand.

The system that matters is **game + player**. The player builds a **mental model** of the game's internal model, and the fun lives in that loop: the player forms an intention, acts, the game changes and gives feedback, and the player updates their model. If that loop isn't closed, there's no game yet.

## First: pick the mode

Look at what the user is asking for and follow the matching flow. Many requests mix modes; in that case do the analysis first and the design or balance after.

- **Design:** create or redesign systems, loops or parts. See "Flow: design".
- **Analyze or critique:** something doesn't work, is boring or doesn't hook players, or an existing game needs to be understood. See "Flow: analyze".
- **Balance:** numbers are involved: costs, curves, drops, rates, prices. See "Flow: balance".

The files in `references/` hold the detail. Read only the one you need:

| File | When to read it |
|---|---|
| `references/systems-and-loops.md` | Loop structure, engines, economies and ecologies, progression, typical loop failures, system document |
| `references/interactivity-and-fun.md` | "Doesn't hook", "boring", "overwhelming": mental model, the six interactive loops, flow, interactivity budget, emotions |
| `references/parts-and-attributes.md` | Getting down to attributes, ranges and behaviors; feedback; emergence; data-driven spreadsheets |
| `references/balance.md` | Curves, cost-benefit, item value, probability, economy, metrics |
| `references/vision-and-analysis.md` | Full analysis checklist, systemic model (decisions, opposition, goals), vision and concept document |
| `references/prototyping-and-playtesting.md` | How to validate: one-question prototypes, playtests, reading feedback |

The references are long (300 to 700 lines). Don't read them whole: each one starts with an **Index**. Read the index, then only the sections the case needs (Grep for the heading, or read that line range). By mode, what you usually need:

- **Design:** in `systems-and-loops.md`, "The three kinds of gameplay loops", "Combining loops" and "Failure catalog". In `parts-and-attributes.md`, "Determining Attributes", "Specifying Behaviors" and "Creating Looping Systems".
- **Analyze:** in `vision-and-analysis.md`, "METHOD: analyzing games" and "Meaningful decisions, opposition and goals". In `interactivity-and-fun.md`, "Diagnostic checklist".
- **Balance:** in `balance.md`, "Types of curves", "Balancing parts (weapons)", "Balancing progression", "Economic system balance" and "Formulas at a glance".

The diagnostic table and the flows in this file are enough for many cases. Open a reference when you need the detail or an example.

## Minimum vocabulary

Use these terms (with their English name the first time, where it differs) and explain them in one line if the user doesn't know them.

- **Reinforcing loop** ("positive feedback"): more generates more. It gives progression and snowballing. Unchecked, it runs away (*runaway*): whoever is winning wins with less and less effort, and whoever is losing runs out of options.
- **Balancing loop** ("negative feedback"): pushes toward an equilibrium. It gives catch-up and stability. In excess, everything stalls or nothing matters.
- Rule: every reinforcing loop needs a limit somewhere (a cost, a cap, a friction, a rubberband or a delay). Always look for it. If it isn't designed, it shows up anyway, and worse.
- **Parts of a loop:** source (faucet) → stock (capped or uncapped) → converter (turns one resource into another) → decider (splits the flow) → sink (drain). A **currency** is exchanged without being consumed.
- **Three kinds of gameplay loops** (ch. 7):
  - **Engine**: same resource. The *boosting* one forces a choice between using the resource now or investing it to get more flow later (Monopoly, deckbuilders). The *braking* one is friction: stamina, upkeep.
  - **Economy**: reinforcement through exchange or conversion between different resources, with non-linear gain in value (wood → plank → bread, production chains).
  - **Ecology**: balance through exchange. Each part holds another in check and the whole sits in dynamic equilibrium (predator/prey, combat, inventory, three factions).
- **Core loop:** what occupies the player's attention at that moment. There are usually several nested at different time scales ("3 seconds inside 30 inside 3 minutes", Halo).
- **Six interactive loops**, fastest to slowest: action/feedback (under 3 s), short-term cognitive (tactics, puzzle), long-term cognitive (strategy), social, emotional, cultural.
- **Interactivity budget**: the total mental load the player is willing to spend. **Fast things crowd out slow things**: if you have to dodge bullets, you can't plan or feel. Keep slow things separated in time from fast ones.
- **Meaningful decision:** there is uncertainty, the outcome changes the state in a perceptible way, and it opens or closes future options. Two doors that lead to the same place aren't a decision.
- **Sources of opposition:** the rules, active opponents, other players, and the player themselves (their trade-offs).
- **Goals:** instant, short-term, long-term, social and emotional. Explicit ones teach. Implicit ones, which the player sets for themselves, are the ones that give longevity.
- **Elegance:** depth (systems within systems) with few exceptions. Easy to learn, hard to master (Bushnell's Law). Every exception spends mental budget.
- **Content vs systems:** content (levels, quests) gets consumed and forces you to produce more (*content treadmill*). Systems generate new situations. A reskin teaches nothing new.

## Flow: design

1. **Anchor the whole in two or three lines:** the player's fantasy, the experience you're after, what they do moment to moment, and which interactive loops they spend their budget in. If the user didn't say, infer it from what they told you and state it as an assumption. Don't stop to ask what can reasonably be assumed.
2. **Define the core loop and the outer loops.** For each loop say what kind it is (engine, economy or ecology; reinforcing or balancing), which resource circulates and where the player's decision sits. Combine a high-tension loop (action, combat) with a low-tension one (building, managing): that pattern works in many genres.
3. **Draw the loops** in text (see "Diagram format"). Mark sources, stocks, sinks, deciders and converters, with + or − on each arrow, and label each cycle R (reinforcing) or B (balancing).
4. **Check each loop against its failures** (diagnostic table). For each reinforcing loop, what limits it? For each resource, do sources outrun sinks (inflation) or the reverse (stagnation)? Is there a dominant strategy?
5. **Go down to parts:** the key parts, each with its minimum attributes (type, range) and its behaviors. Behaviors have to be **local** (they affect parts at the same level and context), **generic** (not one-off scripts) and **perturb without determining** (each part decides how it responds). That is where emergence comes from. Every part has to affect other parts and be affected by them; if a connection is one-way, find a way to close it.
6. **Point out the expected emergence:** two or three concrete situations that nobody scripted by hand and that should arise from the interaction between systems. It is the proof that the design is systemic and not a feature list.
7. **Unfold the complexity gradually** (unfolding complexity): what the player sees at the start and what gets added as their mental model grows.
8. **Close with validation:** the smallest prototype that answers the highest-risk question, and what to observe in the playtest.

Prune ruthlessly. A system that doesn't support the experience goes, even if people like it or it took a lot of work.

## Flow: analyze

A symptom ("it gets boring from act 2", "everyone uses the same thing") is almost never fixed by touching a number. Look for the **structure** that produces it.

1. **Restate the symptom as observable behavior.** What does the player do or stop doing? At what moment?
2. **Map the loops involved**, even roughly: what is reinforced, what is balanced, where resources come from and where they go.
3. **Diagnose with the failure table** and name the root cause. For example: "economy with a growing source and no proportional sink, i.e. inflation", not "there's too much gold".
4. **Check the player's side** (`interactivity-and-fun.md`): can the mental model be built? Are there meaningful decisions? Is the interactivity budget blown? Habituation (same rewards at the same rate)? Is it inside the flow channel? Are there cycles of tension and relief?
5. **Propose systemic fixes, prioritized by impact and cost.** Prefer changing the structure (adding a sink, an opportunity cost, a cyclical counter, a delay, a limit) over stacking patches. The classic anti-pattern: facing a dominant unit, add another that counters it, which in turn becomes dominant. Fix the cost at the source.
6. **State how to measure whether it worked:** which metric, which playtest observation or which simulation.

If the user asks you to analyze an existing game (their own or someone else's), use the seven-step checklist in `vision-and-analysis.md`: first contact with your own mental model, whole, systems, progress loops, interactivity, parts and synthesis.

## Flow: balance

1. **Pick the core resource:** what the player maximizes or can't afford to lose (health, XP, gold, territory). Cost and benefit are measured against it.
2. **Decide the kind of balance:**
   - **Cyclical** (rock-paper-scissors counters): the same point budget distributed differently, with an **odd** number of types (an even number makes it unstable). Sellers calls this "transitive", the opposite of the rest of the literature; use "cyclical" and clarify if needed.
   - **Cost-benefit** (power ladder): more benefit costs proportionally more, along a curve.
3. **Value the parts** with a weighted sum of attributes (the book's "Mod Value"). Order the attributes by causal chain toward the core resource, give weight 1.0 to the most direct one and scale the rest by how many opportunities they multiply (for example, speed or fire rate "open the door" to damage). Then set the **in-game cost by hand**: slightly below value at the cheap end (to get in), slightly above at the top (aspirational), crossing over at a reference piece in the middle. No part can have more value and less cost than another: that is dominance.
4. **Compute the derived numbers** before giving an opinion: sustained DPS (including reload), value per unit of cost, time to kill, time to level up. Show the math in a table so the user can redo it.
5. **Pick the curve** (formulas are in `balance.md`):
   - Exponential `y = B·A^x` for XP thresholds and tiers. Levels to double = ln 2 / ln A.
   - Logistic `y = L/(1+e^(−k(x−x0)))` for ceilings and diminishing returns.
   - Piecewise or hand-made for milestones and surprises.
   - Linear fizzles out because the same "+n" weighs less each time (hedonic fatigue).
   - Multiplying two linears gives a quadratic: it can happen by accident (enemies per level × gold per enemy).
6. **Couple the curves:** challenge, power, reward and cost have to grow with similar bases. If challenge grows ×3 per level and power ×1.25, the game becomes unplayable. Compute how many actions (enemies, matches, minutes) each level takes and look at the **range**, not just the average.
7. **In an economy**, list every source and every sink with its rate. Growing rewards demand growing sinks. Avoid arbitrage: no buyer may pay more than another seller charges. If there is trading between players, consider a channel with a price floor and ceiling (import/export).
8. **Randomness:** probability of at least one success in n attempts = 1 − (1 − p)^n. Players perceive streaks that are statistically normal as unfair; consider bad-luck protection (probability that rises after each failure).
9. **Validate:** numbers find what is most unbalanced, not perfection. Simulate if there is code or a spreadsheet, playtest and measure (funnels per checkpoint, win rates per option, what kills players).

If the project has code, spreadsheets or a simulator, **measure before proposing numbers**. Reading the real data keeps you from balancing from memory.

## Failure diagnostic table

| Symptom you see | Structural cause | Systemic fix |
|---|---|---|
| Whoever is winning pulls away and the match is decided early | Reinforcement without balance (runaway, snowball) | Rubberband (blue shell, Catan robber, reverse turn order), friction proportional to the leader, delay in the return, three or more factions |
| Once behind, the player never recovers | Death spiral: losing reduces the resources needed to recover | Rescue balancing loop, minimum resource floor, a source independent of performance |
| Everyone uses the same build, weapon or unit | Dominant strategy: one badly costed option or a balance that is too fine | Re-cost at the source, add trade-offs or cyclical counters; never stack counter-units |
| Currency piles up and there's nothing to spend it on | Inflation: more sources than sinks, growing rewards without proportional sinks | Limit sources, stock caps, sinks worth paying for (upgrades, wear, consumables), prestige |
| Nobody spends and everybody hoards | Stagnation: scarce sources or expensive upkeep | Restore the gradient: make trading worthwhile |
| The loop can't get started | Deadlock: the resource the loop produces is needed to start it | Independent starting source |
| The player runs out of ways to act | Brake stronger than the engine | Lower the friction or make it proportional |
| "Feels like a checklist" or grind | Linear loops (arcs) with no decisions or interaction between systems; rewards at a fixed rate | Connect systems so they affect each other, add decisions with trade-offs, make risk and reward depend on context |
| What used to be exciting no longer is | Habituation or hedonic fatigue: same reward at the same rate | Novelty, increasing reward rate (with sinks), aspirational goals, new ways to interact |
| Gets boring after X hours | Content exhausted; insufficient systemic depth | Systems that generate situations, implicit goals, ecologies, unfolding complexity |
| Fights or levels all feel the same | Too few variables that change the decision; the variety is only in numbers (reskin) | Vary the rules and the context that change which decision is best, not just health and damage |
| "I don't understand what to do" or early dropout | Mental model impossible to build: exceptions, poor or late feedback, too many novelties at once | Fewer special rules, feedback within 100-250 ms and visual before textual, introduce novelties one at a time |
| Overwhelming or stressful | Interactivity budget exceeded: reflexes mixed with strategy or emotion | Separate fast from slow in time |
| Decisions don't matter | Illusory decisions or a known optimal path | Real uncertainty, consequences that open or close options |
| A patch fixed something and then it came back worse | Fixes that fail: a slow loop with a delay reverts the fix | Find the hidden loop; distrust quick fixes that can be exploited |
| The system "breaks" at any change | Fragility: non-local deciders, choke points, pinned balance | Local behaviors, dynamic equilibrium instead of fixed values |

`systems-and-loops.md` has the extended table, with examples from games.

## Cross-cutting principles

- **Test by operating, not by reading:** systems are understood by running them. Every proposal ends in a prototype (one question per prototype, fast and ugly) or in a measurement.
- **Spreadsheet-specific:** "fast", "a lot" or "stronger" can't be implemented. Give numbers, ranges or formulas; mark whatever isn't decided as an open issue.
- **Minimum attributes:** every new attribute is a new way to unbalance the game. If the player can't tell two attributes apart, merge them.
- **Every verb has feedback** that is immediate, instantly understandable and consistent. A decorative effect with no state behind it is noise the player builds into their mental model.
- **Players bring problems, not solutions:** read feedback looking for the cause, and distrust the vocal minority against the data from the majority.
- **Early success, distant goal:** a "you did it!" in the first minute and an aspiration that is always a little beyond reach.
- **Theme as a filter:** anything that doesn't derive from the theme or support it gets removed or altered.

## Response format

Adapt it to the request; you don't need to use every section. In general:

- **Design:** assumptions and intended experience → loops (diagram, kind, resource, decision) → risks of each loop and how they are held in check → parts (table of attributes and behaviors) → expected emergence → order of unfolding → what to prototype first.
- **Analysis:** diagnosis in one sentence → map of the loops involved → root causes (named with the vocabulary) → prioritized changes (impact/cost, with the why of each) → how to measure that it worked.
- **Balance:** core resource and method → calculation table (derived values, value per cost) → dominant and useless pieces → corrected table → proposed curves with their formula and a sample table → steps to repeat the method → what to validate in play.

Use tables for numbers and parts. If the user asks for a document, build it as a **system document** (name and description, goals in terms of experience, diagram, player interactions, related systems, open questions), a short one per system and not a giant "bible".

### Diagram format

In plain text, readable in any terminal:

```
[Source: enemies]──gold──▶(Stock: gold)──▶<Decider: spend or save?>
                                  ├─▶{Converter: blacksmith}──▶(Weapon +1)──+──▶ damage ──+──▶ enemies killed ─┐
                                  └─▶[Sink: repairs]                                                          │
  R1: more weapon → more kills → more gold → more weapon                                                      │
  B1: more gold spent on weapon → less gold for repairs → weapon degrades  ◀───────────────────────────────────┘
```

`[ ]` source or sink, `( )` stock, `< >` decider, `{ }` converter, `+`/`−` on the arrows, R/B to name the cycles. If the user uses Mermaid or a whiteboard, you can use that format.

## Watch out for

- **Don't recite the book.** Apply a concept only if it explains something about the user's game.
- **Don't invent data from the book.** If a figure or example isn't in the references, present it as your own.
- **Don't assume there is a single answer.** When there are real trade-offs, show two options with their consequences and recommend one.
- **Respect the design rules the user has already set.** If the project has a design document or constraints, work within them and flag it if one of them is the cause of the problem, without changing it on your own.
