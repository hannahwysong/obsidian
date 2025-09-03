Class: [[Comparative Languages]]
Date: 09-02-2025
Topics: #racket #scheme #functional-languages 

Racket 
- Pairs and Lists 
	- everything in function languages are built on lists 
	- dotted pair: compound value made by combining any two arbitrary values in the ordered couple 
Functional Languages 
- a programming paradigm where programs are constructed by applying and comprising functions 
- declarative programming since trees of expressions each return a value, rather than a sequence of imperative statements 
	- evolves from lambda calculus 
-  Racket is a functional language 
	- no iteration - uses recursions instead 
- The basic Racket construct is called a form 
	```(function arg1 arg2 arg3)```
	```(+ 2 5) >> 7```
Substitution Model 
- to evaluate a racket expression 
	- evaluate its operands 
	- evaluate its operator 
- numbers evalue to themselbes 
Varaibles 
- assignments provides an association between symbol and value
	```(define x 3)```
Special Forms
- do not evaluate normally 
	- (define x 3) - don't know the value of x until define is ran
Symbols 
- symbols have two parts, name and value
Arbitrary Data Structure 
- simplest data structure used to create other data structures 
- lists - > linked lists 
Dotted Pairs 
-  uses pairs for many things: 
	-  programs (forms)
	- arguments
	- data structures 
- each pair is a two-cell node aka contains a pointer value to another pair
- node with two pointers is a dotted pair
	```(cons 1 2 ) >> (1 . 2)```
	```'(1 . 2) >> (1 . 2)```
car and cdr 
- access the two parts of a dotted pair with accessors car and cdr: 
	```(define x (cons 1 2))```
	 ```(car x) >> 1```   ```
	 (cdr x) >> 2```
   