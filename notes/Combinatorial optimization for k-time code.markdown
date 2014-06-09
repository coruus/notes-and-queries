# Automatic generation of k-time cryptographic code

## Definitions

Let `c:C` be a processor's cache state. Let `s:BYTES[slen]` be secret data
stored in memory. Let `u:BYTES[ulen]` be untrusted data stored in memory.

For a sequence of machine instructions, `f:LIST[INSTR]`, define
`trace(f, s, u, c)` as the set of all admissible[^admis] execution
orders of `f` given specific values of `c`, `u`, and `s`.

(And define `trace(f, s, u, c)` as `union(trace(f, s, u, c),
forall(s:S)` and so on; i.e., probabilistic marginalization notation.)

Assume a cycle counter or measure of absolute time exists. Then
`cycles(trace(f, c, u, s))` is the set of all admissible cycle counts
of the execution of `f` on specific values.

An algorithm executes in strong k-time if

    cycles(trace(f, s | c, u)) == cycles(trace(f | s, c, u))

(How to weaken for cache states that do not depend on s?)

## Strategy

Combinatorially compile C code under different optimization options. Use
decompilation-based proof techniques to prove or disprove that control flow
(and instruction timing) does not depend on the value of the secret data.
Only accept a compilation for which the k-time condition is true.

See [CakeML][CakeML.org] for relevant work by Magnus O. Myreen.

[^admis]: Where admissible means permissible under a suitably low-level
model of the processor.

