# systemic-game-design

**A Claude skill that designs, diagnoses and balances games the way systems designers do: loops, parts, feedback, and numbers you can check.**

![License: MIT](https://img.shields.io/badge/license-MIT-green)
![Claude Code skill](https://img.shields.io/badge/Claude%20Code-skill-orange)
![Works with claude.ai](https://img.shields.io/badge/claude.ai-compatible-blue)
![Status: pre-release](https://img.shields.io/badge/status-pre--release-yellow)

> Based on the method in *Advanced Game Design: A Systems Approach* by Michael Sellers (Addison-Wesley, 2018). This is an independent, unofficial project. It is **not affiliated with or endorsed by** the author or the publisher. See [Book, attribution and copyright](#book-attribution-and-copyright).

---

## Table of contents

1. [What it is](#what-it-is)
2. [What problem it solves](#what-problem-it-solves)
3. [Quick start](#quick-start)
4. [Install](#install)
5. [How to trigger it (read this)](#how-to-trigger-it-read-this)
6. [The three modes](#the-three-modes)
7. [Example prompts](#example-prompts)
8. [What output to expect](#what-output-to-expect)
9. [How to get the best results](#how-to-get-the-best-results)
10. [When to use it, and when not to](#when-to-use-it-and-when-not-to)
11. [How it works inside](#how-it-works-inside)
12. [Core concepts cheat sheet](#core-concepts-cheat-sheet)
13. [Failure diagnosis table](#failure-diagnosis-table)
14. [The balance toolkit](#the-balance-toolkit)
15. [Worked examples](#worked-examples)
16. [Evaluation results (honest numbers)](#evaluation-results-honest-numbers)
17. [Limitations and known issues](#limitations-and-known-issues)
18. [A note on terminology: "transitive" vs "intransitive"](#a-note-on-terminology-transitive-vs-intransitive)
19. [Language](#language)
20. [FAQ](#faq)
21. [Repository layout](#repository-layout)
22. [Contributing](#contributing)
23. [Roadmap](#roadmap)
24. [Book, attribution and copyright](#book-attribution-and-copyright)
25. [License](#license)

---

## What it is

`systemic-game-design` is an [Agent Skill](https://docs.claude.com) for Claude. It is a folder with a `SKILL.md` file (the method) and six reference files (the detail). When it is active, Claude stops answering game design questions from general intuition and starts working through a fixed, systems-based method:

1. Look at the game on **three levels**: the whole experience, the **loops** that produce it, and the **parts** (attributes, values, behaviors) that make the loops run.
2. Name the **structure** behind a symptom ("the economy has faucets without matching drains") instead of treating the symptom ("there is too much gold").
3. Do the **arithmetic** when numbers are involved, show the table, and explain the method so you can repeat it.
4. Finish with **what to prototype or measure next**, never with a "final" spec.

It covers three kinds of work:

| Mode | You bring | You get |
|---|---|---|
| **Design** | A game idea or a half-built system | Loops (core + outer), parts with attributes and ranges, expected emergent situations, rollout order, first prototypes |
| **Analyze** | A symptom ("players get bored in act 2") or a game to dissect | Root causes named with systems vocabulary, prioritized fixes, how to measure that they worked |
| **Balance** | Stats, costs, XP curves, drop rates, a spreadsheet | Derived values (e.g. sustained DPS), dominated/useless options, corrected prices, curve formulas with sample tables, a repeatable method |

It works for video games (Unity, Godot, anything) and for board and card games.

## What problem it solves

Asking an LLM about game design usually produces a plausible list: "add more variety, add a shop, make elites harder". It is rarely wrong, but it is shallow, and it does not tell you *why* the problem exists or how to check the fix.

This skill pushes the answer toward the kind of reasoning an experienced systems designer does:

- **"Feels like a to-do list"** is diagnosed as a *complicated process* (a line) instead of a *complex system* (loops), and the fix is to close loops, not to add tasks.
- **"Everyone uses the same build"** is diagnosed as a mis-costed option or a missing counter-structure, and the fix is to re-cost at the source, not to stack counter-units that become the next dominant option.
- **"Gold piles up"** is diagnosed as inflation (sources outpacing sinks) and the fix is quantified: how many coins enter per act, what sinks exist, at what price.
- **"The numbers feel off"** becomes a table: sustained DPS including reload, value per coin, dominance check, then a corrected price list.

In short: less brainstorming, more structure and arithmetic.

## Quick start

Claude Code, user-level install (works in every project):

```bash
git clone https://github.com/pauloperrotta/systemic-game-design-skill.git
mkdir -p ~/.claude/skills
cp -r systemic-game-design-skill/skills/systemic-game-design ~/.claude/skills/
```

Then, in Claude Code, ask for it by name:

```text
Use the systemic-game-design skill: my survival game feels like a checklist
(gather, craft, sleep, repeat). Design the loops so things happen that I
did not script.
```

That is the whole setup. Details for other environments are below.

## Install

The skill is the folder [`skills/systemic-game-design`](skills/systemic-game-design). Everything else in the repo is documentation, evaluation data and examples.

### Claude Code (CLI, desktop app, IDE extensions)

**For all your projects** (user-level):

| OS | Destination |
|---|---|
| macOS / Linux | `~/.claude/skills/systemic-game-design/` |
| Windows | `%USERPROFILE%\.claude\skills\systemic-game-design\` |

```bash
cp -r skills/systemic-game-design ~/.claude/skills/
```

**For one project only** (can be committed so the whole team gets it):

```bash
mkdir -p .claude/skills
cp -r skills/systemic-game-design .claude/skills/
```

Restart or start a new session so the skill list is reloaded. You can confirm it loaded by asking Claude "which skills do you have?" or by checking that `systemic-game-design` shows up in the skill list.

### claude.ai (web and desktop apps)

Skills are uploaded as a `.skill` file, which is a zip of the skill folder.

```bash
cd skills
zip -r systemic-game-design.skill systemic-game-design
```

Then upload `systemic-game-design.skill` in your Claude settings (Skills / Capabilities, depending on your plan and organization settings). If your organization disables custom skills you will not see the option.

### Other agents and tools

The skill is plain Markdown with a small YAML header, so you can use it where skills are not supported:

- **Rules / memory file route:** paste the body of `SKILL.md` into your tool's rules file (for example a project instructions file), and keep `references/` next to it so the agent can open the detail files when asked.
- **Manual route:** open `SKILL.md` yourself, copy the flow that matches your task ("Design", "Analyze", "Balance") into the chat, and attach the one reference file you need.

This route is untested. If you try it, please open an issue with what worked.

### Updating and uninstalling

- Update: replace the folder with the new version (`git pull`, then copy again).
- Uninstall: delete the folder.

## How to trigger it (read this)

**The skill does not always activate on its own.** This is the single most important thing to know.

In the project's own measurements (see [Evaluation results](#evaluation-results-honest-numbers)), when a game-design question arrived with no hint, Claude opened the skill only a minority of the time (roughly 1 in 10 to 1 in 5 in the test set). It never activated on unrelated questions, so it is safe to leave installed. But it is better to be explicit. Three reliable ways:

1. **Name it in the request.**

   ```text
   Use the systemic-game-design skill to analyze why my deck-builder gets boring in act 2.
   ```

2. **Add one line to your project instructions** (`CLAUDE.md`, or equivalent), so it applies without you remembering:

   ```markdown
   ## Game design
   For any game design question (loops, progression, economy, balance, difficulty,
   playtest feedback), use the `systemic-game-design` skill before answering.
   ```

3. **Ask for the method's vocabulary.** Mentioning "loops", "sinks and faucets", "dominant strategy" or "core loop" in a request raises the chance the skill is picked, but it is not guaranteed.

If Claude answers without the skill and you want the structured version, reply with: *"Redo that using the systemic-game-design skill."*

## The three modes

The skill has one flow per mode. Claude picks the mode from your request, and many requests mix modes (it then analyzes first, then designs or balances).

### 1. Design

Used when you create or redesign loops, mechanics, progression, crafting, an economy or emergent behavior.

The flow:

1. **Anchor the whole**: player fantasy, intended experience, what the player does moment to moment, and where the attention budget goes. Missing facts become declared assumptions (Claude does not stall to ask).
2. **Define the core loop and the outer loops**, each tagged as engine, economy or ecology, reinforcing or balancing, with the resource that circulates and the player's decision.
3. **Draw the loops** as plain-text diagrams with sources, stocks, converters, deciders and sinks, with `+/-` on the arrows and `R`/`B` labels on the cycles.
4. **Stress each loop against known failures**: what limits each reinforcing loop, whether faucets exceed drains, whether a dominant strategy exists.
5. **Go down to parts**: minimal attributes with types and ranges, and behaviors that are local, generic and "perturb without determining".
6. **Predict emergence**: two or three concrete situations nobody scripted that should arise from the interaction of systems. This is the test that the design is systemic and not a feature list.
7. **Plan the rollout** (complexity unfolds gradually) and **the first prototypes**, one question each.

### 2. Analyze

Used for "this is boring / dominated / inflated / confusing / shallow", for playtest feedback, or to dissect an existing game.

The flow:

1. Restate the symptom as **observable behavior** (what players do or stop doing, and when).
2. **Map the loops** involved, even roughly.
3. **Diagnose with the failure table** and name the root cause with the systems vocabulary.
4. Check the **player side**: can a mental model be built, are decisions meaningful, is the interactivity budget overloaded, is there habituation, is the player inside the flow channel, are there tension/relief cycles.
5. Propose **structural fixes**, prioritized by impact and cost, preferring a change to the structure over stacking patches.
6. State **how to measure** that the fix worked.

For analyzing an existing game (yours or someone else's), the skill carries a seven-step checklist: first-contact mental model, the whole, systems, progression loops, interactivity, parts, synthesis.

### 3. Balance

Used whenever numbers are involved: costs, XP and level curves, damage and prices, drop rates, economy tuning.

The flow:

1. Choose the **core resource** the player maximizes or cannot lose.
2. Choose the **balance type**: cyclical (counters, rock-paper-scissors style) or cost-benefit (a power ladder paid for with cost).
3. **Value the parts** with a weighted sum of attributes ordered by causal chain toward the core resource, then set the in-game **cost by hand** (slightly below value for weak items, slightly above for top items, crossing at a reference item).
4. **Compute derived values** before opining (sustained DPS, value per cost, time to level) and show them in a table.
5. **Pick the curve** (exponential, logistic, piecewise, hand-tuned) and give the formula plus a sample table.
6. **Couple the curves**: challenge, power, reward and cost should grow with similar bases.
7. For economies, list **every faucet and sink** with rates; avoid arbitrage; consider a price floor and ceiling.
8. **Validate**: simulate or playtest, measure funnels and win rates. Numbers find the most unbalanced parts; they do not give perfection.

If your project has a simulator, spreadsheet or code, tell Claude: the skill instructs it to **measure before proposing numbers**.

## Example prompts

Copy and adapt. The more concrete the numbers and symptoms, the better.

**Design**

```text
Use the systemic-game-design skill. I'm making a solo island survival game in
Unity. I have gathering, crafting and a day/night cycle where monsters spawn at
night. It plays like a checklist. Design the loops: core loop, other loops, how
they connect, and the parts (attributes + behaviors) I need so things happen
that I didn't script. Give me a document I can follow.
```

```text
Use the systemic-game-design skill. Board game, 3-5 players, spice trading,
market prices rise when someone buys. In 6 playtests the player who bought the
first big ship in round 2 always won. Diagnose the loop and fix it.
```

**Analyze**

```text
Use the systemic-game-design skill. Slay-the-Spire-like roguelite: 3 acts,
node map, 10-card starter deck, gold, shop, relics. Playtesters say act 2 is
boring: nearly everyone wins with pure-attack decks, gold piles up because the
shop has nothing worth buying, and elites feel like normal fights. What is
happening at the design level? Give prioritized changes.
```

```text
Use the systemic-game-design skill. Analyze why Vampire Survivors hooks people,
from its loops and progression, so I can borrow what works for my bullet heaven
without copying it.
```

**Balance**

```text
Use the systemic-game-design skill. Top-down shooter weapons
(damage/shots per sec/magazine/reload s/price):
Pistol 10/4/12/1.0/0, SMG 6/12/30/1.8/300, Shotgun 8x6 pellets/1.2/6/2.5/450,
Rifle 35/2/10/2.0/600, Minigun 5/20/200/5.0/1200, Rocket 120 AoE/0.5/1/3.0/1500.
XP to go from level n to n+1 is 100*n; an enemy of level n gives 10*n XP and
5*n coins. Is this balanced? Any dominant or useless weapon? Give corrected
prices and a better XP/coin curve, with numbers and a repeatable method.
```

```text
Use the systemic-game-design skill. My idle game is at 1e12 after an hour and
nobody buys old upgrades. Redesign the economy and the prestige multiplier.
```

## What output to expect

The skill adapts to the request, but the default shapes are:

- **Design**: assumptions, intended experience, loop diagrams (with type, resource and decision per loop), the risks of each loop and how they are limited, a table of parts (attributes, ranges, behaviors), expected emergent situations, rollout order, what to prototype first. For "give me a document" requests it uses a short **system document** layout (name, experience goals, diagram, player interactions, related systems, open questions).
- **Analysis**: one-sentence diagnosis, a map of the loops involved, root causes named with the vocabulary, prioritized changes (with the reason for each), and metrics or a playtest to confirm.
- **Balance**: the core resource and method, a calculation table, dominated and useless options, a corrected table, curve proposals with formula and a sample table, the steps to repeat it, and what to validate in play.

Typical traits you will notice:

- Supposition is **declared**, not hidden ("I assume 2.5 targets per rocket").
- Numbers invented by Claude for lack of data are **marked as its own**, not as the book's.
- Diagrams are **plain text**, readable in any terminal. Example:

```text
[Source: enemies]──gold──▶(Stock: gold)──▶<Decider: spend or save?>
                                 ├─▶{Converter: blacksmith}──▶(Weapon +1)──+──▶ damage ──+──▶ kills ─┐
                                 └─▶[Sink: repairs]                                                  │
 R1: better weapon → more kills → more gold → better weapon                                           │
 B1: more gold spent on weapon → less for repairs → weapon degrades  ◀───────────────────────────────┘
```

`[ ]` source or sink, `( )` stock, `< >` decider, `{ }` converter, `+`/`-` on arrows, `R`/`B` to label reinforcing and balancing cycles.

Real outputs from the evaluation are in [`examples/`](examples) (in Spanish, since the test prompts were Spanish).

## How to get the best results

- **Give numbers and symptoms, not adjectives.** "Players win 8 of 10 runs with deck type X" beats "the game is too easy".
- **Say what you already decided.** If some rules are fixed (a frozen lane width, a shield rule), say so. The skill is instructed to work inside your constraints and to tell you if one of them is the cause, without silently changing it.
- **Give your data when you have it:** stats tables, a spreadsheet, a simulator, telemetry. It measures first and proposes numbers second.
- **Ask for one thing at a time.** "Design the loops" and "balance every weapon" in the same message produce thinner answers than two messages.
- **Treat the numbers as a first hypothesis.** The skill states this itself. Playtest, then iterate.
- **Ask it to go deeper on a part.** For example: "now go down to parts for loop L4 and give me ranges", or "give me the validation prototype for P2".
- **Ask it to challenge you.** "Which of my assumptions is most likely wrong?" works well, since assumptions are declared explicitly.
- **Use it before building, and again after playtests.** Its framing (one question per prototype, measure before and after) fits a design-build-test loop.

## When to use it, and when not to

**Good fit**

- Core loops, progression, crafting, economies, difficulty curves, counters, drops.
- "Why is this boring / grindy / dominated / confusing?"
- Turning vague design ideas into parts with attributes and ranges.
- Reviewing playtest feedback for root causes.
- Pricing and leveling math.
- Board and card game balance.

**Poor fit** (use something else)

| Need | Why not |
|---|---|
| Writing gameplay code for an already-closed design | The skill is about design reasoning, not implementation |
| Performance, rendering, shaders, bugs | Out of scope |
| Lore, dialogue, narrative writing | Out of scope (it touches narrative only as a design structure) |
| Marketing, pitch decks, store pages | Out of scope (pitching is summarized only briefly in the references) |
| Economic game theory (Nash equilibria, payoff matrices) | The book itself says game theory is not game design theory |
| Level layout and art direction | Not covered |

## How it works inside

```text
skills/systemic-game-design/
├── SKILL.md                       ← the method: lens, vocabulary, three flows,
│                                    failure table, principles, output formats
└── references/                    ← detail, loaded on demand
    ├── systems-and-loops.md        ← loops, engines/economies/ecologies, progression, failures
    ├── interactivity-and-fun.md  ← mental model, flow, interactivity budget, emotions, "fun"
    ├── parts-and-attributes.md      ← attributes, ranges, behaviors, feedback, spreadsheets
    ├── balance.md                 ← curves, cost-benefit, probability, economy, metrics
    ├── vision-and-analysis.md       ← systemic model of a game, analysis checklist, concept doc
    └── prototyping-and-playtesting.md  ← prototypes, playtests, reading feedback
```

**Progressive disclosure.** Only the short YAML header (name and description) sits in Claude's context all the time. `SKILL.md` (about 180 lines) is read when the skill triggers. The reference files (200 to 700 lines each) are opened only when a case needs the detail. Each reference starts with an index, and `SKILL.md` tells Claude which sections to read per mode, so it does not load whole files.

**Why reference files and not one big file?** A single file with all the book's method would be thousands of lines and would eat context for every question. Splitting by topic lets a pure balance question open only `balance.md`.

**What lives where**

| File | Read it for |
|---|---|
| `SKILL.md` | The three flows, the vocabulary, the failure table, the principles, the output formats |
| `systems-and-loops.md` | Reinforcing and balancing loops, sources/stocks/sinks, the three gameplay loop types (engines, economies, ecologies), core loops, progression, habituation, the extended failure catalog, the system document template |
| `interactivity-and-fun.md` | Player mental model, cognitive load, the six interactive loops by time scale, flow, arousal, the interactivity budget, emotions and motivations, a working definition of fun, a diagnostic checklist |
| `parts-and-attributes.md` | Choosing minimal attributes, attribute orders (amount, rate, rate-of-rate), ranges, local and generic behaviors, feedback rules, closing loops, spreadsheet structure, data-driven design |
| `balance.md` | The four balancing methods, probability, cyclical vs cost-benefit balance, curve types with formulas, valuing items (Mod Value), pacing and time per level, economy balance, analytics (funnels, cohorts, retention) |
| `vision-and-analysis.md` | The systemic model of a game (tokens and rules → mechanics → loops → whole), meaningful decisions, sources of opposition, goal types, the seven-step analysis, the concept document |
| `prototyping-and-playtesting.md` | Finding the fun fast, what a prototype is, one question per prototype, playtest scripts and surveys, reading feedback |

A Spanish version of the whole skill lives in [`i18n/es`](i18n/es) (see [Language](#language)).

## Core concepts cheat sheet

A short version of the vocabulary the skill uses. The skill explains each term in one line when you need it.

**Structure**

- **Parts**: things with state (attributes and values), boundaries and behaviors.
- **Loop**: parts connected in a cycle.
- **Reinforcing loop (R)**: more produces more. It gives progression and snowballing. Without a limit it runs away (the leader wins with less and less effort; the trailing player runs out of options).
- **Balancing loop (B)**: pushes toward equilibrium. It gives catch-up and stability. In excess, nothing matters.
- **Rule of thumb**: every reinforcing loop needs a limit somewhere (a cost, a cap, friction, rubber-banding, a delay). If you did not design it, one appears anyway, and it is worse.
- **Resource pieces**: source (faucet) → stock → converter → decider → sink (drain). A *currency* is exchanged without being consumed.

**Three types of gameplay loops**

- **Engine** (same resource): a *boosting* engine makes you choose between spending a resource now or investing it to get more later (Monopoly, deck builders). A *braking* engine is friction: stamina, upkeep.
- **Economy** (reinforcing, resources exchanged): converting one resource into another with nonlinear gain (wood → lumber → bread; production chains).
- **Ecology** (balancing, resources exchanged): each part brakes another and the whole sits in dynamic equilibrium (predator/prey, combat, inventory, three factions).

**The player side**

- **Core loop**: what holds the player's attention at that moment. There are usually several, nested at different time scales ("3 seconds inside 30 seconds inside 3 minutes").
- **Six interactive loops** from fastest to slowest: action/feedback (under about 3 s), short-term cognitive (tactics, puzzles), long-term cognitive (strategy), social, emotional, cultural.
- **Interactivity budget**: how much mental load the player will spend. **The fast drives out the slow**: if you must dodge bullets you cannot plan or feel. Slow things go apart in time from fast things.
- **Meaningful decision**: there is uncertainty, the result visibly changes state, and it opens or closes future options. Two doors to the same room are not a decision.
- **Goals**: instant, short-term, long-term, social, emotional. Explicit goals teach; implicit ones (the ones players set for themselves) give longevity.
- **Elegance**: depth (systems inside systems) with few exceptions. Easy to learn, hard to master (Bushnell's Law). Every exception spends mental budget.
- **Content vs systems**: content (levels, quests) is consumed and must be produced again (the content treadmill). Systems generate new situations. A reskin teaches nothing new.

## Failure diagnosis table

The compact table the skill uses (the references hold the extended version with game examples).

| What you see | Structural cause | Systemic fix |
|---|---|---|
| The leader pulls away and the game is decided early | Reinforcing loop without balance (runaway, snowball) | Rubber-banding, friction proportional to the leader, a delay in the return, three or more factions |
| After losing you cannot recover | Death spiral: losing reduces the resources needed to recover | Rescue balancing loop, a resource floor, a source independent of performance |
| Everyone uses the same build, weapon or unit | Dominant strategy: a mis-costed option or a too-fine balance | Re-cost at the source; add trade-offs or cyclical counters; never stack counter-units |
| Currency is abundant with nothing to spend on | Inflation: more faucets than drains; rising rewards without proportional sinks | Limit sources, stock caps, sinks that matter (upgrades, wear, consumables), prestige |
| Nobody spends and everybody hoards | Stagnation: scarce sources or heavy upkeep | Restore the gradient: make exchanging worthwhile |
| The loop cannot start | Deadlock: what the loop yields is needed to enter it | An independent starting source |
| The player runs out of ability to act | Brake stronger than the engine | Lower friction or make it proportional |
| "A checklist" or grind | Linear loops (arcs) without decisions or system-to-system interaction; fixed-rate rewards | Connect systems so they affect each other; trade-offs; risk and reward that depend on context |
| What used to thrill no longer does | Habituation: same reward at the same rate | Novelty, rising reward rate (with sinks), aspirational goals, new ways to interact |
| Boring after X hours | Content exhausted; too little systemic depth | Systems that generate situations, implicit goals, ecologies, unfolding complexity |
| Fights or levels all feel the same | Variety is only in numbers (a reskin) | Vary the rules and context that change which decision is best, not just HP and damage |
| "I don't understand what to do" or early churn | Mental model cannot be built: exceptions, poor or late feedback, too many novelties at once | Fewer special rules, feedback within 100 to 250 ms and visual before textual, one novelty at a time |
| Overwhelming or stressful | Interactivity budget exceeded | Separate fast from slow in time |
| Decisions do not matter | Illusory decisions or a known optimal path | Real uncertainty, consequences that open or close options |
| A patch fixed it and then it came back worse | Fixes that fail: a slow loop reverses the fix | Find the hidden loop; distrust quick fixes that can be exploited |
| The system breaks at any change | Brittleness: non-local deciders, choke points, pinned balance | Local behaviors, dynamic equilibrium instead of fixed values |

## The balance toolkit

Formulas the balance reference carries (with notes on when to use each):

| Tool | Formula | Use |
|---|---|---|
| Linear curve | `y = A·x + B` | Short segments; weak alone because the same "+n" matters less and less |
| Polynomial | `y = x^n` (with multipliers) | Moderate accelerating growth. Multiplying two linear progressions gives a quadratic, often by accident |
| Exponential | `y = B·A^x` | XP thresholds, tiers, rarity. Levels to double ≈ `ln 2 / ln A` |
| Logistic | `y = L / (1 + e^(−k(x−x0)))` | Caps and diminishing returns; stacked logistics for several resources |
| Piecewise linear | slope = `(y1−y0)/(x1−x0)` | Hand-made curves with milestones |
| Near-arithmetic progression | hand-tuned, round numbers | Surprise and variety in early levels |
| P(at least one success in n tries) | `1 − (1 − p)^n` | Drop rates and "feels rigged" complaints |
| Tries needed for target chance q | `n = ln(1 − q) / ln(1 − p)` | Pity timers and reward pacing |
| Item value (weighted) | `ModValue = Σ weight·attribute` | Compare parts; set cost by hand around it |
| Time per milestone | `(points per level / points per action) / success rate × time per action` | Check the range, not just the mean |
| F2P iron equation | `LTV > eCPU + Ops` | Whether a free-to-play model can pay for itself |
| Stickiness | `DAU / MAU` | Is the game healthy over time |

Rules of thumb it applies:

- Desired value of an attribute that drives a cost must be **ordered by causal chain** toward the core resource (for a weapon: fire rate, then hit, then damage).
- **Cost is decoupled from value on purpose**: slightly cheaper than value for weak items, slightly dearer for top items, crossing at a mid reference item.
- **Couple curves**: if challenge grows ×3 per level and power ×1.25, the game becomes unplayable fast.
- **Look at the range**, not the average (a level that takes 7 minutes for some players and 75 for others feels unfair).
- **Recompute after any stat change**; keep every attribute as an input to a table, not a mental guess.

## Worked examples

Three real runs are in [`examples/`](examples), kept in Spanish as produced. Summaries:

1. **[Survival game loops](examples/01-design-survival-loops.es.md)**: diagnoses the "checklist" feeling as a complicated process (a line) and proposes an expedition core loop with a day/night regulator, a creature ecology that reads shared signals (light, noise, smell), a table per part (player, resource node, item, creature, structure, zone, time), six emergent situations to verify in playtest, a rollout order and four one-question prototypes.
2. **[Roguelite deck-builder, act 2 boredom](examples/02-analyze-roguelite.es.md)**: links three symptoms (a dominant pure-attack deck, a gold glut, identical elites) to three structural causes (an unbraked reinforcing loop, an unblocked faucet with a clogged sink, variety only in numbers), then lists five prioritized changes with a metric each and a one-change-per-playtest rule.
3. **[Weapon balance and XP curve](examples/03-balance-weapons.es.md)**: computes sustained DPS (Pistol 30.0, SMG 41.9, Shotgun 38.4, Rifle 50.0, Minigun 66.7, Rocket 24.0 against one target), finds the Shotgun dominated by the cheaper SMG, shows the 10-kills-per-level flatness of the original curve, and proposes corrected prices, exponential XP/coin curves with a sample table, and gold sinks.

## Evaluation results (honest numbers)

Three realistic prompts (design, analysis, balance) were each run with the skill and without it (same model, same prompt, no hints), then graded against 7 to 8 assertions per prompt. Prompts and assertions are in [`evals/evals.json`](evals/evals.json); the summary is in [`docs/EVALUATION.md`](docs/EVALUATION.md).

| Metric | With skill | Without skill |
|---|---|---|
| Assertions passed | 23 / 23 | 21 / 23 |
| Average tokens per run | about 144k | about 80k |
| Average time per run | about 111 s | about 72 s |

What this means, without spin:

- **The assertions barely discriminate.** A strong base model already passes almost everything. The two misses without the skill (both in the design case) were loop diagrams without sources/sinks or reinforcing/balancing labels, and part attributes without ranges. Per-prompt, unaided: 6/8, 7/7, 8/8.
- **The real difference is qualitative** and has to be judged by reading the paired outputs in [`examples/`](examples): a loop map with types and limits, named failure modes, quantified sinks, a metric per change, one-change-per-playtest discipline, a repeatable valuation method.
- **It costs about 1.8x the tokens** of an unaided answer, mostly from reading references.
- **Triggering is weak** when you do not ask for the skill (see [How to trigger it](#how-to-trigger-it-read-this)). A rewritten description was tested once and did not improve it; the original was kept.
- This is a **small, early evaluation** (3 prompts, one run each). Treat it as a smoke test, not a benchmark. Contributions of harder prompts are welcome.

## Limitations and known issues

- **Triggering**: see above. Ask for it by name or add the project-instructions line.
- **Length**: reference files are long. The skill tells Claude to read by index and section, but in tests some runs still read only part of a file. If an answer looks thin, ask Claude to open a specific section.
- **Language**: the English skill is a translation of the version that was evaluated (Spanish). It has not been evaluated separately, and the evaluation prompts were in Spanish.
- **No code execution built in**: for numeric work it relies on Claude doing arithmetic, or running scripts if its environment allows it. Ask it to compute in a script when the numbers matter.
- **Numbers it invents are assumptions**: weights, exponents and thresholds that the book does not give are marked as the model's own. Do not treat them as canon.
- **The book's method is not the only method.** It is one coherent, systems-based school of design. It is strong on loops, economies and balance; lighter on narrative design, level design, UX and monetization.
- **Evaluation is small** (see above).

## A note on terminology: "transitive" vs "intransitive"

The book uses *transitive* for rock-paper-scissors style cycles and *intransitive* for cost-benefit ladders. Most other design literature uses the terms the other way around. To avoid confusion the skill talks about **cyclical balance** (counters) and **cost-benefit balance** (power ladders), and says so if you use either term. Rules it carries for cyclical balance: use an **odd** number of types (an even number is unstable), give each type the same budget of points but distribute them differently, and playtest under different external conditions so no single terrain or setup makes one type invincible.

## Language

- This README and the skill (`skills/systemic-game-design`) are in **English**.
- The skill was originally written and tested in **Spanish**. That version is kept, complete, in [`i18n/es/systemic-game-design`](i18n/es/systemic-game-design). To use it, copy that folder instead of the English one. Do not install both: they share the same skill name.
- Claude answers in the language you write in, with either version.
- The English version is a faithful translation of the Spanish one (same structure and line counts). It has not yet been run through its own evaluation; the evaluation results below were measured on the Spanish version with Spanish prompts.
- The files in [`examples/`](examples) are real outputs in Spanish.

## FAQ

**Do I need the book?**
No. The skill works on its own. The book is worth reading if you want the full reasoning, the figures and the many game examples; the skill carries paraphrased, condensed method notes, not the book.

**Does it replace a designer, a spreadsheet or playtesting?**
No. It structures your thinking and does the arithmetic. It will end almost every answer with what to prototype or measure, because numbers on paper find the most unbalanced parts, not perfect ones.

**Will it slow me down on simple questions?**
It adds reading time and tokens (about 1.8x in the evaluation). For a quick one-line question, skip it. It pays off on loop design, diagnosis and balance.

**Why does it declare assumptions instead of asking me questions?**
So you get a usable answer in one turn. If an assumption is wrong, correct it and the relevant section is redone.

**Can it work on a game that already exists (mine or a published one)?**
Yes: "Analyze" mode has a seven-step method for dissecting an existing game, and works from what you describe or from files and data you provide.

**Does it work for board and card games?**
Yes. The book itself uses many tabletop examples, and the analysis is the same: tokens, rules, loops, decisions.

**Does it phone home or need an API key?**
No. It is a folder of Markdown files. It runs wherever your Claude client runs skills.

**Why not just ask Claude for game design advice?**
You can, and for simple questions it is fine. In the evaluation an unaided Claude did well on most points. The skill's value is consistency of method and the extra rigor: loop diagrams with types and limits, named failure modes, quantified sinks, a repeatable valuation method and a validation step.

**Can I edit it for my studio?**
Yes (MIT). Common edits: add your house rules and constraints to `SKILL.md`, add a reference file with your genre's conventions, or change the output formats.

## Repository layout

```text
.
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── skills/
│   └── systemic-game-design/       ← the skill, English (copy this folder)
│       ├── SKILL.md
│       └── references/             ← six topic references
├── i18n/
│   └── es/systemic-game-design/    ← the same skill in Spanish (original)
├── examples/                       ← real outputs (Spanish)
├── evals/
│   └── evals.json                  ← the three evaluation prompts and their assertions
└── docs/
    └── EVALUATION.md               ← how the evaluation was run and what it showed
```

## Contributing

Issues and pull requests are welcome, especially:

- **Harder evaluation prompts** with objective assertions, and results from other models.
- **Triggering reports**: phrasings that did or did not activate the skill, and in which client.
- **Corrections** where a reference misstates a method or a number.
- **Translations** into other languages (the Spanish original is in `i18n/es`; keep file and section names aligned with the English version).
- **Genre notes** (for example racing, fighting, puzzle) as new reference files, kept short and linked from `SKILL.md`.

Please read [CONTRIBUTING.md](CONTRIBUTING.md) first. Do not paste text from the book into issues or pull requests (see below).

## Roadmap

- Evaluate the English version with English prompts.
- Better activation: measure alternatives to the current description, and test a short companion instruction snippet.
- Larger evaluation set across genres, with several runs per prompt.
- Optional worked scripts for the balance toolkit (DPS tables, XP curves, drop probabilities).
- A shorter "lite" skill variant for quick questions.

## Book, attribution and copyright

This project is inspired by and based on the method described in:

> Michael Sellers, *Advanced Game Design: A Systems Approach*, Addison-Wesley, 2018. ISBN 978-0-13-466760-7.

- This repository is **independent and unofficial**. It is not affiliated with, authorized or endorsed by the author or the publisher.
- The skill and its references are **paraphrased, condensed working notes** written in new words and reorganized for use by an AI model, plus original material (flows, tables, output formats, evaluation). They are not a copy or a translation of the book, and they cannot replace it.
- Short mentions of terms, formulas and game examples are used to identify the book's ideas. If you are the rights holder and want something changed or removed, please open an issue.
- **If you want the actual method, with its full reasoning and figures, buy and read the book.**
- Contributors must not paste passages from the book. Paraphrase.

## License

[MIT](LICENSE) for the original material in this repository (the skill structure, flows, tables, evaluation and documentation). The ideas and terminology from the book belong to their author; see the section above.
