Class: [[Comparative Languages]]
Date: 09-04-2025
Topics: #scheme #racket #dotted-pairs 

To evaluate a Racket Expression:
1. evaluate its operands 
2. evaluate the operator
3. apply the operator to the evaluated operands 
- numbers evaluate to themselves
- primitive procedures (+,-,\*) evaluate to the corresponding procedure 
- (define x 3) associates x with 3

Dotted Pairs 
- '() - means a list
- - lists are immutable
- two-cell node, contains a pointer to a value or another pair
- node with two pointers is called a dotted pair
Vector 
- sequences like strings that can contain any element 
	- #() 
- access two parts of a dotted pair with accessors car and cdr 
- dotted pairs can be nested 
	- the car of a pair is a value - car of a list is a value
		- returns first value of list
	- the cdr of a pair is a value - cdr fo a list is a list
		- returns everything except first value
	
```
define (x (cons (cons 1 2) (cons 3 4)))
define (x '(1 . 2) . (3 . 4))
```
 
 Lists 
 - special construct of nested dotted pairs is called a list 
 - every list is a pair but some pairs can have an empty list 
 - (list 1 2 3 4 5 ) = (cons 1(cons 2 (cons 3 (cons 4 (cons 5 null)))))
	 - produces '(1 2 3 4 5)
- a dot means there is no empty list 

Equivalence 
(eg item item) checks the equivalence of two items 
- are the two variables bound/ pointing to the same object
- equal? - recursively performs eq> on each entry in a list

Forms
Calling Functions
- racket form is a list
	- (function arg1 arg2 arg3)
- you cab define a symbol to be a function
- procesdures are first class variables 
	- can assign to them, pass as parameters and otherwise use them
	- procedures can have multiple parameters 
Three ways to specify parameters: 
1. list of parameters (lambda (a b) ...)
- function expects exactly two arguments 
2. single symbol (lambda a)
- all parameters are collected into a list and assigned to a
1. Dotted pair ("required" . "rest"):
Example 1: (lambda (a b c . d) ...)
- function expects at least 3 arguments
- first 3 are assigned to a b c
- remaining arguments are collected as a list and assigned to d
Example 2: (lambda (x . y) ...)
- first argument is assigned to x and the remaining arguments are collected as a list and assigned to y

Sequencing:
- a function definition calls a single function and returns a single value 
	- aka lambda accepts a single form
	- arguments to the function might be other functions 











