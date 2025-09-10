Class: [[Logic for Computer Science]]
Date: 09-08-2025
Topics: 

Fixed Point Semantics 

Example: 
	p(a)
	q(a, b)
	q(b, c)
	p (x) -> r(x)
	r(x) ^ q(x, y) -> r(y)
	r(x) ^ q(y, x) -> q(x, y)
	Collect all facts for ground(p)
	I<sub>1</sub> = {p(a), q(a, b), q(b, c)}
	Collect all heads of rules in ground(p) for which all body items are in I1
	I<sub>2</sub> = I1 U {r(a)}
	Iterate with I<sub>2</sub>
	I<sub>3</sub> = I<sub>2</sub> U {r(b)}
	I<sub>4</sub> = I<sub>3</sub> U {r(c), q(b, a)}
	I<sub>5</sub> = I<sub>4</sub> U {q(c, b)}
	I<sub>6</sub> = I<sub>5</sub> U empty set

Given a Datalog program P with underlying language L, let B<sub>p</sub> be the set of all ground atoms over L, called the Herbrand base of P
- all things to consider as possible logical consequences 
Let Ip = 2<sup>Bp</sup> be the power set of B<sub>p</sub>
- aka I<sub>p</sub> is the set of all subsets of B<sub>p</sub>
I<sub>P</sub> is the set of all herbrand interpretations for P 

Given a datalog program P define a function 
T<sub>P</sub> : I<sub>P</sub> -> I<sub>P</sub> : T<sub>P</sub>(I) = {ground atoms ∈ B<sub>P</sub> | (B<sub>1</sub> ^ ... ^ B<sub>n</sub> -> A) ∈ ground(P) and B<sub>1</sub> for all i=1,2,...,n}
- take set of ground atoms 
- collect all rule heads for which the body atoms are in the input interpretation '
This function is called the single step operator or immediate consequence operator 
- operator refers to function/ mappings