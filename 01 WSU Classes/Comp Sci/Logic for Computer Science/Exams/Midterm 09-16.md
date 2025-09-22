#  Datalog Study Sheet (Midterm Prep)

## 1. Datalog Language & Programs

### **1.2.1 Definition – Datalog Language**
A Datalog language **L = (V, C, R)** consists of:
- **V** – finite set of variables (`x₁, x₂, …`)
- **C** – finite non-empty set of constants (`a, b, c, …`)
- **R** – finite non-empty set of predicate symbols (`p₁, q, r, …`) with an **arity** (number of arguments)

**Atom:** `p(v₁, …, vₙ)` where `p` is predicate of arity `n` and each `vᵢ` is constant or variable  
**Ground Atom:** Atom with no variables (all arguments are constants)

---

### **1.2.3 Definition – Datalog Rule**
A **rule**:  
**B₁ ∧ … ∧ Bₙ → A**  
- **Body** = `B₁ ∧ … ∧ Bₙ`  
- **Head** = `A`  
- Each `Bᵢ` = body atom  

**Fact** = rule with no body (`n = 0`), written simply as `A`.  
**Datalog Program** = set of rules.

---

### **1.2.6 Definition – Herbrand Interpretation**
A **Herbrand interpretation** for program **P** = any set of ground atoms over **L**.

---

### **1.2.11 Definition – Ground Rule**
- **Ground Rule** = rule with no variables  
- **Ground Substitution φ** = mapping that replaces all variables with constants, producing a ground rule

---

### **1.2.13 Definition – Grounding**
- **ground(R)** = set of all ground instances of rule **R**  
- **ground(P)** = ⋃ ground(R) for all R ∈ P  
**Finite** if P is finite (only finitely many constants)

---

### **1.2.16 Definition – Herbrand Model**
A Herbrand interpretation **I** is a **Herbrand model** of **P** if:  
for every ground rule `B₁ ∧ … ∧ Bₙ → A ∈ ground(P)`,  
if `{B₁, …, Bₙ} ⊆ I`, then **A ∈ I**

---

### **1.2.19 Example – Herbrand Models**
P =   p(a)  
	q(b)  
	q(x) → q(x)

Herbrand Models:
- `{p(a), q(b)}`
- `{p(a), q(b), q(a)}`
- `{p(a), q(b), q(a), p(b)}`

---

## 2. Herbrand Base, Interpretations & TP Operator

### **1.3.2 Definition – Herbrand Base**
- **BP** = set of all ground atoms over **L** (the **Herbrand base**)  
- **IP = 2ᴮᴾ** = set of all subsets of BP (all Herbrand interpretations)

---

### **1.3.5 Definition – TP Operator**
**TP: IP → IP** defined by: 
	TP(I) = { A ∈ BP |  (B₁ ∧ … ∧ Bₙ → A) ∈ ground(P) and Bᵢ ∈ I for all i }
- **Pre-fixed point**: TP(I) ⊆ I  
- **Fixed point**: TP(I) = I  

---

### **1.3.11 Theorem – Herbrand Models = Pre-Fixed Points**
**I is a Herbrand model ⇔ TP(I) ⊆ I**

---

### **1.3.12 Lemma – Monotonicity**
If **I₁ ⊆ I₂**, then **TP(I₁) ⊆ TP(I₂)**  
✅ **TP is monotonic**

---

### **1.3.13 Definition – Iteration of TP**
TP ↑ 0 = ∅  
TP ↑ (n+1) = TP(TP ↑ n)  
TP ↑ ω = ⋃ TP ↑ n (limit of all iterates)
Each **TP ↑ n** = **nth iterate** of TP

---

## 3. Least Herbrand Model & Entailment

### **1.3.15 Theorem – Least Herbrand Model**
For every program P:
1. **TP ↑ ω is a fixed point** of TP  
2. **TP ↑ ω is a Herbrand model**  
3. **TP ↑ ω ⊆ M for every Herbrand model M**  

✅ **TP ↑ ω = least Herbrand model**

---

### **1.3.16 Definition – Herbrand Entailment**
P **Herbrand-entails** A (written **P |=H A**) iff **A ∈ TP ↑ ω**  
(i.e., A is true in the least Herbrand model)

---

### **1.3.17 Theorem – Entailment & All Models**
P |=H A ⇔ A ∈ M for **all** Herbrand models M of P

---


