# Session-typed π-calculus

A [session-typed π-calculus](definitions/proc.bel) with binary restriction, parallel composition, channel passing and close/wait processes.

The development proves [canonical forms](canonical_form.bel), [type preservation](preservation.bel) and [absence of prefix-mismatch errors](safety.bel), including after reduction.

```sh
beluga config/case_studies/session_pi.cfg
```
