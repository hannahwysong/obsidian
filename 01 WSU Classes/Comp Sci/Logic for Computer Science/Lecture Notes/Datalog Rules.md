Class: [[Logic for Computer Science]]
Date: 08-27-2025
Topics: #binary-function #datalog #datalog-language #CFG #ML

- Binary Function: takes only two arguments
- Data cleaning: is a important step in the machine learning (ML) pipeline as it involves identifying and removing any missing duplicate or irrelevant data
- Datalog is a declarative logic programming language. While it is syntactically a subset of Prolog, Datalog generally uses a bottom-up rather than top-down evaluation model
- Using inference to take implicit and make it explicit
- explicit is overt and obvious, while implicit is covert and inferred. 
- R(x,y) ^ R(y,z) - > R(x,z): transitive relation
- In transitive logic relations, if an element a is related to b, and b is related to c, then a must also be related to c. 
- Datalog language L = (V, C, R) consists of the following.
	• A finite set V of variables: x1, x2, . . . , xn (also y, z, . . . ).
	• A finite non-empty set C of constants: a, b, c, . . .
	• A finite non-empty set R of predicate symbols: p1, p2, . . . (also q, r, . . . ), each with anarity (∈N) (number of parameters).