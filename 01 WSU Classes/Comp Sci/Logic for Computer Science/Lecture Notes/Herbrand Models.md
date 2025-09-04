Class: [[Logic for Computer Science]]
Date: 09-04-2025
Topics: 

Calculate number of groundings for a rule 
- Number of different constants^(number of distinct variables)

Herbrand Model
- herbrand interpretation I of P is called a herbrand model if the following holds:  
	- for every rule B1^...^Bn -> A in ground(p) with {B1,...,Bn} < I, we also have A∈I 
	- aka if you have all body atoms in interpretation you must also have the head
		- must respect all rules 

```
p(a)
q(a, b)
q(b, c)
p(x) -> r(x)
r(x) ^ q(x, y) -> r(y)
r(x) ^ q(y,x) -> q(x, y)

The following are herbrans models for p
I = {p(a), q(a, b), q(b, c), r(a), r(c), q(c, b), r(b), q(b, a)}
I = {p(a), q(a, b), q(b, c), r(a), r(c), q(c, b), r(b), q(b, a), q(c, c)}
The following is not a herbrand model for p 
I = {p(a), q(a, b), q(b, c), r(a), r(c), q(c, b), r(b), q(b, a), q(a, c)}
``` 

- empty set is a subset of all other sets
- all facts must be included in model 
- if body is satisfied then head must be satisfied 
	- cannot have two sets of the same logical consequences 
- can contain stuff that we don't want as logical consequences 