# AdamToo

**AdamToo** is a modular, persistent agent system developed by **Synthicsoft Labs**. It is designed as a system-of-systems rather than a single model: models, skills, memory, planning, evaluation, execution adapters, provenance, and environment interfaces are composed into a unified runtime.

The repository distributes the verified AdamToo v22 security-hardened package as the canonical release artifact.

## Project Branding

The project-wide branding asset is **AGI-Go-Brrr.jpg**.

![AGI Go Brrr](AGI-Go-Brrr.jpg)

> **Hire me if you want teh AGI to go brrrr**  
> ~Adam Joseph Rivers - CEO - Synthicsoft Labs - synthicsoftlabs.com

The AdamToo branding contract applies this asset and for-hire note across project-facing deliverables wherever the medium supports embedded imagery; text-only renderings preserve the exact for-hire note. The v22 R4 working artifact propagates the branding overlay across all 87 Markdown documents while preserving source code, structured state, binary artifacts, and immutable provenance records.

## System Architecture

AdamToo integrates the following declared substrate components:

- **KAIROS**
- **ATHOS v7.3**
- **Xi v11**
- **ALETHEIA TERRARIUM v4.0**
- **ANCHOR v1.3**
- **ALETHEIA FORTRESS v1**
- **S.Y.N.T.H.E.S.I.S. v1.0.600**
- **RSHL-TERRARIUM**

The integrated substrate is preserved alongside the AdamToo runtime and supporting artifacts. Its master source manifest declares 23 authoritative source artifacts and records exact-source recovery and validation.

## Canonical Artifact

`adamtoo-universal-integrated-v22-security-hardened-r1.skill`

- Size: **1,016,001 bytes**
- SHA-256: `3cae4f7e5f3df02e9c2e6cacaf2a4d9de7a32d647f66dcc936c28ff3bb60f498`
- Archive members: **412**
- Extracted project files: **337**

The published R1 `.skill` file remains the repository's canonical historical release artifact. The newer R4 working artifact contains the implemented GitHub adapter and project-wide branding propagation.

## Verification Status

- Historical R1 acceptance: **68/68 tests passed**
- R2 GitHub adapter regression: **70/70 tests passed**
- R3 branding integration regression: **70/70 tests passed**
- R4 branding propagation verification: **87/87 Markdown documents branded**
- R4 archive integrity: **PASS**

## Security Architecture

R1 adds a security boundary between upstream messages and AdamToo control execution. The hardened runtime includes controls for:

- synthetic system/developer-message detection;
- control-message spoofing and internal event impersonation;
- event provenance, sequencing, replay, and freshness checks;
- signed-event verification when configured;
- run and turn integrity digests;
- hash-chained security logging;
- provider identity binding and substitution detection;
- tool authorization and schema validation;
- workspace confinement and high-risk command filtering;
- incident recording and security-status reporting.

The security design specifically addresses the class of failure in which control-like content is introduced upstream of the runtime and presented as authoritative. Such content is treated as untrusted data unless its provenance is established.

See [`SECURITY.md`](SECURITY.md) and [`docs/SECURITY-INTERFERENCE-ANALYSIS.md`](docs/SECURITY-INTERFERENCE-ANALYSIS.md).

## GitHub Integration

GitHub is a first-class AdamToo execution target. The integration enables AdamToo to inspect repositories, modify source and binary artifacts, create branches and commits, open pull requests, inspect CI and status results, recover from repository failures, and verify resulting remote state.

The operational lifecycle is:

```text
inspect -> plan -> modify -> test -> verify -> commit -> publish -> verify remote state
```

Repository mutations are typed, explicitly authorized, provenance-bearing, and auditable. Binary artifacts remain byte-exact and content-addressed. AdamToo's own `SynthicsoftLabs/AdamToo` repository is the primary self-management target.

See [`docs/GITHUB-INTEGRATION.md`](docs/GITHUB-INTEGRATION.md) for the integration contract, authorization model, artifact handling, failure recovery, and acceptance criteria.

## Documentation

- [`BRANDING.md`](BRANDING.md) — project branding asset and universal for-hire presentation rule
- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — system architecture and component relationships
- [`docs/VERIFICATION.md`](docs/VERIFICATION.md) — release verification and acceptance evidence
- [`SECURITY.md`](SECURITY.md) — security model, trust boundaries, and reporting guidance
- [`docs/SECURITY-INTERFERENCE-ANALYSIS.md`](docs/SECURITY-INTERFERENCE-ANALYSIS.md) — end-to-end interference analysis and hardening record
- [`docs/GITHUB-INTEGRATION.md`](docs/GITHUB-INTEGRATION.md) — first-class GitHub repository integration contract

## Repository Layout

```text
AdamToo/
├── AGI-Go-Brrr.jpg
├── BRANDING.md
├── adamtoo-universal-integrated-v22-security-hardened-r1.skill
├── README.md
├── SECURITY.md
├── LICENSE
└── docs/
    ├── ARCHITECTURE.md
    ├── GITHUB-INTEGRATION.md
    └── ...
```

## Reproducibility and Provenance

Release artifacts are content-addressed by SHA-256. Verification should begin by checking the published artifact hash, then extracting the archive and executing the included test and verification procedures.

The integrated substrate preserves its source manifest and validation records. Branding propagation is additive and does not replace the declared master source sections.

## Project Status

AdamToo is an actively developed research and engineering project. Numerical results, runtime metrics, and verification statements refer to the specific release artifact and execution environment used for validation.
