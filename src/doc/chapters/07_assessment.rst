.. _chapter-assessment:

Evaluation sequence, assumptions and open items
===============================================

The combined evaluation sequence
--------------------------------

The requirement groups compose into one sequence at the enforcement point:

    applicable identity and authority → operation and context binding →
    required structural preconditions → semantic appraisal where required →
    evidence appraisal and action disposition → enforcement or governed
    transition.

Required structural preconditions take precedence over semantic appraisal of
the action (LA-4.1, LA-4.4). Evaluation of dependent structural predicates
occurs when the artifacts necessary for those checks become available
(LA-4.2). Identity and authority come from the layers above the
role-structural one (:ref:`chapter-layering`); the disposition after
``indeterminate`` or a resolved ``escalate`` is governed by LA-6.

Read against the WG2 deliverables, LA-1 and LA-2 are the operation-bound
least-agency path. LA-3 to LA-5 refine the runtime conformance and
semantic-verdict assurance work that FG-TIDA/themes#6 Task 3 brought into
WG2. LA-6 states what happens after ``indeterminate`` or a resolved
escalation and meets the FG-TIDA/themes#16 interface. This reading was
confirmed by Cyril Gorlla on FG-TIDA/themes#4 on 18 October 2026.

Related interfaces
------------------

- FG-TIDA/themes#1: action-time evidence and accountability records; the
  record-side requirements for the decision record.
- FG-TIDA/themes#5: provenance and standing of authority; the conferral
  record.
- FG-TIDA/themes#12: agent memory and context assurance (see the annex).
- FG-TIDA/themes#13: ecosystem defense signals that may affect operation
  preconditions (LA-1.4); the coordination row proposed on WG2 issue #7.
- FG-TIDA/themes#16: human intervention, escalation, and return-to-operation
  authority.
- FG-TIDA/themes#21: population-level evaluation of verdict and evaluator
  performance.
- FG-TIDA/themes#23: authorization and privilege lifecycle.
- FG-TIDA/themes#26: runtime enforcement of the action disposition.
- FG-TIDA/themes#31: preservation of authority and context through memory,
  retrieval, summarization, and agent handoff.
- FG-TIDA/themes#59 and #60: the trust control plane and its interface with
  WG2 (:ref:`chapter-interface`).

Assumptions and limitations
---------------------------

The requirements are grounded in an architecture whose relevant correctness
arguments are semi-formal and conditional on stated system properties.

- Tamper-resistant logging and correct execution-state reset are
  architectural assumptions.
- Contract coherence checks address detectable conflicts and specification
  gaps within the coverage of the applied checking method, and the
  assessment record declares that coverage (LA-2.7).
- Plan-log verification depends on the observability and integrity of
  execution evidence. Interactions absent from both artifacts remain outside
  that detection mechanism.
- The architecture was developed at deployment scope. Cross-domain trust
  interoperability requires additional mechanisms; the coordination of
  several organizations operating one system is addressed in
  FG-TIDA-INCUBATION-006.
- The requirements do not establish empirical performance guarantees for the
  underlying architecture.
- Runtime enforcement interfaces remain subject to the mechanisms developed
  under FG-TIDA/themes#26.
- Change arriving through provider-side model updates belongs with
  FG-TIDA/themes#11 and #22.
- Agent identity, persistent context, and execution ownership may be realized
  through a harness or other accountable runtime arrangement, as
  wardduchamps proposed on FG-TIDA/themes#1 and #22, provided the applicable
  attribution and verification properties are preserved.

Settled questions
-----------------

The four assessment questions posted on 17 October were answered by Cyril
Gorlla on 18 October and integrated on 4 November:

1. Asymmetric thresholds for verdicts that block and verdicts that permit:
   yes, per decision class (LA-5.2).
2. Adversarial inputs directed at the evaluator in qualification cases: yes,
   kept out of tuning (LA-5.2).
3. Evaluator configuration in the verdict record: yes, engine version,
   template and inference settings (LA-5.1).
4. Dependency-aware ordering: adequate, with the addition that a failed
   semantic step leaves the dependent structural predicate unsatisfied and
   the action ``indeterminate`` (LA-4.2).

Against the three situations Iván Abril Palma raised on FG-TIDA/themes#4:
a pending action is LA-1.4; a dependency change is LA-1.4 where the
operation's contract declares the affected precondition and a coverage gap
under LA-2.7 where it declares none; a component replacement is LA-2.5 and
LA-2.6 for contract versions and LA-5.5 for evaluator versions.

Open items
----------

- An optional, separately scoped observation slice for LA-1.4, coordinated
  with the FG-TIDA/themes#13 H1 review cases and leaving them unchanged. From
  the least-agency side, the native re-evaluation record carries the LA-2.3
  association, the affected precondition, the source and receiver-used
  versions, evaluation time and native disposition, in causal order with
  receipt of the amendment. Whether it enters deliverable 5 is the
  co-chairs' call (WG2 issue #7).
- The composition test for several locally valid references
  (:ref:`chapter-interface`). The author's answer is held until the test
  runs.
- The open points on FG-TIDA/themes#60 (no silent permit, distinguishable
  failures, recency in the decision record), which the contract's
  disposition clause will have to state once settled.
- Whether deliverable 1 records the path-neutral and path-specific split of
  :ref:`chapter-layering`, and the layering itself.

The author is available to serve as contributing editor for the layering in
deliverable 1 and the least-agency clauses of deliverable 2.
