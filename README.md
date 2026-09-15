# Overview

This is an artifact supporting the paper "[Split Decisions: Explicit Contexts for Substructural Languages](https://doi.org/10.1145/3703595.3705888)" (CPP 2025). The artifact contains an implementation in [Beluga](https://github.com/Beluga-lang/Beluga) of CARVe, a general infrastructure for encoding substructural systems and reasoning about their meta-theory. It also includes encodings of several case studies: the linear λ-calculus using HOAS (`linear_lambda`), the linear λ-calculus using de Bruijn levels and an environment-based operational semantics (`closures`), the affine λ-calculus (`affine_lambda`), the linear sequent calculus (`seq`), the bidirectional linear natural deduction calculus (`nd`), and the multiplicative-additive fragment of the session-typed process calculus [CP](https://dl.acm.org/doi/10.1145/2398856.2364568) (`cp`). We implement proofs of various metatheoretical and equivalence properties for each encoding.

## Structure

To ease navigation, the artifact is organized into folders by theme: The `lib` folder contains the general infrastructure, including both definitions (`defs`) and lemmas (`lemmas`). The subfolders of `case_studies` hold the abovementioned case studies; each has a `thms.bel` file containing the main results mechanized. The folder `run` contains configuration files to run the case studies and test the common infrastructure against different multiplicity structures; for convenience, the file `run_all.cfg` is available to execute all of the tests.

Below is a more detailed breakdown:

    run_all.cfg                    - Collects Beluga source files

    lib/prelude/logic.bel          - Encodings of definitions for proofs
    lib/prelude/nat.bel            - Encodings of natural numbers
    lib/prelude/nat_*.bel          - Lemmas about natural numbers
    lib/defs/obj.bel               - Generic encoding of objects
    lib/defs/obj2.bel              - Encodings of object properties, context schema
    lib/defs/tp.bel                - Generic encoding of object-level types
    lib/defs/mult/                 - Encodings of algebraic structures as multiplicities
    lib/defs/ctx.bel               - Encodings of substructural contexts and operations on them

    lib/lemmas/obj.bel, obj2.bel   - Lemmas about objects
    lib/lemmas/mult/               - Lemmas about multiplicities
    lib/lemmas/upd/                - Lemmas about update operation
    lib/lemmas/merge/              - Lemmas about merge operation
    lib/lemmas/exh.bel             - Lemmas about exhaustedness
    lib/lemmas/same_elts.bel       - Lemmas about contexts containing the same elements
    lib/lemmas/wf.bel, varctx.bel  - Lemmas about well-formedness predicates

    case_studies/shared/lambda_tm.bel      - Encoding of terms (linear_lambda, affine_lambda)
    case_studies/shared/lambda_tp.bel      - Encoding of object-level types (linear_lambda, affine_lambda, closures)
    case_studies/shared/lambda_dyn.bel     - Encoding of dynamics (linear_lambda, affine_lambda)
    case_studies/linear_lambda/statics.bel - Encoding of typing rules (linear_lambda)
    case_studies/linear_lambda/lemmas/     - Lemmas about typing judgment (linear_lambda)
    case_studies/linear_lambda/thms.bel    - Proof of type preservation (linear_lambda)

    case_studies/affine_lambda/statics.bel - Encoding of typing rules (affine_lambda)
    case_studies/affine_lambda/lemmas/     - Lemmas about typing judgment (affine_lambda)
    case_studies/affine_lambda/thms.bel    - Proof of type preservation (affine_lambda)

    case_studies/closures/tm.bel      - Encoding of terms (closures)
    case_studies/closures/dyn.bel     - Encoding of dynamics (closures)
    case_studies/closures/statics.bel - Encoding of typing rules (closures)
    case_studies/closures/lemmas/     - Lemmas about typing judgment (closures)
    case_studies/closures/thms.bel    - Proof of type preservation (closures)

    case_studies/seq-nd/tm.bel        - Encoding of terms (nd)
    case_studies/seq-nd/tp.bel        - Encoding of object-level types (seq, nd)
    case_studies/seq-nd/seq.bel       - Encoding of typing rules (seq)
    case_studies/seq-nd/nd.bel        - Encoding of typing rules (nd)
    case_studies/seq-nd/subst.bel     - Encoding of simultaneous substitution (seq, nd)
    case_studies/seq-nd/lemmas/       - Lemmas about seq, nd
    case_studies/seq-nd/thms.bel      - Proof of cut elimination (seq), equivalence of seq and nd

    case_studies/cp/proc.bel          - Encoding of processes and operations on processes (cp)
    case_studies/cp/tp.bel            - Encoding of object-level types (cp)
    case_studies/cp/dyn.bel           - Encoding of dynamics (cp)
    case_studies/cp/statics.bel       - Encoding of typing rules (cp)
    case_studies/cp/scp.bel           - Encoding of Structural CP
    case_studies/cp/transl.bel        - Encoding of translation between CP and SCP contexts
    case_studies/cp/lemmas/           - Lemmas about CP, SCP
    case_studies/cp/thms.bel          - Proof of type preservation (cp), equivalence of CP and SCP

## Paper-to-artifact correspondence guide

### Definitions

| Definition | Paper | File / folder | Definition name |
|-|-|-|-|
| Typing contexts | §2, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | lctx |
| Linear multiplicities | §2.1, §4.1 | [lib/defs/mult/linear.bel](lib/defs/mult/linear.bel) | mult, •, hal |
| Alternative multiplicity structures | §5 | [lib/defs/mult/](lib/defs/mult/) | mult, •, hal |
| Context merge  | §2.1, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | merge |
| Exhaustedness  | §2.2, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | exh |
| Context update | §2.3, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | upd |
| Context element permutation | §2.3, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | exch |
| Context look-up | §2.3, §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | lookup_intm, lookup_n |
| Context well-formedness | §4.1 | [lib/defs/ctx.bel](lib/defs/ctx.bel)   | Wf |
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
| Algebraic properties of lin. multiplicities | §2.1 | [lib/lemmas/mult/linear.bel](lib/lemmas/mult/linear.bel) | mult_func, mult_canc, mult_assoc, mult_comm, mult_zsfree |
| Algebraic properties of context merge | §2.1, Prop 2.1 | [lib/lemmas/merge/halid.bel](lib/lemmas/merge/halid.bel) | merge_id |
| | | [lib/lemmas/merge/main.bel](lib/lemmas/merge/main.bel) | merge_assoc, merge_comm |
| | | [lib/lemmas/merge/cancl.bel](lib/lemmas/merge/cancl.bel) | merge_cancl, merge_cancl_l |
| Well-formedness properties of context merge | §2.1, Prop 2.2 | [lib/lemmas/wf.bel](lib/lemmas/wf.bel) | wf_merge, wf_split (variants: wf_merge_r, wf_split_r) |
| Algebraic properties of context update | §2.3, Prop 2.3 | [lib/lemmas/upd/main.bel](lib/lemmas/upd/main.bel) | upd_func, upd_refl, upd_symm, upd_trans, upd_conf |
| | | [lib/lemmas/merge/main.bel](lib/lemmas/merge/main.bel) | merge_upd |
| Properties of context look-up | §2.3, Prop 2.4 | [lib/lemmas/upd/main.bel](lib/lemmas/upd/main.bel) | lookup_unq, lookup_upd |
| | | [lib/lemmas/merge/main.bel](lib/lemmas/merge/main.bel) | merge_lookup, merge_lookup2 |
| Well-formedness properties of context update | §2.1, Prop 2.5 | [lib/lemmas/upd/main.bel](lib/lemmas/upd/main.bel) | lookup_neq_nat2var, lookup_neq_var2nat, |
| | | [lib/lemmas/wf.bel](lib/lemmas/wf.bel) | wf_upd, wf_upd_neq |
| Properties of substitution | §3.2, Lemma 3.1 | [case_studies/seq-nd/lemmas/subst.bel](case_studies/seq-nd/lemmas/subst.bel) | subst_exh, subst_merge, subst_upd |
| Equivalence theorem (seq. / nat. deduction) | §3.2, Thm. 3.2 | [case_studies/seq-nd/thms.bel](case_studies/seq-nd/thms.bel) | seq2nd, chk2seq, syn2seq |
| Extract linearity judgment in CP | §4.2 | [case_studies/cp/lemmas/cp2scp.bel](case_studies/cp/lemmas/cp2scp.bel) | oft_linear |
| Equivalence of CP and SCP | §4.2 | [case_studies/cp/thms.bel](case_studies/cp/thms.bel) | cp2scp, scp2cp |
| Type preservation for linear λ-calculus | §4.2 | [case_studies/closures/thms.bel](case_studies/closures/thms.bel) | tps |

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
