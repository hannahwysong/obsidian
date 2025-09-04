Class: [[Comparative Languages]]
Date: 09-04-2025
Topics: #scheme #racket #dotted-pairs 

Dotted Pairs 
- '() - means a list
- - lists are immutable
Vector 
- sequences like strings that can contain any element 
	- #() 
- access two parts of a dotted pair with accessors car and cdr 
- dotted pairs can be nested 
	- the car of a pair is a value 
	- the cdr of a pair is a value 
	
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
- car of a pair is a value, the car for a list is a value
- cdr of a pair is a vlue, the cdr for a list is a list
Equivalence 
(eg item item) checks the equivalence of two items 
- are the two variables bound/ pointing to the same object
- equal? - recursively performs eq> on each entry in a list