# lowdisc

[![crates.io](https://img.shields.io/crates/v/lowdisc.svg)](https://crates.io/crates/lowdisc)
[![Documentation](https://docs.rs/lowdisc/badge.svg)](https://docs.rs/lowdisc)
[![CI](https://github.com/arclabs561/lowdisc/actions/workflows/ci.yml/badge.svg)](https://github.com/arclabs561/lowdisc/actions/workflows/ci.yml)

Low-discrepancy sequences.

`lowdisc` provides Halton sequences, Sobol sequences, and hash-based
Owen-scrambled Sobol points for quasi-Monte Carlo integration and deterministic
sampling designs.

Dual-licensed under MIT or Apache-2.0.

[crates.io](https://crates.io/crates/lowdisc) | [docs.rs](https://docs.rs/lowdisc)

```toml
[dependencies]
lowdisc = "0.1.1"
```

```rust
let pts = lowdisc::sobol_sequence(4, 2);
assert_eq!(pts.len(), 4);
assert!((pts[0][0] - 0.5).abs() < 1e-12);
assert!((pts[0][1] - 0.5).abs() < 1e-12);
```

## Operations

| Function / Type | Description |
|----------------|-------------|
| `halton_point` | Single Halton point in `[0, 1)^d` |
| `halton_sequence` | Halton sequence using the first 20 prime bases |
| `SobolGenerator` | Incremental Sobol generator |
| `sobol_sequence` | Sobol sequence, skipping the origin |
| `sobol_scrambled` | Hash-based Owen-scrambled Sobol sequence |
