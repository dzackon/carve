
# Paper-to-artifact correspondence guide

## Definitions

| Definition | Paper | File | Definition name |
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
| Linear natural deduction terms | §3.1 | [case_studies/seq-nd/definitions/tm.bel](case_studies/seq-nd/definitions/tm.bel)  | obj |
| Lin. seq. / nat. deduction types | §4.2 | [case_studies/seq-nd/definitions/tp.bel](case_studies/seq-nd/definitions/tp.bel)  | tp |
| Linear sequent calculus typing judgment | §3.1 | [case_studies/seq-nd/definitions/seq.bel](case_studies/seq-nd/definitions/seq.bel) | seq |
| Linear natural deduction typing judgment | §3.1 | [case_studies/seq-nd/definitions/nd.bel](case_studies/seq-nd/definitions/nd.bel)  | syn, chk |
| Simultaneous substitutions  | §3.2 | [case_studies/seq-nd/definitions/subst.bel](case_studies/seq-nd/definitions/subst.bel) | subst, wf_subst |
| CP processes   | §4.2 | [case_studies/cp/definitions/proc.bel](case_studies/cp/definitions/proc.bel) | obj |
| CP typing judgment   | §4.2 | [case_studies/cp/definitions/statics.bel](case_studies/cp/definitions/statics.bel) | oft |
| CP / SCP context relations  | §4.2 | [case_studies/cp/definitions/transl.bel](case_studies/cp/definitions/transl.bel)  | Enc, Dec |
| Linear λ-calculus terms (de Bruijn) | §4.2 | [case_studies/closures/definitions/tm.bel](case_studies/closures/definitions/tm.bel) | obj |
| Environment-based operational semantics | §4.2 | [case_studies/closures/definitions/dyn.bel](case_studies/closures/definitions/dyn.bel) | venv, val, eval |
| Linear λ-calculus typing rules | §4.2 | [case_studies/closures/definitions/statics.bel](case_studies/closures/definitions/statics.bel) | oft |

## Theorems

| Theorem | Paper | File | Definition name |
|-|-|-|-|
| Algebraic properties of lin. multiplicities | §2.1 | [lib/algebra/instances/linear_props.bel](lib/algebra/instances/linear_props.bel) | mult_func, mult_cancel, mult_assoc, mult_comm, mult_zsfree |
| Algebraic properties of context merge | §2.1, Prop 2.1 | [lib/context/merge_identity.bel](lib/context/merge_identity.bel) | merge_id |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_assoc, merge_comm |
| | | [lib/context/merge_cancel.bel](lib/context/merge_cancel.bel) | merge_cancel, merge_cancel_l |
| Well-formedness properties of context merge | §2.1, Prop 2.2 | [lib/context/wellformed.bel](lib/context/wellformed.bel) | wf_merge, wf_split (variants: wf_merge_r, wf_split_r) |
| Algebraic properties of context update | §2.3, Prop 2.3 | [lib/context/update.bel](lib/context/update.bel) | upd_func, upd_refl, upd_symm, upd_trans, upd_conf |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_upd |
| Properties of context look-up | §2.3, Prop 2.4 | [lib/context/update.bel](lib/context/update.bel) | lookup_unique, lookup_upd |
| | | [lib/context/merge.bel](lib/context/merge.bel) | merge_lookup, merge_lookup2 |
| Well-formedness properties of context update | §2.1, Prop 2.5 | [lib/context/update.bel](lib/context/update.bel) | lookup_neq_var2nat |
| | | [lib/context/update_wf.bel](lib/context/update_wf.bel) | lookup_neq_nat2var |
| | | [lib/context/wellformed.bel](lib/context/wellformed.bel) | wf_upd |
| | | [lib/context/wellformed_rename.bel](lib/context/wellformed_rename.bel) | wf_upd_neq |
| Properties of substitution | §3.2, Lemma 3.1 | [case_studies/seq-nd/lemmas/subst.bel](case_studies/seq-nd/lemmas/subst.bel) | subst_exh, subst_merge, subst_upd |
| Equivalence theorem (seq. / nat. deduction) | §3.2, Thm. 3.2 | [case_studies/seq-nd/equivalence.bel](case_studies/seq-nd/equivalence.bel) | seq2nd, chk2seq, syn2seq |
| Extract linearity judgment in CP | §4.2 | [case_studies/cp/lemmas/cp2scp.bel](case_studies/cp/lemmas/cp2scp.bel) | oft_linear |
| Equivalence of CP and SCP | §4.2 | [case_studies/cp/equivalence.bel](case_studies/cp/equivalence.bel) | cp2scp, scp2cp |
| Type preservation for linear λ-calculus | §4.2 | [case_studies/closures/preservation.bel](case_studies/closures/preservation.bel) | preservation |
