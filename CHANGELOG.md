# Changelog

## [Unreleased]

## [0.1.2] - 2026-10-09

### Changed

- `sobol_scrambled` points change for a fixed seed. The fixes below alter its
  output: index 0 is kept, the scramble hash includes tree depth, and (for
  `d >= 3`) Sobol dimensions 3 to 5 use corrected direction numbers. Callers that
  stored scrambled points or seeds expecting reproducible values across
  versions will see different points.

### Fixed

- Sobol direction numbers for dimensions 3, 4 and 5 now match the Joe & Kuo
  `new-joe-kuo-6.21201` table. `sobol_sequence` and `SobolGenerator` output in
  those dimensions changes; the first points now equal the publisher's
  reference generator.
- `sobol_scrambled` keeps index 0 instead of skipping it. After scrambling it
  is a uniform point, not the origin, and keeping it makes the first `2^m`
  points a net (Owen 2020, "On dropping the first Sobol' point").
  `sobol_sequence` still skips the origin.
- The Owen scramble hash now includes the tree depth. Previously prefix 0 at
  depth `i` reused the random bit of prefix 0 at depth `i - 1`, so the top
  two scrambled bits of `x = 0` could never be `01` and scrambled points were
  not uniform.
- Docs state that the embedded direction numbers support up to 8 dimensions,
  not 1111.

## [0.1.1] - 2026-07-07

### Changed

- Added a changelog to the published package.

## [0.1.0] - 2026-07-07

### Added

- Initial low-discrepancy sequence implementations: Halton, Sobol, and
  hash-based Owen-scrambled Sobol.
