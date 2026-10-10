# lowdisc

[![crates.io](https://img.shields.io/crates/v/lowdisc.svg)](https://crates.io/crates/lowdisc)
[![Documentation](https://docs.rs/lowdisc/badge.svg)](https://docs.rs/lowdisc)

Low-discrepancy sequences.

`lowdisc` provides Halton sequences, Sobol sequences, and hash-based
Owen-scrambled Sobol points for quasi-Monte Carlo integration and deterministic
sampling designs.

For Sobol points in more than 8 dimensions use `sobol_burley` (seedable
Owen-scrambled Sobol, up to 256 dimensions, `f32` output); in Python,
`scipy.stats.qmc` covers Sobol, Halton and discrepancy measures.

Dual-licensed under MIT or Apache-2.0.

```toml
[dependencies]
lowdisc = "0.1.2"
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
| `SobolGenerator` | Incremental Sobol generator, up to 8 dimensions |
| `sobol_sequence` | Sobol sequence, skipping the origin, up to 8 dimensions |
| `sobol_scrambled` | Hash-based Owen-scrambled Sobol sequence, keeping index 0, up to 8 dimensions |
