# Interactivity, engagement and fun (ch. 4)

Read this when the problem is that the game doesn't hook players, bores them, overwhelms them or "doesn't feel right": the player's mental model, cognitive load and articulatory/semantic distance, the six interactive loops and their time scales, flow, arousal, the interactivity budget ('the fast drives out the slow'), emotions and motivations, and the working definition of fun. It ends with a diagnostic checklist.

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). The book section each block comes from is given in brackets.

## Index
- 1. The player as part of the system (sec. "The Player's Part of the Game as a System")
- 2. A systemic approach to interactivity (sec. "A Systemic Approach to Interactivity")
- 3. Mental models, arousal and engagement (sec. "Mental Models, Arousal, and Engagement")
- 4. Interactive loops: six types (sec. "Interactive Loops")
- 5. Flow (sec. "Flow in Interactive Loops")
- 6. Time-scale view: stacked loops (sec. "A Time-Scale View of Interactive Loops")
- 7. Mental load and the interactivity budget (sec. "Mental Load and the Interactivity Budget")
- 8. Recognizing, defining and creating "fun" (sec. "Recognizing, Defining, and Creating 'Fun'")
- 9. Diagnostic checklist and design questions (synthesis of the chapter's heuristics)

---

---
## 1. The player as part of the system (sec. "The Player's Part of the Game as a System")

- **Game+player system**: the play experience exists only when game and player come together; each is a subsystem with parts (structure), loops (function) and a whole (theme).
- **Mental model**: a reflection the player builds of the game's **internal model** (the one the designer defines). The whole chapter is about how that model gets built and what keeps it alive.
- The mutual loop (the player acts, the game changes and returns feedback, the player updates their model) is the core of interactivity, gameplay, engagement and fun.

## 2. A systemic approach to interactivity (sec. "A Systemic Approach to Interactivity")

### Definition
- Interactive = two or more agents that affect each other mutually/reciprocally (Webster). Rafaeli: a series of exchanges in which each message relates to the previous ones. **Crawford (1984)**: a cycle in which each agent alternately *listens, thinks and speaks* (a "conversation").
- Academic debate: some place interactivity solely in the individual, solely in the medium, or solely in human-to-human exchange. Sellers: it is a property of the **system** formed by the agents.

### Parts (structure)
- At least one human in the loop. A game that "plays itself" is useful for testing, but loses the meaningful experience.
- Each part has **state, boundaries and behaviors**. Behaviors **affect but do not fully determine** the other's state.
- **The player's internal state** = their mental model. It includes their understanding of:
  1. Current game variables (health, wealth, population, inventory...).
  2. The game state, above all how their understanding changed based on the feedback from their last action.
  3. Immediate, short-term and long-term goals, including predictions of what will happen based on their actions.
  4. The effects of past decisions and what they learned from them.
- **The game's internal state** = the design in operation (variables, rules, event loop, when it accepts input).

### Behaviors
- Actions are the ones the designer enables; the game can disable them (e.g. cooldown). Extraordinary abilities and limits are part of the **magic circle**.
- Player behavior: starts as a mental goal and must become physical (moving a piece, click, tap, swipe, even gaze). That transition is the boundary between mental model and conduct.

### Cognitive load and the two "distances" (Norman & Draper 1986; Sweller 1988)
- **Cognitive load**: the mental resources consumed by thinking/attending. Less load for *how* to play = more resources for *what* to do = more engagement and fun.
- **Articulatory distance**: how direct the physical action is. Pointing with a finger < mouse cursor < typing (x,y) coordinates. Less distance = less load.
- **Semantic distance**: how easy it is to interpret the result/feedback. It shrinks with abundant, timely, easy-to-interpret feedback.
  - The author's examples: sword icon < letter "w" < the word "sword"; animation of a building going up < progress bar < text "563/989 bricks".
- Rule: fewer special cases in the rules = less to remember = smaller semantic distance. **Go** as the extreme case (almost zero distance, all cognition goes into the game space). Ties in with *elegance* (ch. 2).
- Design heuristic: every time you add an exception, a mode or a cryptic icon, you are spending the player's cognitive budget.

### Game behaviors and feedback
- The game gives feedback (graphics, text, animation, sound) so the player can update their model.
- Feedback must be **perceptible** (a color that can't be seen or a sound that can't be heard = no feedback), but it **doesn't have to be complete**: hidden state is a key ingredient. **Koster**: the "black box" part the player infers. **Ellenor**: internal systems as "a machine that does X" that the player knows only through its behavior.
- **Everything the player knows about the game comes from its behavior and feedback.** Beware of assuming prior knowledge (mouse, touching a screen, dice): if the game doesn't teach it and it's needed, the player can't play.
- The zones of the mental model that feel solid to the player help them predict the uncertain zones; much of gameplay lives there (trying actions with a predicted result and adjusting the model).

### Intentional choice
The player must be able to understand which actions: (a) are valid in the current context, (b) have the information needed to decide, (c) bring them closer to their goal according to the result they predict, (d) can be decided on and executed in a reasonable time. If any of these fails, the action is random, not a choice.

### Interactive loop (Figs. 4.2, 4.3)
- Player gives **input** → the game processes it and returns **feedback** → the player's internal state changes. This is the origin of the **core loop** (refined further below and in ch. 7). Both also have their own internal loops.
- **Designer's loop** (fourth loop): the designer is outside the system; they give input (ideas/prototypes) and receive feedback (what works). This is the iterative design process.
- Four loops in total are mentioned: the player's internal mental loop, the game's internal loop, the player-game interactive loop, and the designer's loop.

### The whole
- The meaning of the game (theme, moral, what remains afterward) is **emergent** from the interactive system; it lives neither in the player alone nor in the game alone (Newhagen 2004). These higher-level symbols form the mental model.

---
## 3. Mental models, arousal and engagement (sec. "Mental Models, Arousal, and Engagement")

### Building the mental model
- The player tests their understanding through actions. Positive feedback ("I did something right") = a sense of accomplishment, and the concept is added to the model; negative feedback = review and correct.
- Mental model = attention + plans + goals + emotions. It includes systems (combat, economy, ecology) and the **navigation** of geographic or logical spaces.
  - Examples: knowing how to get from Ashenvale to Stormwind in *WoW* (world model); understanding the skill tree of *The Witcher 3* (e.g. why pick Muscle Memory over Lightning Reflexes).
- If the player can't build a model consistent with the designer's, or the interactions are tedious/boring/overwhelming, they **stop playing**. Psychological term: **behavior extinction**; in games, *burnout*.
- **Bushnell's Law**: easy to learn, hard to master. In mental-model terms: it is easy to build and validate the model (no ambiguities or exceptions that trip up newcomers), with clear, familiar basic information that invites exploration.
- Good game = a wide mental space to explore: it can be replayed without feeling it was mastered quickly. **Once the player has seen all the content and explored every interaction, there is nothing left to learn and the game stops hooking them.** Go as the archetype.

### Detailed interactive loop (Fig. 4.4)
Sequence: the player **forms intentions and goals** → **performs actions** in the game → the game **processes input and changes state** (it also changes on its own by design) → the game **gives feedback with extra information, new abilities and a call to action** → the player **adjusts their mental model**. Repeat.
- **Call to action / hook**: what drives the player to start or keep going (from the splash screen). Similar to, but not the same as, *affordance* (Norman 1988: a perceptible clue about how something operates; "plates are for pushing..."). A call to action needs *affordance* (it's obvious how to act) **plus motivation** (wanting to act). The author's metaphor: not just a cup with a handle, but an attractive cup with hot cocoa.
- The game must sustain the loop with **new information/abilities and new opportunities** so the model keeps growing.

### Arousal and attention
- To play, the player has to be interested and **aroused** (alert, ready to take part). Bored or overwhelmed/anxious = they don't invest energy.
- Warning signs:
  - **Boredom**: they see no usable controls or don't understand what is displayed.
  - **Overwhelm**: so much is happening on screen (especially visually) that they don't know what to do or where to start.
- Nobody is obliged to play: it is the designer's responsibility that the game looks interesting enough to attract and retain.

### Yerkes-Dodson Law (1908)
- Inverted-U curve: the more arousal, the better the performance up to a point; after that come anxiety, loss of focus, panic and a drop in performance. Zones of the graph: sleep → boredom (low) → mild alertness (optimal) → stress → anxiety → panic.
- Variations: on **simple tasks** performance drops less at high arousal; on **complex tasks** the optimum is reached sooner. **Expert effect**: the more skill/practice, the more arousal is tolerated without losing performance (pilot, surgeon, driver).
- The optimal zone / slightly past the peak: that's where learning and skill improvement happen ("surfing the edge"). Sliding down the right-hand side = too much input/cognitive load.
- **Psychological engagement** = being in the middle zone: alert, attentive to the task, able to ignore what's irrelevant, performing well and aware of it.

### Engagement (definition)
- An internal state of the individual toward the world (Gambetti & Graffigna 2010). **Schaufeli et al. (2002)**: a combination of **vigor** (energy, resilience, effort, persistence in the face of difficulty), **dedication** (meaning, enthusiasm, inspiration, pride, challenge) and **absorption** (total concentration, time flies, hard to disengage).
- These are the qualities of players that describe a satisfying experience. The player arrives at a model that matches the game's, forms hypotheses, acts and receives satisfying feedback; the cycle continues.
- **Fun (sketch)**: an activity that is engaging, pleasurable, voluntary, separate and without consequences (magic circle) → "having fun".
- "Player engagement" is used as a business metric without being defined; this definition anchors it.

### Neurochemical engagement (careful: don't reduce fun to chemistry)
| Neurochemical | What it signals | Design implication |
|---|---|---|
| **Dopamine** | "Reward": alertness, motivation; novelty (not too strange), exploration, goal achieved. Seeing points go up = dopamine. If the expected reward doesn't arrive, dopamine drops and the behavior is valued less. | **Habituation**: we value the new more than the expected; the familiar loses appeal until it becomes boring. A large part of design is providing new rewards/new ways of engaging. |
| **Serotonin** | Counterweight to dopamine: safety, accomplishment, social status, completing achievements, gaining skill ("harm avoidance"). Dopamine pushes toward seeking the new/impulsivity; serotonin toward sticking with the familiar. | Leveling up is satisfying partly through serotonin. Audiovisual celebration effects ("Ding!" in MMOs) condition the association; don't underestimate them. |
| **Oxytocin / vasopressin** | Social bonds, support, belonging to a partner/family/team/community. | Basis of social participation in games. |
| **Norepinephrine / endorphins** | "Stress": short-term vigilance, fast reaction, fast learning (NE); masking pain, a sense of extra energy (endorphins). Less relevant in sedentary games but they help focus attention under stress. | Useful in action/tension games. |

- **Five sensations of engagement** (not all at once): alert/seeking novelty or awaiting reward; secure in the reward or in one's place in the social hierarchy; connected to others through social ties; vigilant under stress; "pushing on" successfully despite the effort.
- **Pacing**: a hard level or climax is followed by a calm moment to lower vigilance, rest and consolidate achievements and social connection. Manipulating these sensations is part of sustaining engagement.
- Consequential context (work) → "accomplishing"; separate, voluntary context without consequences (magic circle) → "fun".
- The types of engagement that follow run from reflexive to executive to reflexive-reflexive, with more individual control and longer time scales. They correspond to the types of **player goals** from ch. 3: each loop offers an opportunity to form an intention, from an instant reflex to a distant goal. Motivations are covered in ch. 6.

---
## 4. Interactive loops: six types (sec. "Interactive Loops")

They are all the same loop (intention → action → state change → feedback). They differ in the **mental resources required, time scale and resulting experience**. **They happen at the same time, nested** (many fast loops inside one long cognitive loop).

Order from fastest/least cognitive to slowest/most reflective (Fig. 4.6):
1. Action/feedback
2. Short-term cognitive
3. Long-term cognitive
4. Social
5. Emotional
6. Cultural

### 4.1 Action/Feedback (A/F)
- Scale: < 1 s up to 2-3 s. Physical player action, sensory feedback from the game, almost no thinking.
- **Latency**: it is perceived as instantaneous with **< 100 ms** between action and feedback; to keep the feeling of an immediate connection, **~250 ms at most** (Card et al. 1983). Beyond that, the player doesn't associate the feedback with the action unless it is symbolic of a longer cognitive model, and even then it feels slow.
- **Present tense**: a test for which loop dominates. If the player describes what they do in present-tense verbs (walking, running, shooting, jumping), their attention is on A/F. If they describe it in future goals ("I'm completing this quest", "I'm building an army to help my friend"), A/F exists but inside a larger cognitive/emotional/social loop.
- **Reflexive (exogenous) attention**: attention guided by external events (Mayer 2004). The brain is on alert for new stimuli: threats, bright, colorful, fast-appearing objects, especially peripheral ones (Yantis & Jonides 1990). *Whack-a-Mole* and advanced FPSs use it as the main gameplay; players report excitement and positive tension (Yee 2016b).
- **Juiciness**: fast, colorful, animated, noisy feedback (Gabler 2005, Juul & Begy 2016). As long as the loop stays "juicy", the player remains alert, focused and learns to react quickly.
- **Game feel** (Swink 2009): the tactile/kinesthetic sensation of manipulating a virtual object; a sense of control. Pleasurable in itself.
- **Fitts' Law** (Fitts & Peterson 1964): the time to reach a target varies inversely with its size (and is slower if its position isn't known beforehand). Large targets = easy; small ones = more motor stress. Hitting releases dopamine and norepinephrine ("one more"). It also contributes some of Caillois's *ilinx* (the pleasure of moving fast, precisely and well, even if only with your fingers).
- **Deterministic arcade games** (e.g. *Pac-Man*, ghosts always the same): the player learns a fixed pattern; with practice it is executed through **procedural memory/"muscle memory"** without meaningful cognition, until the speed exceeds their ability to respond.
- **Endless runners** (*Temple Run*): the A/F loop gets shorter and the game speeds up; it's fun until it becomes unplayable. That unplayability generates the **"just one more try"** (the outer loop's meta-game): brain primed for the next achievement, I want to get a bit further. The mental model improves at the perceptual-motor level through repetition.
- Even games with cognition on top use A/F: precisely timed actions (moving, tapping, jumping, shooting) or juicy feedback. **Peggle** is an example of outsized perceptual reward: zoom camera and slow motion on the key shot, drum roll, fireworks, "EXTREME FEVER" text, a chorus of *Ode to Joy*, rainbows and an enormous score = perceptual and neurochemical positive reinforcement.
- **Moment-to-moment gameplay**: the designer's key question: **"what is the player doing at each moment they play?"** and what feedback they get, how it serves their model and what actions they can take. Games without feedback and regular opportunities for action bore the player unless they have another loop to sustain them. The A/F loop is a **"carrier wave"** for the other types.

### 4.2 Cognitive (short-term and long-term)
- Short term = **puzzles / tactics**; long term = **goals / strategy**. Both require **endogenous/executive attention** (thinking in order to plan). "Short" and "long" are relative (an easy Sudoku lasts seconds; strategy, minutes to hours).
- Key: rationality and **conscious learning**; growth in skill and knowledge (**mastery**). A strong motivator for achievement/progress-oriented players (learning a skill releases dopamine). E.g. crosswords, Sudoku.
- **How to create cognitive interaction**: give plannable, achievable goals, simple at first (kill this monster, build this building, go to this point) and let them grow with the model in **steps (complicated)** and in **loops/building on results (complex)**. It requires the player to be able to predict results in the short and long term.
- **The game needs depth in its internal model** to sustain depth in the mental one. Without systemic hierarchy there are no deep goals to form.
  - *Content-driven* (level after level): only short-term thinking; some compensate with long-term customization (skill trees), but once the options run out nothing is left.
  - *Systemic* (e.g. where to build the castle for its defensive value and future market): solutions as varied as the systems allow, a wide play space, better and longer retention.
- **Blending**: pure cognition almost doesn't exist. Chess and Go are the purest, but pieces are still handled and people talk about a "beautiful game". **Chunking**: with expertise, low-level tactics get grouped into hierarchies, become tacit (almost as little load as picking up a stone) and free up resources for strategy; the model becomes deeper and more hierarchical.
- Common combinations: rich sensory + short puzzle (*Candy Crush*); strategy with "juicy" visuals that aren't operational but improve the experience.
- Example of stacking in an RPG: click (A/F) to attack → kill monster (short term) → level up (long term) → join a guild (social).

### 4.3 Social
- It involves planning and executive attention plus a reflexive-emotional component (inclusion, exclusion, status, esteem). Neurochemical basis: serotonin and oxytocin. **It takes longer**: a conversation is brief, but resolving a social loop takes hours, days or weeks; feeling part of a community takes a long time.
- It can exist in single-player: *Firewatch* (walkie-talkie dialogue with Delilah; the relationship depends on social choices).
- **Game-mediated social interaction**: in multiplayer the game (its internal model) mediates between players; each has their own loop with the game and the effects propagate to others. Only text/voice chat is direct social contact. The author's observation (he ran MMOs): many players stayed for the community even after exhausting the content (a *content-driven* game sustained by the social side).
- **Techniques for fostering social interaction** (when players need or benefit from each other):
  1. **Social referents** (external social referents): objects that several players can interact with (the ball). A lesson from the 3D graphical chats of the 90s, which lost their hook with chatting alone. "Playful" objects catalyze the social.
  2. **Competition**: winners/losers, rankings, leaderboards; FPS and MOBA, professional leagues; teams add an in-group/out-group effect. A strong motivator for many, **demotivating for others**, and the one that fades most with age (Yee 2016a).
  3. **Grouping**: alliances, guilds, parties, corporations; one player founds and administers (membership, privileges, handing over leadership). Ad hoc alternative: *Realm of the Mad God* gives XP shared by proximity (low friction, but no lasting group structure, so the social bond stays shallow). With formal structures (guilds/alliances as clubs), social engagement lasts much longer.
  4. **Complementary roles**: nobody can do everything (tank, DPS, support/buff). Players achieve together what nobody achieves alone. It subsumes dopamine, serotonin, oxytocin plus A/F and short cognition: a very powerful engagement mechanism.
  5. **Social reciprocity**: returning favors (*Game of War: Fire Age*: helping an ally build/repair faster; gifts to the alliance when someone buys, which drives others to do the same). The same "mundane" gameplay as other games but almost 2 million USD/day in microtransactions for months (the author's figure): the value of the social loop.
- **Fake social**: *FarmVille* is almost non-social (asynchronous visits, players as "ghosts in parallel dimensions"); it doesn't satisfy real social motivations, only the pride of showing off the farm.

### 4.4 Emotional
- It moves from executive to reflective attention. Games have mostly explored **primary/basic emotions** (Damasio 2003, Ekman 1992): anger, fear, tension, surprise, accomplishment, delight; biological, fast, reflexive, exogenous.
- More nuanced emotions (dread, guilt, loss, longing, fulfillment, love, complicity, gratitude, honor) have only recently begun to be explored; they take **minutes to hours** to arise and sometimes last much longer.
- Difference from a book/film: in a game there is a loop; if I feel shame I can act to change it; if I feel tenderness I may be surprised that the game doesn't go along with it.
- **Examples**: *Papers, Please* (deciding other people's fates as an immigration officer), *This War of Mine* (civilians in war), *The Grizzled* (WWI soldiers), decisions with no right answer; *Journey* (awe); *Knights of the Old Republic* (interactive romance arc); *Burgle Bros* (cooperative heist on the brink of disaster); *Fugitive* ("almost got away" tension). Emotion is part of the game and conditions decisions, not an add-on "stuck on".
- **There is no consolidated theory**; models cited: Lazzaro (2004), Bura (2008), Cook (2011a). Much of the literature treats the game like a novel/film (a single path with predefined emotional beats, no agency): avoid it.
- **Two-axis model (Russell)**: **valence** (displeasure→pleasure, horizontal) × **arousal** (low→high energy, vertical) = 4 quadrants: high energy/happy; low energy/happy; low energy/unhappy; high energy/unhappy (≈ sanguine, phlegmatic, melancholic, choleric humors). Variants: Russell's circumplex (1980) and Sellers's multilayer circumplex (2013). Useful for locating target emotions (anger, joy, fear, contentment, greed, jealousy, compassion, delight, resignation).
- **Emotions = companions of motivations** ("how we feel about what we want or don't want"). Mapping with **Maslow** (the time scale matches that of the loops):

| Maslow level | Example motivations | Example emotions |
|---|---|---|
| Contribution (self-actualization) | Looking beyond oneself, leading and serving the group | Compassion, unity, righteous anger (wrath), awe, joy, despair, resignation, humility |
| Skill and attainment (esteem/skill) | Skill, professional worth, accomplishment | Victory, honor, guilt, courage, fulfillment, pride, remorse, mercy |
| Social (belonging) | Friends, family, inclusion, group, identity | Sympathy, shame, jealousy, friendship, hatred, contempt, acceptance |
| Security and objects (safety) | Acquisition, preparation, shelter, protection | Delight, hope, envy, disappointment, playfulness, settledness, unease |
| Physical (physiological) | Food, water, human contact, novelty, avoiding pain/harm | Attraction, pleasure, disgust, anger, fear, surprise, fatigue |

- Use: pick the emotions you want, find the motivation that generates them and create situations/systems that sustain it; or the other way around, look at which motivations your game dominates and predict the emotions. In-game motivations ≠ motivations outside the game (ch. 6).
- Example: a character under waves of the undead = physical/security motivations → fear, disgust, surprise, hope/disappointment; not friendship, compassion or revenge, unless you add a social component (someone to rescue) or a skill component (victory, courage).
- **Techniques**:
  1. **Context**: create atmosphere (colors, light, camera angles, music, setting) that primes emotions. Example: a sunny amusement park seen from above vs. at night in a storm, low light and a camera from the ground.
  2. **Situation and goals**: give meaningful goals the player wants to reach, keep or avoid, tied to Maslow's levels; put life, possessions, friends, esteem or group at risk. Achieving/avoiding the end generates emotion (victory, disappointment, loneliness, inclusion). **The player has to truly care about the goal**; the magnitude of the emotion matches the importance assigned.
  3. Remember the magic circle: emotions usually stay inside, but the more "real" the game becomes, the more they leak outside (like the death of a beloved character).
- **Challenge**: create systems that produce the emotional experience **without reducing the game to a single path with linear set pieces**. Trade-off: cut-scenes/linear content = **emotional precision and reliability** (author role); emergent systems = less precision but a more interactive, personal and authentic experience (designer-of-conditions role).
- **Cautions**: the player may miss the opportunity or not invest meaning (the emotion doesn't occur); may react more strongly than expected; may feel other motivations/emotions than the ones planned; it takes time to build the systems and for the player to live through and resolve them (hours to weeks). The higher up Maslow, the longer it takes to generate and resolve, but the longer it lasts.

### 4.5 Cultural
- Scale of years (conversations about values, identity, history, rights). Games don't last that long but can capture currents and prompt reflection on lifelong themes.
- **Train** (Brenda Romero): yellow pawns in boxcars; the destination is revealed late (Nazi concentration camps); subtle clues (broken glass under the board). Rules with "procedural gaps" that force the player to decide and be complicit; final question: how far do we follow rules without asking "what for?". Reactions: revulsion, crying, or finishing it all, or subverting it.
- Possible only in games: the player inhabits the story/culture through model systems. It **blurs the edges of the magic circle**: the conversation continues outside (is it moral to play *Train*?).
- Extra-game cultural loops: fandom, cosplay, forums, criticism. E.g. *Bioshock* and Objectivism generated conversations. They are a larger loop, designed and detached from the game; a nascent area.

---
## 5. Flow (sec. "Flow in Interactive Loops")

- **Flow (Csikszentmihalyi 1990)**: "being in the zone". Similar to engagement: a challenging task with uncertainty (not memorized), understandable goals, clear feedback, focused attention without stress, distorted time but an unintrusive awareness of performing well; absorption without self-consciousness; the task becomes meaningful in itself.
- **Autotelic experience**: maintaining the flow state becomes a goal in itself.
- **Flow channel (Fig. 4.8)**, axes challenge (vertical) × skill (horizontal):
  - Low challenge and low skill: **apathy**.
  - Small challenge matching beginner skill: **interest** → entry into flow.
  - The channel rises diagonally as both grow.
  - Challenge slightly above skill: **arousal**; if it keeps growing: **anxiety** (falling off the right side of Yerkes-Dodson).
  - Skill above challenge: **relaxation** → **boredom**.
  - The player oscillates (sinusoid) between arousal and relaxation without leaving the channel = Goldilocks zone: engaged, learning, performing well.
- **Habituation** drives progress: what delighted before is no longer enough → pushes toward learning more and taking on bigger challenges ("surfing" on the upper right edge). They can drop into relaxation without breaking the flow thanks to the stacking of cycles.
- **Autotelic goals**: once the player has progressed enough, they start setting their own goals and no longer need external pressure. Not every game needs this (*Tetris*, match-3 achieve flow with A/F and short cognition). Internal models deep enough for autotelic goals are the ones that get played the longest and loved the most.

---
## 6. Time-scale view: stacked loops (sec. "A Time-Scale View of Interactive Loops")

- Loops stack at different scales; fast ones are perceived as **less meaningful**; depth of meaning requires long loops (social, emotional, cultural).
- Examples: match-3 = A/F + short cognitive (and a longer recurring short cognitive when solving puzzles), with no strategy or emotional/social/cultural loop. Online wargame = A/F + tactical, strategic and social.
- **"Light" (fast) games**: easy to pick up and put down, lower lasting value. **"Heavy" games (long-term, social, emotional, cultural)**: hook for longer and build loyalty over years. Data point: on mobile, only **38%** of players are still playing a month after starting (Dmytryshyn 2014).
- **Halo / Jaime Griesemer — "30 seconds of fun"**: "a 3-second loop inside a 30-second one inside a 3-minute one that is always different" → a unique experience every time. Short loops = moment to moment (where to stand, when to shoot, when to dodge a grenade); long ones = more tactical/cognitive. Stack loops, build engagement at each scale and vary what each one gives.

### Core loop (Fig. 4.9)
- Working definition: what the player does most of the time. Cycle: **player intention → action (input) → internal game change → feedback to the player → progression and reward (or call to action) → new intention**.
- The game defines which type of interaction is the main one (it almost always includes A/F, but it isn't always the most meaningful): it can be moving/jumping/shooting, or merely a means to build buildings, discover technologies, manage an empire or build relationships. Detail in ch. 7.

### Cycles of engagement
- Stacking loops of different durations creates **natural cycles of high and low tension**: challenge/tension and then relaxation/consolidation. It prevents **attentional fatigue** (the player can't keep up and engagement and performance drop).
- Metaphor: small waves (A/F, always present) over large rolling swells (long cognitive, social, emotional, cultural) (Fig. 4.10).
- **Rhythm and ritual** (Chelsea Howe 2017): cycles that mark the passage of time: new content (daily quests/rewards), natural session start/end points, battle or repair moments, rise and release of tension in dramatic arcs, social or celebratory rhythms (seasons, leveling up).

### Narrative vs. interaction
- **Cook (2012)**: narrative forms **arcs, not loops**: it delivers a "payload of preprocessed information"; it isn't interactive, the player is a passive spectator during the narration.
- Narrative as **bookends** (introduces the mission, you play, the ending is narrated): it can give the appearance of interactive narrative, but if the player senses that beginning and end are fixed, their decisions lose meaning and futility sets in. **"Gilligan's Island problem"**: whatever happens, you return to the starting point (limits growth/change).
- Chaining loops with non-interactive arcs can hook but **lowers replayability**. Used sparingly as context and scaffolding for systemic play, narrative speeds up the player's mental model.

---
## 7. Mental load and the interactivity budget (sec. "Mental Load and the Interactivity Budget")

- **Mental load**: an expanded version of cognitive load (attentional, perceptual, cognitive, emotional, social, cultural). There is a cap on how many enemies, explosions, conversations or puzzle parts can be followed.
- **Attention priority: the fast drives out the slow**. Order: reflexive/involuntary/exogenous > executive > slow-reflective. If you have to dodge projectiles or watch the periphery, tactics, strategy and emotional reflection get suppressed. Exception: executive concentration so intense that cues from the environment are ignored.
- **Quantic Foundry** (almost 300,000 players surveyed): *excitement* axis (fast action, surprise, thrill) vs. *strategy* axis (thinking ahead, complex decisions).
  - Top-left (high excitement, low strategy): *Counter-Strike*, *League of Legends*. Bottom-right (low excitement, high strategy): *Europa Universalis*.
  - **The top-right corner is empty**: no game is high on both; it would be too much mental load. There is a **cognitive threshold** (Fig. 4.11).
  - The farther out along either axis, the more "hardcore" (more resources to learn and model); the bottom-left corner = "casual", **"easy fun"**. Bands: **easy fun, balanced fun, hard fun** (Fig. 4.12). Within each band the genre varies, but the relative difficulty of learning and succeeding is similar.

### Interactivity budget
- How much total mental load a player is willing to spend at a given moment, and which types of interaction they spend it on. Willing players go to games further along the axes or with heavy emotional interaction (*Gone Home*, *Papers, Please*); someone who wants something light goes to *Candy Crush* (little short cognitive + gentle, juicy A/F). Fewer requirements = more casual, you drop in and out at will.
- **Short (reflexive) loops consume the budget first**: A/F can drown out short cognitive, which drowns out long cognitive, and so on.
- **Derived design rules**:
  1. High-action game (A/F + short cognitive): don't also ask for long cognitive, emotional or social at the same time. If you include them, **separate them in time** from the fast stretch.
     - RPGs: long-term customization **between** tactical stretches of quests and combat.
     - *League of Legends*: social in the lobby, separate from high-intensity matches.
  2. Thinking/long-form game: avoid heavy A/F or short cognitive under pressure. E.g. *Stellaris* (galactic strategy; the player doesn't direct the battles, they can be watched effortlessly; attractive visuals without time pressure).
  3. Emotional-impact game (*Papers, Please*, *Train*): austere presentation and little A/F, little short/long cognitive, to leave energy for the emotional.
- State of the science: **we don't know how to measure** the budget or how much sensory feedback is needed to hold attention, except through surveys; it is practice and future exploration.

---
## 8. Recognizing, defining and creating "fun" (sec. "Recognizing, Defining, and Creating 'Fun'")

### Previous attempts at a definition
- Caillois & Barash: *agon, alea, ilinx, mimicry*. Koster (2004): "fun is just another word for learning". Others propose 8 (Hunicke et al. 2004), 14 (Garneau 2001) or as many as 21 (Winter 2010) types of fun.

### Characteristics of fun (sec. "Characteristics of Fun")
- A pleasant/emotionally positive experience with **duration** (more than a quick jolt) that you'd want to repeat. Schaufeli: "a generalized affective-cognitive state".
- **Voluntary and typically without consequences** (magic circle). If you remove the possibility of quitting, the fun disappears.
- Attractive (not avoided and not merely informative), **positive valence**, even if the surface is sad or frightening (a drama film, a haunted house) as long as it is voluntary and without real consequence.
- Many flavors: sensory (fireworks, vertigo/ilinx), neurochemical, material reward, social inclusion, accomplishment, completeness (completing sets).
- **It can include learning but doesn't require it**; it can be purely sensory or emotional; it doesn't require rationality (but mental puzzles can give a "clever" victory).
- It implies **satisfaction and a sense of balance**: too boring, stressful, chaotic or arbitrary stops being fun. Fun and flow are deeply related.

### Definition (sec. "Defining Fun")
- There is no single definition, but there are regularities. Consistent with the types of engagement.
- **Voluntary first**: if participation is forced (coercion, addiction, loss of agency), the fun goes away. The same with a real consequence of loss (except gambling: there the voluntary risk and the anticipation of reward/dopamine keep the "fun").
- By type: sensory/physical (ilinx, roller coaster, light show); cognitive (puzzles to strategies, learning: building a mental model can be fun; beware of rote learning or learning under too much stress, which is not fun); social and emotional (dances, party games, conversation); cultural (museums, for some).
- Everything must fall within the **subjective interactivity budget**, which varies by person and moment; if it is outside the flow channel, it isn't fun at that moment.

**Formal summary (four attributes of fun):**
1. Voluntary and (typically) without consequences.
2. Positive emotional valence (sometimes under a negative surface) and some duration, not a "jolt".
3. Elements of one or more engagements: sensory, cognitive, social, emotional, cultural.
4. Fits the current level of desire for interactivity (interactivity budget), which varies by person and moment.

- Key phrase: **not everything engaging is fun, but every fun experience is engaging.**

### Working definition for design: a successful game needs to be
1. A **voluntary** activity the player chooses for themselves.
2. **Perceptually attractive**, with an obvious call to action that starts the loops.
3. **Interactively engaging** in one or more of the ways in this chapter: opportunities for player decisions in a broad play-space, inviting "vigor, dedication and absorption".
4. **Not too demanding** for their mental capacity/interactivity budget.

- You don't "design" these qualities and tick them off: they are **emergent** from the whole.
- **Questions the designer should keep repeating** during design, construction and testing: Am I adding to or subtracting from these qualities with each decision? Does the design provide enough opportunities for engagement, including meaningful decisions? Does it do so without overflowing the mental budget?

### Do games have to be fun?
- Not strictly. A game can use its attractive/interactive nature in a "subversive" way (*Train*) to lead to valuable experiences that wouldn't otherwise be sought out.
- Birk et al. (2015): games produce the full emotional range. Games built on enormous **frustration**: *Super Meat Boy*, *Dark Souls*, *Dwarf Fortress*; with negative emotional contexts: *The Last of Us*, *That Dragon, Cancer*. They are still voluntary, engaging and compelling even if they aren't "fun".
- Conclusion: most are fun, but not necessarily; they must be **highly interactive and engaging**.

### Depth and elegance revisited
- **Systemic depth**: a hierarchy of systems within systems; if the player can move up and down between levels and interact at each one, engagement increases and a "cognitive awe" appears (like fractals/self-similar systems).
- **Elegance**: depth without exceptions or special cases that break symmetry; it satisfies Bushnell's Law (reusing structures learned in one area when tackling another, without collapsing the play-space).
- Rules with exceptions, or two systems that operate in contradictory ways, **consume the interactivity budget** and reduce engagement: the player works harder to reach the point of worrying less about *how* to play and simply enjoying. Fewer rules, **fewer exceptions**, a large play space and many levels of organization = more elegant, more engaging and more enjoyable.

---
## 9. Diagnostic checklist and design questions (synthesis of the chapter's heuristics)

**Signs that a game doesn't hook (and the probable cause):**
- Nobody understands what to do at the start → missing affordance/call to action (controls not visible, illegible screen). [Low arousal/boredom]
- A screen with too much visual noise or too many things at once → overload, anxiety (right side of Yerkes-Dodson).
- The player needs to read text/numbers to interpret results → high semantic distance.
- Indirect inputs or many modes/exceptions → articulatory distance and rules with exceptions eat budget.
- Feedback late (> ~250 ms) or nonexistent → the action-result association is lost; a sense of lag.
- All the content seen and the systems exhausted → nothing new to learn; lacking systemic depth/autotelic goals (content-driven vs. systemic).
- Expected, repeated rewards → habituation; it needs novelty, new forms of engagement.
- Continuous tension without rest → attentional fatigue; tension/relaxation cycles are missing.
- Asking for reflexes + deep strategy + emotion/social at the same time → breaks the interactivity budget ("the fast drives out the slow").
- A predetermined beginning and end with decisions that change nothing → "Gilligan's Island problem", a sense of futility.
- A "social" game with no real mutual need (asynchronous, no referents or roles) → doesn't satisfy the social side (FarmVille).
- Difficulty misaligned with skill → outside the flow channel (boredom or anxiety).

**What to look at when designing a loop or feature:**
1. What does the player do at each moment (moment-to-moment)? What feedback do they get and what actions can they take?
2. At which scales are there loops (3 s / 30 s / 3 min / session / goal / social / emotional)? Does each contribute something different (Halo)?
3. Which loop(s) are the core loop? Which one consumes the interactivity budget?
4. Are there cycles of high/low tension? Rhythm and ritual?
5. Can the player form valid intentions, with information, predictable and on time?
6. Do I make it easy to learn (few rules, no exceptions) and leave depth for mastery (Bushnell)?
7. What emotions do I want and what motivation (Maslow) generates them? Does the player truly care?
8. What is voluntary? What real consequence could kill the fun?
9. Does the call to action have affordance and motivation?
10. Is there useful hidden state so the player can infer and make predictions (black box)?
11. Is the feedback juicy, with good game feel, when the main loop is A/F? Do the target size/tolerance respect Fitts?
12. Measurement: the author acknowledges that the interactivity budget can currently only be measured by survey; use playtesting, not a formula.

**Numbers from the chapter:** <100 ms = instantaneous; <=250 ms maximum to feel an immediate connection (Card et al. 1983); A/F: <1 s to 2-3 s; Halo: 3 s / 30 s / 3 min loops; mobile: 38% retained at one month; Quantic Foundry: ~300,000 respondents; Game of War: ~2 M USD/day in microtransactions; types of fun: 8 / 14 / 21 depending on author; emotions: 2 axes = 4 quadrants; Maslow: 5 levels; loops: 6 types.
