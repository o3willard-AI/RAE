# Registered Accountable Entity (RAE)

**Version 1.0.2** — 2026-09-18 — **Status: Draft for public critique.**

This is an open specification. Issues and pull requests are welcome — see
[CONTRIBUTING.md](CONTRIBUTING.md). If you implement RAE, cite the version you
conform to. The spec is a framework any product, service, or process can
implement and be judged against; it is not a product badge.

The key words MUST, MUST NOT, SHOULD, SHOULD NOT are to be interpreted as
described in RFC 2119.

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
  silent. A system MUST declare which tier it operates at.
- **N4 — Influenced actions.** A human who acts on an agent's output is
  trivially the RAE of their own action; the agent's contribution is recorded
  as *provenance metadata* ("agent-influenced"), not as separate RAE
  attribution. Two RAEs is no RAE. Where the influencing agent's output was
  produced under a sponsorship, the provenance record MUST reference that
  sponsorship record, or explicitly mark it unresolved. An unresolved marking
  is distinct from an absent reference; a reference that cannot be resolved
  from this system (for example, a sponsorship held in a registry the system
  cannot read) MUST be marked unresolvable rather than not-yet-resolved. The
  reference is descriptive: it confers no accountability on the referenced
  sponsor for the influenced action, whose RAE remains the acting human alone.
  Provenance references are depth-1; deeper chains are resolved through the
  registry, not carried in the record.
- **N5 — Natural-person resolution.** "Entity" remains the term of art, but
  every RAE resolves to a single natural person. An organization participates
  only through designated humans; responsibility never terminates at the
  organizational boundary.
- **N6a — Sponsorship scope (runtime).** A standing sponsorship satisfies N1
  only if the specific action falls within the sponsorship's declared scope
  expression, evaluable at execution time. An action outside the declared scope
  is unattributed under N3.
- **N6b — Sponsorship breadth (registry-time).** The declared scope MUST be
  narrow enough to be meaningful, assessed at registration and on review. A
  sponsorship whose scope cannot be tested against a concrete action does not
  establish pre-attribution. Registries SHOULD record scope breadth, measured
  in aggregate across an RAE's sponsorships, so that over-broad or enumerated
  sponsorship is detectable.
- **N7 — Sponsorship lifecycle.** A standing sponsorship is a relationship
  with a lifecycle. When a sponsor leaves the organization or their authority
  is withdrawn, the sponsorship lapses: no new actions are attributed to them,
  and their standing scope is treated as revoked. Actions already attributed to
  them remain their responsibility. Standing sponsorships SHOULD carry an
  expiry, and a system MUST define what happens to in-flight actions when a
  sponsorship is revoked mid-execution (attributed per the record at execution
  time).
- **N8 — Agent-to-agent delegation.** An action taken by an agent invoked by
  another agent is attributable to the RAE whose sponsorship covers the
  invoking agent, unless the invoked agent acts under its own sponsorship. The
  covering sponsorship's scope (N6) governs: a delegated action the sponsor
  could not have anticipated is unattributed under N3. Attribution resolves to
  the nearest covering sponsorship and never vanishes into the chain.

## 3. Assurance levels

| Level | Name | Meaning |
|---|---|---|
| L0 | Declared | Claimed identity only (e.g., a bare OS username). Below the registration bar — a seed of the practice, not the practice. |
| L1 | Registered | Identity verified by the deploying organization + a signing credential bound to authorization records. |
| L2 | Registered (verified) | Identity verified by a third party (KYC/eID-grade) + a tamper-evident registry, where "tamper-evident" means the registry is verifiable by an independent party per the Proof glossary test. |

## 4. Conformance

A product, service, or process may claim to **display an RAE at L0** (declared,
unverified) — the display-only claim — or to **implement RAE** at L1 or L2, with
an explicit enforcement tier ("implements RAE L1, enforcement tier"). L0 never
takes the verb *implement*: it asserts only the display criterion, not the RAE
practice, whose attribution machinery (N1/N3/N4/N6/N7/N8) begins at L1. Claims
without a level are non-conformant. At every level, the RAE is a single natural
person (N5) and never an agent (N2).

A conformant implementation MUST publish a **conformance statement** recording:
the spec version, the claimed level, the enforcement tier (N3), the
clause-by-clause status (enforced / informational / not applicable), and the
location of its proof records. A claim without a published conformance
statement is not independently judgeable.

| Level | Minimum criteria |
|---|---|
| L0 (declared) — display only | Displays the declared identity of the accountable person with the explicit label "declared, unverified (L0)"; makes no claim of verification or registration. |
| L1 (registered) | Organization-verified identity; a signing credential bound to authorization records; pre-attribution records (N1) naming the sponsorship or approval and its scope (N6); no-RAE handling per N3 with a declared tier; provenance carrying sponsorship references per N4; a published conformance statement. |
| L2 (registered, verified) | Everything in L1, plus third-party-verified identity (KYC/eID-grade) and a tamper-evident registry verifiable by an independent party, per the Proof glossary test. |

Any UI or API surface that displays an RAE MUST state its level and tier
explicitly. Conformance is self-declared; this spec supplies the criteria — and
requires the statement — against which a self-declaration can be independently
judged.

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
  an agent or action class (subject to N6 and N7). *Approval*: specific
  authorization of a particular action. Either establishes the RAE link; the
  record MUST show which one covered a given action.
- **Registered (the institution)** — Recorded in a registry that binds
  identity to authorization records so attribution outlives the runtime.
  Graded by the assurance levels in §3.
- **Proof (the mechanism)** — Evidence sufficient for an independent party to
  reconstruct person → authorization → action. L0 = unsigned claim; L1 =
  cryptographic signature over the action/approval record by an org-verified
  credential + timestamped log; L2 = as L1, over a tamper-evident registry
  verifiable by an independent party. The core definition never requires a
  specific level — only that *some declared level is met and stated*.

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
- **in-toto** is arguably a closer structural cousin than SLSA: it attributes
  individual pipeline steps to identities, the way RAE attributes actions to
  natural persons.
- **Non-repudiation** (ISO/IEC 27000) is the classic infosec name for RAE's
  proof leg: assurance that an action's origin and approval cannot be denied.
  RAE's L1/L2 proof ("non-repudiation of approval/origin") anchors here. Note
  that non-repudiation covers the cryptographic portion only; L2's third-party
  identity verification and the registry institution sit outside classic
  non-repudiation.
- **Four-eyes / separation of duties / named-approver change management**
  (ITIL, SOX) is the existing enterprise practice RAE most resembles — the
  easiest on-ramp for the buyer RAE is written for.
- **NIST AI RMF — the GOVERN function** is squarely about assigning
  accountability for AI systems; RAE is a concrete mechanism for that
  assignment.
- **ISO/IEC 42001** (AI management systems) is the standard organizations will
  actually be certified against; its accountability requirements are ones RAE
  maps onto directly.
- **EU AI Act** — Article 14 requires human oversight of high-risk AI systems
  without specifying how to operationalize it; RAE is a concrete
  operationalization of the accountability side of that oversight. Article 12
  (record-keeping) maps to RAE's proof leg (signed, timestamped, traceable
  records). These citations are signposts for readers seeking regulatory
  framing, not compliance claims; RAE itself is jurisdiction-neutral.

## 7. FAQ

**Can an unowned project ship an accountability framework?**

Yes — because the project practices the same attribution discipline it
advocates, at the build layer, using the regime RAE's own lineage cites. Every
change has a committer, a signature, and a timestamp. This is not conformance —
RAE governs *agent* actions, and unaided human commits to a spec repo sit
outside its subject matter — but it demonstrates the discipline at the layer
the project does control.

**Is a signed commit L0?**

No. L0 is an unsigned claim. A cryptographic signature bound to a key is
stronger than L0 (a signature is present) but short of L1 (no org-verified
identity). The signed-commit policy sits between L0 and L1.

## 8. IPR

This specification is licensed under Apache-2.0. No patents are asserted over
implementations of this practice, and none are planned. The specification and
its reference implementations are published openly in part to establish prior
art.

## Changelog

- **1.0.2** (2026-09-18): second audit round — verb split by level in §4
  (display@L0 vs implement@L1/L2), enforcement tier as a declared property (N3,
  §4), conformance-statement artifact (§4), N6 split into N6a (runtime
  scope-match) and N6b (registry-time breadth), new N7 (sponsorship lifecycle:
  revocation/expiry/succession) and N8 (agent-to-agent delegation), L2 registry
  tied to the Proof test, unresolvable-vs-unresolved in N4, four prior-art
  additions (§6), dogfooding tightened and signed-commit level corrected (§7),
  IPR statement (§8).
- **1.0.1** (2026-09-18): one-pass review (hermes-ox-chap) — L0 conformance
  scope clarified (display-only, not implementation), N2/N5 conformance
  lead-in added, RFC 2119 casing normalized, N4 unresolved-vs-absent made
  explicit.
- **1.0.0** (2026-09-18): Initial public release. Incorporates the converged
  definition (v3), normative clauses N1–N6 (including the sponsorship-
  granularity clause N6 and the amended N4 provenance-reference clause),
  graded assurance levels, a Conformance section, and related work.
