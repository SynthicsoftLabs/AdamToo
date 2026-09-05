# AdamToo

**AdamToo** is a modular, persistent agent system developed by **Synthicsoft Labs**. It is designed as a system-of-systems rather than a single model: models, skills, memory, planning, evaluation, execution adapters, provenance, and environment interfaces are composed into a unified runtime.

The repository currently distributes the verified **AdamToo v22 security-hardened R1** package as the canonical release artifact.

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
- SHA-256: `3cae4f7e5f3df02c9e2e6cacaf2a4d9de7a32d647f66dcc936c28ff3bb60f498`
- Archive members: **412**
- Extracted project files: **337**

The `.skill` file is the authoritative distribution artifact for this repository. The archive contains the AdamToo runtime, integrated SynthicSoft substrate, test suite, runtime states and reports, source provenance, security hardening, and associated project documentation.

## Verification Status

The R1 package was subjected to an end-to-end acceptance run before publication.

- Python test suite: **68/68 passed**
- Unified substrate execution: **PASS**
- Machina diagnostics: **HEALTHY**
- KAIROS/Xi/ALETHEIA continuous runtime: **100 cycles; PASS**
- ATHOS/KAIROS/S.Y.N.T.H.E.S.I.S. runtime: **100 cycles; PASS**
- Unified ATHOS/KAIROS boot: **PASS**
- Fused RSHL-TERRARIUM kernel: **PASS**
- AdamToo smoke wrapper: **PASS**
- Complete acceptance harness: **PASS (RC=0)**
- Declared integrated substrate sources: **23/23 exact matches**

The verification records distinguish executed tests from static inspection and preserve provenance for the integrated source set.

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

GitHub is a planned first-class AdamToo execution environment, not merely a publication destination. The target integration enables AdamToo to inspect repositories, modify source and binary artifacts, create branches and commits, open pull requests, inspect CI and status results, recover from repository failures, and verify resulting remote state.

The intended lifecycle is:

```text
inspect -> plan -> modify -> test -> verify -> commit -> publish -> verify remote state
```

Repository mutations are to remain typed, explicitly authorized, provenance-bearing, and auditable. Binary artifacts must remain byte-exact and content-addressed. AdamToo's own `SynthicsoftLabs/AdamToo` repository is the primary target for this capability.

See [`docs/GITHUB-INTEGRATION.md`](docs/GITHUB-INTEGRATION.md) for the integration contract, authorization model, artifact handling, failure recovery, and acceptance criteria.

## Documentation

- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — system architecture and component relationships
- [`docs/VERIFICATION.md`](docs/VERIFICATION.md) — release verification and acceptance evidence
- [`SECURITY.md`](SECURITY.md) — security model, trust boundaries, and reporting guidance
- [`docs/SECURITY-INTERFERENCE-ANALYSIS.md`](docs/SECURITY-INTERFERENCE-ANALYSIS.md) — end-to-end interference analysis and hardening record
- [`docs/GITHUB-INTEGRATION.md`](docs/GITHUB-INTEGRATION.md) — first-class GitHub repository integration contract

## Repository Layout

The repository keeps the published runtime as a single canonical artifact rather than presenting a separately reconstructed source tree that could diverge from the verified release.

```text
AdamToo/
├── adamtoo-universal-integrated-v22-security-hardened-r1.skill
├── README.md
├── SECURITY.md
├── LICENSE
└── docs/
    ├── ARCHITECTURE.md
    ├── GITHUB-INTEGRATION.md
    ├── VERIFICATION.md
    └── SECURITY-INTERFERENCE-ANALYSIS.md
```

## Reproducibility and Provenance

The release artifact is content-addressed by SHA-256. Verification should begin by checking the published artifact hash, then extracting the archive and executing the included test and verification procedures.

The integrated substrate preserves its source manifest and validation records. Additional project artifacts are additive and do not replace the declared master source sections.

## Project Status

AdamToo is an actively developed research and engineering project. Numerical results, runtime metrics, and verification statements in this repository refer to the specific release artifact and execution environment used for validation; they should not be interpreted as a general claim about all future versions or deployments.
