# From Business Capabilities to Agentic Opportunities: A Practical Guide

*Part 2 of 7 | How to decompose enterprise capabilities and identify where AI agents, workflows, and traditional automation belong.*

“We need a Sales Agent” is not an architecture requirement.

It tells us neither the business problem nor the action the agent should be allowed to take. Before designing an agent, we need to understand the capability it is meant to improve.

Consider **Quote Management** at an industrial supplier. A customer request might require product matching, technical compatibility checks, contract pricing, inventory checks, discount approval, and quote creation. Calling the whole process “agentic” hides important differences among those tasks.

## Step 1: Define the business outcome

Begin with a short capability statement:

- **Capability:** B2B Quote Management
- **Business owner:** Sales Operations
- **Current problem:** Complex requests involve repeated manual handoffs
- **Desired outcome:** Prepare accurate quotes faster without bypassing policies
- **Measures:** Time per quote, pricing correctness, manual review rate, cost per quote

These are example fields, not measured results. A real assessment should first record the current baseline.

## Step 2: Decompose the decisions

Break the capability into individual steps. For each step, ask four questions:

1. Does it require interpretation or reasoning?
2. Is there a stable business rule or authoritative system?
3. What could go wrong if the result is incorrect?
4. Can the result be independently checked?

Now the architecture becomes clearer.

## Practical artifact: Business Capability Decomposition Matrix

| Workflow step | Reasoning needed? | Authoritative control | Suggested pattern |
|---|---|---|---|
| Understand buyer request | High | Customer context and input validation | Agent or AI-assisted extraction |
| Find matching products | High | Product catalog and compatibility evidence | Agent with catalog tools |
| Verify compatibility | Medium | Product rules and specialist review | Rules plus assisted review |
| Calculate contract price | Low | ERP pricing engine | Deterministic API |
| Check stock | Low | Inventory service | Deterministic API |
| Prepare draft quote | Medium | Quote schema and policy checks | AI-enabled workflow |
| Approve exception | Business judgment | Delegated approval authority | Human approval workflow |
| Submit order | Low reasoning, high impact | Commerce/ERP transaction service | Governed transactional workflow |

This matrix is deliberately more useful than drawing a box labeled “Quote Agent.” It shows where language-model reasoning is justified and where an agent must rely on existing software.

## Step 3: Define the boundary, not just the component

Suppose the agent finds a lower-cost alternative pump. It may recommend it only when there is verified compatibility evidence. If that evidence is missing, the correct response is to ask for more information or route the request to a specialist.

Similarly, a price returned by the ERP is a business fact. The agent can explain the price, but it cannot change the contract calculation.

A useful design rule is:

**The agent may select a governed capability. The underlying service decides whether the requested operation is valid and authorized.**

This keeps domain ownership intact and reduces the risk of an AI response becoming an uncontrolled transaction.

## Step 4: Compare against the simpler alternative

Before choosing an agent, consider whether a conventional workflow with one AI extraction step can meet the same goal. A dynamic agent adds planning flexibility, but also adds uncertainty, evaluation work, latency, and operational cost.

Use an agent when the business needs adaptive decisions and the added complexity is justified by measurable results.

**Try it:** Choose one capability and list its steps using the four columns above. Mark the steps that need reasoning, the steps that must remain deterministic, and the steps that require human authority. That table becomes the starting point for a C4 architecture and an Agent Operating Contract.

*Next in Part 3: Seven principles that turn this analysis into consistent architecture decisions.*
