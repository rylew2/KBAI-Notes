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
