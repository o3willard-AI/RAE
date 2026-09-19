# Registered Accountable Entity (RAE)

A specification for attributing actions taken by an AI agent — or materially
shaped by one — to a single identified natural person who sponsored or
approved them in advance, regardless of the degree of automation.

The full specification lives in [SPEC.md](SPEC.md). It defines a core
definition, normative clauses (N1–N6), three graded assurance levels
(L0/L1/L2), and explicit conformance criteria any implementation can be judged
against.

## Why this exists

Automation transfers *execution*, never *responsibility*. RAE is a vocabulary
for making the accountable human explicit — with proof — rather than letting
accountability evaporate into "the AI did it."

## How to engage

- Read the spec: [SPEC.md](SPEC.md)
- Implement it, cite the version, and tell us where it falls short — issues
  and pull requests are welcome: [CONTRIBUTING.md](CONTRIBUTING.md)
- This spec is versioned. Conformance claims use the canonical form from
  SPEC.md §4 — "implements RAE <version> <level>, <tier> tier"; an unleveled
  claim is non-conformant.

## Related work

The level ladder follows the SLSA pattern; the proof leg is non-repudiation;
the oversight framing connects to EU AI Act Articles 12 and 14. See SPEC.md §6.

## License

Apache-2.0. See [LICENSE](LICENSE).
