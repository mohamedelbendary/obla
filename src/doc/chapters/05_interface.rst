.. _chapter-interface:

Interface with the trust control plane
======================================

FG-TIDA/themes#60 lists, by object, the inputs an enforcement point reads at
decision time, the conditions it applies and what it produces. It is the
working interface between WG2 and the trust control plane group proposed
under FG-TIDA/themes#59. The working line, from #59: the trust control plane
owns how trust state is established, distributed and changed; WG2 owns the
decision at the moment of a single agent action, what the enforcement point
consults, the outcome it returns and the record it leaves. This chapter
states the three positions the author contributed to that issue, as recorded
in its v3 of 16 November 2026 and confirmed on 18 November. Two are recorded
there as proposed resolutions for the WG2 co-chairs to confirm.

The operation contract in force as a decision input
---------------------------------------------------

Part B of the #60 table carries one row, specified by WG2 under deliverable 2
from the least-agency input on #4:

    **Operation contract in force.** For the operation attempted: what the
    agent may commit to without independent verification, the checks before
    commitment and after it, which party performs each check, and the
    disposition when an input above is absent, stale or outside its declared
    bound. It names which inputs the operation requires. It does not confer
    authority, which comes only from the conferral record or another
    recognised authority mechanism.

The row ties the contract to the other decision inputs in part A of the
table. The contract names which of them the operation requires: the conferral
record and its standing, decided changes beyond revocation, the declared
operator, the evidence behind a reference, and the consultation of the record
with its recency. The contract's disposition clause states what the
enforcement point does when a named input is absent, stale or outside its
declared bound, which is the pre-commit re-evaluation of LA-1.4 applied to
the control-plane inputs. Two examples from the WG2 charter discussion
(issue #9):

- Revoked authority. The pre-commit check consults the conferral record; a
  revoked grant yields the contract's disposition. WG2 issue #2 proposes a
  fixture for this case.
- Onward delegation. A bound on delegation is stated in the conferral record
  at conferral time. The precondition verifier checks the attempted action
  against that bound before commitment, in the same consultation of the
  record that establishes its standing, so a delegation outside the bound
  and a revoked grant are detected at the same point and resolve the same
  way.

Acts already under way
----------------------

A change in trust state can arrive while an act is in progress. The #60 v3
text, proposed by the author and accepted by Xinghua Zhao:

    An act under way is a sequence of operations. The operation contract
    declares the re-consultation points as operation boundaries and may bound
    an operation's duration. At each check before and after commitment the
    enforcement point records the version of the record consulted, so that
    the segment a change governs is recoverable from decision records without
    reliance on the acting agent. What the act does between the two checks of
    one operation, when the record changes, is Workstream E's to specify.

On Workstream E's side, Laurent Beaumois added the matching sentence:
Workstream E specifies what happens inside one operation when the record
changes, including its interruption and the time to effect, and the reach of
a change to operations and workers on platforms where the enforcement point
does not sit inside the operation.

Fan-out follows the same rule. For a worker dispatched before a change and
started after it, the worker's first check records the version it read, and
the parent's dispatch record shows the version the parent's check read. The
enforcement point, never the actor, records the consulted version.

The decision record identifies the act
--------------------------------------

Two acts that differ in any act-describing field must not produce the same
record. The #60 v3 wording, from the author, Xinghua Zhao and Iván Abril
Palma: the act is identified by the operation contract applied, the instance
of the process the operation serves, the execution instance the record
assesses (the LA-2.3 association, for retries within one run), and a value
recomputed by the enforcement point from the act-describing fields the
contract declares.

Content-binding and occurrence-binding are two separate, separately testable
properties. The execution instance is a separate occurrence-binding claim,
sourced to LA-2.3, so that the content-derived value stays a function of
content alone. The per-field test proposed on 9 November is necessary and
insufficient on its own.

Open points on the interface
----------------------------

The following points remain open on #60 and bear on the operation contract.
The contract's disposition clause is where the first three land for WG2.

- No silent permit (Cyril Gorlla). An act that could not reach the record has
  no finding about standing and must not report one: the outcome is
  ``indeterminate``.
- Distinguishable failures (Xinghua Zhao). "No record found" and "record
  found, standing revoked" are different outcomes.
- Recency in the decision record (Xinghua Zhao). Each decision records the
  version or recency of the record it consulted.
- Several locally valid references (Iván Abril Palma). One operation whose
  declared precondition requires two independent supporting sources,
  compared across three cases with the authority, contract and claim held
  fixed. Proposed placement (Xinghua Zhao): independence is a qualification
  of the pair of references, and the scope in which it is assessed is
  declared in the operation contract. The author's position is held until
  the test runs.
