Class: [[Logic for Computer Science]]
Date: 09-10-2025
Topics: 

Given any datalog program P. we iteratively define the following: 
Tp↑0 = {}
Tp↑1 = Tp(Tp↑0)
...
Tp↑(n+1) = Tp(Tp↑Tp↑n)
We further define Tp↑omgea as the union over all natural numbers of Tp↑n
- omega defines all the natural numbers 
The sets Tp↑n are called iterates of the Tp operator 
- Tp↑0 is the empty set
- Tp↑1 is the facts or Tp(Tp↑0)
	- constructs logical consequences
- Eventually results in Tp(n+1) = Tp(Tp↑n)
In = Tp↑n (n=1, ..., 6) which means that Tp↑omega = I5

Theorem 
For every datalog program P the following holds:
- Tp↑omega is a fixed point of Tp
- Tp↑omega is a Herbrand model of P
- For any herbrand model M of P, we have Tp↑omega is a subset of M
	- Tp↑omega is the least herbrand  model of P with respect to set inclusion
	- we get it by exhaustively firing the rules 
- there is always a least herbrand model which is included in the others 
- a datalog program P herbrand entails a ground atom A, written P|=H A, if A is in Tp↑omega 
	- entailment is a synonym of a logical consequence 
	- set of ground atoms entailed by the program
- in this case we also call A a logical consequence of P (under the herbrand semantics)
- 