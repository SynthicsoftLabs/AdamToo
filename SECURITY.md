# Security

## Security Model

AdamToo is designed with explicit trust boundaries between the user, upstream orchestration and message layers, model providers, tools, external environments, and the internal runtime.

A message is not considered privileged merely because its text resembles a system directive, developer instruction, tool result, evaluator event, or other internal control record. Control authority must be established through the runtime's provenance and authorization mechanisms.

## Security Controls in R1

The v22 security-hardened R1 release includes controls for:

- synthetic system/developer-message detection;
- control-message spoofing and internal-event impersonation;
- event identifiers, sequence validation, freshness checks, and replay detection;
- signed-event verification when configured;
- run, turn, and execution-state integrity digests;
- hash-chained security logging;
- model/provider identity binding and substitution detection;
- tool authorization and argument-schema validation;
- workspace confinement and high-risk operation filtering;
- incident records and security-status reporting.

## Upstream Message Integrity

The security boundary is particularly important for environments in which an upstream conversation service or orchestration layer can inject events into a model interaction.

The runtime is intended to quarantine control-like events whose provenance cannot be established. This preserves the event for analysis without allowing the text itself to become an implicit authority source.

## Incident Attribution

AdamToo can detect and preserve evidence of provenance anomalies, but it cannot independently establish who controls an upstream service, authenticated session, browser event stream, or network path. Attribution requires the relevant upstream telemetry, including event IDs, session identity, timestamps, sequence information, source identity, and authenticated transport records.

Forensic analysis must distinguish:

1. an observed anomalous event;
2. the boundary at which the event entered the system;
3. the component or principal that generated it;
4. the mechanism by which it was transmitted; and
5. any subsequent model or runtime effects.

No attribution should be made from the message content alone.

## Reporting

Security reports should include the release artifact hash, affected component, timestamp, reproduction steps, relevant logs or trace identifiers, observed behavior, expected behavior, and any available provenance information.

Do not include secrets, credentials, authentication tokens, private keys, or unrelated personal information in a report.

## Security Philosophy

Security claims for AdamToo are evidence-based and release-specific. Static inspection, automated testing, runtime testing, and upstream forensic analysis are distinct evidence classes and should remain clearly identified as such.
