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

All commits to this repository must be signed. This is deliberate: the project
practices the attribution discipline the spec advocates, at the build layer —
every change has a committer, a signature, and a timestamp. A signed commit
sits between L0 (unsigned claim) and L1 (org-verified identity); it is not
conformance, but it is the same discipline applied to the one layer the project
controls. Unsigned commits will not be merged.

## Governance

The specification is maintained by its named editors (see SPEC.md). Editors
decide what lands; objections are resolved by discussion in issues, and a
sustained objection from an implementer is treated as a blocking review.
Neutral stewardship — transfer to a foundation or standards body — is a future
option, not ruled out. The change discipline below defines what a given change
touches; the editors decide whether it lands.

## Change discipline

- Normative clauses (§2), assurance levels (§3), and conformance criteria (§4)
  are the normative core. Changes there bump the minor version and are
  recorded in the changelog.
- Glossary (§5), related work (§6), FAQ (§7), and IPR (§8) are explanatory;
  changes there bump the patch version.

## Versioning

The spec follows semver. A conformance claim uses the canonical form from SPEC.md §4 —
"implements RAE <version> <level>, <tier> tier" (e.g.
"implements RAE 1.0.3 L1, enforcement tier").

## IPR

No patents are asserted over implementations of this practice, and none are
planned. See SPEC.md §8.
