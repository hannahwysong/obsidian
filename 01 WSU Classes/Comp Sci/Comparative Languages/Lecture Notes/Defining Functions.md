Class: [[Comparative Languages]]
Date: 09-16-2025
Topics: 

(define  x 7)
- global variable 
(define add2 (lambda (x) (+ x 2)))
- x is a local variable in the function definition 
(add2 x) >> 9

- let can be used to introduce local variables 
(let ( [x 1]
	[y 2]
	[z 3])
	list(x y z))

initializers in the let form are not considered part of the let body
local variables can be bound to procedures too 
Scope 
Procedures can access any variable in their scope that they don't shadow 
- scope determined when defined not called