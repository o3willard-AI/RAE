# RAE Adopters

Products and services that display or implement the [RAE specification](../SPEC.md).

Each adopter lives in its own subfolder under this directory, named after the
project. The subfolder holds that project's conformance statement (or a short
entry linking to it) and any supporting material. Add a new subfolder for each
adopter — Prisentic's own products and third-party projects alike — never a flat
file at this level.

| Product | Claim | Status |
|---|---|---|
| [SafeKeyPass](safekeypass/) | `implements RAE 1.0.4 L1, enforcement tier` | conformant (L1) |
| [PairAdmin Enterprise](pairadmin-enterprise/) | targeting `implements RAE 1.0.4 L1, enforcement tier` | in progress |
| [Chaperone](chaperone/) | `displays an RAE at L0 (declared, unverified)` | deprecated — superseded by SafeKeyPass |

## Adding an adopter

1. Create `adopters/<project>/`.
2. Place the conformance statement there — `adopters/<project>/README.md` as the landing file (optionally a machine-readable `conformance.json`/`conformance.yaml` alongside it).
3. Add a row to the table above.
