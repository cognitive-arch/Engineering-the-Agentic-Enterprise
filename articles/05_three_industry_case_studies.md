# Three Industries, One Agentic Architecture Challenge

*Part 5 of 7 | B2B Commerce, Healthcare, and Airline Disruption Recovery*

Should a quotation agent, a patient scheduling assistant, and an airline disruption agent use the same architecture?

They can share architectural principles and technical building blocks, but **they should not share the same autonomy rules**.

Across all three industries, agents can interpret requests, retrieve trusted information, compare options, and recommend actions. The difference is the business authority, risk, and verification required before acting.

## Case 1: B2B Commerce, Quote-to-Order

A buyer asks for industrial pumps, spare parts, contract pricing, and delivery information. The agent interprets the request, searches the catalog, checks alternatives, and prepares a quote.

The ERP determines prices. Product rules and specialists validate compatibility. Inventory services provide availability. A governed workflow handles approval and order submission.

**Reasoning opportunity:** Product discovery, ambiguous requirements, and exception handling.

**Protected boundary:** Contract pricing, discounts, and order transactions.

**Business measure:** Quote turnaround time, price correctness, cost per quote.

## Case 2: Healthcare, Patient Access

A patient wants an appointment and explains the request in everyday language. The assistant helps identify administrative options and retrieves available appointments.

The patient management and scheduling systems remain authoritative. Identity, consent, privacy, and eligibility are validated independently. Clinical questions or urgent symptoms require an appropriate human or clinical pathway, not an uncontrolled scheduling-agent decision.

**Reasoning opportunity:** Understanding administrative requests and navigating options.

**Protected boundary:** Patient data, clinical decisions, and appointment transactions.

**Business measure:** Scheduling completion, access time, administrative effort.

## Case 3: Airlines, Disruption Recovery

A flight is canceled. A passenger needs another route, possibly with connections and special constraints. An agent can review the disrupted journey, find feasible alternatives, and prepare recommendations.

Reservation services must confirm seats, fare and servicing rules, and booking validity. Availability may change before confirmation. Ticketing and rebooking actions require authorized transactional controls.

**Reasoning opportunity:** Comparing dynamic recovery options across multiple constraints.

**Protected boundary:** Reservation inventory, ticketing, servicing rules, and passenger authorization.

**Business measure:** Recovery handling time, servicing cost, passenger experience.

This is an illustrative international airline scenario, not a description of any airline's internal systems.

## Practical artifact: Cross-Industry Capability and Autonomy Matrix

| Domain | AI-led activity | Authoritative system | Starting autonomy | Escalation trigger |
|---|---|---|---|---|
| B2B Commerce | Match products and draft quote | Catalog, ERP, inventory, quote services | L2–L3 | Unverified compatibility or exception pricing |
| Healthcare | Explain scheduling options | PMS/EHR and scheduling services | L1–L2 | Identity uncertainty or clinical concern |
| Airline | Recommend recovery options | Reservation and flight operations systems | L2 | Unavailable inventory or complex policy exception |

The starting autonomy levels are proposed design choices, not assertions about real deployments.

## What is reusable and what is not?

**Reusable:** Agent runtime, governed tool interface, identity propagation, policy checks, audit logs, evaluations, observability, and escalation workflow.

**Domain-specific:** Pricing rules, patient privacy policies, booking constraints, approvals, source-of-truth systems, and definitions of an acceptable outcome.

A common agent platform can provide reusable infrastructure. It cannot decide which business actions are safe or valid in every domain.

**Try it:** Copy the matrix and add one workflow from your own industry. Identify the authoritative system, the highest permitted action, and the event that must trigger human review.

*Next in Part 6: Turn one of these scenarios into the smallest useful implementation.*
