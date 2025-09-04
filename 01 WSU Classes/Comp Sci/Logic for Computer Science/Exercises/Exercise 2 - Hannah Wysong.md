###### Exercise 7 Let L = (V, C, R) with V = {w, y}, C = {d, e} and R = {r, s} where r has arity 1 and s has arity 2. Which of the following are atoms over L? Which are ground atoms? Justify your answers.  
	(a) r(d, e) - false arity of 2
	(b) d(w, w)  - false d is not a predicate 
	(c) s(w, w)  - true arity of 2
	(d) r(y)  - true arity of 1
	There are no ground atoms

###### Exercise 8 Let L = (V, C, R) with V = {x, y}, C = {barack, michelle, craig, sasha} and R =  {motherOf, parentOf, grandmotherOf }, all with arity 2. Which of the Datalog facts (1) to (9) from Example 1.1.1 are atoms over L? Justify your answers  
None of them are atoms over L because there are no predicates for parentOf or grandmotherOf, and all of the motherOf's contain a constant that doesn't exist.

###### Exercise 9 Write a Datalog program which captures the following natural language sentences.  
	1. Luke Skywalker is an orphan. 
	orphan(x)
	2. If a person is an orphan, then all his parents are dead.
	orphan(x) -> parentsDead(x)
	3. Anakin Skywalker is Luke Skywalker’s father. 
	luke(x) -> father(y) ^ anakin(y)
	4. Every orphan is a human being. 
	orphan(x) -> human(x)
	5. Somebody’s mother is also that person’s parent.
	motherOf(x, y) -> parentOf(x, y)
###### Exercise 10 Give three distinct Herbrand interpretations for the following Datalog program, where a, b, and c are constants.  
	q(a)               
	q(c)               
	p(b)               
	q(x) → p(x)        
	q(y) ∧ p(y) → r(b) 
I = {q(a), q(c), p(a), r(a)}
I = {q(c), q(a), p(c), r(c)}
I = {q(b), q(c), p(b), r(b)}
###### Exercise 11 Evaluate the following.  
	a) (p(x) ∧ q(x) → r(x))[x/c][x/d] = (p(c) ^ q(c) -> r(c))
	b) (p(x, y, x) ∧ q(x, y, y) ∧ r(y, y) → t(x))[x/a, y/b] = (p(a, b, a) ^ q(a, b, b) ^ r(y, y) -> t(a))
	c) (p(x, x) ∧ q(x, y) → p(x, y))[y/b][y/c][x/b] = (p(b, b) ^ q(b, b) -> p(b, b))
	d) (q(a, x) ∧ p(x, y) ∧ q(y, a) → r(y))[x/a][x/b] = (q(a, a) ^ p(a, y) ^ q(y, a) -> r(y))

###### Exercise 12 Indicate which of the substitutions from Exercise 11 are ground substitutions. 
A is a ground substitution 
B is a ground substitution 
C is a ground substitution 
###### Exercise 13 Provide a Herbrand model for the Datalog program from Exercise 10.  


###### Exercise 14 Provide the grounding for the Datalog program from Exercise 10.  

###### Exercise 15 Create three distinct Herbrand models for the Datalog program P that contains the  following rules.  
	p(a, b)       
	q(c)          
	q(d)          
	p(x, y) → q(x)