# Contributing to RAE

RAE is an open, versioned specification. Critique is the point — the spec is
only as strong as the scrutiny it survives.

## Ways to contribute

- **Open an issue** for anything that reads as a loophole, an ambiguity, or a
  claim the spec can't back. This is the highest-value contribution.
- **Open a pull request** to amend the spec, add a normative clause, tighten
  conformance criteria, or fix wording.
- **Implement it** in a product or process and report where reality diverged
  from the spec.

## Signed-commit policy

All commits to this repository must be signed. This is deliberate: the spec's
own maintenance history is a live conformance demonstration of its §1 claim —
every change has a committer, a signature, and a timestamp, at L0 (declared)
or better. Unsigned commits will not be merged.

## Change discipline

- Normative clauses (§2), assurance levels (§3), and conformance criteria (§4)
  are the normative core. Changes there bump the minor version and are
  recorded in the changelog.
- Glossary (§5), related work (§6), and FAQ (§7) are explanatory; changes there
  bump the patch version.

## Versioning

The spec follows semver. A conformance claim must cite a specific version
(e.g. "implements RAE 1.0 L1").
