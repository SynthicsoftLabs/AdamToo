# AdamToo Architecture

## 1. Overview

AdamToo is a system-of-systems architecture for persistent, tool-using agent execution. The runtime is organized around a cognitive kernel that coordinates model providers, a skill graph, memory, planning, evaluation, artifact production, and typed world interfaces.

The architecture is provider-neutral. Model selection is determined by task requirements such as reasoning depth, context requirements, modality, latency, cost, privacy, and tool compatibility.

## 2. Integrated Substrate

The current integrated substrate declares the following architectural components:

| Component | Declared version / identity |
|---|---|
| KAIROS | KAIROS |
| ATHOS | v7.3 |
| Xi | v11 |
| ALETHEIA TERRARIUM | v4.0 |
| ANCHOR | v1.3 |
| ALETHEIA FORTRESS | v1 |
| S.Y.N.T.H.E.S.I.S. | v1.0.600 |
| RSHL-TERRARIUM | integrated kernel/system |

The substrate manifest declares **23 authoritative source artifacts**. The release validation record reports **23 declared sources, 23 exact matches, and `all_declared_exact: true`**.

## 3. Runtime Layers

### Cognitive Kernel

The cognitive kernel provides the primary coordination layer for task intake, decomposition, routing, memory interaction, evaluation, and artifact production.

### Model Federation

AdamToo can operate above multiple model providers and specialist model classes. Provider identity is tracked as part of execution provenance so that a runtime can detect unexpected provider substitution within a run.

### Skill Graph

Capabilities are represented as normalized skill records with activation metadata, provenance, compatibility information, and validation state. The universal router selects a sufficient capability chain, binds the required tools, executes through the applicable adapter, and records the resulting provenance.

### Memory

Memory is divided by operational purpose, including working, episodic, semantic, procedural, and artifact-oriented information. Run IDs, events, checkpoints, tool records, and provider records are used to preserve execution continuity and reconstruction information.

### Planner and Evaluator

A task is decomposed into executable stages and evaluated against objective-specific criteria. The runtime supports retries, repair, refinement, checkpointing, and completion records.

### World Interface

External environments are exposed through typed adapters for files, APIs, browsers, data stores, simulations, and other approved connectors. Adapter contracts carry capability metadata, input/output schemas, provenance, and execution receipts.

## 4. Execution Lifecycle

The normal lifecycle is:

1. Receive an objective.
2. Establish context and applicable constraints.
3. Build a task/world representation from available evidence.
4. Select models, skills, tools, and environments.
5. Execute the dependency graph.
6. Record observations and update working memory.
7. Evaluate the result against completion criteria.
8. Repair, refine, or continue when required.
9. Consolidate durable memory and produce final artifacts.

The adapter lifecycle is explicitly defined as:

`resolve -> bind -> preflight -> execute -> normalize_output -> record_provenance`

## 5. Security Boundary

R1 places an explicit trust boundary between upstream message sources and AdamToo's internal control plane. Control-bearing content is not treated as authoritative solely because it resembles a system, developer, tool, or evaluator message.

The security layer can identify and quarantine synthetic control messages, replayed events, sequence gaps, stale events, privileged-channel injections, invalid signatures, provider substitution, and tool-schema violations.

The runtime cannot independently attribute an upstream event to a specific person or service without authenticated upstream metadata. Attribution therefore remains a separate platform/session forensic problem.

## 6. Evidence and Reproducibility

Architectural claims should be evaluated against the published release artifact and its embedded provenance records. The canonical R1 artifact is hashed and distributed as a single package so that the verified release can be identified independently of a working-directory reconstruction.
