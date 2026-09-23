# RAE Adoption Backlog

Status of RAE adoption across `o3willard-AI`. Tier-1 repos are adopted
(operator/sponsor identity + attribution + an L0 conformance statement). This
file tracks the deferred Tier-2 and Tier-3 considerations, plus one
reclassification from the 2026-09 deep-dive review.

## Tier-1 — adopted (operator/sponsor identity + attribution + L0 conformance statement)

- **PairAdmin** — terminal + AI assistant. Displays an RAE at L0 (declared,
  unverified) via the logged-in OS account in the Settings Security tab
  (`RAE_L0_SUFFIX`, hardcoded so the label can't drift); attribution is
  structural via the assistant's hard execution boundary (the model produces
  text only; every action is operator-initiated). Claim discipline in
  `docs/security/rae.md`, SECURITY.md, and `docs/MESSAGING.md` §2.10/§3;
  voluntary L0 `RAE-CONFORMANCE.md` at the repo root. **Distinct from the rest
  of this list:** PairAdmin has a planned *paid enterprise tier* whose stated
  goal is to reach **RAE L1** (org-verified identity via SSO + an operator
  signing credential + sponsorship/scope records + a published L1 conformance
  statement). That L1 work is tracked in the separate private
  `PairAdmin-Enterprise` repo, not here; the open-source build's claim stays
  L0 and is complete on its own (not a crippled preview). Recorded so the L0
  (open) vs L1 (enterprise) split for this one product is visible in the
  portfolio view.
- **Chaperone** — credential broker. Sponsor bound at enrollment, propagated
  to the audit chain; L0 conformance statement.
- **Machina-Parousia** — agent presence server. Human sponsor via invite
  (`sponsor_id`/`sponsor_contact`) → account → action records; L0 conformance
  statement.
- **MR-Krabs** — multi-tier orchestrator. Operator who submits the spec and
  reviews output is the RAE; L0 conformance statement, with explicit
  model-tier-vs-assurance-level disambiguation.
- **linus-deployment-specialist** — infrastructure automation. Operator
  (env/`$USER`) attributable for provision/destroy including `FORCE=true`;
  L0 conformance statement.

## Reclassification

**Token-Jet: Tier-3 → Tier-1.** Reclassified after a deep dive into the repo.
Token-Jet's install (`scripts/install-local.sh`) does not merely serve local
inference — it instantiates a **full working coding agent** (PI) with
pre-configured tooling:

- web search + URL fetch (`jetson-provider.ts`, `ddg-search`)
- Wi-Fi management including **irreversible actions**: `wifi_off` / `air_gap`
  disables the radio **and wipes all saved Wi-Fi profiles** (`wifi-manager.ts`)
- model switching and code generation
- a browser UI (`pi-web`) bound to `0.0.0.0:30141`, auto-started on boot

No operator / accountability / attribution concept exists anywhere in the repo.
A single install command produces an autonomous, network-reachable agent with
irreversible tools and no recorded accountable human — the exact state RAE
exists to close. **Needs the same Tier-1 treatment as Chaperone, Machina-Parousia,
MR-Krabs, and linus-deployment-specialist** (operator identity + attribution +
conformance), scheduled once current Tier-1 product work settles.

## Tier-2 — relevant but advisory / non-destructive (deferred)

- **Prism** — shapes agent output (RAE N4, influenced actions). Lower stakes
  (no direct destructive action); a natural N4 conformance note when revisited.
- **Spindle** — observes agent fleets rather than acting, so attribution is
  second-order. Deferred.
- **CINC-Fleet-Chaos-Creator** — lab-scoped chaos/QA demo, never production;
  attribution is moot for an isolated lab. Deferred.

## Tier-3 — peripheral (deferred)

- **SSSonector** — cross-platform installers for a network daemon; not agentic,
  no accountability gap.
- **Lieutenant-Underwood** — Python utility; no agent instantiation.
- **hermes-agent-backup** — shell backup scripts; not agentic.
- **mrkrabs-challenge-1/2/3** — challenge/eval repos; not running agents.
