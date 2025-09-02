###### Exercise 1 Specify whether deriving each of the following facts is possible. Utilize (1) to (14) in Example 1.1.1. Justify all solutions.  
(a) Marian is Natasha’s grandmother. 
		True Marian is the mother of Michelle (1) who is the mother of Natasha (7) making Marian her grandmother. 
(b) Craig is Natasha’s uncle.  
		True Craig is the brother of Michelle (2) and Michelle is the mom of Natasha (7) making Craig her uncle.
(c) Clark is male. 
		False we don't know anything about Clark.
###### Exercise 2 Write the following sentences as Datalog rules.  
(a) To be a father, they must be male and have a child.  
		 parentOf(x, y) ^ male(x) - > fatherOf(x, y)
(b) If somebody is the father of a female person, then that female person is the daughter of this father.  
		fatherOf(x, y) ^ female(y) -> daughterOf(y, x) 
(c) If a person is the daughter of somebody’s daughter, then this first person is the granddaughter of this “somebody.”  
		daughterOf(x, y) ^ daughterOf(y, z) -> granddaughterOf(x, z)
###### Exercise 3 Use resources at your disposal to specify a Datalog rule for the following.  
(a) A person’s first cousin.  
		siblingOf(x, y) ^ parent(x, z) ^ parent(y, w) > cousinOf(z, w)
(b) A person’s second cousin, twice removed aka second cousins grandchild
		grandchildOf(x, y) ^ siblingOf(y, z) ^ grandchildOf(w, z) ^ grandchildOf(v, w) -> secCousinTwiceOf(x, v)
###### Exercise 4 In the context of (1) to (14) of Example 1.1.1,  
(a) define sibling hood (i.e., specify the binary relation siblingOf ) and 
		parentOf(x, y) ^ parentOf(x, z) -> siblingOf(y, z)
 (b) specify a rule that asserts that siblingOf is symmetric.
		siblingOf(a, b) -> siblingOf(b, a)
###### Exercise 5 A vertex v in a graph is self-connected if there is a path from v to v in the graph. By extending the Datalog facts and rules from Example 1.1.5, complete the Datalog rule  . . . → sc(x) such that a vertex v is self-connected if and only if sc(v) can be derived. Fully justify your answer.  
vertex(v) ^ edge(v, x) -> path(v, x)
vertex(x) ^ edge(x, v) -> path(x, v)
path(x, v) -> connected(x, v)
path(v, x) -> connected(v, x)		
connected(v, x) ^ connected(x, v) -> sc(v)
connected(x, v) ^ sc(v) -> sc(x)
###### Exercise 6 A vertex v is said to be vain if an edge starts and ends at the same vertex v. Is it the case that sc(v) → vain(v)  
No, a vertex is self connected when there is a path from v to the same vertex. A path is an edge from one vertex to a different vertex. An edge that starts and ends at the same vertex is not a path. 
