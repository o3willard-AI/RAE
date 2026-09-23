# RAE Adoption Backlog

Where RAE is core, advisory, or peripheral, expressed as the *types* of products
and projects the standard is valuable for — deliberately not a named list of
any particular repositories, so it stays meaningful as the standard spreads.
Tier-1 types are those where RAE is core (operator/sponsor identity +
attribution + an L0 conformance statement); Tier-2 and Tier-3 cover where RAE
is advisory or peripheral.

## Tier 1 — RAE is core

Product and project types that should carry operator/sponsor identity,
attribution, and a conformance statement before they ship:

- **AI-assisted desktop and terminal tools.** A human-in-the-loop assistant with
  a hard execution boundary (the model produces text only; every consequential
  action is operator-initiated) displays an RAE at L0 — a declared, unverified
  identity resolved from the logged-in OS account, with a fixed label that
  cannot drift. The free build claims L0 and is complete on its own; a paid
  tier may separately commit to L1 (org-verified identity, an operator signing
  credential, sponsorship/scope records, and a published L1 conformance
  statement). That L1 work lives in its own distribution — the L0 build is not
  a crippled preview, and the two levels are tracked separately so the split is
  visible.
- **Credential brokers and auth gateways.** A sponsor is bound at enrollment and
  propagated to the audit chain; the broker records *who* authorized *which*
  credential for *what* action.
- **Agent presence and orchestration servers.** Human sponsors are established
  by invite and linked to accounts and their action records.
- **Multi-tier agent orchestrators.** The operator who submits the work and
  reviews the output is the RAE; the product explicitly disambiguates the
  model's capability tier from the RAE assurance level.
- **Infrastructure automation.** The operator is attributable for every
  provision and destroy action, including forced/destructive operations.

A recurring reason to treat something as Tier 1 rather than peripheral: a tool
that *looks* like an installer or local utility but actually instantiates a
full, network-reachable autonomous agent — with irreversible actions (network
disablement, wiping stored credentials) and no recorded accountable human. A
single install command producing an autonomous agent with no attribution is
the exact state RAE exists to close; anything matching that pattern needs the
Tier-1 treatment (operator identity + attribution + conformance) regardless of
how modest its surface appears.

## Tier 2 — RAE is advisory

- **Output-shaping / influence tools.** They shape what an agent produces
  (RAE N4, influenced actions) but take no direct destructive action — a natural
  N4 conformance note when revisited.
- **Observation and monitoring tools.** They watch agent fleets rather than act,
  so attribution is second-order.

## Tier 3 — RAE is peripheral

- **Installers and cross-platform packaging.** Not agentic; no accountability
  gap.
- **Utility scripts and libraries.** No agent instantiation.
- **Backup and ops scripts.** Not agentic.
- **Challenge and evaluation repositories.** Benchmarks and evals, not running
  agents.
