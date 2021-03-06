`Lesson 10 - Incremental Concept Learning`
---------------------------------------------
-Small number of exmaples leads to a very complex learning space, so generalization/specialization heuristics help guide the agent through this compelx environment
- In general - generalization includes new positive examples, specialization excludes negative examples
- final concept includes all positive exampels and excludes all negative examples. Final concept depends purely on input examples and background knowledge


`Lesson 11- Classification`
---------------------------------------------
- Core process of mapping percepts to an equivalence class that we can act in the world in an efficient process

- If n percepts (binary), k concepts, m actions (binary) -  2^n percepts ==> k concepts ==> 2^m possible actions
- k equivalence class concepts is much smaller than mapping 2^n to 2^m in a giant table
- equivalnce class concepts can be learned from ICL
- power of knowledge - breaking down problem to smaller/simpler problems

-classification is both top-down and bottom-up:
- classification hierarchy/establish-refine (top-down) can aid in classification - using establish and refine allows us to focus on specific variables at each stage
- Identify and abstract (bottom-up) - predict stock market direction from core economic indicators (leaf nodes)

- concepts are on spectrum from more formal to less formal: 
-axiomatic are more formal (math concepts) that have necessary and sufficient conditions. Easy to explain to others.
- prototypical are typical examples of the concept w/ overridable properties (chair, stool)
- exemplar concepts are abstract concepts that are difficult to explain and have no necessary and sufficient conditions (holiday, subjective experiences)


`Lesson 12 - Logic`
---------------------------------------------
--We have a knowledge base and rules of inference (inference engine) that allow us to make assertions (truth value) in the world 
- knowledge base is in language of logic, a sentence (predicate) and rules of inference (modus ponens, modus tolens)
- To be provable correct - we must have 1) complete and correct knowledge and 2 ) rules of inference guaranteeing correctness
- `Soundness` - Only prove true things , `Correctness` - can prove all true things

- Prior lesson knowledge representations used objects and their relationships, however logic represents in the form of predicates
- We can translate variabilization of foo concept into a predicate (language of logic)
- feather(animal) => bird(animal)  
- implication elimination  A=>B  --> !A V B
- Rules of inference: modus ponens S1)P=>Q  S2)P  S3)therefore Q , modus tolens S1) P=>Q  S2) !Q  3) !P
- modus ponens and modus tolens allow us to make sound and complete inferences that are guaranteed to be correct

-Proving the truth value of sentences can happen in 2 ways: 1) truth tables  2)applying rules of inference . However both methods are difficult for large/complex sentences

- 0th order logic (propositional logic) - logic w/o vaariables ,  1st order logic (predicate logic) - has variable quantifiers
- 1st order logic => universal quantifier  -  for all x[ flies(x) V feather(x) => bird(x)],  for some x[flies(x) V feather(x) => bird(x)]
- 1st order logic allows us to reduce the # of sentences we need to write

-Resolution theorem proving (RTP) is a proof by refutation. It is a more efficient method that is used when other methods (truth tables, rules of inference)
are computationally infeasible.

- RTP steps: 1)convert to CNF  2) Stmt 1 is from implication elimination, Stmt2 is observations/perceppts, Stmt3 is negation of what we're trying to prove
- If we can cancel out (resolve) all literals we arrive at a null condition and we have proved the negation is false, so what we're trying to prove is true
- Efficiency of RTP arises from the fact that we use `Horn Clauses` (disjunctions with at most 1 positive literal) - horn clauses allow a focus 
of attention that allows agent to be efficient.

`Lesson 13 - Planning `
-----------------------
- Intelligent agent maps perceptual histories into actions.
- Planning is a powerful method for action selection (using formal logic). It is a central process for achieving multiple goals @ same time
- Prior lesson (problem solving methods like MEA and PR) didn't tell us how to select which goal

- Planning has an initial state and tries to go toward a goal state. 
- State - Represented in formal logic ( On(robot, floor) or painted(ladder) )
- Operator - an action that is defined through a set of pre and post conditions. Preconditions can't have any negative literal
- Preconditions are true before operator is applied, postcondition true after operator applied
- Operator can be applied *IFF* preconditions true 
- Assertions are propagated to subsequent states provided the assertions aren't deleted/negated 

- Planning vs. Search - In "search" we try all possible operations at every step - leading to a combinatorial explosion (very inefficient) (Ie.. the nav problem)
- MEA used initial state and goal state to select b/w diff operators (this is one way of using control knowledge)
- Planning, however, uses a more systematic approach of choosing b/w operators (using pre/postcondition checks, and partial order planning/detection of conflicts)
- 2 Kinds of knowledge - 1) world knowledge (states/operators) and 2) control/tacit knowledge about operator selection. Goals provide us with control knowledge
- Partial order plan allows us to view multiple goals and select operators using goal/control knowledge

- Partial order planning can prevent conflicts by checking each precondition and seeing if it's `clobbered` by a state in another plan - if it is we promote the plan
- Other methods (MEA, PR) would not be able to avoid clobbering conflicts

-3 lessons learned: 1) knowledge is about world knowledge and control knowledge. 2)goals provide control knowledge. and 3)"Society of Mind" - multiple agents working together

- Hierarchical decomposition - using a categorical operation like `Stack` and `Unstack` that are composed of multiple operations
- This decomposition allows the agent to address complex environments by thinking at multiple levels of abstraction: 1) at the level of move operations,
2) at the level of macro operations (stack, unstack) and 3) at higher-level operations like "sort"
- The hope is that at any level of abstraction, the problem appears smaller/simpler



`Lesson 14 - Understanding` 
------------------------------------------ 
- Frames (from prior lesson) offered no way to disambiguate similar meaning
- World offers a lot of data- and we use stories to help structure this data
- In order to disambiguate sentences with the same word but different meanings (killed 25 proposals, killed 25 people) - we need background knowledge and some ability to diambiguate
- 3 types of analysis: 1) lexical (categorize words in noun/verb) , 2) syntactical (categorize by structure- noun or verb phrase) and 3) semantic - meaning of each word
- Semantic analysis is the one that allows questions to be asked and inferences to be made (KBAI focuses on semantic analysis)
- lexical and syntactical serve/support semantic analysis

- `Thematic Role System` (TRS) - the relationship of various words in a sentence. Each word takes on a thematic role (agent, verb, object, beneficiary, instrument etc..)
- TRS is a frame system that represents actions identified by the verb - it keys off the verb and will then generate expectations of other roles needed
- `Constraints` - used for prepositions or verbs - we know the word `by` refers to either an agent, conveyance, or location
- Constraints don't always determine exact role of words, we use additional knowledge (ontology) to find exact meanings.
- Ontology Hierarchy - conceptualization of the world that helps key in on exact roles of words. they are categorizations that become the vocabulary of knolwedge of the world
- Understanding starts with bottom-up processing (categorizing words: verb, noun etc..) - that leads to queries in memory triggering top-down (using constraitns and ontology)

- Limitations of Semantic Analysis - as we get more and more variations of sentences - difficult to cover all variations (12 different meanings of verb "take" )
- Constraints helps us resolve most cases (good heuristic)



`Lesson 15 - Common Sense Reasoning` (CSR)
------------------------------------------ 
- CSR about making common sense reasoning in the world by interpreting from formal structures
- We have to disambiguate both: 1) multiple meanings of the same word ("ate") and 2) multiple words with the same meanings("ate", "consumed" "ingested)

- `Primitive Actions` - map different words with same meaning to a combined usage   ate/devoured/ingested ==> Ingest (primitive)
- Power of primitives - we specify a small number of primitives to represent a large number of stories
- Primitive actions serve as an ontology (conecptualization of the world) of actions
- Each primitive has a frame associated.
- Sometimes a sentence maps into two frames - this is the "theory of humor". It's possible to even select the wrong frame, but we would soon find out from story (prior sentence or sentence after)
- Some primitives may capture sentence in a very natural/intuitive sense, while others may are more difficult to map and may involve more effort (process of selecting a frame not always linear)

- `Implied Action ` - change original word in sentence to better map to primitive
- "John fertilized the field" ==> "John put fertilizer on the field"   (put => move-object primitive)
- Possible to map multiple implied actions from single sentence -a nd would need multiple surrounding sentences (story understanding) to disambiguate)

- `Actions/subactions` - Primitives can be decomposed into smaller stories. "Ashok put the wedge on the block" - subactions are closing fingers, and unclosing fingers
- As implied action and subactions show, CSR is about making inferences that are not necessarily pare of the input sentence

-State change frames - let us predict effect/cause of events. (Ie.. Networked frames where result => Ashok's mood is happy )
- which verb to key state change off depends on precise rules that put value into slots

-When we can't find what primitive to use - we can use a `generic primitive` like `do` 


`Lesson 16 - Scripts`
------------------------------------------ 
- Knowledge representation that lets us make sense of discourse, stories, and scenes (culmination of frames and understanding
- Have to use `stories` which allow us to make connections between seemingly disparate things (agent must make causal connections, and generate expectations in order to infer and answer questions


- Script -  a `causally` `coherent` set of `events`
- `Causally` - each event sets off or causes the next event. `Coherent` - causal connections make sense in the world. `Events` - primarily actions,scenes or observable events in the world
- Stories don't come in perfect order, it's up to the agent to make sense/inferences

-Parts of script: 1) entry - conditions necessary to execute script, 2)result - conditions true after script 3) props - obj involved in execution 4) roles - agents involved 5)track - variation/subclasses of particular script 6)scenes - sequence of events during execution
- Each part of the script is a slot in the script frame
-  Script is a large molecule representation
- We capture what is known about a stereotypical situation for a particular scene (ie..this may vary based on restaurant or culture involved )

-Instantiating script - we have a general/abstract script that gets instantiated when appropriate (ie.. agent instantiates script when entering restaurant)
- Script is an example of ak nowledge structure composed of other knowledge structures - scripts composed of frames, and frames composed of primitives
- Scripts generate expectations that allow us to make sense of the world (and generate more expectations)

- Theory of surprise - 1)things don't happen way we expect or 2)things happen in way we're not expecting
- Creativity is involved here if there is a novle, useful/valuable, or unexpected/surprising event
- `Form vs Content` - form of a script tells overall prototype , while content is the specific instantiation of script

- `Tracks` - variations of a particular script (similar to concept hierarchy). It is a semantic hierarchy of concepts.
- Restaurant is tope node - cafe, fast food, casual, fine dining are all variables of the restaurant script. 
- agent walks down hierarchy depending on conditions - first invoking restaurant script thats then invoking fast food script
- Becomes a classification problem ==> agent has very large # of scripts and has to find one that is most useful for the current situation

- MEA and planning generate a plan at runtime (using initial state and goal state) 
- However, Scripts are compiled plans which helps the agent process in a complex environment in near real time. (MEA and planning take a long time)

-Topics that help `learn a script`:
- Semantic Net and Frames are similar. If a script is composed of frames - it's conceivable that SN can be in script
- ICL - agent abstracts a concept from seeing different examples. ICL could develop the difference between fast food, fine dining scripts
- Planning generate a navigation plan (using initial and goal states) - it can transfer this nav plan directly to a script w/o needing to replan route
- CSR - can help agent learn script from primitive actions it understands (make sense of new/novel situations)
- Topics that don't help learn a script: Prod systems - atoms of knowledge instead of molecules like scripts. Learning by recorded cases is just retrieving a case whereas scripts is an abstraction over many cases. Both are too low level of abstraction.


-Topics that help `use a script`:
- Problem Reduction - break script down to smaller scenes - helping catch expectation violations
- Classification - classify which script to use based on percepts
- Logic - put script in formal logic
- understanding - help disambiguate similar events in diff situations
- CBR related in the sense that it and scripts both use memory to supply answer
- Topics not useful to use a script: GnT and MEA - problem solving methods vs scripts. Scripts are already solutions themselves and just need to be executed. CBR is also individual cases whereas scripts are abstractions
- 

`Lesson 17 - Explanation Based Learning` EBL
------------------------------------------ 
- instead of learning new concepts, EBL is about learning connections between existing concepts
- EBL transfers knowledge from old to new situations

-IE.. "Prove an object is a cup"
- How can an AI agent use prior knowledge to build explanation that object is a cup? We have prior knowledge of concepts: brick, briefcase, glass, bowl
- Arrows denote causal connections

-`Abstract and Transfer`: Agent works backward/recursively to prove object is a cup. We know a cup is stable and enables drinking - so we look into memory for examples of stability and drinking
- Abstraction - look for a causal explanation and abstract only the things that are causally related. 
- Abstraction will turn a specific example into a generic example that uses objects.
- Brick abstraction and glass abstraction prove object is a cup. 

-EBL is similar to problem reduction - breaking down into smaller/simpler problems.
- EBL aslo similar to planning - we have open preconditions - 1) object is stable, and 2)obj enables drinking. Preconditions become levers for selecting explanatory proofs

-EBL - use existing concepts by combining them in new ways - this is called `speedup learning` - its a powerful way of dealing with a large nubmer of situations 

- Agent will use the minimum amount of knowledge needed to do proof. Agent opportunistically builds causal proof - it builds the proof it needs baseed on background knowledge it has

