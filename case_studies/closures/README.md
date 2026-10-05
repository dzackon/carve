# Linear λ-calculus with closures

A simply typed linear λ-calculus using [de Bruijn levels](definitions/tm.bel) and an [environment-based operational semantics](definitions/dyn.bel). Exponentials are omitted.

The development proves [type preservation](preservation.bel): evaluating a well-typed term in a compatible environment produces a value of the same type.

```sh
beluga config/case_studies/closures.cfg
```
