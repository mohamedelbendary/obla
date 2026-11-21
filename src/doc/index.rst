.. raw:: latex

    \pagestyle{plain}
    \thispagestyle{plain}
    \let\osiaorigaddcontentsline\addcontentsline
    \renewcommand{\addcontentsline}[3]{}

.. _chapter-overview:

Operation-Bound Least Agency: Requirements for Enforcing Security Policy on Agent Actions
=========================================================================================

Abstract
--------

A verified identity and a valid authorization establish who an agent is and
what it may reach. Neither bounds what the agent may commit to at the moment
of the act. The WG2 charter states this gap as its problems 1 and 2. This
contribution addresses it with a control dimension distinct from least
privilege: least agency, the bounded scope of operations and decisions an
agent may autonomously perform or commit to, together with the required
verification structure and the responsible roles.

The contribution consolidates the least-agency requirements the author
contributed on FG-TIDA/themes#4 on 17 October 2026, which the WG2 charter
lists as an input to deliverable 2, with the revisions settled in that thread
on 4 November and the positions settled on FG-TIDA/themes#60 by 18 November.
It specifies 29 requirements in six groups, each with its rationale and its
source: least agency (LA-1), operation-bound enforcement (LA-2), predicate
classification (LA-3), evaluation order and predicate composition (LA-4),
semantic verdict eligibility for action gating (LA-5), and alternate
operations (LA-6). Three companion requirements on memory-mediated evolution
are given in an annex. The unit of analysis is the charter's: the enforcement
decision for one action.

Two further parts serve deliverable 1. The first states the interface between
the operation contract and the trust control plane proposed under
FG-TIDA/themes#59, as recorded on FG-TIDA/themes#60: the operation contract in
force as a decision input, acts under way as sequences of operations with
re-consultation at operation boundaries, and the identification of the act in
the decision record. The second proposes a reference layering of enforcement
concerns (identity and trust infrastructure, resource access, role-structural,
semantic) against which each solution path assessed in deliverables 3 and 4 is
positioned, and records which requirements are path-neutral and which belong
to the operation-bound path.

The requirements derive from the agentic AI containment architecture
published in the IntelliSys 2026 proceedings. Encodings and protocol
specifications are out of scope.

History
-------

.. tabularcolumns:: |>{\raggedright\arraybackslash}p{0.08\linewidth}|>{\raggedright\arraybackslash}p{0.36\linewidth}|>{\raggedright\arraybackslash}p{0.12\linewidth}|>{\raggedright\arraybackslash}p{0.09\linewidth}|>{\raggedright\arraybackslash}p{0.17\linewidth}|

.. list-table::
    :header-rows: 1
    :widths: 10 40 14 12 24

    * - Version
      - Document
      - Date
      - Focus Group
      - Working Group
    * - 0.1
      - Operation-Bound Least Agency: Requirements for Enforcing Security Policy on Agent Actions
      - 2026-11-21
      - TIDA
      - WG2 (IBEA)

Authors
-------

.. tabularcolumns:: |>{\raggedright\arraybackslash}p{0.17\linewidth}|>{\raggedright\arraybackslash}p{0.33\linewidth}|>{\raggedright\arraybackslash}p{0.42\linewidth}|

.. list-table::
    :header-rows: 1
    :widths: 18 34 48

    * - Name
      - Affiliation
      - Contact
    * - Mohamed ElBendary
      - Individual capacity (independent expert, United States)
      - mohamed.elbendary@gmail.com

Keywords
--------

Agentic AI, least agency, operation contract, enforcement point, structural
predicate, semantic predicate, verification, decision record, security policy
enforcement.

.. raw:: latex

    \newpage

Foreword
--------

Agentic AI systems now act as autonomous entities capable of reasoning, planning, and
executing tasks across services, infrastructures, and organizational boundaries. This
fundamentally changes the nature of identity in digital systems: identity is no longer
limited to human users and static machine instances but must also encompass autonomous,
dynamic, and goal-oriented agents. And identity alone is insufficient: the core question
extends beyond "what an entity is" to "whether, and under what conditions, that entity
should be trusted to act".

The Focus Group on Trust and Identity for humans and agentic AI (FG-TIDA) addresses trust
management and interoperable digital identity infrastructure for humans and for agentic AI,
supporting the development of secure, trustworthy digital ecosystems in which humans and
agentic AI can safely interact and collaborate.

FG-TIDA was established under Recommendation ITU-T A.7 (Focus groups: Establishment and
working procedures), with ITU-T Study Group 17 as its parent group. Further details are
available in the group's terms of reference.

Note
----

This document is a contribution to the first FG-TIDA in-person meeting (Paris, 30 November to 1 December 2026), submitted in the
author's individual capacity and targeted at WG2. It consolidates technical
input the author posted on FG-TIDA/themes#4 (17 October and 4 November 2026),
on the WG2 charter repository (issues #5 to #9, November 2026) and on
FG-TIDA/themes#60 (6 to 18 November 2026). Where a requirement was revised
following a point raised by another participant, the revision is marked and
credited. The requirements derive from an architecture paper by the author
published in the IntelliSys 2026 proceedings (Springer LNNS), listed in the
references; section numbers in the source mappings refer to the arXiv version
of that paper. The author requests clause-level attribution of any part of
this contribution that the working group takes up, per section 9 of the WG2
charter.

Material prepared with the assistance of generative AI tools was reviewed and
approved by the author, who is responsible for the content.

.. raw:: latex

    \let\addcontentsline\osiaorigaddcontentsline
    \sphinxtableofcontents
    \osiamainmatter
    %% The toctree below sits inside the Note section, so Sphinx emits the
    %% body documents one level down. Shift LaTeX headings up one level so
    %% body documents are chapters, as in the HTML.
    \let\paragraph\subsubsection \let\subsubsection\subsection \let\subsection\section \let\section\chapter

.. toctree::
    :maxdepth: 3
    :numbered:
    :hidden:

    chapters/01_problem
    chapters/02_scope
    chapters/03_terms
    chapters/04_requirements
    chapters/05_interface
    chapters/06_layering
    chapters/07_assessment
    chapters/08_references
    chapters/09_annex/index
