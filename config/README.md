# Configurations

Beluga configurations list source files and nested configurations in dependency
order.

- [algebra/](algebra/): check the library against individual resource algebras.
- [case_studies/](case_studies/): load each calculus and its supporting lemmas and main results.
- [fragments/](fragments/): shared dependency lists; these are not standalone entry points.

Run from the repository root:

```sh
beluga config/algebra/linear.cfg
beluga config/case_studies/linear_lambda.cfg
beluga run_all.cfg
```

[`run_all.cfg`](../run_all.cfg) checks all resource-algebra and case-study
configurations.
