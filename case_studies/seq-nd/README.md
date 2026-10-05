# Linear sequent and natural deduction calculi

A [linear sequent calculus](definitions/seq.bel) and a [bidirectional linear natural deduction calculus](definitions/nd.bel) with proof terms, covering unit, tensor, linear implication, additive conjunction and additive disjunction. Proof terms use higher-order abstract syntax (HOAS).

The development includes [equivalence of the two calculi](equivalence.bel) via [well-typed simultaneous substitutions](definitions/subst.bel), and [cut elimination](cut_elim.bel).

```sh
beluga config/case_studies/seq-nd.cfg
```
