.. _chapter-layering:

Reference layering for deliverable 1
====================================

Section 2 of the WG2 charter sorts existing work by concern: agent identity
(ITU-T X.1285, IETF WIMSE), what an agent may access in general (OASIS XACML,
attribute-based access control) and the platform it runs on (IETF RATS,
Trusted Computing). Deliverables 3 and 4 assess identity and intent-based
policy as solution paths, with least-agency enforcement among further paths.
An enforcement decision on one action composes controls from several of these
concerns at the same enforcement point. This chapter proposes that
deliverable 1 include a reference layering of those concerns, so that each
path is positioned by the layer it addresses and assessed for what it
guarantees there and how it composes with the others. The proposal was filed
as WG2 charter issue #5 on 6 November 2026.

The layering
------------

.. tabularcolumns:: |>{\raggedright\arraybackslash}p{0.20\linewidth}|>{\raggedright\arraybackslash}p{0.34\linewidth}|>{\raggedright\arraybackslash}p{0.38\linewidth}|

.. list-table::
    :header-rows: 1
    :widths: 22 36 42

    * - Layer
      - Concern
      - Charter content positioned there
    * - Identity and trust infrastructure
      - Who the agent is; attestation; non-repudiation and tamper-resistant records
      - Deliverable 3 (design-invariant identity); WG1 attestation; FG-TIDA/themes#1 records
    * - Resource access
      - What an authenticated agent may reach (least privilege)
      - XACML and attribute-based access control
    * - Role-structural
      - What an agent may commit to without independent verification, how that verification is performed and by whom (least agency), per operation and grounded in the process the operation serves
      - The requirements in :ref:`chapter-requirements`
    * - Semantic
      - Conditions that require interpretation of content
      - Deliverable 4 (intent expressed as wanted and unwanted outcomes), with outcomes operationalized into deterministic checks where possible (LA-3.3) and the residual governed by LA-5

The layering follows Section 3.2 of [ElBendary2026]. The principle of least
agency was stated by the OWASP Top 10 for Agentic Applications (2026)
[OWASP2026]; the layering gives it an architectural placement, separate from
least privilege. A system can satisfy least privilege while leaving least
agency unbounded.

Proposed charter text
---------------------

- Deliverable 1, short description: "Terminology, environment, threat cases,
  a reference layering of enforcement concerns against which each solution
  path is positioned, and the requirements set against which every path is
  assessed."
- Deliverable 4, short description: "Policy expressed as wanted and unwanted
  outcomes, its coexistence with legacy policy and with operation-level
  controls at a common enforcement point, and further policy paths, each
  assessed against deliverable 1."

Problem 2 under the layering
----------------------------

Problem 2 states that a policy written as a list of permitted operations
either confines the agent until its purpose is lost or leaves its behaviour
unconstrained. At the role-structural layer, the operation contract confines
the agent in whichever form the workflow requires: a prespecified set of
operations where the process calls for one, or operational conditions on
state, scope and context where confinement by condition fits better. Both
forms are verified deterministically, and the agent's action within the bound
remains open. Conditions that require interpretation belong to the semantic
layer. Suggested addition to problem 2:

    A policy can instead bound what an agent may commit to without
    independent verification, by a prespecified set of operations or by
    operational conditions, with each form verified deterministically and the
    agent's action within the bound left open.

Path-neutral and path-specific content
--------------------------------------

Much of the requirement set applies to every path and falls within goal 2 and
deliverable 2:

- decision semantics and the statement of absence: LA-1.3, LA-4.3, LA-5.3 to
  LA-5.6;
- re-evaluation before commitment: LA-1.4;
- actor-verifier separation: LA-1.2;
- predicate classification: LA-3.1 to LA-3.3;
- coherence checking: LA-2.7.

The operation-bound mechanism belongs to the role-structural layer: LA-2.1 to
LA-2.6 and LA-6. Deliverable 1 should record this split, so that requirements
carried into deliverable 2 keep clause-level attribution per section 9 of the
charter.

Sequencing of judgement
-----------------------

WG2 issue #8 proposes that deliverable 1 set the requirements before any path
is judged against them. The layering serves the same end: identification of
paths informs the comparison without settling it, because each candidate
path is positioned by the layer it addresses and assessed for what it
guarantees there.
