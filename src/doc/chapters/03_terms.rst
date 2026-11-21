.. _chapter-terms:

Terms
=====

The terms below are used as defined here. New terms will be communicated to
WG0 per section 8 of the WG2 charter.

Operation
    A unit of behaviour with defined contextual semantics, inputs,
    preconditions, postconditions, failure conditions, and corresponding
    handling procedures.

Operation contract
    A versioned, machine-readable, schema-based specification governing
    exactly one operation, identified by a version-specific digest. Within a
    deployment, each governed operation shall have exactly one approved
    contract version, bound to the specific intent(s) and process(es) it
    serves, for each execution instance.

Execution instance
    A uniquely identified, time-bound traversal of a process or workflow.

Enforcement point
    The component that takes the enforcement decision for one action against
    the policy in force, consults the required inputs, applies the operation
    contract in force, and leaves the decision record. The enforcement point
    is never the acting agent.

Verifier
    A component bound to one approved operation contract that evaluates the
    contract's preconditions or postconditions. Separate precondition and
    postcondition verifiers may be bound to the same contract.

Structural predicate
    A condition decidable through deterministic logic over specified and
    observable artifacts.

Semantic predicate
    A condition whose evaluation requires interpretation of content or
    meaning.

Escalation authority
    An agent or human party authorized to receive and resolve an
    ``escalate`` verdict within a defined mandate, with authority provenance
    established under FG-TIDA/themes#5 and applicable human-oversight
    requirements governed by FG-TIDA/themes#16.

Least agency
    The bounded scope of operations and decisions an agent may autonomously
    perform or commit to, together with the required verification structure
    and responsible roles.

Least privilege
    The bounded scope of resources an agent is authorized to access.

Decision class
    A defined category of semantic determinations governed by specified
    evaluation and performance criteria.

Semantic residual
    The portion of an obligation whose satisfaction remains dependent on
    semantic appraisal after applicable deterministic controls have been
    established.

Decision record
    The record the enforcement point leaves for one decision: the outcome,
    what was consulted, which version of it, and the operation contract
    applied (FG-TIDA/themes#60, part C).
