.. _chapter-problem:

Problem and purpose
===================

The gap stated by the WG2 charter
---------------------------------

The WG2 charter (v0.4, section 2) states that a verified identity and a valid
authorization say little about what an AI agent will do on a given task. Its
problem 1 states that identity does not determine behaviour: an agent that
passes every identity and authorization check can still take an action
outside the authority it was granted, and a re-run is generally not the same
as the run. Its problem 2 states that security policy is not written for
agents: a policy written as a list of permitted operations either confines the
agent until its purpose is lost or leaves its behaviour unconstrained.

Both problems describe one missing control. Identity establishes who acts.
Authorization establishes what the actor may reach. Least privilege bounds the
second. Nothing in either bounds what the agent may commit to at the moment
of the act, how that commitment is verified, or by whom. A system can satisfy
least privilege and leave that scope unbounded.

Least agency
------------

This contribution names the missing control least agency: the bounded scope of
operations and decisions an agent may autonomously perform or commit to,
together with the required verification structure and the responsible roles.
The principle was stated by the OWASP Top 10 for Agentic Applications (2026).
The requirements here give it an architectural placement separate from least
privilege and a form an enforcement point can apply.

The placement is per operation. An operation is a unit of behaviour with
defined contextual semantics, inputs, preconditions, postconditions, failure
conditions and handling procedures. Each governed operation has exactly one
approved operation contract in force for a given process and execution
instance. The contract states what the agent may commit to without
independent verification, the checks before and after commitment, which party
performs each check, and the disposition when a required input is absent,
stale or outside its declared bound. The contract confers no authority.
Authority comes from the conferral record (FG-TIDA/themes#5) or another
recognised authority mechanism.

The form answers problem 2. The contract confines the agent in whichever form
the workflow requires: a prespecified set of operations where the process
calls for one, or operational conditions on state, scope and context where
confinement by condition fits better. Both forms are verified
deterministically, and the agent's action within the bound remains open.
Conditions that require interpretation of content are declared as semantic
predicates and governed by the requirements on semantic verdicts.

Purpose of this contribution
----------------------------

The contribution has three purposes.

First, to place the least-agency requirements on the record as a formal
contribution to WG2. The requirements were posted on FG-TIDA/themes#4 on
17 October 2026 and revised on 4 November following the review by Cyril Gorlla
and Iván Abril Palma in that thread. The charter lists them as an input to
deliverable 2. :ref:`chapter-requirements` carries the consolidated text.

Second, to state the interface between the operation contract and the trust
control plane proposed under FG-TIDA/themes#59, as recorded on
FG-TIDA/themes#60 (v3, 16 November 2026). :ref:`chapter-interface` carries
the operation contract in force as a decision input, acts under way, and the
identification of the act in the decision record.

Third, to propose for deliverable 1 a reference layering of enforcement
concerns against which each solution path is positioned, and to record which
requirements apply to every path and which belong to the operation-bound
path. :ref:`chapter-layering` carries the proposal, first filed as WG2 charter
issue #5.
