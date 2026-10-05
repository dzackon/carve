# Affine λ-calculus

A simply typed affine λ-calculus using higher-order abstract syntax (HOAS). Contexts use the **linear** resource algebra ([`linear.bel`](../../lib/algebra/instances/linear.bel)) with multiplicities 0 and 1 rather than [`affine.bel`](../../lib/algebra/instances/affine.bel). Weakening is permitted by omitting an exhaustedness premise from the variable rule; exponentials are omitted.

The development proves [type preservation](preservation.bel) under the full strong reduction of [`lambda_dyn.bel`](../shared/lambda_dyn.bel).

```sh
beluga config/case_studies/affine_lambda.cfg
```
