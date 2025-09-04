Class: [[Logic for Computer Science]]
Date: 09-02-2025
Topics: #syntax #semantics #datalog #datalog-language 

Datalog Language 
	```L = (V, C, R)```
- finite set of V variables 
- finite non-empty set C of constants 
- finite non-empty R of predicate symbol with an arity  
	- arity is the number of parameters 
Atom 
- is of the following form 
	- p( v, ...), where p is a predicate symbol of arity n 
	- v or n are either constants or variables 
Ground Atom
- all the variables in the atom are constants 

``` 
L constists of constants a, b, of variables x, y, of predicate symbols p of arity 1 and q with arity 2 
the following are examples of atomic formula over L 
p(a) p(b) q(a, b) q(b, b) q(b, x) q(y, y)
Of these, p(a) q(a, b) q(b, b) are ground atoms 
```

Datalog rule
- statement of the form B1 ^ ... ^ Bn -> A1 where B and A are atoms 
- B1^...^Bn is the body of the rule 
	- B1 is called a body atom of the rule 
	- A is called the head of the rule 
- A rule with n=0, ie no body, is called a fact
	- arrow is omitted in this case
Datalog Program
- set of datalog rules 
Herbrand Interpretation 
- given datalog program P over L, is a set of ground atoms over L
-  every set of logical consequences is a herbrand but not every herbrand is 
	- those are referred to as herbrand models 
-  any empty set is still a herbrand interpretation 
- a substitution [x1/c1, .... , xn/cn] where x are variables and the c is a constant 
	- this maps a function
	- maps each datalog rule R
- obtained by replacing all occurrences of x with c
A Ground Rule 
- datalog rule that contains no variables 
	- A substitution for a datalog rule is a ground substitution if it makes all variables into constants
Every ground of r is a set of all ground rules each rule in the datalog program has a ground of r, which is the ground of p
- matches facts with variables
Ground(p) is always finite if the datalog program is finite 
- L by definition has a finite number of constants 
	- if no L then we assume the set C of constants in L is exactly given in the example  