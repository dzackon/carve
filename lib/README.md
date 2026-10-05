# Structure

To ease navigation, the artifact is organized by concept: each directory
collects a topic's definitions and the lemmas about them. [`lib`](../lib/)
contains the general infrastructure and [`case_studies`](../case_studies/) the
case studies using it. [`config`](../config/) contains configuration files to
run the case studies and test the common infrastructure against different
multiplicity structures; for convenience, [`run_all.cfg`](../run_all.cfg) is
available to execute all of the tests.

Below is a more detailed breakdown:

| File or directory | Description |
| --- | --- |
| `run_all.cfg` | Top-level entry point: runs every configuration below |
| `config/algebra/*.cfg` | The common infrastructure, checked against each multiplicity structure |
| `config/case_studies/*.cfg` | One configuration per case study |
| `config/fragments/` | Shared pieces included by the configurations above (not run on their own) |
| `lib/prelude/logic.bel` | Falsity |
| `lib/prelude/nat.bel` | Natural numbers |
| `lib/prelude/nat_order.bel` | Inequality (`lt`, `neq`) |
| `lib/prelude/nat_plus.bel` | Addition |
| `lib/syntax/obj.bel` | `obj` extension point |
| `lib/syntax/tp.bel` | `tp` extension point |
| `lib/syntax/obj_base.bel` | Encodings of object properties, context schema |
| `lib/syntax/obj_props.bel` | Lemmas about objects |
| `lib/syntax/obj_as_var.bel` | Decidable equality (constructor-free `obj` only) |
| `lib/algebra/interface.bel` | Generic multiplicity interface and conditional algebraic laws |
| `lib/algebra/props.bel` | Lemmas derivable from the interface alone |
| `lib/algebra/instances/` | Multiplicity structures (X.bel) and their properties (X_props.bel) |
| `lib/context/base.bel` | Substructural contexts and the operations on them |
| `lib/context/update.bel` | Positional update and look-up lemmas |
| `lib/context/update_wf.bel` | Optional name-based update lemmas requiring Wf |
| `lib/context/merge*.bel` | Lemmas about merge |
| `lib/context/exchange.bel` | Lemmas about exchange |
| `lib/context/delete.bel` | Deleting an entry of multiplicity 𝟘 |
| `lib/context/exhausted.bel` | Lemmas about exhaustedness |
| `lib/context/linear_lookup.bel` | Look-up corollaries for linear / affine systems |
| `lib/context/same_elements.bel` | Lemmas about contexts containing the same elements |
| `lib/context/wellformed*.bel, varctx.bel` | Lemmas about well-formedness predicates |
| `case_studies/shared/lambda_*.bel` | Types, terms and dynamics shared by the λ-calculus studies |
| `case_studies/<study>/definitions/` | A study's syntax, typing rules and dynamics |
| `case_studies/<study>/lemmas/` | Its lemmas |
| `case_studies/<study>/<property>.bel` | Its theorems |
