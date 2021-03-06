## A Brief Intro to Type Theory and Lambda Calculus

#### William DeMeo   
[&lt;williamdemeo@gmail.com&gt;](mailto:williamdemeo@gmail.com)  

#### CU Boulder Logic Seminar, 23 Jan 2018  

+++

### Main References

+ [Thorsten Altenkirch's notes on Type Theory](http://www.cs.nott.ac.uk/~psztxa/ewscs-17/notes.pdf)  
www.cs.nott.ac.uk/~psztxa/ewscs-17/notes.pdf

+ [Paul Levy's notes on Lambda Calculus](http://www.cs.bham.ac.uk/~pbl/mgsall.pdf)   
www.cs.bham.ac.uk/~pbl/mgsall.pdf

+++

### Other References

+ [Naive Type Theory short course](http://www.cs.nott.ac.uk/~psztxa/ntt/)   
  Altenkirch (2016) www.cs.nott.ac.uk/~psztxa/ntt/

+ [Typed Lambda Calculus short course](http://www.cs.bham.ac.uk/~pbl/mgs2014lam.html)   
  Levy (2014) www.cs.bham.ac.uk/~pbl/mgs2014lam.html

+ [Abstraction and Computation](http://www.cs.nott.ac.uk/~vxc/publications/Abstraction_Computation.pdf)    
Capretta (2002)  
www.cs.nott.ac.uk/~vxc/publications/Abstraction_Computation.pdf

+ [CMU course on HoTT](http://www.cs.cmu.edu/~rwh/courses/hott/)   
  Harper (2013) www.cs.cmu.edu/~rwh/courses/hott/

---

## Type Theory

---

### Type Theory vs. Set Theory

#### Preliminaries

<ul>
<li class="fragment"> Organize mathematical objects into <a style="color:#e7ad52">**Types**</a> instead of <a style="color:green">**Sets**</a> eg, the <a style="color:#e7ad52">**Type** $\mathbb N$</a> of natural numbers, the <a style="color:#e7ad52">**Type** $\mathbb R$</a> of reals, etc.</li>

<li class="fragment"> To say $\pi$ is a real number, we say "$\pi$ has type $\mathbb R$," denoted <a style="color:#e7ad52">$\pi : \mathbb R$</a></li>

<li class="fragment"> Is <a style="color:#e7ad52">Type Theory</a> merely <a style="color:green">Set Theory</a> with the word <a style="color:green">Set</a> replaced by <a style="color:#e7ad52">Type</a> and the symbol <a style="color:green">$\in$</a> replaced by <a style="color:#e7ad52">$:$</a> ?</li>

<li class="fragment"> No, of course not.</li>
</ul>

+++

#### Type Theory vs. Set Theory: preliminaries

<ul>
<li>In <a style="color:#e7ad52">Type Theory</a> we are only allowed objects of a *given* type.   
*The type comes first!*</li>

<li class="fragment"> In <a style="color:green">Set Theory</a> all objects are there already and we organize them into different sets, classify them, etc.  
We might have an object $x$ and ask wether this object is a **nat** ($x\in \mathbb N$) or a **real** ($x \in \mathbb R$).</li>
</ul>

+++

#### Type Theory vs. Set Theory: preliminaries

<ul>
<li class="fragment"> In <a style="color:#e7ad52">Type Theory</a> we think of $x : \mathbb{N}$ as
  meaning "$x$ is a natural number *by birth*"  </li>
<li class="fragment">...we might go on to ask whether $x$ is also a real number.</li>
<p>
<li class="fragment"> We call <a style="color:#e7ad52">$x : \mathbb N$</a> a ***judgement***</li>
<li class="fragment"> ...while <a style="color:green">$x \in \mathbb N$</a> is a ***proposition***.</li>
</p>
<li class="fragment"> These ideas become clearer and more meaningful after gaining some experience with Type Theory, and we'll revisit them later.</li>
</ul>

---

## Constructive Math

+++

#### Questions and Motivations

<ul>
<li class="fragment"> What is a good language for writing proofs?</li>  

<li class="fragment"> What kind of math do we want to do?</li>  

<li class="fragment"> In principle all math can be formalized in ZFC.</li>  

<li class="fragment"> Usually a much weaker theory suffices.  

(PA suffices for much of Number Theory, analysis can be formalized in PA2, etc.)</li>  

<li class="fragment"> In fact, we don't need to commit, as long as our proofs use
  standard techniques that are formalizable in *some* system.</li>
</ul>

+++

<!-- ------ JPS ------------ -->
<!-- <img style="float:right" src="assets/image/jps.jpg" alt="Choices" style="width: 350px;float: right"/> -->

<ul>
<li class="fragment"> But to do math on a computer (and to exist)   
  *we must make choices*.</li>
<!-- ------ DVF ------------ -->
<div class="fragment fade-left">
<img src="assets/image/jps.jpg"
alt="Choices: JPS" style="float: right;width: 350px" />
</div>
<li class="fragment"> A computer program must be  
  based on *some* formal system.</li>
<li class="fragment"> Is **ZFC** the most natural choice?</li>
<li class="fragment"> **Constructive type theory** can   
be justified on practical (and maybe philosophical) grounds.</li>
  </ul>

+++

#### Questions and Motivations

Why do math on a computer?

<ul>
<p>
<li class="fragment"> Because computers can check whether proofs are correct?  
</li>
<li class="fragment"> <a style="color:#e7ad52">No. The peer review process works pretty well.</a></li>  

</p>

<p>
<li class="fragment"> Because computers can prove many things humans can't?  </li>
<li class="fragment"> <a style="color:#e7ad52">No.  At least not anytime soon.</a></li>
</p>

<p>
<li class="fragment"> Because computers are really good at computing?  </li>
<li class="fragment"> <a style="color:#e7ad52">Yes!</a></li>
</p>
</ul>

+++

<p class="fragment">
No one questions the utility of computer programs on the grounds that
it's easier to handwrite programs on paper in pseudo-code.</p>

<p class="fragment fade-left">
<a style="color:#e7ad52">*Programs written on paper cannot be executed!*</a>
</p>

<p class="fragment">
The objection that formalizing math on computer
is pointless because we can more easily write it down on a piece of paper can
be disputed on similar grounds.  
</p>
<p class="fragment fade-left">
But...  

<a style="color:#e7ad52">*Proofs of math theorems cannot be executed!*</a>  
</p>
<p class="fragment"> ...or can they? </p>

+++

<ul>
<li class="fragment"> *Classical* proofs cannot always be executed, but *constructive* proofs can, in a sense.</li>

<li class="fragment"> Constructive proofs give algorithms to compute all objects claimed to exist and decide all properties claimed decidable.</li>
<!-- ------ DVF ------------ -->
<div class="fragment fade-left">
<img src="assets/image/Darth-Vader-faith.jpg" alt="Darth Vader faith" style="width: 300px;float: right"/>
<li class="fragment"> It may seem strange to think of a proof  
as a program, even stranger that there  
can be different proofs of the same  
result that differ in "efficiency."</li></div>
</ul>

---

### A Change of Tack

<ul>
<p>
<li class="fragment"> Instead of worrying about which system is best for formalizing math, 
let's consider ways to extend programming languages, e.g. richer data types, new paradigms/techniques.</li>
</p>  
<p>
<li class="fragment"> Later we will look at a functional programming language 
called <a style="color:purple">Lean</a>, and consider
how it makes programming easier. </li>
</p>  
<p>
<li class="fragment"> 
Some classical algorithms become easy or obvious;
even previously inconceivable programs become possible.</li>
</p>
<!-- <p>
<li class="fragment"> We hold logical foundations in abeyance.</li>
</p> -->
</ul>

---

### Curry-Howard Correspondence

<p class="fragment">
Eventually, we'll see <a style="color:#e7ad52">*programs as proofs*</a>
of theorems and <a style="color:#e7ad52">**constructive math**</a>
as a subsystem of the programming language.</p>

<p class="fragment">**The most important advantage:**  
<a style="color:#e7ad52">*programs are guaranteed correct*</a>   
by virtue of the their inherent logical content!</p>

---

### Sets vs Types: redux

+++

#### Sets vs Types: redux
<ul>
<p>
<li class="fragment"> In <a style="color:green">Set Theory</a>,
	$3 \in \mathbb N$ means  
	"3 is an element of the <a style="color:green">set</a> of natural numbers"</li>
</p><p>
<li class="fragment"> In <a style="color:#e7ad52">Type Theory</a>,
	$3 : \mathbb N$ means  
	"3 is an element of the <a style="color:#e7ad52">type</a> of natural numbers"</li>
<p>
<li class="fragment"> Seems trivial, but recall the significance...</li>
</p><p>
<li class="fragment"> While  <a style="color:green">$3 \in \mathbb N$</a> is a *proposition*, we think of
<a style="color:#e7ad52">$3 : \mathbb N$</a> as a ***judgment***   
a piece of static information.</li>
</p>

</ul>

+++

#### Sets vs Types: redux

<ul>
<li class="fragment"> In <a style="color:#e7ad52">Type Theory</a> every object and every expression has a (unique) type
  which is statically determined.</li>

<li class="fragment"> Hence it doesn't make sense to use <a style="color:#e7ad52">$a : A$</a> as a proposition.</li>

<li class="fragment"> This is similar to the distinction between statically and dynamically typed
   programming languages. While in dynamically typed languages there are
   runtime functions to check the type of an object this doesn't make sense
   in statically typed languages.</li>
</ul>


+++

#### Sets vs Types: redux

<ul>
<li class="fragment"> In <a style="color:green">Set Theory</a> we define
$P \subseteq Q$ as   
$\forall x . x \in P \to x \in Q$ </li>

<li class="fragment"> This doesn't work in <a style="color:#e7ad52">Type Theory</a> since $x \in P$ is not a proposition.</li>

<li class="fragment"> <a style="color:green">Set theoretic</a> operations like $\cup$ or $\cap$ are not operations on <a style="color:#e7ad52">types</a> </li>

<li class="fragment"> ...but they can be defined as operations on predicates (subsets) of
  a given type. $\subseteq$ can be defined as a predicate on such subsets.</li>
</ul>

---

### Truth Vs. Evidence

<p class="fragment">
Another important difference between Set Theory and Type Theory is the
way propositions are treated. 
</p>

<p class="fragment">
Set Theory is formulated using predicate logic
which relies on the notion of **truth**.
</p>

<p class="fragment">
 Type Theory is self-contained and doesn't
refer to **truth**, but rather **evidence**.
</p>

---

### Curry-Howard Correspondence

+++

#### Curry-Howard Correspondence

Using the <a style="color:#e7ad52">propositions-as-types</a> translation
we can assign to any proposition $P$ the type of its evidence $[[P]]$
as follows:

$[[P \Rightarrow Q]] \equiv [[P]] \to [[Q]]$

$[[P ∧ Q]] ≡ [[P ]] × [[Q]]$

$[[\mathsf{True}]] ≡ 1$

$[[P ∨ Q]] ≡ [[P ]] + [[Q]]$

$[[\mathsf{False}]] ≡ 0$

$[[∀x : A.P ]] ≡ Πx : A.[[P ]]$

$[[∃x : A.P ]] ≡ Σx : A.[[P ]]$

+++

#### Curry-Howard Correspondence

0 is the empty type, 1 is the type with exactly one element

disjoint union +, product ×, and → (function) types are familiar

Π and Σ may be less familiar; we look at them later.

---

### Universes

+++

#### Universes
<ul>
<li class="fragment"> To get started we have to say what a *type* is. We could introduce another judgement, but
  instead we'll use **universes.**</li>

<li class="fragment"> A **universe** is a type of types. For example, to say that $\mathbb N$ is a type,
  we write <a style="color:#e7ad52">$\mathbb N : \mathsf{Type}$</a>, where
  <a style="color:#e7ad52">$\mathsf{Type}$</a> is a universe.</li>

<li class="fragment"> But what is the type of <a style="color:#e7ad52">$\mathsf{Type}$</a>? Do we have
  <a style="color:#e7ad52">$\mathsf{Type} : \mathsf{Type}$</a>?</li>

<li class="fragment"> This doesn't work in   <a style="color:green">Set Theory</a> (Russell's paradox)
</li>

<li class="fragment"> In Type Theory <a style="color:#e7ad52">$a : A$</a> is not a Prop, hence it's not immediately clear wether the paradox still occurs.</li>
</ul>

+++

#### Universes

<ul>
<li class="fragment"> It turns out a Type Theory with <a style="color:#e7ad52">$\mathsf{Type} : \mathsf{Type}$</a> does
  exhibit **Russell's paradox**.</li>

<li class="fragment"> (**Example:** construct the tree <a style="color:#e7ad52">$T : \mathsf{Tree}$</a> of all trees
  that don't have themselves as immediate subtrees. Then <a style="color:#e7ad52">$T$</a>
  is a subtree of itself iff it isn't.)</li>

<li class="fragment"> To avoid this, we introduce a hierarchy of universes  


  <a style="color:#e7ad52">
  $\mathsf{Type}_0 : \mathsf{Type}_1 : \mathsf{Type}_2 : \cdots$
  </a>    

  <!-- and we decree that any $A : \mathsf{Type}_i$ can be *lifted* to
  $A^+ : \mathsf{Type}_{i+1}$ </li>
 -->
<li class="fragment"> Being explicit about universe levels can be annoying.  
  In notation we ignore levels, but take care to avoid using universes in a cyclic way.</li>

<li class="fragment"> We write $\mathsf{Type}$ as a metavariable for
$\mathsf{Type}_i$ and assume that all levels act the same unless stated otherwise.</li>
</ul>

---

### Functions

+++

#### Functions

<ul>
<li class="fragment"> In <a style="color:green">Set Theory</a> **function** is a derived concept
  (a subset of the cartesian product with certain properties)</li>

<li class="fragment"> In <a style="color:#e7ad52">Type Theory</a> **function** is a primitive concept.
</li>
<li class="fragment"> The basic idea is the same as in functional programming:   
a function is a **black box**  
you feed it elements from its domain and out come
elements of its codomain.</li>

<li class="fragment"> Hence given $A, B : \mathsf{Type}$ we introduce the type of
  functions   
  $A \to B : \mathsf{Type}$
</li>

</ul>

+++

#### Functions

<ul>

<li class="fragment"> We can define a function
  $f : \mathbb{N} \to \mathbb{N}$
  explicitly, eg, $f (x) :\equiv x +3$
</li>
<li class="fragment"> We can apply, $f (2) : \mathbb{N}$, and
  evaluate this application by replacing all
  $x$'s with 2; hence $f (2) \equiv 2 + 3$
</li>
<li class="fragment"> If we can calculate $2 + 3$, we conclude $f (2) \equiv 5$
</li>

</ul>

---

### Syntax

#### Anonymous functions and lambda abstractions

+++

<ul>
<li class="fragment"> In Type Theory, as in functional programming, we usually
try to save parentheses and write $f x :\equiv x + 3$
and $f 2$
</li>
<li class="fragment"> The explicit definition of a function requires a name but we want
**anonymous functions** as well---this is one justification for the  
<a style="color:#e7ad52">λ-notation</a>
</li>
<li class="fragment"> We write $\lambda x.x + 3 : \mathbb{N} \to \mathbb{N}$
to avoid naming the function.
</li>
<li class="fragment"> We can apply: $(\lambda x . x + 3)(2)$
</li>
<li class="fragment"> The equivalence
$(\lambda x . x + 3)(2) \equiv 2 + 3$
is called <a style="color:#e7ad52">β-reduction</a>
</li>
<li class="fragment">  The explicit definition $f x \equiv x + 3$ can now be understood
as a shorthand for $f \equiv \lambda x . x + 3$.
</li>
</ul>

+++

### Products and sums

<ul>
<p>
<li class="fragment"> Given $A, B : \mathsf{Type}$ we can form  

their product <a style="color:#e7ad52">$A \times B : \mathsf{Type}$</a>  

their sum <a style="color:#e7ad52">$A + B : \mathsf{Type}$</a>
</li></p>
<p>
<li class="fragment"> The elements of a product are tuples, that is  
  $(a, b) : A \times B$ if $a : A$ and $b : B$</li>
</p>

<p>
<li class="fragment"> The elements of a sum are injections, that is  
  $\mathsf{inl}\ a : A + B$ if $a : A$ and $\mathsf{inr}\ b : A + B$, if $b : B$</li>
</p>
</ul>

+++

#### Example
<ul>
<p>
<li class="fragment"> To define a function from a product or a sum it suffices to say   
  what the function returns for the
  constructors  
  (tuples for products; injections for sums)
</li></p>

<p>
<li class="fragment"> As an example we derive the tautology  

$P ∧ (Q ∨ R) ⇔ (P ∧ Q) ∨ (P ∧ R)$  

using the propositions as types translation.
</li></p>

+++

#### Example 

<p class="fragment"> Assuming $P, Q, R : \mathsf{Type}$,
  construct an element of the following type  

  $((P × (Q + R) → (P × Q) + (P × R))$  

  $\qquad ×((P × Q) + (P × R) → P × (Q + R))$
</p>

+++

#### Solution

<ul>
<p>
<li class="fragment"> Define $f : P × (Q + R) \to (P × Q) + (P × R)$ as follows:

$f (p, \mathsf{inl}\ q) :\equiv \mathsf{inl}\ (p, q)$  

$f (p, \mathsf{inr}\ r) :\equiv \mathsf{inr}\ (p, r)$  
</li></p><p><li>
Define $g : (P × Q) + (P × R) \to P × (Q + R)$ as follows:

$g (\mathsf{inl}\ (p, q)) :\equiv (p, l\mathsf{inl}\ q)$  

$g (\mathsf{inr} (p, r))) :\equiv (p, \mathsf{inr}\ r)$  

The tuple $(f, g)$ is an element of the desired type!
</li></p></ul>

---

### exercises

+++

#### Exercise 1

Using the propositions as types translation, try to prove the following tautologies
(where P, Q, R : Type are propositions represented as types)

1. (P ∧ Q ⇒ R) ⇔ (P ⇒ Q ⇒ R)
2. ((P ∨ Q) ⇒ R) ⇔ (P ⇒ R) ∧ (Q ⇒ R)
3. ¬(P ∨ Q) ⇔ ¬P ∧ ¬Q
4. ¬(P ∧ Q) ⇔ ¬P ∨ ¬Q
5. ¬(P ⇔ ¬P )

+++

#### Exercise 2

**Law of Excluded Middle** $(\forall P) (P \vee \neg P)$
is not provable in TT

However, we can prove its double negation (ie "LEM is not refutable")

Using the **propositions-as-types** translation, prove  

$(\forall P)\neg \neg(P \vee \neg P )$

If for a particular proposition $P$ we can establish $P \vee \neg P$
then we can also derive the principle of indirect proof $\neg \neg P \Rightarrow P$
for the same proposition.

Show $(P \vee \neg P ) \Rightarrow (\neg \neg P \Rightarrow P )$

The converse does not hold **locally** (Counterexample?)

...but it holds **globally**. Show that the two principles are equivalent.
That is, prove:  

$(\forall P)(P \vee \neg P ) \Longrightarrow (\forall P)(\neg \neg P \Rightarrow P )$

+++

Functions out of products and sums can be reduced to using a fixed set of
**combinators** called <a style="color:#e7ad52">*non-dependent eliminators*</a>
or <a style="color:#e7ad52">*recursors*</a> (even though there
is no recursion going on).

$R^\times : (A → B → C) → A × B → C$

$R^\times f\ (a, b) :\equiv f a b$

$R^+ : (A → C) → (B → C) → A + B → C$

$R^+ f g\ (\mathsf{inl}\ a) :\equiv f a$

$R^+ f g\ (\mathsf{inr}\ b) :\equiv g b$

<li class="fragment"> The **recursor** $R^\times$ for products maps a **curried** function $f : A → B → C$
to its **uncurried** form, taking tuples as arguments.

<li class="fragment"> The **recursor** $R^+$ basically implements the case function performing case
analysis over elements of $A + B$.

+++

#### Exercise 3

Show that using the **recursor** $R^\times$ we can define the projections:

fst : A × B → A

fst (a, b) :≡ a

snd : A × B → B

snd (a, b) :≡ b

Vice versa: can the recursor be defined using only the projections?

+++

### The unit and empty types

+ Denote by $\mathbf{1}$ the empty product, called the <a style="color:#e7ad52">*unit type*</a>

+ Denote by $\mathbf{0}$ the empty sum, called the <a style="color:#e7ad52">*empty type*</a>

+ $() : \mathbf{1}$ is the only inhabitant of the unit type

+ Nothing inhabits $\mathbf{0}$ (it's the *empty* type!)

+ We introduce the corresponding recursors:<br>
$R^\mathbf{1} : C → (\mathbf{1} → C)$ is defined by $R^\mathbf{1} c () :\equiv c$<br>
$R^\mathbf{0} : \mathbf{0} → C$ (no defining eqn since it won't be applied)

+ The recursor for $\mathbf{1}$ is pretty useless. It just defines a constant function.

+ The recursor for the empty type implements the logical principle *ex falso quod libet*

+++

#### Exercise 4

Construct solutions to exercises 1 and 2 using only the eliminators.

+++

+ The use of arithmetical symbols for operators on types is justified because
they act like the corresponding operations on finite types.

+ Let us identify the number $n$ with a **type** inhabited by the following elements:
$0_n, 1_n, \dots, (n - 1)_n : \underline{n}$

+ Then we observe that
\begin{align*}
\underline{0} &= 0\\
\underline{m+n} &= \underline{m} + \underline{n}\\
\underline{1} &= 1\\
\underline{m \times n} &= \underline{m}\times \underline{n}
\end{align*}

+ Read $=$ here as "has the same number of elements"  
This use of equality will be justified later when we introduce the
**univalence principle**

+++

### Function Types are Exponentials

The arithmetic interpretation of types also extends to the function type,
which corresponds to exponentiation. Indeed, in Mathematics the function type
$A \to B$ is often written as $B^A$, and indeed we have:
$\underline{m^n} = \underline{n} \to \underline{m}$.

---

### Dependent Types

+++

#### What are Dependent Types?

<p class="fragment fade-left">
You may be familiar with <a style="color:#e7ad52">polymorphic types</a> (aka generics)  
These are types that are indexed by other types  
</p>

<div class="fragment fade-left">
<a style="color:olivedrab">**Example**</a>

```java
Array<Integer>      // Java

List[(String, Int)] // Scala
```
</div>

<p class="fragment fade-left">
A <a style="color:#e7ad52">*dependent type*</a> is
indexed by an <u>*element*</u> of another type
</p>

<div class="fragment fade-left">
<a style="color:olivedrab">**Examples**</a>

<a style="color:#e7ad52">$A^n : \mathsf{Type}$</a>, the *type of $n$-tuples* whose inhabitants are $(a_0, a_1, \dots, a_{n-1}) : A^n$ where $a_i : A$

<a style="color:#e7ad52">$\underline{n} : \mathsf{Type}$</a>, the *finite type* whose inhabitants are $0_n, 1_n, \dots, (n - 1)_n : \underline{n}$
</div>


+++

#### What are Dependent Types?

The **$n$-tuple type**
<a style="color:#e7ad52">$A^n : \mathsf{Type}$</a>
is indexed by \underline{*two*} parameters  

$\underline{n} : \mathsf{Type} \quad \text{ and } \quad A : \mathsf{Type}$  

<div class="fragment fade-left">
In general, a <a style="color:#e7ad52">*dependent type*</a> is obtained by applying a
function with codomain $\mathsf{Type}$.
</div>

<div class="fragment fade-left">
<a style="color:olivedrab">**Example 1**</a>

$\mathsf{Vec} : \mathsf{Type} \to \mathbb{N} \to \mathsf{Type}$

$\mathsf{Vec}\; A\; n :\equiv A^n$
</div>

<div class="fragment fade-left">
<a style="color:olivedrab">**Example 2**</a>

$\mathsf{Fin} : \mathbb{N} \to \mathsf{Type}$

$\mathsf{Fin}\; n :\equiv \underline{n}$
</div>

+++

### Curry-Howard again

In the *propositions-as-types* view, <a style="color:#e7ad52">**dependent types**</a>
are used to encode predicates.

<div class="fragment fade-left">
<a style="color:olivedrab">**Example**</a>  
<a style="color:#e7ad52">$\mathsf{Prime} : \mathbb N \to \mathsf{Type}$</a>  
This takes <a style="color:#e7ad52">$n : \mathbb N$</a> as input and outputs
<a style="color:#e7ad52">$\mathsf{Prime}\; n : \mathsf{Type}$</a>,  
the type representing *evidence that $n$ is a prime number*.
</div>

<div class="fragment fade-left">
If <a style="color:#e7ad52">$\varphi$</a> is a proof that <a style="color:#e7ad52">$n : \mathbb N$</a> is prime, then
<a style="color:#e7ad52">$\varphi : \mathsf{Prime}\; n$</a>.</div>
<!-- and say "<a style="color:#e7ad52">$\varphi$</a> has type <a style="color:#e7ad52">$\mathsf{Prime}\; n$</a>" -->
<!-- <a style="color:#e7ad52">$p$</a> has type <a style="color:#e7ad52">$\mathsf{Prime}\; n$</a> and we write -->

<div class="fragment fade-left">
Of course <a style="color:#e7ad52">$\mathsf{Prime}\; n$</a> could be uninhabited, eg <a style="color:#e7ad52">$\mathsf{Prime}\; 4$</a>.
</div>

---

### Codifying Relations

+++

#### Codifying Relations


By <a style="color:#e7ad52">currying</a> we can also use dependent types to represent **relations**

<a style="color:olivedrab">**Example**</a>
<a style="color:#e7ad52">$\leq\; : \mathbb N \to \mathbb N \to \mathsf{Type}$</a>  
<a style="color:#e7ad52">$m \leq n : \mathsf{Type}$</a>,
the type of *evidence that <a style="color:#e7ad52">$m$</a> is less or equal to <a style="color:#e7ad52">$n$</a>*

<div class="fragment fade-left">
If <a style="color:#e7ad52">$\varphi$</a> is a proof of
<a style="color:#e7ad52">$m \leq n$</a>, then
<a style="color:#e7ad52">$\varphi : m \leq n$</a>
</div>

<div class="fragment fade-left">
<a style="color:olivedrab">**Example**</a> Let
<a style="color:#e7ad52">$\mathbf A$</a> be an algebra and
<a style="color:#e7ad52">$\theta \in \operatorname{Con} \mathbf A$</a> a congruence
</div>

<div class="fragment fade-left">
<a style="color:#e7ad52">$\theta : A \to A \to \mathsf{Type}$</a> takes inputs
<a style="color:#e7ad52">$a, b : A$</a> and outputs <a style="color:#e7ad52">$a \mathrel{\theta} b : \mathsf{Type}$</a>,
the type of *evidence for <a style="color:#e7ad52">$(a,b) \in \theta$</a>*
</div>

<div class="fragment fade-left">
If <a style="color:#e7ad52">$\varphi$</a> is a proof of
<a style="color:#e7ad52">$a \mathrel{\theta} b$</a>, then
<a style="color:#e7ad52">$\varphi : a \mathrel{\theta} b$</a>
</div>

---

### Proof Assistants

Type Theory is the foundation of many computer systems for
interactive theorem proving and very advanced (functional) programming languages.

#### An incomplete list

<ul>
<li class="fragment"> [NuPRL](https://en.wikipedia.org/wiki/Nuprl) is maybe the oldest implementation of Type Theory, which was developed
at Cornell. It is based on a different flavour of type theory which
was called Extensional Type Theory but which is now referred to as Computational
Type Theory.</li>

<li class="fragment"> [Coq](https://en.wikipedia.org/wiki/Coq) is maybe now the system most used in formal Mathematics and has been
used for some impressive developments, including a formal proof of the
Four Colour Theorem and the verification of an optimising C compiler.</li>

<li class="fragment"> [Agda](https://en.wikipedia.org/wiki/Agda_(programming_language)) is a sort of a twitter it can be used as a interactive proof assistant or as
a dependently typed programming language.</li>

<li class="fragment"> [Idris](https://en.wikipedia.org/wiki/Idris_(programming_language)) goes further on the programming language road by addressing more pragmatic
concerns when using Type Theory for programming.</li>

<li class="fragment"> [Lean](https://leanprover.github.io/) is developed at CMU and Microsoft Research with strong support for automatic  reasoning.</li>
</ul>

---

### Martin-Lof intensional type theory

<ul>
<li class="fragment"> <a style="color:rgb(231,173,82)">Intensional type theory</a> is the brand of type
theory used in systems like
<a style="color:mediumpurple">Agda</a> and <a style="color:orangered">Coq</a></li>

<li class="fragment"> <a style="color:crimson">NuPrl</a>
  is based on **extensional** type theory </li>

<li class="fragment"> This is an important distinction and it centers around different notions of
**equality**</li>
</ul>


---
<ul>
<li class="fragment"> In the original formulation by Martin-Lof, there is a judgement called
*definitional equality*, which is asserted when two terms denote the same value.</li>

<li class="fragment"> Today, this is most often replaced by a reduction relation.  Two terms are
called *convertible* when they can be reduced to a common decendant using the
reduction rules.  If we reduce a term as much as possible, we always obtain
after a finite number of steps, a unique *normal form* (that
cannot be simplified further).  Convertible terms are interchangeable.</li>

<li class="fragment"> *extensional* versions of type theory,
  like <a style="color:crimson">NuPrl</a>,
  have a stronger notion of **definitional equality**   
  for example, two functions can be identified if their graphs are the same  </li>

<li class="fragment"> However, the price to pay is *undecidability of type checking*</li>
</ul>

---

## <a style="color:crimson">Extensional Type Theory</a>

<a style="color:mediumpurple">Intensional</a>
<a style="color:crimson">Extensional</a>

<ul>
<li class="fragment"> <a style="color:crimson">ETT</a>
  does not distinguish between **definitional equality** (computational)
  and **propositional equality** (requires proof)</li>

<li class="fragment"> Type checking is **undecidable** in
  <a style="color:crimson">ETT</a>  
  *programs in the theory might not terminate*</li>

<li class="fragment"> <a style="color:olivedrab">**Example**</a>
  In <a style="color:crimson">ETT</a> we can give a type to the **Y-combinator**</li>

<li class="fragment"> This does not prevent <a style="color:crimson">ETT</a> from being a basis
  for a practical tool, as <a style="color:crimson">NuPRL</a> demonstrates.</li>

<li class="fragment"> From a practical standpoint, there's no difference between a program which doesn't terminate and a program which takes a million years to terminate</li>
</ul>

---

## <a style="color:mediumpurple">Intensional Type Theory</a>

<a style="color:mediumpurple">Intensional</a>
<a style="color:crimson">Extensional</a>

<ul>
<li class="fragment"> <a style="color:mediumpurple">ITT</a>
  has decidable type checking, but the representation of
  standard math concepts can be more cumbersome.</li>

<li class="fragment"> In <a style="color:mediumpurple">ITT</a>
  **extensional reasoning** requires using
  <a style="color:rgb(231,173,82)">setoids</a> or similar constructions.</li>

<li class="fragment"> There are many common math objects that are hard to work
  with and/or can't be represented without this.</li>

<li class="fragment"> **Examples:** Integers and rational numbers can be
  represented without setoids, but the representations are not
  easy to work with; Reals cannot be represented without
  setoids or something similar.</li>
</ul>

---

## Homotopy type theory

<ul>
<li class="fragment"> [HoTT](http://www.homotopytypetheory.org) works on resolving these problems</li>

<li class="fragment"> [HoTT](http://www.homotopytypetheory.org)
  allows one to define <a style="color:rgb(231,173,82)">higher inductive types</a>
  that not only define **first-order constructors** (values or points), but **higher-order
  constructors** (equalities between elements--paths), equalities between equalities
  (homotopies), ad infinitum.</li>
</ul>
