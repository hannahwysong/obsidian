
###### Exercise 16 Give BP for P as in Example 1.2.19. How many elements does IP have?  
	Bp = {p(a), q(b), q(a), p(b)}
	elements = 2^4 = 16
###### Exercise 17 For the program P in Example 1.2.18, compute the following.  
	a) TP({p(c), q(c, c)}) = {p(a), q(a, b), q(b, c), r(c)}
	
	b) TP(p(a), p(b), p(c), r(a), r(b), r(c), q(a, a), q(a, b), q(a, c), q(b, a), q(b, b), q(b, c), q(c, a), q(c, b), q(c, c)) = {p(a), q(a, b), q(b, c)} U {r(a), r(b), r(c), q(b, a), q(c, b), q(a, a), q(c, a), q(b, b), q(a, c), q(c, c)}
###### Exercise 18 With respect to Example 1.2.18, verify that BP is a pre-fixed point of TP .  
	Because Bp is a subset of Tp
###### Exercise 19 Give three pre-fixed points and one fixed point of the T P -operator for P as in Exercise 16.  
	Tp(∅) = {p(a), q(b)} - Pre-Fixed Point
	Tp(p(a)) = {p(a), q(b)} - Pre-Fixed Point
	Tp(q(b)) = {p(a), q(b)} - Pre-Fixed Point
	Tp(p(a), q(b)) = {p(a), q(b)} - Fixed Point
###### Exercise 20 Compute T P ↑ n for all n ∈ N and T P ↑ ω for P as in Example 1.2.7.  
	Tp↑0 = {}
	Tp(Tp↑0) = Tp↑0 U {bOf(c, m), mOf(m, n)} = Tp↑1
	Tp(Tp↑1) =  Tp↑1 U {pOf(m, n)} = Tp↑2
	Tp(Tp↑2) = Tp(Tp↑2) U uOf(c, n)} = Tp↑3
	Tp(Tp↑3) = Tp↑3 U ∅
###### Exercise 21 Compute T P ↑ n for all n ∈ N and T P ↑ ω for P as in Exercise 15.  
	Tp(Tp↑0) = {}
	Tp(Tp↑0) = Tp↑0 U {p(a, b), q(c), q(d)} = Tp↑1
	Tp(Tp↑1) =  Tp↑1 U {q(a)} = Tp↑2
	Tp(Tp↑2) = Tp↑2 U ∅
###### Exercise 22 Compute T P ↑ n for all n ∈ N and T P ↑ ω as in Exercise 10.  
	Tp↑0 = {}
	Tp(Tp↑0) = Tp↑0 U {q(a), q(c), p(b)} = Tp↑1
	Tp(Tp↑1) = Tp↑1 U {p(a), p(c)} = Tp↑2
	Tp(Tp↑2) = Tp↑2 {r(b)} = Tp↑3
	Tp(Tp↑3) = Tp↑3 U ∅
###### Exercise 23 Compute T P ↑ n for all n ∈ N and T P ↑ ω as in Example 1.2.19. 
	Tp↑0 = {}
	Tp(Tp↑0) = Tp↑0 U {p(a), q(b)} = Tp↑1
	Tp(Tp↑1) = Tp↑1 U ∅
###### Exercise 24 T P ↑ n for all n ∈ N and T P ↑ ω for P as in Example 1.2.8.  
	Tp↑0 = {}
	Tp(Tp↑0) = Tp↑0 U {p(a, b), p(b, c), p(c, a), p(d, d)} = Tp↑1
	Tp(Tp↑1) = Tp↑1 U {q(a, b), q(b, c), q(c, a), q(d, d)} = Tp↑2
	Tp(Tp↑2) = Tp↑2 U {q(a, c), q(b, a), r(a, b), r(b, c), r(c, a), r(d, d)} = Tp↑3
	Tp(Tp↑3) = Tp↑3 U {q(b, b), q(a, a), q(c, c), r(a, c), r(b, a) r(c, b), t(d)} = Tp↑4
	Tp(Tp↑4) = Tp↑4 U {r(b, b), r(a, a), r(c, c)} = Tp↑5
	Tp(Tp↑5) = Tp↑5 U {t(b), t(a), t(c)} = Tp↑6
	Tp(Tp↑6) = Tp↑6 U ∅
###### Exercise 25 Show that the Datalog program from Example 1.1.1 Herbrand-entails grandmotherOf(ann, malia).  
	Tp↑0 = {}
	Tp(Tp↑0) = Tp↑0 U {motherOf(ann, barack), fatherOf(barack, malia) ...} = Tp↑1
	Tp(Tp↑1) = Tp↑0 U {parentOf(barack, malia), ...} = Tp↑2
	Tp(Tp↑2) = Tp↑1 U {grandmotherOf(ann, malia), ...} = Tp↑3
	Tp(Tp↑3) = Tp↑ U ∅
	A ∈ TP ↑ ω so P|=H A



