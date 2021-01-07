# Artificial Intelligence Part II

## Logical Agents
### The Knowledge-Based Approach
- Agents that *know*
	- achieve competence by being told new knowledge or by learning.
	- achieve adaptability by updating their knowledge.
	- *Knowledge Representation* = syntax + semantics
- Agents that *reason*
	- use knowledge to deduce the course of action.
	- *Knowledge Inference*: sentence entails sentence, fact follows a fact.

### Knowledge-Based Agents (example of a Knowledge-Based-System)
- Knowledge Base (KB): Set of Sentences (Sentence = Representation of a Fact/Rule).
- Adding & Querying Knowledge
	- *TELL*: add a sentence to the KB
	- *ASK*: retrieve knowledge from the KB
		- Answers must *follow* from what has been *TELL*-ed.
- Inference Mechanism: Determines what follows from the KB.
- Knowledge Based System
	- States: Instances of the KB
	- Operators: Add/Infer a New Sentence
	- Goal: Answer a Query

### Knowledge-Based System
- States:
	- Instances of Knowledge Base
	- Defined by Sets of sentences (facts and rules)
- Operators:
	- Add-TELL
	- Infer-ASK
- Goal: Answer a query (ASK)
- Components:
	- **Rule base** - contains facts and rules.
	- **Reasoning mechanism** – the derivation of new knowledge from existing facts and rules in the KBS.


### Levels of Knowledge
- Epistemological Level: Declarative description of knowledge.
	- e.g. facts: "there is smoke", rules: "if there is smoke, there is fire"
- Logical Level: Logical encoding of knowledge (into sentences).
	- e.g. facts: Smoke, rules: Implies(Smoke, Fire)
- Implementation Level: Physical representation of knowledge.
	- e.g. Strings, 2-D Arrays etc.

### Knowledge Representation
- The KB (set of sentences) needs to be expressed in a computer-tractable form.
- The KR language must be expressive, concise, unambiguous, context-independent & effective.
- KR Language split into:
	- **Syntax** - *Grammatical Validity*. A set of rules for writing sentences. Implementation level.
	- **Semantics** - *Meaning, Sense*. A set of rules (or constraints) for relating sentences to real-world facts.

#### Knowledge Representation Languages
- Formal (programming) languages
	- Good at describing algorithms and data structures
	- Poor at representing incomplete / uncertain information
	- -> not expressive enough
- Natural languages
	- Very expressive (too much, thus very complex)
	- More appropriate for communication than representation
	- Suffer from ambiguity


#### Implication and Consequence
- Implication, logical Inference
	- **X &rArr; Y**
	- **&rarr;** in most notations
	- Expresses truth-functional conditional between formulas A and B.
	- *"X implies Y"*
- Syntactic consequence
	- **X &#8866; Y**
	- Expresses consequence relations between formal sentences 'X' and 'Y', not the formulas.
	- *"Y follows from X in the current proof-system"*
		- Existence of proof from X to Y: "In some relevant deductive system, there is a proof from *premise* **X** to the *conclusion* **Y**"".
- Semantic consequence
	- **X &#8872; Y**
	- Like syntactic consequence, expresses consequence relations between formal sentences 'X' and 'Y', not the formulas.
	- *"Y follows from X"*
		- "On every possible interpretation, if X comes true, so does Y"
		- **X &rArr; (&rarr;) Y** is valid (true in all interpretations).
- Implication vs Consequence
	- **&rArr; (&rarr;)** is a logic symbol that connects 2 logic formulas.
	- **&#8866;** and **&#8872;** are metalinguistic claims about relationship between sentences 'X' and 'Y'.
- For sound logic: if **X &#8866; Y**, **X &#8872; Y**
- For complete logic: if **X &#8872; Y**, **X &#8866; Y**
- For sound and complete logic: **X &#8866; Y** is equivalent to **X &#8872; Y**



### Reasoning & Logic
- Logic = Representation + Inference
- Representation = Syntax + Semantics
- Inference (Reasoning) - Generation of new sentences (true or not true) from existing ones.
	- Entailment - Generation of true sentences, given that the existing sentences are true.
		- Notation: **KB &#8872; &alpha;**
	- Sentence entails sentence, fact follows a fact.

### Inference (Reasoning):

#### Properties of Inference:
- **Soundness**: An inference algorithm is sound if it derives only sentences that are entailed by the KB.
- **Completeness**: An inference algorithm is complete if it can derive any sentence that is entailed by the KB.
- **Proof Theory**:
	- Specifies a Reasoning process that we operate, a set of rules.
			- MP is a proof procedure. It is sound, but incomplete.
	- e.g. Truth table
	- Proof theory must implement sound inference, which may or may not be complete.
	- Specifies the reasoning operations that are sound. A set of rules for deducing the entailments of sentences.
	- A complete proof theory means that all entailed (true sentences) can be derived.


#### Deductive Inference:

> X &rArr; (&rarr;) Y, X &#8866; Y

- Sound.
- *Modus Ponens*.


#### Inductive Inference:

> X &rArr; (&rarr;) Y, Y &#8866; X

- Not sound.
- Generalisation.

### Different Logics
- **Propositional Logic (Sentential):**
	- Symbols represent propositions (facts).
	- Boolean connectives combine symbols.


- **First-Order Logic (Predicate):**
	- Objects and predicates (unary, binary or n-ary) represent properties of and relations between objects.
	- Variables, boolean connectives and quantifiers.


- **Temporal Logic: Logic of time**
	- Temporal logic extends normal propositional logic.
	- 1 Option:
		- Ordering and scheduling of events. Which comes first.
	- 2 Option:
		- *Quantification over time*.
		- Statements like “φ always holds” or “eventually α will hold and then later β will hold”.
		- At its heart, temporal logic is a kind of *modal logic*. Essentially, this just means it introduces two particular quantifiers often written as □ and **◇**:
	 		- □φ means “φ is always true”
	 		- **◇** φ means “φ will eventually be true”


- **Probabilistic & Fuzzy Logic:**
	- Degrees of **belief** and **truth** in sentences.
	- Probabilistic (belief): “Today will be sunny” with a belief degree 0.7.
	- Fuzzy (truth): "Washington is a large city" with truth degree 0.6.


- **Propositional (Sentential) vs First Order (Predicate) Logic**:
	- Propositional: Simple logic of from A &or; B &and; C
	- First Order: Propositional++
		- individual objects
		- quantifiers
		- symbols for predicates (functions and relations)

## Propositional (sentential) Logic
- **Symbols:**
	- Logical Constants: TRUE, FALSE
	- Propositional Symbols: P, Q, R etc.
	- Logical Connectives: &not;, &and;, &or;,  &rArr;, &hArr; (&rarr; and &harr; in german notation)
	- Parentheses: ( )
- **Sentences:**
	- Atomic sentences combined with connectives or wrapped in parentheses.

### Validity & Inference
- Validity of a sentence can be tested using a *truth table*
- **Truth table**
	- checks all possible configurations.
	- Can check Soundness of inference for *Premises &rArr; (&rarr;) Conclusion*.
	- Complete proof theory for propositional logic
	- Not scalable

### Model
- Model - a world in which a sentence is true under a particular interpretation.
- **As a mathematical object**:
	- A mapping from propositional symbols to truth-values.

### Inference Rules
**Implication-Elimination or** ***Modus Ponens***:
> &alpha; &rArr; &beta;,&nbsp; &alpha; &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &beta;

**And-Elimination:**
> &alpha;<sub>1</sub> &and; &alpha;<sub>2</sub> &and; &alpha;<sub>3</sub> &and; ... &alpha;<sub>n</sub> &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha;<sub>i</sub>

**And-Introduction:**
> &alpha;<sub>1</sub>, &alpha;<sub>2</sub>, &alpha;<sub>3</sub>, ... &alpha;<sub>n</sub> &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha;<sub>1</sub> &and; &alpha;<sub>2</sub> &and; &alpha;<sub>3</sub> &and; ... &alpha;<sub>n</sub>

**Or-Introduction:**
> &alpha;<sub>i</sub> &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha;<sub>1</sub> &or; &alpha;<sub>2</sub> &or; &alpha;<sub>3</sub> &or; ... &alpha;<sub>n</sub>

**Double-Negation-Elimination:**
> &not;&not;&alpha; &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha;

**Unit Resolution:**
> &alpha; &or; &beta;,&nbsp; &not;&beta; &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha;

**Disjunctive Resolution:**
> &alpha; &or; &beta;,&nbsp; &not;&beta; &or; &gamma; &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &alpha; &or; &gamma;

**Implicative Resolution:**
> &not;&alpha; &rArr; &beta;,&nbsp; &beta; &rArr; &gamma; &nbsp;&nbsp; &#8872; &nbsp;&nbsp; &not;&alpha; &rArr; &gamma;

### Equivalence Rules
**Associativity:**
> &alpha; &and; (&beta; &and; &gamma;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; (&alpha; &and; &beta;) &and; &gamma;

> &alpha; &or; (&beta; &or; &gamma;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; (&alpha; &or; &beta;) &or; &gamma;

**Distributivity:**
> &alpha; &and; (&beta; &or; &gamma;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; (&alpha; &and; &beta;) &or; (&alpha; &and; &gamma;)

> &alpha; &or; (&beta; &and; &gamma;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; (&alpha; &or; &beta;) &and; (&alpha; &or; &gamma;)

**De Morgan's Law:**
> &not;(&alpha; &or; &beta;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; &not;&alpha; &and; &not;&beta;

> &not;(&alpha; &and; &beta;) &nbsp;&nbsp; &hArr; &nbsp;&nbsp; &not;&alpha; &or; &not;&beta;

**Conjunctive Normal Form:**
> A &rArr; B &nbsp;&nbsp; &hArr; &nbsp;&nbsp; &not;A &or; B

> A &hArr; B &nbsp;&nbsp; &hArr; &nbsp;&nbsp; (&not;A &or; B) &and; (A &or; &not;B)

### Complexity of Inference
- Proof by truth-table is complete but has exponential time complexity.
- Inferring new sentences using various inference rules and proving thus is more efficient.
- Using a logic programming language like ***Prolog***, inference can be achieved in polynomial time complexity.

#### Prolog
- Backward Reasoning (goal-directed)
- *Horn Clauses* + *Modus Ponens*
- AND-OR tree Search
- Polynomial time complexity

#### Horn Clauses
- **A disjunction of literals with at most one unnegated literal**.
	- Definite Clause:
		- &not;P &or; &not;Q &or; ... &or; &not;T &or; U
		- P &and; Q &and; ... &and; T &rArr; U
	- Fact: U

### Limits of Propositional Logic
Propositional logic is a **weak logic**.

- Too many propositions to TELL the KB. Results in increased time complexity of inference.
- Handling changes in the environment is difficult.
- e.g. facts and rules for each position on the board, each point in time etc.

## First Order Logic
- In first-order logic, the world is seen as objects with properties (about each object) and relations (between objects).
- **Sentences** are built from quantifiers, predicate symbols and terms.
- **Constant Symbols** refer to the *name* of particular objects. e.g. `John`.
- **Predicate Symbols** refer to particular relations on objects. e.g. `Brother(John, Richard)` → T or F.
- **Function Symbols** refer to functional relations on objects. e.g. `BrotherOf(John)` → a person.
- **Variables** refer to any object of the world and can be substituted by a constant symbol. e.g. x, y.
- **Terms** are logical expressions referring to objects that may include function symbols, constant symbols and variables. e.g. `LeftLegOf(John)` to refer to the leg without naming it.

#### Usage
- A very powerful KR scheme
- Universal language
	- Can express anything that can be programmed
- More powerful proposals still debated
- Less powerful schemes too limited

#### Propositional vs First-Order logic
- Propositional Logic only supports rules for distinct objects, but not for object classes.
- FOL allows Generalisations and abstractions.
- Aristotle's syllogism: Socrates is a man. All mean are mortal. Therefore Socrates is mortal.
	- Propositional would create following statements:
		- SocratesMan, Man &rarr; Mortal
		- MortalSocrates can not be proven.


### Sentences in FOL
- **Atomic Sentences**
	- state facts using terms and predicate symbols
		- e.g. `Brother(Richard, John)`
	- can have complex terms as arguments
		- e.g. `Married(FatherOf(John), MotherOf(Richard))`
	- have a truth value
- **Complex Sentences** combine sentences with connectives identical to propositional logic.

### Quantifiers
#### Universal Quantifier &forall;
- Express properties about a collection of objects.
- Applies to every object in the collection.
- e.g. &forall;x, King(x) &rArr; Mortal(x)
- &rArr; is the natural connective to use with &forall;.

#### Existential Quantifier &exist;
- Express properties of one or more particular objects in a collection.
- e.g. &exist;x, P(x) &and; Q(x)
- &and; is the natural connective to use with &exist;.

#### Connections between Quantifiers
> &forall;x P(x) &nbsp; &hArr; &nbsp; &not;&exist;x &not;P(x)

> &forall;x &not;P(x) &nbsp; &hArr; &nbsp; &not;&exist;x P(x)

> &not;&forall;x P(x) &nbsp; &hArr; &nbsp; &exist;x &not;P(x)

> &not;&forall;x &not;P(x) &nbsp; &hArr; &nbsp; &exist;x P(x)

#### Ordering
- Semantics depends on the ordering of the quantifiers if more than one is used.
- **∀x** Person(x) &rArr; **∃y** Parent(y, x)
	- "Every person has a parent".
- **∃y**, **∀x** Person(x) &rArr; Parent(y,x)
	- "There is someone who is everybody's parent"

### Equality Predicate Symbol
- States that two terms refer to the same object.
	- e.g. Father(John) = Henry
	- e.g. =(Father(John), Henry)
- Useful to define properties.
	- ∃x,y Brother(x, KingJohn) &and; Brother(y, KingJohn) &and; ¬(x=y)

### Well-formed formula(WFF)
– Sentences with all variables properly quantified


### Higher-order Logics
#### Zeroth-order Logic
- Propositional Logic
- Only objects, no quantifiers, no variables

#### First-order Logics
- Predicate Logic
- Quantifiers over objects, relations

#### Second-order Logics
- Quantifiers over relations
- e.g. “2 objects are equal iff all properties are equivalent”
	- ∀ x,y Equal(x, y) ⇔ (∀ p p(x)=p(y))
- e.g. “2 functions are equal iff they have the same value for all args”:
	- ∀ f,g (f=g) ⇔ (∀x f(x)=g(x))
- Problem: inference procedures not well understood.

### Using First-Order Logic
- The *knowledge domain* is the part of the world we want to express knowledge about.
- The **facts** and **rules** are fed into the KB.
- TELLing the KB:
	- i.e. Assertion (add a sentence to the KB)
	- e.g. TELL(KB, &forall;x,y MotherOf(x)=y &hArr; Parent(x,y) &and; Female(y))
- ASKing the KB:
	- i.e. Query (retrieve/infer a sentence from the KB)
	- Yes/No Answer
		- e.g. ASK(KB, Grandparent(Elizabeth, William))
	- Binding List or *Substitution*
		- e.g. ASK(KB, &exist;x Child(William, x)) yields {x / Charles}
- Knowledge-based agents need to use goals in conjunction with knowledge to make plans.

## Inference in First-Order Logic

### Steps in Proof Procedure
- Comprehension of problem statement in NL
- Translation NL to FOL
- Apply Inference steps

### Inference Rules w/ Quantifiers
- Propositional logic rules
- Substitutions
- Universal and Existential Elimination

#### Substitutions
- SUBST(&theta;, &alpha;): binding list &theta; is applied to a sentence &alpha;.
	- e.g. SUBST({x / John, y / Richard}, Brother(x, y)) = Brother(John, Richard)

#### Additional Inference Rules
**Universal Elimination:**
> &forall;x &alpha; &#8872; SUBST({x / g}, &alpha;) &nbsp;&nbsp;&nbsp; where `g` is a ground term

**Existential Elimination:**
> &exist;x &alpha; &#8872; SUBST({x / K}, &alpha;) &nbsp;&nbsp;&nbsp; where `K` is a Skolem constant

**Existential Introduction:**
> &alpha; &#8872; &exist;x SUBST({x / g}, &alpha;) &nbsp;&nbsp;&nbsp; where `g` is a ground term

#### Skolemization
Existential quantifiers (&exist;) can be eliminated by replacing the corresponding variable with a Skolem function. The arguments of a Skolem function include all the universally quantified variables that are bound by universal quantifiers whose scopes include the scope of the existential quantifier being eliminated. If a Skolem function has no arguments, it's known as a Skolem constant.

- &forall;x &exist;y P(x, y) becomes &forall;x P(x, S(x))
- &exist;y &forall;x P(x, y) becomes &forall;x P(x, S)
- &exist;y P(y) becomes P(S)

### Unification
- Find a substitution that makes two atomic sentences identical.
- i.e. UNIFY(&alpha;, &beta;) = &theta; where SUBST(&theta;, &alpha;) = SUBST(&theta;, &beta;)

#### Most General Unifier (MGU)
- Unifying yields an infinite number of substitutions.
- The **MGU is a unifier that makes the least commitments** about the bindings of the variables. UNIFY always returns the MGU.

#### Composition of Substitutions
- SUBST(Compose(&theta;<sub>1</sub>, &theta;<sub>2</sub>), &alpha;) = SUBST(&theta;<sub>2</sub>, SUBST(&theta;<sub>1</sub>, &alpha;))
- e.g:
	- α = Knows(x,y)
	- θ1 = {x/John}
	- θ2 = {y/ Elizabeth}
	- Subst(θ2,Subst(θ1 ,α)) =
	Subst(θ2,Knows(John,y)) =
	Subst( {x/John,y/Elizabeth}, Knows(x,y)) = Knows(John,Elizabeth)

### Proof as a Search Problem
- Proof procedure:
 	- A sequence of inference rules applied to the KB.
- Search Problem Formulation:
	-	Initial state: KB
	- Operators: Applicable inference rules
	- Goal State: KB w/ Goal
- Branching factor increases as the KB grows.

### Generalised Modus Ponens (GMP)
**Universal-Elimination + And-Introduction + Modus Ponens**

**Example:**<br>
Missile(M1),<br>
Owns(Nono, M1),<br>
&forall;x Missile(x) &and; Owns(Nono, x) &rArr; Sells(West, Nono, x)<br>
&#8872; Sells(West, Nono, M1)

> &gamma;<sub>1</sub>, &gamma;<sub>2</sub>,...,&gamma;<sub>n</sub>, (&alpha;<sub>1</sub> &and; &alpha;<sub>2</sub> &and; ... &and; &alpha;<sub>n</sub> &rArr; &beta;) &#8872; SUBST(&theta;, &beta;)
> where &forall;i SUBST(&theta;, &gamma;<sub>i</sub>) = SUBST(&theta;, &alpha;<sub>i</sub>)

Every fact (&gamma;<sub>i</sub>) must have a corresponding antecedent (&alpha;<sub>i</sub>) in the rule for GMP.

### Forward & Backward Chaining

#### Forward Chaining (event-directed)
- If *< Premise >* then *< Conclusion >*
- **KB, &beta; &#8866; ?**.
- Given a KB and a newly added event &beta;, generate new sentences using *Modus Ponens* or *Resolution inference rule*

#### Backward Chaining (goal-directed)
- *< Conclusion >* if *< Premise >*
- **KB &#8866; &beta;?**.
- "Prolog Horn clauses"
- Start with a sentence not in the KB and attempt to establish
its premises, e.g. to prove some new fact.

#### Forward Chaining
**Idea:** Inferring new consequences.

**Pseudo Algorithm**

1. TELLing a new sentence &alpha;.
2. If &alpha; is already in the KB, do nothing.
3. Find all the implications that have &alpha; as a premise, i.e. &alpha; &and; &alpha;<sub>1</sub> &and; ... &and; &alpha;<sub>n</sub> &rArr; &beta;.
4. Then, if all the other premises &alpha;<sub>i</sub> are known under some MGU &theta;, infer the conclusion &beta; under &theta;.
5. If some premises &alpha;<sub>i</sub> can be matched several ways, then infer each corresponding conclusion.
	- Branching

**Using Forward Chaining**

1. Given a KB, derive all the facts and rules.
2. If there are facts with &exist;, skolemize them and derive the new facts.
3. Use GMP to satisfy the rules and derive new facts recursively until the goal is reached.

#### Backward Chaining
**Idea:** Checking for causes.

**Pseudo Algorithm**

1. ASKing a query &beta;.
2. If &beta; is already in the KB, proof immediate.
3. Else, find all implications that have &beta; as a conclusion, i.e. &alpha;<sub>1</sub> &and; &alpha;<sub>2</sub> &and; ... &and; &alpha;<sub>n</sub> &rArr; &beta;.
4. Then, try and establish all the premises &alpha;<sub>i</sub> and infer &beta;.

**Using Backward Chaining**

1. Given a KB, derive all the facts and rules.
2. If there are facts with &exist;, skolemize them and derive the new facts.
3. Derive a unifying list that satisfies the goal &beta;.

### Normal Forms

#### Conjunctive Normal Form (CNF):
- (&not; A &or; B) &and; (B &or; &not; C) &and; ... &and; D.

#### Disjunctive Normal Form (DNF):
- (&not; A &and; B) &or; (B &and; &not; C) &or; ... &or; D.

#### Implicative Normal Form (INF):
- Examples:
	- A &and; B &and; C &rarr; D &or; E &or; F
	- true &rarr; A &or; B &or; C
	- A &and; B &and; C &rarr; false

#### Conversion from INF to DNF
> A &and; B &and; C &rArr; D &or; E &or; F &nbsp;&nbsp; &hArr; &nbsp;&nbsp;
&not;A &or; &not;B &or; &not;C &or; D &or; E &or; F

#### Conjunctive Knowledge Base:
- All sentences are joined in one big, implicit conjunction.

#### Converting FOL to Normal Form
1. Eliminate implications by converting them to CNF.
2. Reduce the scope of negations using De Morgan's laws. e.g. &not;(A &or; B) becomes &not;A &and; &not;B.
3. Standardise sentences apart by renaming variables.
4. Move quantifiers to the left.
5. Remove existential quantifiers using skolemization.
6. Drop the universal quantifiers.
7. Distribute conjunctions (&and;) over disjunctions (&or;). e.g. (P &and; Q) &or; R becomes (P &or; R) &and; (Q &and; R).
8. Flatten nested conjunctions and disjunctions. e.g. (P &or; Q) &or; R becomes P &or; Q &or; R.
9. Convert disjunctions back to implications.

### Generalised Resolution
- **Complete and sound!**
- The Completeness comes from ***Refutation***
- Uses NF. CNF for Resolution, INF for Modus Ponens
- Can use several strategies (heuristics) to improve efficiency and reduce the size of the search space.

#### Generalised Resolution for Normal formulas
#### CNF
- A &or; ¬B &or; **X**, **¬X** &or; C  |– A &or; ¬B &or; C

#### INF
- A &and; E &rArr; **X**, **X** &rArr; C |– A &and; E &rArr; C

#### Refutation
- Resolution by refutation is proof by contradiction.
	- To prove *P* to be true, assume it to be false and assert *&not;P* as a new fact.
	- Infer new sentences using Resolution on *KB,&not;P*.
	- If a contradiction is found, *P* is true.
- Resolution by refutation is simple, sound and complete.
- Resolution with refutation is guaranteed to find a solution.

##### Resolution Strategies
- **P2: Unit Preference**: Favour short sentences (fewer terms, even unit clauses, if possible).
- Set of Support: Define a subset of the KB and use those sentences only.
- **P1: Input Resolution**: Combine KB sentences to the inferred sentence (use asserted refutation as the first clause).
- Subsumption: Eliminate all sentences subsumed (more specific than) existing sentences in the KB. e.g. P(A) is not needed if P(x) is present.

### Generalised Modus Ponens vs. Generalised Resolution
- GMP is not complete while GR is complete.
- GMP uses unification to provide a powerful inference rule while GR uses refutation to prove.
- GMP uses sentences in Horn form while GR uses sentences in either CNF or INF.
- GMP can be either data-driven or goal-oriented.
- GR can use several strategies (heuristics) to improve efficiency and reduce the size of the search space.

## Logical Reasoning Systems
### Forward Chaining Production Systems
- **Forward Chaining System**
	- All clauses represented as Horn clauses.
	- Assertions instead of queries. Inference generates new knowledge until a criterion is met.
	- Appropriate for condition-action rules.
	- Theorem provers too generic and can result in huge branching factor.
- **Typical Features**
	- Rule Memory (KB) - Sentences, Rules
	- Working Memory (WM) - Positive Literals w/ No Variables, Facts
	- 3-Step Inference (Matching, Conflict Resolution, Acting)

#### Using Production Systems
- Modular Systems - Inference Engine + Domain Specific KB
- Expert Systems
- Cognitive Architectures - Models human reasoning.

#### Conflict Resolution
- Which of the matching rules should be fired first?
- **None:** Execute systematically all rules.
- **No duplication:** Do not execute the same rule on the same arguments twice.
- **Recency:** Favour rules that refer to elements recently created in the WM.
- **Specificity:** Favour rules that are more specific i.e. have more constraints.
- **Operation Priority:** Favour rules that yield high-priority actions.

#### KBS Structure
- Rule base – Long-Term-Memory (*same rules apply*, hehe)
- Facts – Working Memory
- Rule Conflict – Meta Rules for ordering
- Inference – forward and backward reasoning

## Building Knowledge-Based Agents
- **Knowledge Representation:**
	- Logic-based (propositional logic, FOL etc.)
	- Graphic-based (frames, semantic networks, etc.).
- **Knowledge Inference (Reasoning):**
	- Inference Rules: Modus Ponens, Resolution
	- Handling Changes: Truth Maintenance Systems
	- Handling Uncertainty: Probabilistic and Fuzzy logics
- **Knowledge Engineering:**
	- Acquiring Knowledge
	- Building the KB.

### Acquiring Knowledge
- Domain Expert
	- Knows about the domain.
	- Knows nothing about the knowledge-based system or logic.
- Knowledge Engineer
	- Knows little or nothing about the domain.
	- Knows how to use knowledge representation language.
- Knowledge Acquisition
	- via interviews, examples etc.
	- Build a clear, effective & correct KB.
	- Computational tools available to extract a KB from data.

### Building the KB
- Decide what to talk about. What are the important concepts/relations?
	- e.g. Man, Woman, Age, Young, Old, Mortal
- Decide what vocabulary to use. Translate important domain concepts into logical names.
	- e.g. YoungMan or separate Young and Man
- Encode general domain knowledge. Translate known relations and rules into logical axioms.
	- e.g. Man(x) ⇒ Mortal(x), Old(y) ⇒ ¬Young(y)
- Encode specific domain knowledge. Translate known facts into logical atomic sentences.
	- e.g. Man(Socrates), Old(Plato), ...

## Fuzzy Logic

### Fuzzy Sets

- **A = {( x, μ<sub>A</sub>(x))| x ∈ X }**, with
	- A being a *Fuzzy set*
	- μ<sub>A</sub>(x) - a *Membership Function* (MF)
	- X - *Universe of discourse*.


- e.g. Fuzzy set C = “desirable city to live in”:
	- X = {SF, Boston, LA} (discrete and nonordered)
	- C = {(SF, 0.9), (Boston, 0.8), (LA, 0.6)}


- Universes can be discrete or continuous

#### Partitioning
- Non-Pseudo Partitioning
 	- Summation of MFs:  ∑μ(X)) ≠ 1
- Pseudo Partitioning
 	- Summation of MFs:  ∑μ(X)) = 1

### Member Function
#### MF Terminology
- Core (MF=1)
- Crossover points (MF=0.5)
- &alpha;-cut (MF&ge;&alpha;)
- Support (MF>0)

#### Set-Theoretic Operations
- Subset:
	- A ⊆ B ⇔ μ<sub>A</sub> ≤ μ<sub>B</sub>
- Complement:
	- A = X − A ⇔ μ<sub>A</sub>(x) = 1 − μ<sub>A</sub>(x)
- Union: (OR - Disjunction)
	- C = A∪B ⇔ μ<sub>c</sub> (x) = max(μ<sub>A</sub>(x), μ<sub>B</sub> (x))
- Intersection: (AND – Conjunction)
	- C = A∩B ⇔ μc (x) = min(μ<sub>A</sub>(x), μ<sub>B</sub>(x))


### Fuzzy Rule Base Systems (FRBS)
#### Operation
1. **Measurements** are taken of all variables from the process.
2. **Fuzzification**: measurements are converted into appropriate fuzzy sets to express measurement uncertainties.
3. **Fuzzy inference engine** uses the fuzzified measurements to evaluate the control rules stored in the **fuzzy rule base**.
4. **Defuzzification**: The result of the evaluation in Step 3 is one or several fuzzy sets representing possible control actions. These set are then converted into a single value or a vector of values which is used to control the process.

#### Steps in Fuzzy Inference
- Fuzzify inputs: Resolve all linguistic values/labels to a degree of membership between 0 and 1
- Apply fuzzy operator if needed: If there are multiple parts to the antecedent, apply fuzzy logic operators and resolve to a single number between 0 and 1.
- Apply implication method.
- Aggregation of the consequents across the rules into a single number [0, 1]
- Defuzzification of the number to an output value

### Fuzzy Neural Networks (FNN)
#### Structure - 5 Layers:
1. Input linguistic layer: Linguistic input nodes
	- Original input
2. Condition layer: Label input nodes (Fuzzy values)
	- Fuzzification
3. Rule layer: Rule nodes
	- Each node forms an if-then fuzzy rule
4. Consequent layer: Label output nodes (Fuzzy values)
	- Rule Outputs
5. Output linguistic layer: Linguistic output node
	- Aggregation, Defuzzification, Result

#### Learning Steps
1. Clustering to form fuzzy labels for input and outputs
2. Learn the rule association weights with Hebbian rule.
3. Rule Pruning:
	1. Keep high weights
	2. Delete zero and low weights links.
4. Back Propagation to fine tune the final Membership Functions for fuzzy labels


- Potentially the rules link the input label nodes with the output
label nodes.
- True learning and also possibility for *re-learning* – self reorganisation
when data distribution shifts or drifts over time.


## Appendix
### Expert System (example of a Knowledge-Based Systems)
#### Idea
- A computer system that emulates the decision-making ability of a human expert.
- Solve complex problems by reasoning through bodies of knowledge, represented mainly as if–then rules rather than through conventional procedural code.
- The goal is to make the critical information explicit rather than implicit.
Clearly defined rules that can be edited by domain experts instead of IT specialist.

#### Characteristics
- Pros:
	- Rapid development and prototyping
	- Ease of debugging and maintenance
- Cons:
	- Knowledge Acquisition
	- Performance (interpreted Languages)
	- Integration with databases and business apps still required Software Engineers.

#### Implementation
- Knowledge Base (facts and rules) + Inference Engine
- Mainly Lisp, Prolog

#### Timeline
- Developed in 70s-80s, among first successful AIs.
- Popularity declined in 90s, Expert Systems migrated from being standalone tools, to being one of many standard tools and parts of bigger Software in Business Logic and AI


### Fuzzy vs Probability
- Probability theory can be expressed as a subtheory of Fuzzy logic.
- On the other hand, fuzzy logic is different in character from probability, so the replacement is unnecessary.


### Hebian Learning
TODO:http://www.cs.bham.ac.uk/~pxt/NC/l5_JB.pdf
#### Hebbian Learning
- A principe according to which biological neurons learn (actually takes place in hippocampus):

> If two neurons on either side of a synapse (connection) are activated simultaneously (i.e. synchronously), then the strength of that synapse is selectively increased.

- Δwij =η.outj.ini

- The rule represents biological situation in the brain.
