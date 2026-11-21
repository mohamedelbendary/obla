.. _chapter-scope:

Scope and relation to the WG2 charter
=====================================

Scope
-----

This contribution specifies:

- terms for operation-bound least agency;
- requirements on the declaration of autonomous decision authority per
  operation, on the binding of verifiers to operation contracts, on the
  classification of contract predicates as structural or semantic, on the
  order in which they are evaluated, on the eligibility of semantic verdicts
  for action gating, and on alternate operations after an ``indeterminate``
  or ``escalate`` verdict;
- the content of the operation contract as an input the enforcement point
  reads at decision time, and the elements of the decision record that
  identify the act;
- a reference layering of enforcement concerns for deliverable 1.

Unit of analysis
----------------

The unit of analysis is the charter's: the enforcement decision for one
action, taken at an enforcement point when the action is attempted, against
the policy in force. Sequences of actions, delegation chains and longer-running
tasks are series of such decisions. :ref:`chapter-interface` states how an act
under way decomposes into operations with re-consultation at operation
boundaries.

Relation to the charter deliverables
------------------------------------

.. tabularcolumns:: |>{\raggedright\arraybackslash}p{0.22\linewidth}|>{\raggedright\arraybackslash}p{0.70\linewidth}|

.. list-table::
    :header-rows: 1
    :widths: 24 76

    * - Charter item
      - What this contribution provides
    * - Deliverable 1, requirements set
      - The path-neutral requirements (:ref:`chapter-layering`, section on path-neutral and path-specific content) and the reference layering of enforcement concerns.
    * - Deliverable 2, policy expression and decision outcomes
      - Operation contract content (LA-1, LA-2), predicate classification (LA-3), evaluation order (LA-4), verdict eligibility and the dispositions ``indeterminate`` and ``escalate`` (LA-5), and the statement that no decision was taken as distinct from evidence rejection (LA-4.3, LA-5.3).
    * - Deliverable 3, identity paths
      - Change control separating autonomous decision scope from persistent identity (LA-2.5), and the positioning of identity at the first layer of the reference layering.
    * - Deliverable 4, intent-based policy paths
      - Coexistence of operation-level controls with outcome-expressed policy at a common enforcement point: outcomes operationalized into deterministic checks where possible (LA-3.3) and the residual governed by LA-5.
    * - Deliverable 5, fixtures
      - The LA-1.4 pre-commit re-evaluation case proposed on WG2 issue #2, and the optional test-only observation profile discussed on WG2 issue #7.
    * - Section 7, coordination
      - The interface with the trust control plane (FG-TIDA/themes#60) and the coordination row for FG-TIDA/themes#13 (WG2 issue #7).

Out of scope
------------

- Encodings and protocol specifications.
- The mechanisms by which an action disposition is enforced at runtime
  (FG-TIDA/themes#26).
- Change arriving through provider-side model updates (FG-TIDA/themes#11 and
  #22).
- The internal evaluation methods of semantic evaluators, beyond the
  eligibility conditions in LA-5.
- Cross-domain trust interoperability beyond deployment scope. The
  coordination of several organizations operating one agentic system is the
  subject of the author's separate contribution FG-TIDA-INCUBATION-006.

Conventions
-----------

"Shall" states a requirement. "Should" states a recommendation. "May" states a
permission. The identifiers ``LA-n`` are working labels for discussion and
citation, independent of FG-TIDA document numbering. Verdict names in
``monospace`` (``permit``, ``remediate``, ``block``, ``escalate``,
``indeterminate``) are the five outcomes recorded on FG-TIDA/themes#60.

Each requirement is followed by its rationale and its source mapping. Section
numbers in source mappings refer to the arXiv version of [ElBendary2026].
Where the text was revised after the 17 October posting, the revision is
marked "Revision, 4 November" with the participant whose point it answers.
