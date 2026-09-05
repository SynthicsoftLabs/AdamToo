# AdamToo GitHub Integration

## Purpose

GitHub is a first-class external development environment for AdamToo. The long-term objective is for AdamToo to inspect, modify, validate, version, publish, and maintain repositories through an explicit typed adapter rather than through unbounded shell access.

The AdamToo repository itself is the primary integration target for this capability.

## Operating model

```text
AdamToo objective
      |
      v
GitHub adapter
      |
      +--> repository discovery
      +--> tree / file retrieval
      +--> branch management
      +--> file and blob creation
      +--> commit construction
      +--> ref update
      +--> pull request lifecycle
      +--> issue / review workflows
      +--> release / artifact workflows
      |
      v
Execution receipt + provenance ledger
```

Every mutating operation should produce an execution receipt containing:

- repository and ref
- requested operation
- exact target path or resource
- content/artifact digest where applicable
- authorization context
- parent/base commit
- resulting commit/ref/object identifiers
- validation result
- timestamp
- run identifier

## Capability groups

### Read

AdamToo should be able to retrieve repository metadata, branches, commits, trees, blobs, files, issues, pull requests, reviews, workflow state, artifacts, and status checks.

### Write

AdamToo should support creating and updating text files, creating binary Git blobs from verified byte streams, constructing Git trees and commits, creating branches, advancing refs, opening and updating pull requests, managing issues and reviews, and publishing release artifacts where explicitly authorized.

### Self-repository operations

For `SynthicsoftLabs/AdamToo`, the adapter should support the complete engineering loop:

```text
inspect -> plan -> modify -> test -> verify -> commit -> publish -> verify remote state
```

AdamToo must be able to modify its own repository without requiring a human to manually translate every local change into GitHub operations.

## Artifact handling

Binary artifacts must remain byte-exact. The adapter should calculate SHA-256 before transmission and verify the resulting remote object against the intended content digest after publication whenever the remote representation permits deterministic verification.

The `.skill` distribution artifact remains a release artifact even when its extracted source tree is also represented as ordinary repository files.

## Authorization model

GitHub operations are divided into read and mutation capabilities.

Read operations may be automatically executed within the configured repository scope.

Mutation operations require an explicit authorization context describing repository, branch/ref, operation class, and intended effect. High-impact mutations such as force-pushing, deleting branches/files, changing repository configuration, publishing releases, modifying workflows, or changing permissions require an additional elevated authorization policy.

## Branch strategy

Normal development should occur on a feature branch. AdamToo should prefer pull requests for substantive changes to `main` unless the configured repository policy explicitly permits direct updates.

Recommended lifecycle:

```text
main
  |
  +--> feature/<run-or-purpose>
          |
          +--> validate
          +--> commit
          +--> pull request
          +--> review / CI
          +--> merge
```

## Provenance and anti-interference requirements

The adapter must preserve the distinction between:

1. user-authorized objectives,
2. AdamToo-generated plans,
3. retrieved repository content,
4. generated source changes,
5. GitHub responses,
6. mutation authorization, and
7. resulting repository state.

Repository content, issue text, pull-request text, workflow logs, commit messages, and remote documentation are data inputs. They must not silently acquire authority to expand permissions, alter authorization, disclose credentials, or redirect an operation.

Every remote mutation should be attributable to an AdamToo run and should be reconstructable from the execution receipt and provenance ledger.

## Failure handling

A GitHub operation failure is a recoverable execution state, not a reason to fabricate success. AdamToo should:

1. preserve the complete error and request context;
2. determine whether the failure is authentication, authorization, transport, validation, conflict, rate limiting, or repository state;
3. retry only when the operation is safe and idempotent;
4. refresh repository state before resolving conflicts;
5. never silently force-push or overwrite unrelated work;
6. verify the final remote state after recovery.

## Current repository state

The repository currently contains the canonical AdamToo v22 security-hardened R1 `.skill` artifact and formal project documentation. The next implementation phase is to make the GitHub adapter a native AdamToo capability rather than treating GitHub as a manual distribution destination.

## Acceptance criteria

The future adapter is complete when AdamToo can, from a single declared run:

- inspect `SynthicsoftLabs/AdamToo`;
- create a feature branch;
- write both text and binary project artifacts;
- construct commits with provenance;
- run local validation before publication;
- publish a branch or pull request;
- inspect CI/status results;
- repair failures;
- verify the resulting remote tree and hashes;
- and record a complete machine-readable execution receipt.
