.. _chapter-requirements:

Requirements
============

The requirements are grouped as posted on FG-TIDA/themes#4 on 17 October
2026. Revisions settled in that thread on 4 November are integrated into the
requirement text and marked. The evaluation sequence the groups compose into
is stated in :ref:`chapter-assessment`.

.. _la-1:

LA-1. Least agency
------------------

**LA-1.1. Declare autonomous decision authority per operation.**

For each governed operation, the applicable contract shall specify the
decisions and commitments permitted to the actor, the verification required
before and after execution, and the roles responsible for that verification.

*Rationale.* Agent identity and resource privileges alone do not establish the
permitted scope of autonomous decisions. Operation-level declarations
establish explicit limits on commitments and identify the verification
responsibilities governing their exercise.

*Source mapping.* Section 3.2 defines least agency through role-structural
constraints on permissible decisions, verification conditions, and
responsibility assignments.

**LA-1.2. Separate actor and verifier responsibilities.**

The actor executing an operation shall be distinct from the independent
verifier of that operation. An orchestrator that proposes, directs, or commits
an operation holds an actor role for that operation and shall not verify it.
The escalation authority for an operation shall be distinct from that
operation's actor and orchestrator.

*Rationale.* Separation of execution and verification responsibilities
reduces the ability of a compromised actor or orchestrator to suppress
evidence of non-conformance or determine the validity of its own conduct.

*Source mapping.* Section 3.2 defines the separation of responsibility
assignments constraint (S), and Proposition 2 in Section 5.3 applies the
actor-verifier distinction to orchestrator manipulation.

*Revision, 4 November.* The last sentence was added as a clarification for
the co-chairs.

**LA-1.3. Require an explicit verification structure.**

An operation governed by this least-agency profile shall declare its
applicable verification structure. An operation lacking a required verifier,
contract binding, or verification condition shall be non-conforming.

*Rationale.* Explicit verification assignments establish the control
conditions under which an operation may proceed. Missing assignments leave
the corresponding decisions without an established conformance
determination.

*Source mapping.* Section 3.2 binds governed operations to explicit contracts
and verification roles; this requirement expresses missing verification
assignments as a conformance failure.

**LA-1.4. Re-evaluate execution-sensitive preconditions.**

Preconditions whose validity may change between authorization and execution
commitment shall be re-evaluated immediately before commitment using the
applicable execution context and current evidence. Relevant operational
indicators, including those supplied through FG-TIDA/themes#13 mechanisms,
shall be considered where required by the governing contract.

*Rationale.* Authority, context, and operational conditions can change after
initial authorization. Execution-time appraisal establishes whether the
conditions governing commitment remain satisfied.

*Source mapping.* Section 3.2 places precondition verification before
execution control passes to the actor; incorporating external operational
indicators extends that mechanism to runtime trust evidence.

*Reading settled on 4 November (with Iván Abril Palma and the FG-TIDA/themes#13
proposers).* LA-1.4 governs current contractual re-evaluation on the local
operation-control path. Signalling and ecosystem awareness supply evidence
and confer no authority. A source amendment reaching the responsible party is
not evidence that the affected precondition was re-evaluated before
commitment; the re-evaluation record is. Because every execution binds to one
operation, contract version and execution instance (LA-2.3), reassessment can
be confined to the affected operation while unaffected activity continues
under its applicable controls.

.. _la-2:

LA-2. Operation-bound enforcement
---------------------------------

**LA-2.1. Bind each verifier to a single approved operation contract.**

Each verifier shall be bound to one approved operation contract identified by
its version-specific digest. Separate precondition and postcondition verifiers
may be bound to the same contract.

*Rationale.* Contract-specific binding limits the scope within which a
verifier can issue accepted determinations and makes contract-version
mismatches detectable at the verification boundary.

*Source mapping.* Section 3.2 defines contract-specific verifier binding,
Figure 1 depicts separate precondition and postcondition verifiers, and
Corollary 2.1 in Section 5.3 examines verifier-compromise containment under
the stated architectural assumptions.

**LA-2.2. Verify externally presented contracts against trusted bindings.**

The applicable operation contract shall be presented to its verifier as an
evaluation input. The verifier's approved contract digest shall be maintained
independently of the presented contract artifact. A digest mismatch shall
prevent execution and produce the defined escalation disposition.

*Rationale.* Independent contract presentation and trusted digest binding
enable detection of reference substitution at the point of evaluation. A
compromised contract artifact cannot satisfy a previously established binding
through content replacement alone.

*Source mapping.* Section 3.2 requires externally supplied contracts bound to
verifier-specific hashes, and Proposition 1 in Section 5.2 addresses
contract-substitution detection and escalation.

**LA-2.3. Bind each execution to its operational context.**

Each operation execution shall be associated with the process, value stream,
and execution instance it serves. The action-time evidence record shall
support association of the agent, operation, contract version, process,
execution instance, and verifier.

*Rationale.* Execution-context binding associates an action with the
operational purpose and constraints under which it was performed. The
resulting evidence supports reconstruction of the applicable contract,
participating entities, and verification decisions.

*Source mapping.* Section 3.2 defines value-stream binding (V), and Section 6
applies contract, execution-context, and verification references to operation
instrumentation.

*Use on FG-TIDA/themes#60.* The six-element association is the
occurrence-binding claim in the identification of the act in the decision
record (:ref:`chapter-interface`).

**LA-2.4. Distinguish operations whose permitted conduct varies by process.**

Where permitted conduct differs between processes or value streams, the
corresponding activities shall be governed by distinct operation contracts. A
verifier shall reject an execution whose declared process binding conflicts
with its approved contract.

*Rationale.* A technical capability may be permitted under one operational
purpose and restricted under another. Distinct contracts preserve those
conditions at specification time and make process-context mismatches
detectable during execution.

*Source mapping.* Section 3.2 defines process-specific value-stream binding,
and Proposition 4 in Section 5.5 addresses unauthorized generalization across
operational contexts.

**LA-2.5. Apply operation-level change control to autonomous decision scope.**

Changes to the operations or decisions an agent may autonomously perform
shall be reflected in the applicable operation contract and verifier binding.
These changes shall be independently identifiable from changes to the agent's
persistent identity.

*Rationale.* Autonomous decision authority can change while agent identity
remains stable. Contract-level change control provides versioned, assessable
authority boundaries for the affected operation.

*Source mapping.* Section 3.2 treats the contract-verifier relationship as the
unit of change for role-structural execution constraints.

**LA-2.6. Establish verifier readiness before activating a contract version.**

A revised operation contract shall become eligible for execution only after
its corresponding approved verifier binding has been deployed and made
available for evaluation.

*Rationale.* A revised contract requires an enforcement mechanism capable of
evaluating its specific conditions. Activation after verifier readiness
preserves the intended relationship between the approved specification and
execution control.

*Source mapping.* Section 3.2 requires verifier rebuilding and deployment when
changes alter the approved operation contract hash.

**LA-2.7. Check contract coherence and coverage before deployment.**

Before deployment, the applicable operation contracts shall undergo coherence
and coverage checks against defined assessment criteria. Detected conflicts
shall prevent deployment until resolved. Runtime-dependent consistency
conditions shall be evaluated at the relevant execution point with defined
failure dispositions. The assessment record shall declare the dependencies
and assumptions covered, the known exclusions, and the material coverage not
established.

*Rationale.* Contradictory conditions and specification gaps can create
conflicting permissions, undefined transitions, or exploitable execution
paths. Design-time checks address detectable inconsistencies, while runtime
verification evaluates conditions dependent on current operational state.
The coverage declaration keeps the check honest about its reach: a contract
may pass its stated checks while a material dependency lies outside the
assessed scope, and the record says so.

*Source mapping.* Section 3.2 establishes pre-deployment coherence checking
(P), and Proposition 6 in Section 5.7 examines specification gaming within
the limits of detectable specification defects.

*Revision, 4 November (answering Iván Abril Palma).* The coverage declaration
was added. LA-2.7 requires checks against declared criteria and makes no
completeness claim relative to an open ecosystem. A negative coverage test
requires an independently frozen reference establishing the omitted condition
under the declared criteria; otherwise the limitation remains unresolved.

**LA-2.8. Preserve accountability for contract approval and deployment.**

Approval of the operational specification and deployment of the
contract-verifier arrangement shall each be attributable to an accountable
party traceable to a human or legal entity. The standing of those parties
shall be established under the applicable authority-provenance framework,
including FG-TIDA/themes#5.

*Rationale.* Approval and deployment are separate governance acts, each with
its own responsible party. Independent attribution supports examination of
who approved the governing constraints and who authorized their operational
deployment.

*Source mapping.* Section 3.2 establishes human approval within coherence
checking and traceability of contract-bound verifier deployment to a human
or legal entity under the separation-of-responsibilities constraint.

.. _la-3:

LA-3. Predicate classification
------------------------------

**LA-3.1. Declare the verification class of each required predicate.**

Each operation-contract condition shall identify the structural and semantic
predicates required to establish its satisfaction. Each predicate shall
declare its evaluation class and applicable verification mechanism. An
unassigned required predicate shall be non-conforming.

*Rationale.* A single obligation may require deterministic and semantic
checks. Explicit predicate assignment establishes the verification method for
each constituent condition and exposes missing evaluation responsibilities.

*Source mapping.* Section 4, Step 8 requires separation of structural and
semantic contract conditions; this requirement extends the classification to
composite obligations and explicit evaluator assignments.

**LA-3.2. Verify structural predicates deterministically.**

Structural and process predicates with fully specified conditions and
observable evaluation inputs shall be evaluated by deterministic, non-model
verification components. A structural or process predicate with a detected
specification gap shall be treated as a coverage gap under LA-2.7. Where an
evaluation input is unobservable at evaluation time, the predicate shall
remain unsatisfied, and the action shall yield ``indeterminate``.

*Rationale.* Deterministic verification supports repeatability,
replayability, and fault localization for conditions with explicitly defined
expected states. It also limits the influence of adversarial natural-language
content on structural enforcement decisions.

*Source mapping.* Section 3.2 defines deterministic verification of structural
and process integrity (D), with Proposition 1 in Section 5.2 illustrating its
use against contract substitution.

*Revision, 4 November.* The last two sentences were added as a clarification
for the co-chairs.

**LA-3.3. Reduce and declare the semantic residual.**

Where an obligation can be represented through falsifiable checks while
preserving its required meaning, the operation contract should specify those
checks. Approved content forms, versioned templates, schema constraints, and
other machine-checkable conditions may be used. The remaining semantic
predicates shall be declared explicitly. Deterministic predicates derived
from the obligation shall preserve the applicable reference's version,
precedence rules, criticality weights, and confidence thresholds where
relevant.

*Rationale.* Translating suitable obligations into deterministic checks
reduces exposure to probabilistic evaluation error and adversarial
interpretation. Explicit residual predicates identify the conditions
requiring semantic assurance, and preserving reference-owned parameters keeps
derived checks faithful to the governing reference.

*Source mapping.* This requirement extends the structural-semantic
decomposition in Section 4, Step 8 by using predicate classification to
constrain the portion of an obligation requiring semantic appraisal, with
reference-owned parameters as stated in FG-TIDA/themes#6 Task 3.

.. _la-4:

LA-4. Evaluation order and predicate composition
------------------------------------------------

The ordering requirements below incorporate the structural-first condition
proposed by Cyril Gorlla on FG-TIDA/themes#4.

**LA-4.1. Evaluate structural preconditions before semantic appraisal.**

Required structural and process preconditions on an action shall be
evaluated before semantic appraisal of that action. A failed required
structural precondition shall determine the action's disposition before
semantic appraisal proceeds.

*Rationale.* Structural preconditions establish whether the action is
eligible for subsequent evaluation and commitment. Their prior evaluation
resolves ineligible actions through deterministic controls and avoids
unnecessary semantic computation.

*Source mapping.* Section 3.2 places precondition verification before
execution in the Propose-Verify-Act-Verify model; the explicit
structural-first ordering follows Cyril Gorlla's contribution to the
FG-TIDA/themes#4 discussion.

**LA-4.2. Preserve predicate dependencies during evaluation.**

A structural predicate requiring an intermediate artifact produced through
semantic extraction or other processing shall be evaluated after that
artifact becomes available. The evaluation sequence shall preserve all
required structural prerequisites and their precedence over final action
admission. Where the semantic step producing that artifact fails, the
dependent structural predicate shall remain unsatisfied, and the action shall
yield ``indeterminate``.

*Rationale.* Evaluation order must respect dependencies between predicates
and the artifacts they inspect. Dependency-aware sequencing permits
deterministic verification of derived artifacts while maintaining the
controlling effect of structural prerequisites. A dependent structural check
must not pass by default when its input was never produced.

*Source mapping.* This requirement extends the precondition and postcondition
verification structure in Section 3.2 to dependency-aware composition of
structural and semantic evaluations.

*Revision, 4 November (answering Cyril Gorlla).* The last sentence of the
requirement was added from his answer to assessment question 4.

**LA-4.3. Establish evidentiary admissibility of carried semantic verdicts.**

A carried semantic verdict used for action gating shall satisfy the
applicable evidence-appraisal requirements referenced by FG-TIDA/themes#6
(AVS, tyche-dev). A rejected verdict record shall be excluded from
action-verdict reliance, with its appraisal rejection and originating claim
preserved. Evidence rejection shall remain distinct from ``indeterminate``
and attested absence of evaluation.

*Rationale.* Evidence appraisal establishes whether a verdict can be relied
upon as an attributed and interpretable claim. Excluding a rejected record
from reliance while preserving the rejection and the original claim keeps a
defective record from acquiring standing and retains the evidence for review.

*Source mapping.* This requirement extends the verification separation in
Section 3.2 through FG-TIDA/themes#6 Task 3 and the AVS evidence-appraisal
work of tyche-dev; the specific record-admissibility semantics originate in
that FG-TIDA work.

**LA-4.4. Preserve structural failure precedence.**

A favorable semantic verdict shall not satisfy or override a failed required
structural precondition.

*Rationale.* Structural prerequisites govern eligibility for evaluation and
execution. Preserving their precedence prevents semantic appraisal from
authorizing conduct that fails an applicable authority, contract, context, or
process condition.

*Source mapping.* Section 3.2 separates deterministic structural enforcement
from probabilistic semantic evaluation, and Proposition 7 in Section 5.8
establishes the limits of the architecture's semantic assurances.

.. _la-5:

LA-5. Semantic verdict eligibility for action gating
----------------------------------------------------

**LA-5.1. Require reproducible, attributable, and independently appraisable
semantic verdicts.**

A semantic verdict used as a basis for action gating shall be reproducible
against an identifiable, versioned reference, attributable to its issuing
evaluator, and independently appraisable by a party that did not participate
in the evaluation. The verdict record shall identify the evaluator
configuration required for recomputation, including engine version,
evaluation template, and inference settings.

*Rationale.* Semantic gating decisions require stable reference conditions,
identifiable evaluation provenance, and evidence sufficient for independent
examination. These properties establish the evidentiary standing required for
use of the verdict in an action decision. The evaluator configuration is the
evaluator-side counterpart of reference currency: without it a verdict cannot
be recomputed.

*Source mapping.* This requirement extends the semantic-appraisal boundary in
Section 3.2 using the assurance conditions proposed by Cyril Gorlla in
FG-TIDA/themes#6 Task 3.

*Revision, 4 November (answering Cyril Gorlla).* The last sentence of the
requirement was added from his answer to assessment question 3.

**LA-5.2. Establish independent decision-class performance evidence.**

The applicable reference shall declare performance criteria for each
semantic decision class. Eligibility of an evaluator version for
consequential action gating shall be supported by assessment against those
criteria using evaluation cases excluded from the evaluator's development and
tuning processes. Performance evidence shall be produced or independently
validated by an authorized assessment party distinct from the runtime verdict
issuer. Population-level results are read under FG-TIDA/themes#21. The
governing reference may declare separate performance and confidence
thresholds per decision class for verdicts that block an action and verdicts
that permit one. Qualification cases shall include adversarial inputs
directed at the evaluator, excluded from development and tuning.

*Rationale.* A reproducible semantic verdict can remain systematically
incorrect. Independent, decision-class-specific assessment establishes
whether the evaluator version meets the performance criteria associated with
the consequences of its assigned gating function. Blocking and permitting
carry different error costs, and the evaluator is an attack surface.

*Source mapping.* This requirement extends Proposition 7 in Section 5.8, which
leaves semantic-evaluator effectiveness outside the established architectural
guarantees, and incorporates the formulation Cyril Gorlla stated on
FG-TIDA/themes#4.

*Revision, 4 November (answering Cyril Gorlla).* The last two sentences of the
requirement were added from his answers to assessment questions 1 and 2.

**LA-5.3. Define failure dispositions for insufficient semantic assurance.**

Where an eligible semantic evaluator cannot meet the confidence threshold
declared in the governing reference, it shall yield ``indeterminate`` with
the scope examined, examination period, and evaluation time, or ``escalate``
according to the governing reference. Where an evaluator lacks gating
eligibility under LA-5.5, its output shall be advisory under LA-5.4, and the
gated action shall yield ``escalate`` or ``indeterminate``. A verdict record
rejected in evidence appraisal shall be handled under LA-4.3.

*Rationale.* Scoped indeterminacy records the limits of an otherwise valid
evaluation. Routing ineligible evaluators to advisory use and rejected
records to LA-4.3 keeps defective evidence from acquiring gating standing.

*Source mapping.* Section 3.2 provides escalation for semantic concerns, while
the five-state verdict vocabulary and evidence-appraisal distinction
originate in FG-TIDA/themes#6 Task 3.

**LA-5.4. Preserve advisory use of semantic evaluations lacking gating
eligibility.**

Semantic evaluators whose outputs lack the assurance required for gating
eligibility may produce risk signals, anomaly indicators, and escalation
requests. These outputs shall have no authority to override required
structural enforcement conditions.

*Rationale.* Advisory semantic outputs can identify concerns requiring
additional evaluation or intervention. Structural enforcement remains
governed by its specified deterministic conditions.

*Source mapping.* Section 3.2 assigns the semantic guardrail layer risk-signal
and escalation functions while reserving structural and process enforcement
for deterministic verification.

**LA-5.5. Qualify semantic gating eligibility by evaluator version and
decision class.**

Eligibility to serve as the basis for a consequential action-gating decision
shall be established for a specified evaluator version and decision class
against the applicable reference and performance criteria. Changes to the
evaluator version, relevant reference requirements, or qualification evidence
shall trigger reassessment of eligibility. The issuing evaluator's declared
relationship to the evaluated party shall be recorded in accordance with
FG-TIDA/themes#6. Any required issuer independence shall be specified by
decision class in the governing reference.

*Rationale.* Evaluator capability and error characteristics vary across
versions and decision classes. Qualification at this granularity associates
verdict eligibility with applicable performance evidence and supports
reassessment when the underlying assurance basis changes. Recording the
issuer's relationship to the evaluated party lets a reference require
independence for the decision classes that need it.

*Source mapping.* This requirement develops the performance-assurance
extension to Proposition 7 in Section 5.8, the evaluator-version
qualification discussed with Cyril Gorlla on FG-TIDA/themes#4, and the
issuer-relationship field GospelNerd introduced on FG-TIDA/themes#6.

**LA-5.6. Separate verdict eligibility from action authority.**

Satisfaction of LA-5.1 and LA-5.2 shall establish eligibility of the semantic
verdict for action-gating consideration. Authority to perform the action
shall be determined through the applicable authorization and policy controls,
with provenance under FG-TIDA/themes#5 and human-intervention authority under
FG-TIDA/themes#16 where applicable.

*Rationale.* Verdict assurance, action authorization, and intervention
authority are independently established control properties. Their separation
prevents an admissible semantic verdict from implicitly expanding the
authority under which an operation may proceed.

*Source mapping.* This requirement extends the operation-bound authority
concepts in Section 3.2 and records the eligibility-authority distinction
Cyril Gorlla stated on FG-TIDA/themes#6.

**LA-5.7. Preserve historical verdicts across reevaluation.**

A reevaluation of an action shall produce a separately identifiable verdict
record referencing the earlier verdict it supersedes. The earlier record
shall remain available with its original reference version, evaluation
context, and appraisal outcome.

*Rationale.* Reevaluation may change the current determination as the
governing reference, evidence, or context changes. Explicit supersession
preserves the history of decisions and the conditions under which each was
issued.

*Source mapping.* This requirement extends operation-contract versioning and
execution traceability in Section 3.2 using the supersession semantics Cyril
Gorlla demonstrated in the FG-TIDA/themes#6 TIDA6-FX fixture.

.. _la-6:

LA-6. Alternate operations
--------------------------

**LA-6.1. Permit separately authorized alternate operations.**

Following an ``indeterminate`` verdict, or a decision by the escalation
authority following ``escalate``, the workflow may transition to a
separately authorized alternate operation where the governing process
defines one.

*Rationale.* Some operational contexts require controlled continuation when
the evaluated action cannot proceed with sufficient assurance. A separately
authorized operation provides a defined continuation path within the
governing constraints.

*Source mapping.* Section 3.1 represents alternate paths within operational
use cases, and Section 4, Steps 4 and 7 provide for alternate transitions,
escalation, and rollback conditions.

**LA-6.2. Evaluate alternate operations under their own contracts.**

Each alternate operation shall have its own applicable authority, contract,
predicates, verification process, and action disposition. Its selection
shall preserve the verdict semantics of the originating action.

*Rationale.* Separate operation contracts establish independent control
conditions for alternative conduct. Preserving the originating verdict
maintains the meaning of the original evaluation while permitting the
workflow to follow an authorized path.

*Source mapping.* Section 3.1 decomposes alternate paths into operations
governed by explicit contracts, consistent with the operation-level
verification architecture in Section 3.2.

**LA-6.3. Preserve the upstream verdict binding.**

The evidence record for an alternate operation shall identify the originating
action record, the verdict that caused the transition, and the applicable
transition authority or policy. The originating verdict shall remain
preserved in its original evidentiary context.

*Rationale.* Explicit upstream references establish the causal relationship
between an unresolved action and the resulting alternate operation.
Preserving the original verdict and transition authority supports
independent reconstruction and appraisal of the workflow.

*Source mapping.* Section 3.2 provides execution-context binding, while the
explicit upstream-verdict record linkage follows Cyril Gorlla's contribution
concerning the proposed AVS-0.3 binding.

**LA-6.4. Preserve contract coherence and execution continuity across
alternate operations.**

An alternate operation shall belong to an approved contract set subject to
the coherence checks in LA-2.7. Its execution shall retain an explicit
association with the originating execution instance, including where the
alternate operation uses a separate instance identifier.

*Rationale.* Coherence checking subjects alternate paths to the same
specification controls as ordinary operations. Execution linkage preserves
traceability across recovery, continuation, or transition boundaries.

*Source mapping.* Section 3.2 applies pre-deployment coherence checking (P)
to applicable contracts and value-stream binding (V) to execution instances.
