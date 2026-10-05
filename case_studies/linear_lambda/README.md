# Linear λ-calculus

A simply typed linear λ-calculus using [higher-order abstract syntax (HOAS)](../shared/lambda_tm.bel), with exponentials in the style of dual intuitionistic linear logic. A single explicit typing context tracks linear and unrestricted assumptions using multiplicities from [exponential_partial.bel](../../lib/algebra/instances/exponential_partial.bel).

The development proves [type preservation](preservation.bel) and weak normalization both [with](weak_norm_ub.bel) and [without](weak_norm.bel) reduction under binders. The [weak](../shared/lambda_dyn_weak.bel) and [strong](../shared/lambda_dyn.bel) reduction relations are defined separately.

```sh
beluga config/case_studies/linear_lambda.cfg
```
