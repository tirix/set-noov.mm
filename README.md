# set-noov.mm
A set.mm version with no overloading

In the [`set.mm`](https://github.com/set.mm) [Metamath](http://metamath.org/) database, the equality and membership predicates are overloaded. That is, the same predicate is used both for sets and classes.

This is a copy of the beginning of the `set.mm` database, where this overloading has been removed:

- In the first part, "Predicate Calculus", where set equality and set membership are introduced, new predicates are used. The whole development of predicate calculus is identical, with these predicates replaced with their set-only versions:
  - ` =s ` is defined for set equality (instead of the overloaded `=`):   ` wequ $a wff x =s y $. `
  - ` e.s ` is defined for set membership (instead of the overloaded `e.`), ` wsel $a wff x e.s y $. `
- Then, a new predicate for set-class membership ` e.c ` is defined: ` wscel $a wff x e.c A $. `
- The corresponding definition is introduced for class abstractions:
  - ` df-sclab $a |- ( x e.c { y | ph } <-> [ x / y ] ph ) $. `
- Class equality/extentionality is then defined using that predicate:
  - ` df-cleq $a |- ( A = B <-> A. x ( x e.c A <-> x e.c B ) ) $. `
- However, **two new axioms seem to be necessary** :
  - ` ax-abidc $a |- A = { x | x e.c A } $. ` seems to be necessary to allow the first substitution of a class variable with a class abstraction,
  - ` ax-sclabsel $a |- ( x e.c y <-> x e.s y ) $. ` seems to be necessarry to extend set membership to set-class membership.
  - as a consequence, set equality is extended to class equality for sets: ` seqeq $p |- ( x =s y <-> x = y ) $. `
- Class membership is then introduced and defined as ` df-clel $a |- ( A e. B <-> E. x ( x = A /\ x e.c B ) ) $. `
  - as a consequence, set membership is extended to class membership for sets: ` selel $p |- ( x e. y <-> x e.s y ) $. `
- It is then possible to reformulate with the class-predicates the previous theorems which were introduced using the set predicate. Especially, the two definitions can be reformulated:
  - Class equality : ` dfcleq $p |- ( A = B <-> A. x ( x e. A <-> x e. B ) ) $. `
  - Class membership: ` dfclel $p |- ( A e. B <-> E. x ( x = A /\ x e. B ) ) $. `
- From then on, all foundations are identical, and the development can continue just as in the original `set.mm` database.
