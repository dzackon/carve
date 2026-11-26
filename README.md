# CARVe: Contexts as Resource Vectors

[![check](https://github.com/dzackon/carve/actions/workflows/check.yml/badge.svg)](https://github.com/dzackon/carve/actions/workflows/check.yml)
[![License](https://img.shields.io/github/license/dzackon/carve)](LICENSE)
[![Paper](https://img.shields.io/badge/CPP_2025-paper-blue)](https://doi.org/10.1145/3703595.3705888)
[![Artifact](https://img.shields.io/badge/CPP_2025-artifact-orange)](https://doi.org/10.5281/zenodo.13777001)

CARVe is a [Beluga](https://github.com/Beluga-lang/Beluga) library for encoding substructural systems and reasoning about their meta-theory. The library was first described in the paper "[Split Decisions: Explicit Contexts for Substructural Languages](https://doi.org/10.1145/3703595.3705888)" (CPP 2025).

The repository also includes several case studies with mechanized meta-theory:

- `linear_lambda`: the linear λ-calculus in HOAS
- `closures`: the linear λ-calculus with de Bruijn levels and an environment-based operational semantics
- `affine_lambda`: the affine λ-calculus
- `seq-nd`: the linear sequent calculus and bidirectional linear natural deduction
- `cp`: the multiplicative-additive fragment of the session-typed process calculus [CP](https://dl.acm.org/doi/10.1145/2398856.2364568)
- `session_pi`: the session-typed π-calculus with co-variables of *[Session Types](https://www.cambridge.org/core/books/session-types/basic-concepts/52FCB7E4BEF6850DC7D63D5F05861FC6)*

For an overview of the library, see [lib/README.md](lib/README.md). For a paper-to-code correspondence guide, refer to [PAPER_ARTIFACT_GUIDE.md](PAPER_ARTIFACT_GUIDE.md).

# Installation and execution

This library is compatible with Beluga 1.1.3, which may be installed using the OCaml package manager ([`opam`](https://opam.ocaml.org/doc/Install.html)):

```sh
opam install beluga.1.1.3
```

Beluga can also be built from source following the instructions at https://github.com/Beluga-lang/Beluga.

To check the library and all case studies, run:

```sh
beluga all.cfg
```
