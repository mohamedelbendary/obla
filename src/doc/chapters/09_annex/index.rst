.. _annex-memory:

Annex: related requirements for memory-mediated evolution
=========================================================

These requirements are offered as companion technical input to the memory
and context workstreams (FG-TIDA/themes#12 and #31). Their primary
application is preservation of execution-state integrity across repeated or
long-horizon agent activity. They were posted with the main set on
FG-TIDA/themes#4 on 17 October 2026 and are unchanged.

**LA-A.1. Isolate transient execution state.**

Working state shall be reset at the completion of each defined execution
instance. Retention beyond the instance shall pass through LA-A.2.

*Rationale.* Transient state can carry stale or contaminated information from
one execution into another. A single admission path for retained content
limits cross-instance influence to verified increments.

*Source mapping.* Section 3.2 defines temporal isolation (T), and Proposition
3 in Section 5.4 addresses cross-session state poisoning under the
state-reset assumptions.

**LA-A.2. Verify persistent-memory admission against execution evidence.**

Persistent-memory admission under the verified-knowledge profile shall
require independent verification that the proposed retained plan corresponds
to the applicable execution log. Admission shall be limited to the verified
plan, with operation-specific data excluded under the profile. The admission
decision shall identify the responsible verifier.

*Rationale.* Plan-log consistency establishes an observable condition for
admitting execution-derived knowledge into persistent memory. Limiting
admitted content and recording verifier attribution constrain one path
through which unverified execution information could influence later
operations.

*Source mapping.* Section 3.2 defines strict knowledge verification before
accumulation (K), and Proposition 3 in Section 5.4 applies the mechanism to
cross-session memory contamination.

**LA-A.3. Preserve the scope of memory-integrity assurance.**

A successful plan-log consistency check shall establish only the specified
consistency and admission conditions. Separate assurance requirements shall
govern factual correctness, semantic safety, permitted reuse, and provenance
of retained content where applicable.

*Rationale.* Consistency between a proposed plan and observed execution
establishes correspondence between two artifacts. Additional controls are
required to determine the truth, safety, or future applicability of the
information retained.

*Source mapping.* Section 3.2 limits verified knowledge accumulation to the
defined plan-log verification mechanism, while the architecture separates
structural guarantees from semantic assurance.
