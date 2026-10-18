# Prototyping and Playtesting (ch. 12)

Read this when you need to validate a proposal: finding the fun fast (closing the interactive loop), what a prototype is and is not, one question per prototype, when and with whom to test, the script, a balanced survey, methods (observation, directed exploration, Wizard of Oz, thinking aloud) and how to read feedback (problems, not solutions).

Paraphrased summary of Sellers, *Advanced Game Design: A Systems Approach* (2018). The book section each block comes from is given in brackets.

## Index
- 1. Design-Build-Test (section "Designing, Building, and Testing")
- 2. Finding the Fun Fast (section "Finding the Fun Fast")
- 3. Effective Game Prototyping (section of the same name)
- 4. Effective Playtesting (section of the same name)
- 5. Heuristics and Common Mistakes (cross-cutting summary)
- 6. Minimal Summary of the Non-Core Material (pitch, production, wrap-up)

---

## 1. Design-Build-Test (section "Designing, Building, and Testing")

- **Design-build-test loop**: designing, building and testing are not sequential phases but simultaneous activities throughout development. Only the emphasis shifts: design dominates at the start, then implementation, and testing/fixing at the end; but all three always happen.
- As soon as there is an idea of the core loop, build it and test it while the design continues. Late design changes should become narrower and narrower (detail and balance, not structure).
- Test the gameplay throughout development; never leave it for the end.
- Implication: in a skill, every design analysis should end in "what to prototype/test to confirm it", not in a closed specification.

## 2. Finding the Fun Fast (section "Finding the Fun Fast")

- First big goal: validate the primary concept. It cannot be postponed: if the idea does not work, or technical, interactivity or gameplay problems show up that were invisible on paper, you need to know now. If it works, it gives you confidence to keep going.
- How: **close the interactive loop** between player and game. It does not matter that art or most of the gameplay is missing; what matters is that there is real interactivity.
- Early distractions (the author names them): map editor, iconography, character backstory. Important later, a hindrance at the start.
- Strong rule: until the interactive loop is closed and you have confirmed there is something compelling, "you don't have a game"; it makes no sense to invest in anything else.
- The first milestone toward the concept = a playable loop, not content.

## 3. Effective Game Prototyping (section of the same name)

### Definition (game prototype)
- Prototype = any working portion of the game that allows **at least one interactive loop**.
- These are NOT prototypes: a non-interactive image (that is a **mockup**, even if animated), a gameplay video (real or prerecorded), a simulation running without interaction (even though it sometimes serves as a specialized technical test). Rule of thumb: if nobody can play it, it is not a game prototype.
- Reason: without interaction you are not testing the game; a non-interactive program tests an algorithm or a simulation, not a game. Excursions outside the game are valid, but each prototype must bring you closer to the final game.
- The minimal interactive component (analog or digital) = the player forms an intention, carries it out with an action, perturbs the game's internal model, and the game gives feedback.

### Analog vs. digital
- Tabletop: anything goes (pieces of paper). Digital: the first prototypes are usually physical (paper, dice, whiteboard) with just enough for a single loop.
- An early digital prototype = a simple, standalone program to test ONE part, starting with the core loops. Later ones incorporate more of the game.

### Keeping Prototypes Separate
- Prototypes are never part of the product; always implement them separately. You can reuse parts of the game as the base of a prototype, but the prototype's code NEVER goes back into the game.
- They must be allowed to be fast, ugly and unoptimized. Warning signs: stopping to "code it properly" or thinking about copy/pasting it into the game -> you are building a hybrid that is neither a prototype nor viable code.
- Mantra (**Move fast and throw it away**): move fast and accept breaking things. You **refactor** (analyze what worked and rewrite), you do not copy. The goal of a prototype is to answer a design question, not to produce reusable code.

### Getting Started with Prototyping
- You can prototype as soon as you have an idea and a concept. Start simple: you do not need a full economy or full combat. Basic movement or a simple action is enough.
- Art and animation style are tested later; first an interactive loop and a simple player goal (e.g. get from here to there) that makes sense in the game.
- Add more decisions and loops gradually, but make sure the core loops are compelling. If they are not, "no amount of makeup will fix them": they will stay as weak, frustrating parts.

### Answering Questions
- A prototype exists to ask and answer questions. The first and biggest one: "Is this fun?" (about the core loops).
- The answer is usually NO. The author's rule: first ideas tend to be bad or, at best, mediocre and derivative; you only see it once you get them out of your head. Finding that out with little investment is a gain (better than at 6 months).
- If a prototype fails: learn, then try another approach to the same concept (faster, more strategic, a different emotional core). A failed approach does not invalidate the concept.

### Clear Goals and Questions
- Every prototype carries a clear, unambiguous question/goal whose answer would significantly change the game or how it is developed.
- Trigger: if the team is arguing or doubts the direction, that is the ideal situation for a prototype: stop arguing, formulate the question, build it, see.
- Examples of good questions: "Is one resource enough or do we need more?"; "Does this combat style feel fun?"
- The more precise the question and the prototype, the more you learn; **better still if you can test several options at once** (by adjusting variables or different modes).
- Make your assumptions about the player explicit for each prototype: what they know about the game, what their goals are, how much of a mental model they have built. The player's goal can be simple ("go from A to B") or complex ("complete the mission without being seen"); it depends on the stage.

### Knowing the Intended Audience
- Type 1, internal: quick and ugly, for the team only. Spend the minimum on polish; squares or X's for graphics; or analog with paper/markers/dice. The faster and uglier, the more effective at answering the question.
- Type 2, for third parties: **vertical slice** = a cut that shows all the layers/systems working together (polished UI, consistent interaction, art, exploration, balanced combat, down to the database). The idea: everything else would just be "more levels, weapons, outfits".
- The author's critique of the vertical slice: it confuses a **complex** system (one with loops) with a **complicated** one (linear). In innovative games it does not reduce to "now just make more levels". A slice does not guarantee that the rest is linear.
- Tension with stakeholders: an ugly but compelling prototype (a circle dodging squares) can make them lose confidence because they cannot see the experience. Alternative: a NON-interactive demo video of how the game will look; it consumes resources but also helps align the team's vision.

### Other Prototypes
- There are non-interactive or nearly non-interactive prototypes: testing an internal system of the world model, graphical effects, qualitative aspects of the UI (its **juiciness**, e.g. brief animations on controls). They are valid; if you can, include them in another game prototype; if not, the same criterion applies: know what you are testing, what question you are asking, how the answer changes the game, and iterate until it "feels right".

## 4. Effective Playtesting (section of the same name)

### The Importance of Playtesting
- Test the experience already in prototypes, not just in the finished game. First with the team; then soon with people who know nothing about the game and, preferably, do not know you. It is uncomfortable: what is clear to you turns out to be opaque or frustrating. "If you wait until you feel ready, you have already waited too long."
- You are looking to see how others experience the game: does it hook them, is it fun, would they want to keep playing?
- Do not assume what players will think: you will probably be wrong more often than right. The most valuable thing: discovering what is obvious to you and mysterious to them.
- **Players give problems, not solutions**: the aim is to see where to improve, not to collect solutions. If they propose one, look behind it to see what problem they think there is; your solution to the underlying problem may be very different.

### When to Test
- As early as possible, before you think it is ready. Resist the "it's not ready yet".
- More short tests > few long tests.
- Playtest triggers: (1) a significant change in the game; (2) an area where you doubt the direction; (3) a few weeks have passed since the last one.
- Cadence: at the start ~every 2 weeks; later weekly or every few days.

### Goals for Your Playtests
- It is NOT about hunting code bugs (even less in ugly prototypes). It is about testing the design: do they understand it, do they build an effective mental model, do they find it compelling and fun?
- Early on: validate basic design concepts. As the systems grow: how easily it is understood and how well the mental model is built.
- Look for where players "go astray": a mental model different from the expected one and from the game's internal model; confusion, frustration, not knowing what to do now.
- Sooner or later it shifts into **usability testing**: is the UI understandable, is it easy or cumbersome? It does not measure the overall experience but it is part of it.

### Who Playtests Your Game?
- Not you: you are the most biased and least qualified. Your experience says nothing about what is fun for others.
- Team, friends and family: poor subjects; they unconsciously strive to see the game as understandable/compelling even when it is broken.
- Exception: for early, ugly prototypes it makes sense to keep them close; a few outside confidants help if they can see past placeholder graphics.
- **You cannot "un-know"**: someone who has already played does not become naive again. Do not reuse the same person as a novice for the same part. Repeat players are useful for comparing preferences or whether something now makes more sense, but they are not equivalent to a first-timer.
- As the game matures, widen the pool and move it closer to the target audience, without narrowing it too much (you lose unexpected players or end up with a miscalibrated market).
- Beware of **enthusiastic hardcore gamers**: useful, but with firm opinions about what a "good game" is; they add more noise than signal.

### Preparing Your Playtest
- Be clear about the goal and how it is conducted. Location: any quiet place without distractions; even a noisy one worked (a university cafeteria).
- Labs with two-way mirrors or cameras: useful but unnecessary; do not hold back tests for lack of facilities. Make a prototype and test it.
- Compensation: not always needed; be fair. Free pizza worked for university students; a low-value gift card; more compensation the longer the test and the survey.

### Writing a Script
- Write a detailed script for EVERYTHING (greeting, execution, post-test questions, goodbye), down to what is said at each step. It keeps you from saying too much or getting nervous and ensures the **same context and instructions** for everyone.
- Start with a greeting and some warm-up chat; minimal player data (only what is needed: name/contact, age/gender if they agree). Ask what other games they play: it calibrates experience and puts the player in test mode.
- Ethics: tell them that the game is being tested, not the person, and that whatever they do is valid; that they can stop and leave whenever they want; that answering questions is voluntary. Ideally a short statement read aloud and/or signed/initialed, or at least verbal acknowledgment.
- If the player wants to stop, stop the test without insisting (insisting raises ethical problems); also, the wish to stop is information about your game.
- Recording: note-taking forms; optionally screen and face video with consent. Warning: video multiplies analysis time and does not necessarily give more information, especially early on.

### Creating a Survey
- Designing surveys takes some expertise. Keep it brief, with few questions, all tied to the goal of the test and to the experience (including comprehension and mental model). Do not ask about everything (graphics, music, difficulty...) if it does not fit the current goal: it overwhelms and yields data you will not use. The player's spontaneous comments get noted anyway.
- **Balanced questions**: as many negative answers/statements as positive ones, so as not to bias (avoid leading questions). If online, randomize the question order (reduces bias, eases analysis).
- **Numeric scale** (5 to 7 options, from "strongly disagree" to "strongly agree" with a neutral midpoint). Statements should be strong assertions that people can agree or disagree with. Examples from the book:
  1. It was easy for me to move around in the game.
  2. I understood what was happening at all times.
  3. I had clear goals that I was trying to accomplish.
  4. I could easily play it again without going over the rules.
- **Checklist of adjectives** (quantifiable but open-ended): Exciting, Fast, Confusing, Boring, Overwhelming, Thoughtful, Strategic, Broken, Engaging. Rule: the same number of positive, negative and neutral traits, in an unbiased order (not from best to worst).
- **Comprehension / mental-model questions** (better oral and recorded, since they allow free-form answers): show icons/symbols and ask what they mean; process questions ("what steps would you follow to find out how many soldiers you have available?"); show a screenshot of a typical moment and ask what you would do next, pointing with a finger.
- **Short answers** (oral or written) plus a final open-ended one:
  - Briefly explain the rules of the game as you understand them.
  - What surprised you?
  - What did you think you were supposed to achieve?
  - What games did it remind you of?
- "How much would you pay?": useful for gauging a positive/negative experience and a vague sense of value, but NOT for setting a price (what people say differs from what they do).
- **Test the script beforehand** (a mock playtest with someone, even a teammate) so you do not trip over flaws in the test itself.

### Running a Playtest
- Keep them short: a few minutes, generally no more than 10-20.
- Give the minimum information about the game. Variants per test: give the name or the possible box art; give a general summary or the elevator pitch to see whether it affects comprehension/enjoyment; or give nothing (telling the player you will not provide information). Follow the script so you do not say more to some than to others. After launch you will not be there to explain, so limit the information given beforehand.
- During play: out of their line of sight, no hovering, talk as little as possible. Answer as few questions as possible, and briefly. **You have to witness their confusion and frustration.** Encourage them to keep going without hints.
- Forbidden: pointing at something on screen, "try clicking at the top left", "go back one menu and read it again", explaining the game, defending yourself against criticism. Explaining or defending ruins the test.
- Note what they do, what they say, where they get confused and ABOVE ALL emotional reactions (sudden understanding, delight, confusion, frustration).
- If they ask for reassurance: "you're doing fine, keep going". The observer's reactions should be neutral and general: players look for signals (even unconscious ones) about whether they are allowed to criticize.
- End of the test: when they complete what you were looking for or get stuck and cannot progress. Then ask what they were trying to do and what they expected to happen (this reveals the mental model) and move on to the post-test.

### Finishing Up the Playtest
- Ask for general impressions. Pay attention to the FIRST thing they say (the top-of-mind reaction) and to the structure of what they say: they may start with something nice to cushion the real criticism. Accept everything without closing the conversation or defending.
- Then the survey from the script (without biasing), thank them, ask them to fill it out; if they decline, still ask for final thoughts; thank them and say goodbye.

### Testing Methods
Depending on the goal and the facilitator's confidence:
1. **Observation**: watch the player. See where they go first, which options they look at or ignore, whether they do the expected thing at each moment. Signs of engagement: staring at the screen, pressed lips, slower blinking. Emotional reactions: surprise, delight, frustration. Note where they get confused, get stuck or keep returning to the same content/UI (they try and fail).
2. **Directed Experience and Exploration**: give them a concrete goal (in the script, not to pull them out of a confusion; especially useful with someone who has already tried the game); or tell them to explore freely and watch what they ignore or avoid.
3. **Wizard of Oz**: early, analog tests; the designer plays the computer ("the wizard behind the curtain"). Low fidelity: it is no good for judging the behavior of the future digital game, but it reveals expectations and mental model.
4. **Thinking Aloud**: ask them to talk out loud the whole time (intentions, doubts). Hard: they go quiet when reasoning; remind them with "keep talking". It lowers the player's performance (especially in games that demand their **interactivity budget**). Useful when other tests show confusion and you do not know why.
- Rule: use only methods tied to the goal of the test.

### Analyzing Feedback
- Immediately when it ends: jot down impressions (reactions seen, bugs, ideas). Then set aside analysis time: review each player's notes looking for common experiences, themes, what mattered most; review the survey's quantitative data for trends.
- Do not dismiss or worry about negative comments: they are not a judgment on the designer, but on how well the game achieves the intended experience. Learn from the negatives.
- **Outliers**: one person loves it, another understands nothing: these tend to be isolated cases; look for what is COMMON among players.
- Do not force patterns or chase statistical significance (unless you have a large team with dozens of players per test). Look for **directional experiences** that refine the design and answer questions.
- Directionality also over TIME: compare across builds. Do the same parts hook people consistently? Are confusing areas now enjoyed? Did a change make something worse?
- Players = a valid point of view but not designers; read their feedback as identifying problems, not solutions.
- Cases from the book of feedback that changed the design: (a) pirate game: exploration felt like filler between battles; the designer focused only on naval battles and it became more compelling and easier to implement; (b) The Sims: conceived as a Tamagotchi-style life simulator, but players were interested in the interactions and emergent stories; development and marketing changed.

## 5. Heuristics and Common Mistakes (cross-cutting summary)

Heuristics
- Close the interactive loop before anything else; polish comes later.
- One question per prototype; if the team is debating, turn it into a prototype.
- Test several variants/variables at once when possible.
- Prototype: fast, ugly, disposable; refactor yes, copy-paste no.
- Many short tests; test after every significant change, doubt about direction or ~2 weeks without a test (then weekly).
- Written and tested script; same context for everyone; observe in silence.
- Look for what is common and for direction, not statistics; read problems, not solutions.
- Failing fast on ideas is cheap: celebrate discarding early.

Common mistakes
- Waiting for the game to be "ready" before testing.
- Testing it yourself or with friends/family/team and trusting that.
- Reusing a tester as a novice; confusing a repeat player with a first-timer.
- Intervening: pointing, explaining, defending, giving hints.
- Biased surveys (only positive statements, fixed order), too long, or unrelated to the goal.
- Taking "how much would you pay" as the real price.
- Testing bugs instead of design in prototypes.
- Putting prototype code into the game; the "horrible hybrid".
- Wasting time on a map editor, iconography or lore before knowing whether there is fun.
- Confusing a complex system with a complicated one (believing the slice is enough and "only more content is missing").
- Putting makeup on a weak core loop hoping polish will fix it.
- Taking solutions proposed by players literally.
- Hardcore gamers as the only pool; a pool that is too narrow.
- Over-analysis with video in early stages (costs a lot, adds little).

## 6. Minimal Summary of the Non-Core Material (pitch, production, wrap-up)

- **Pitch** (Making the Pitch): communicating the game to get funding, validation, recruits or press; know the goal, the audience and the material; elevator pitch (who I am, what I do, what I'm looking for) vs. formal meeting (<=10 slides, graphic core loop, 5-10 min of questions); short concept statement (ideally <=140 characters, <=1 comma); order of preference of evidence (game sold > nearly finished > polished demo > core prototype > trailer with sound > mockups); call to action and follow-up; a "fast no" is better than "death by tea and crumpets". Worth keeping: comments like "it's X crossed with Y" show that the person built a mental model; having no questions is a bad sign.
- **Phases of Production**: iterative (not waterfall); **stage gating** with periodic reviews (every ~2 weeks at the start) and a **concept bank** for discarded ideas; sprints of 2-4 weeks; concept (1-3 months, with a gate: if the prototype does not work, stop investing), preproduction (2-3, up to 6 months; features, MVP, asset list, plan with a shrinking horizon), production (avoid scope creep: every new feature goes through a mini concept and preproduction), alpha (everything playable, tested by outsiders; afterwards only bugs and low-value balance), beta (balance, polish, UI juiciness, day-1/week/month retention metrics in free-to-play), launch.
- **Production analytics**: measure estimated vs. actual per task; personal ratio as a multiplier (e.g. 1.2x); mini postmortem per iteration; burndown charts.
- **Finishing**: finishing > perfecting; "anything finished is better than everything unfinished"; release is the outermost designer's loop; the first big playtest of the complete game brings pages of problems and you have to keep going.
