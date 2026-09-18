# Overview

This is an artifact supporting the paper "[Split Decisions: Explicit Contexts for Substructural Languages](https://doi.org/10.1145/3703595.3705888)" (CPP 2025). The artifact contains an implementation in [Beluga](https://github.com/Beluga-lang/Beluga) of CARVe, a general infrastructure for encoding substructural systems and reasoning about their meta-theory. It also includes encodings of several case studies: the linear λ-calculus using HOAS (`linear_lambda`), the linear λ-calculus using de Bruijn levels and an environment-based operational semantics (`closures`), the affine λ-calculus (`affine_lambda`), the linear sequent calculus (`seq`), the bidirectional linear natural deduction calculus (`nd`), and the multiplicative-additive fragment of the session-typed process calculus [CP](https://dl.acm.org/doi/10.1145/2398856.2364568) (`cp`). We implement proofs of various metatheoretical and equivalence properties for each encoding.

## Structure

To ease navigation, the artifact is organized by concept: each directory
collects a topic's definitions and the lemmas about them. `lib` contains the general infrastructure and `case_studies`
the case studies using it. `config` contains configuration files to run the case studies and test the common infrastructure against different multiplicity structures; for convenience, `run_all.cfg` is available to execute all of the tests.

Below is a more detailed breakdown:

    run_all.cfg                          - Collects Beluga source files

    lib/prelude/logic.bel                - Falsity
    lib/prelude/nat.bel                  - Natural numbers
    lib/prelude/nat_order.bel            - Inequality (lt, neq)
    lib/prelude/nat_plus.bel             - Addition

    lib/syntax/obj.bel                   - obj extension point
    lib/syntax/tp.bel                    - tp extension point
    lib/syntax/obj_props.bel             - Lemmas about objects
    lib/syntax/obj_base.bel              - Encodings of object properties, context schema
    lib/syntax/obj_as_var.bel            - Decidable equality (constructor-free obj only)

    lib/algebra                          - Encodings of algebraic structures as multiplicities
    lib/context/base.bel                 - Encodings of substructural contexts and operations on them

    lib/lemmas/mult/                     - Lemmas about multiplicities
    lib/lemmas/upd/                      - Lemmas about update operation
    lib/lemmas/merge/                    - Lemmas about merge operation
    lib/context/exhausted.bel            - Lemmas about exhaustedness
    lib/context/same_elements.bel        - Lemmas about contexts containing the same elements
    lib/context/wellformed.bel, varctx.bel - Lemmas about well-formedness predicates

    case_studies/shared/lambda_*.bel     - Types, terms and dynamics shared by the λ-calculus studies
    case_studies/<study>/statics.bel     - That study's typing rules
    case_studies/<study>/lemmas/         - Lemmas
    case_studies/<study>/<theorem>.bel   - The theorems

## Paper-to-artifact correspondence guide

### Definitions

| Definition | Paper | File / folder | Definition name |
|-|-|-|-|
| Typing contexts | §2, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | lctx |
| Linear multiplicities | §2.1, §4.1 | [lib/algebra/instances/linear.bel](lib/algebra/instances/linear.bel) | mult, •, hal |
| Alternative multiplicity structures | §5 | [lib/algebra/instances/](lib/algebra/instances/) | mult, •, hal |
| Context merge  | §2.1, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | merge |
| Exhaustedness  | §2.2, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | exh |
| Context update | §2.3, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | upd |
| Context element permutation | §2.3, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | exch |
| Context look-up | §2.3, §4.1 | [lib/context/base.bel](lib/context/base.bel)   | lookup_intm, lookup_n |
| Context well-formedness | §4.1 | [lib/context/base.bel](lib/context/base.bel)   | Wf |
| Linear natural deduction terms | §3.1 | [case_studies/seq-nd/tm.bel](case_studies/seq-nd/tm.bel)  | obj |
| Lin. seq. / nat. deduction types | §4.2 | [case_studies/seq-nd/tp.bel](case_studies/seq-nd/tp.bel)  | tp |
| Linear sequent calculus typing judgment | §3.1 | [case_studies/seq-nd/seq.bel](case_studies/seq-nd/seq.bel) | seq |
| Linear natural deduction typing judgment | §3.1 | [case_studies/seq-nd/nd.bel](case_studies/seq-nd/nd.bel)  | syn, chk |
| Simultaneous substitutions  | §3.2 | [case_studies/seq-nd/subst.bel](case_studies/seq-nd/subst.bel) | subst, wf_subst |
| CP processes   | §4.2 | [case_studies/cp/proc.bel](case_studies/cp/proc.bel) | obj |
| CP typing judgment   | §4.2 | [case_studies/cp/statics.bel](case_studies/cp/statics.bel) | oft |
| CP / SCP context relations  | §4.2 | [case_studies/cp/transl.bel](case_studies/cp/transl.bel)  | Enc, Dec |
| Linear λ-calculus terms (de Bruijn) | §4.2 | [case_studies/closures/tm.bel](case_studies/closures/tm.bel) | obj |
| Environment-based operational semantics | §4.2 | [case_studies/closures/dyn.bel](case_studies/closures/dyn.bel) | venv, val, eval |
| Linear λ-calculus typing rules | §4.2 | [case_studies/closures/statics.bel](case_studies/closures/statics.bel) | oft |

### Theorems

| Theorem | Paper | File / folder | Definition name |
|-|-|-|-|
| Algebraic properties of lin. multiplicities | §2.1 | [lib/algebra/instances/linear_props.bel](lib/algebra/instances/linear_props.bel) | mult_func, mult_canc, mult_assoc, mult_comm, mult_zsfree |
| Algebraic properties of context merge | §2.1, Prop 2.1 | [lib/context/merge_identity.bel](lib/context/merge_identity.bel) | merge_id |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_assoc, merge_comm |
| | | [lib/context/merge_cancel.bel](lib/context/merge_cancel.bel) | merge_cancel, merge_cancel_l |
| Well-formedness properties of context merge | §2.1, Prop 2.2 | [lib/context/wellformed.bel](lib/context/wellformed.bel) | wf_merge, wf_split (variants: wf_merge_r, wf_split_r) |
| Algebraic properties of context update | §2.3, Prop 2.3 | [lib/context/update.bel](lib/context/update.bel) | upd_func, upd_refl, upd_symm, upd_trans, upd_conf |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_upd |
| Properties of context look-up | §2.3, Prop 2.4 | [lib/context/update.bel](lib/context/update.bel) | lookup_unique, lookup_upd |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_lookup, merge_lookup2 |
| Well-formedness properties of context update | §2.1, Prop 2.5 | [lib/context/update.bel](lib/context/update.bel) | lookup_neq_nat2var, lookup_neq_var2nat, |
| | | [lib/context/wellformed.bel](lib/context/wellformed.bel) | wf_upd, wf_upd_neq |
| Properties of substitution | §3.2, Lemma 3.1 | [case_studies/seq-nd/lemmas/subst.bel](case_studies/seq-nd/lemmas/subst.bel) | subst_exh, subst_merge, subst_upd |
| Equivalence theorem (seq. / nat. deduction) | §3.2, Thm. 3.2 | [case_studies/seq-nd/thms.bel](case_studies/seq-nd/thms.bel) | seq2nd, chk2seq, syn2seq |
| Extract linearity judgment in CP | §4.2 | [case_studies/cp/lemmas/cp2scp.bel](case_studies/cp/lemmas/cp2scp.bel) | oft_linear |
| Equivalence of CP and SCP | §4.2 | [case_studies/cp/thms.bel](case_studies/cp/thms.bel) | cp2scp, scp2cp |
| Type preservation for linear λ-calculus | §4.2 | [case_studies/closures/thms.bel](case_studies/closures/thms.bel) | preservation |

## Trusted declarations

Two declarations carry `/ trust /` due to limitations of Beluga's current totality checker, namely `cut_admis` in `case_studies/seq-nd/thms.bel` and `dec2enc` in `case_studies/cp/thms.bel`. While their bodies are type-checked, their termination and case coverage were verified manually.

# Installation and execution

This mechanization is compatible with Beluga version 1.1.1.

## Installation

Beluga may be installed using the OCaml package manager ([`opam`](https://opam.ocaml.org/doc/Install.html)):

    >> opam install beluga.1.1.1

It may also be built and installed from source following the instructions at https://github.com/Beluga-lang/Beluga.

## Execution

Once installed, Beluga can be run on the file `run_all.cfg`. The expected total runtime is approximately 0m8s.
