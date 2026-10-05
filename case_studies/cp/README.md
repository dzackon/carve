# CP

The multiplicative–additive fragment of the session-typed process calculus [CP](definitions/proc.bel), using a continuation-passing encoding with higher-order abstract syntax (HOAS).

The development proves [type preservation](preservation.bel) and [the equivalence](equivalence.bel) of CP and [Structural CP (SCP)](definitions/scp.bel), through translations relating explicit contexts to hypothetical judgments.

```sh
beluga config/case_studies/cp.cfg
```
