# Overview

This is an artifact supporting the paper "[Split Decisions: Explicit Contexts for Substructural Languages](https://doi.org/10.1145/3703595.3705888)" (CPP 2025). The artifact contains an implementation in [Beluga](https://github.com/Beluga-lang/Beluga) of CARVe, a generic infrastructure for encoding substructural systems and reasoning about their meta-theory. It also includes encodings of several case studies: the linear λ-calculus using HOAS (`linear_lambda`), the linear λ-calculus using de Bruijn levels and an environment-based operational semantics (`closures`), the affine λ-calculus (`affine_lambda`), the linear sequent and bidirectional linear natural deduction calculi (`seq-nd`), the multiplicative-additive fragment of the classical session-typed process calculus [CP](https://dl.acm.org/doi/10.1145/2398856.2364568) (`cp`), and the session-typed π-calculus with co-variables of *[Session Types](https://www.cambridge.org/core/books/session-types/basic-concepts/52FCB7E4BEF6850DC7D63D5F05861FC6)*. We implement proofs of various meta-theoretical and equivalence properties for each encoding.

For an overview of the library structure, refer to [lib/README.md](lib/README.md). For a paper-to-artifact correspondence guide, refer to [PAPER_ARTIFACT_GUIDE.md](PAPER_ARTIFACT_GUIDE.md).

# Installation and execution

This mechanization is compatible with Beluga version 1.1.3. Beluga may be installed using the OCaml package manager ([`opam`](https://opam.ocaml.org/doc/Install.html)):

```sh
opam install beluga.1.1.3
```

It may also be built and installed from source following the instructions at https://github.com/Beluga-lang/Beluga.

Once installed, Beluga can be run on the file `run_all.cfg`. The expected total runtime is approximately 0m13s.

```sh
beluga run_all.cfg
```
