Class: [[Logic for Computer Science]]
Date: 09-09-2025
Topics: 

Given a datalog program P define a function 
T<sub>P</sub> : I<sub>P</sub> -> I<sub>P</sub> : T<sub>P</sub>(I) = {A ∈ B<sub>P</sub> | (B<sub>1</sub> ^ ... ^ B<sub>n</sub> -> A) ∈ ground(P) and B<sub>1</sub> for all i=1,2,...,n}
- takes set of ground atoms and outputs another set of ground atoms
- collect all rule heads for which the body atoms are in the input interpretation 
This function is called the single step operator or immediate consequence operator 
- operator refers to function/ mappings

Example 
	p(a)
	q(a, b)
	q(b, c)
	p (x) -> r(x)
	r(x) ^ q(x, y) -> r(y)
	r(x) ^ q(y, x) -> q(x, y)

Tp(∅) = {p(a), q(a, b) q(b, c)} = I1
- only contains rules without a head aka facts 
Tp(I1) = I1 U {r(a)} = I2
Tp(I2) = I2 U {r(b)} = I3
Tp(I3) = I4
Tp(I4) = I5
Tp(I5) = I5

Tp({r(c), q(c, c)}) ={p(a), q(a, b), q(b, c), r(c), q(c, c)}
- contains the facts
- fire the rules based on the input
	- since there is an r(c) and q(c, c) in the input we get r(c)
	- since there is an r(c) and q(c, c) in the input we get q(c, c)

Tp({p(b)}) = {p(a), q(a, b), q(b, c), r(b)}
- there is a p(b) in the input so we get r(b)
- there is no r(x) in the input so none of the other rules apply

Given a datalog program P and I in Ip, we call I a pre-fixed point of Tp is Tp(I) is a subset of I. We call I a fixed point of Tp if Tp(I) = I
- from set x -> set x, fixed point is any x with f(x) = x
- not changed by the function 
(x1 <) is a partially ordered set then x in x is a prefixed point of fro set x to x, if f(x) <= x
- fixed set has the same input and output
- pre-fixed points have the output as a subset of the input 

Example 
	p(a)
	q(b)
	q(x) -> q(x)

Tp({p(a), q(b)}) = {p(a), q(b)}, which is a fixed point 
Tp(p(a), q(b), p(b)) = {p(a), q(b)} which is a pre-fixed point 

Theorem: 
- Given any datalog program P, the pre-fixed points of P are exactly the Herbrand Models of P
Proof:
- Let I be a pre-fixed point of Tp, i.e, Tp(I) is a subset of I
- Now let B1, ^ ... ^, Bn -> be any rule in ground(P)
	- If the {B1, ^ ... ^, Bn} is in I, then A is in Tp(I) by definition of Tp, and hence A in I because Tp(I) is a subset of I
- Conversely, let I be a Herbrand model for P. Now for any A in Tp(I) there must be a rule B1, ^ ... ^, Bn -> A in ground(P) with {B1, ^ ... ^, Bn} subset in I. Since we know I is a herbrand model. We obtained A in I. Hence Tp(I) is a subet of I. 
Pre-fixed points are Herbrand models

Lemma
- Given any datalog program P and I1 subset of I2 in Ip, we have that Tp(I1) is a subset of Tp(I2)
	- i.e the Tp is monotonic 
Proof 
- For any A in Tp(I) there must be a rule B1, ^ ... ^, Bn -> in ground(P) with {B1, ^ ... ^, Bn} subset of I1, since I1 is a subset of I2 we obtain {B1, ^ ... ^, Bn} subset of I2 and hence A in Tp(I2) as required 
	- for any A in Tp(I2) there is A in Tp(I1) showing its monotonic 