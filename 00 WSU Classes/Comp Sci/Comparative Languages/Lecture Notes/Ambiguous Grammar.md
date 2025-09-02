Class: [[Comparative Languages]]
Date: 08-28-2025
Topics: #code #code-language #CFG #ambiguous-language 

Disambiguating a grammar 
- add explicit parentheses 
	- E -> (E-E) | 0 | 1
Example of Ambiguous Language
- S -> aSb | aSbb | λ
	- Language L + {a^nb^m / 0 < n < m < 2n }
		- number of b's is between the number of a's and twice number of a's 
	- aabbbb can normally be produced two ways 
	- Disambiguating:  
		- produce all a's with matching b's 
		- produce all extra b's
	- New Rule: S -> aSb | A | λ 
			   A -> aAbb | abb
BNF - [Backus Naur Form](https://adacomputerscience.org/concepts/trans_bnf)
- standard notation for CFG's 
	- nonterminal variables are enclosed in <>

