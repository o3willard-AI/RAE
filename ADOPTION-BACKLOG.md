# RAE Adoption Backlog

Status of RAE adoption across `o3willard-AI`. Tier-1 repos are adopted
(operator/sponsor identity + attribution + an L0 conformance statement). This
file tracks the deferred Tier-2 and Tier-3 considerations, plus one
reclassification from the 2026-09 deep-dive review.

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
