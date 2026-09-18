# Registered Accountable Entity (RAE)

**Version 1.0.1** — 2026-09-18 — **Status: Draft for public critique.**

The key words MUST, MUST NOT, SHOULD, SHOULD NOT are to be interpreted as
described in RFC 2119.

This is an open specification. Issues and pull requests are welcome — see
[CONTRIBUTING.md](CONTRIBUTING.md). If you implement RAE, cite the version you
conform to. The spec is a framework any product, service, or process can
implement and be judged against; it is not a product badge.

---

## 1. Core definition

**Registered Accountable Entity (RAE):** The single identified natural person
to whom an action taken by an AI agent or agentic process is attributable, and
who is answerable for that action by virtue of advance sponsorship or approval
covering it — attribution that holds regardless of the degree or speed of
automation employed. How firmly the attribution is established varies by
assurance level (see §3); that it is established, and to exactly one person, is
what the term asserts.

**Why it matters:** An action with no RAE is an action no one owns. The
practice exists to make that state impossible — or at minimum loudly visible —
wherever RAE is enforced. Regulations increasingly require human oversight of
automated action without specifying how to operationalize it; RAE is one
concrete operationalization (see §6, Related work).

## 2. Normative clauses

- **N1 — Pre-attribution.** Registration precedes the action. "In advance" is
  load-bearing: naming someone after the fact is *post-hoc audit attribution*,
  not RAE. That is the line between accountability and blame-allocation.
- **N2 — Agents are never RAEs.** An agent is the *subject* of attribution,
  never the *object*. This forecloses the "the AI decided" deferral — the
  failure mode RAE exists to eliminate.
- **N3 — The no-RAE invariant.** In a system practicing RAE, every agent
  action has an RAE at execution time. Actions without one are *blocked*
  (enforcement tier) or *flagged unattributed* (informational tier) — never
  silent.
- **N4 — Influenced actions.** A human who acts on an agent's output is
  trivially the RAE of their own action; the agent's contribution is recorded
  as *provenance metadata* ("agent-influenced"), not as separate RAE
  attribution. Two RAEs is no RAE. Where the influencing agent's output was
  produced under a sponsorship, the provenance record MUST reference that
  sponsorship record, or explicitly mark it unresolved, where an unresolved marking is distinct from an absent reference. This reference is
  descriptive: it confers no accountability on the referenced sponsor for the
  influenced action, whose RAE remains the acting human alone. Provenance
  references are depth-1; deeper chains are resolved through the registry, not
  carried in the record.
- **N5 — Natural-person resolution.** "Entity" remains the term of art, but
  every RAE resolves to a single natural person. An organization participates
  only through designated humans; responsibility never terminates at the
  organizational boundary.
- **N6 — Sponsorship granularity.** A standing sponsorship satisfies N1 only
  if its action class is specified narrowly enough that the sponsor could
  reasonably have anticipated the target, nature, and consequence of the
  specific action it covered. A sponsorship whose scope cannot be tested
  against a concrete action does not establish pre-attribution; the system
  treats the action as unattributed under N3. Registries SHOULD record scope
  breadth so that over-broad sponsorship is detectable.

## 3. Assurance levels

| Level | Name | Meaning |
|---|---|---|
| L0 | Declared | Claimed identity only (e.g., a bare OS username). Below the registration bar — a seed of the practice, not the practice. |
| L1 | Registered | Identity verified by the deploying organization + a signing credential bound to authorization records. |
| L2 | Registered (verified) | Identity verified by a third party (KYC/eID-grade) + a tamper-evident registry. |

## 4. Conformance

A product, service, or process may claim to "implement RAE" only with an
explicit assurance level — e.g. "implements RAE L1". Claims without a level are
non-conformant. At every level, the RAE is a single natural person (N5)
and never an agent (N2). An L0 claim asserts only the display criterion; it
does not assert implementation of the RAE practice, whose attribution
machinery (N1/N3/N4/N6) begins at L1.

| Level | Minimum conformance criteria |
|---|---|
| L0 (declared) | Displays the declared identity of the accountable person with the explicit label "declared, unverified (L0)"; makes no claim of verification or registration. |
| L1 (registered) | Organization-verified identity; a signing credential bound to authorization records; pre-attribution records (N1) naming the sponsorship or approval and its scope (N6); no-RAE handling per N3 (blocked or flagged, never silent); provenance carrying sponsorship references per N4. |
| L2 (registered, verified) | Everything in L1, plus third-party-verified identity (KYC/eID-grade) and a tamper-evident registry; proof sufficient for independent reconstruction, per the Proof glossary entry. |

Any UI or API surface that displays an RAE MUST state its level explicitly.
Conformance is self-declared; this spec supplies the criteria against which a
self-declaration can be independently judged.

## 5. Glossary

- **Attribution (the property)** — The durable, independently reconstructable
  linkage of a specific action to a specific person. The core asserts
  attribution as a *property*; the assurance ladder carries the *mechanism*.
- **Accountable / Answerable** — Obligated to explain, justify, and bear the
  consequences of the action. Non-delegable to software: automation transfers
  *execution*, never *answerability*. Operational accountability only — the
  term neither confers nor disclaims legal liability, which is
  jurisdiction-specific.
- **In advance (pre-attribution)** — Sponsorship or approval recorded before
  the action executes (N1).
- **Entity vs. natural person** — "Entity" kept in the name as registry/legal
  idiom; normatively pinned to "natural person," the precise legal term that
  cleanly excludes organizations.
- **Agent** — A software system that selects and executes actions toward a
  goal with some autonomy (tool calls, code execution, message sending, system
  changes).
- **Agentic process** — Any workflow in which one or more agents act, or whose
  outputs *materially shape* a subsequent action. "Materially shapes" = the
  agent output changed the action's target, nature, or consequence, such that
  a reasonable person would treat the action as co-determined.
- **Sponsored / Approved** — *Sponsorship*: standing advance authorization of
  an agent or action class (subject to N6). *Approval*: specific authorization
  of a particular action. Either establishes the RAE link; the record MUST
  show which one covered a given action.
- **Registered (the institution)** — Recorded in a registry that binds
  identity to authorization records so attribution outlives the runtime.
  Graded by the assurance levels in §3.
- **Proof (the mechanism)** — Evidence sufficient for an independent party to
  reconstruct person → authorization → action. L0 = unsigned claim; L1 =
  cryptographic signature over the action/approval record by an org-verified
  credential + timestamped log; L2 = as L1, over a tamper-evident registry.
  The core definition never requires a specific level — only that *some
  declared level is met and stated*.

## 6. Design lineage and related work

Attribution regimes that inform this spec: git signed commits (author +
credential + signature) and RACI (exactly one accountable party). Three-leg
separation is maintained throughout: **attribution (property) / proof
(mechanism) / registration (institution)** — conflating these is what lets
"we have audit logs" products overclaim accountability.

Related work:

- **SLSA** (Supply-chain Levels for Software Artifacts) is the structural
  precedent for a level-based assurance ladder — each declared level names an
  explicit mechanism, and claims state which level is met. RAE borrows the
  ladder *pattern*, not SLSA's subject matter: SLSA levels measure supply-chain
  build integrity; RAE levels measure identity-verification strength and proof
  strength. The sibling project Chaperone already invokes SLSA — the ladder is
  native to this ecosystem.
- **Non-repudiation** (ISO/IEC 27000) is the classic infosec name for RAE's
  proof leg: assurance that an action's origin and approval cannot be denied.
  RAE's L1/L2 proof ("non-repudiation of approval/origin") anchors here. Note
  that non-repudiation covers the cryptographic portion only; L2's third-party
  identity verification and the registry institution sit outside classic
  non-repudiation.
- **EU AI Act** — Article 14 requires human oversight of high-risk AI systems
  without specifying how to operationalize it; RAE is a concrete
  operationalization of the accountability side of that oversight. Article 12
  (record-keeping) maps to RAE's proof leg (signed, timestamped, traceable
  records). These citations are signposts for readers seeking regulatory
  framing, not compliance claims; RAE itself is jurisdiction-neutral.

## 7. FAQ

**Can an unowned project ship an accountability framework?**

Yes — because the spec's own maintenance dogfoods its attribution story, on
two layers. (1) *Build provenance*: authorship of the spec is attributed by
signed git commits — the same regime RAE's lineage cites. Every change has a
committer, a signature, and a timestamp. (2) *Runtime action attribution*:
what RAE governs, applied in deployed systems — not to the spec's own
authorship. An unowned project fully satisfies layer 1 and builds tooling for
layer 2 rather than operating systems where layer 2 applies.

## Changelog

- **1.0.1** (2026-09-18): one-pass review fixes — L0 conformance scope
  (display-only, not implementation), N2/N5 conformance lead-in, RFC 2119
  casing normalized, N4 unresolved-vs-absent made explicit.
- **1.0.0** (2026-09-18): Initial public release. Incorporates the converged
  definition (v3), normative clauses N1–N6 (including the sponsorship-
  granularity clause N6 and the amended N4 provenance-reference clause),
  graded assurance levels, a Conformance section, and related work.
