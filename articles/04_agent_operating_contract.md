# Designing Agent-Enabled Operating Capabilities

*Part 4 of 7 | Autonomy, business ownership, and the Agent Operating Contract*

A critical question in enterprise AI is often missed during implementation:

**Who is accountable when an agent takes an action that affects a customer or business transaction?**

The model cannot own that responsibility. The enterprise must assign it, then encode the boundaries in architecture and operating policy.

Let’s use our B2B Quote Management example. An agent can identify products, check prices, and prepare a draft. But it should not be able to modify contractual prices or submit an order simply because it has access to the required API.

## Separate five responsibilities

An agent-enabled capability should distinguish:

1. **Business capability:** Defines the outcome and the policies that govern it.
2. **Agent reasoning:** Interprets requests and selects from permitted actions.
3. **Governed workflow:** Tracks state, validates permissions, and handles approvals.
4. **Domain services:** Enforce authoritative rules and commit transactions.
5. **Operations and governance:** Monitor quality, security, cost, incidents, and changes.

This is a logical separation. It does not require five separate products or microservices.

## Use a practical autonomy model

For this series, I use five working levels:

| Level | Allowed responsibility | Example |
|---|---|---|
| L0 | Deterministic, no AI decision | ERP calculates contract price |
| L1 | Assist a user | Suggest matching products |
| L2 | Recommend a decision | Recommend a quote configuration |
| L3 | Prepare a controlled work product | Save a draft quotation |
| L4 | Trigger an explicitly authorized action | Submit an approved order through a governed service |

These levels are our teaching model, not an industry standard. L4 is never blanket permission. Even an approved action must pass identity, authorization, policy, and transaction checks.

## Practical artifact: Agent Operating Contract

Before building an agent, write down what it may do, how success is defined, and what happens when it fails.

Here is a compact, **filled example**:

| Contract field | B2B Quote Agent |
|---|---|
| Business owner | Sales Operations |
| Objective | Prepare a valid draft quote from a buyer request |
| Trusted sources | Authorized customer context, catalog, pricing and inventory services |
| Permitted reads | Search catalog, retrieve compatibility evidence, check price and stock |
| Permitted writes | Create or update a draft quote through the Quote API |
| Prohibited actions | Change contract prices, approve exceptions, submit orders |
| Maximum autonomy | L3 for draft preparation |
| Required validations | Customer scope, compatibility evidence, current prices, quote schema |
| Human escalation | Missing compatibility evidence, commercial exception, repeated tool failure |
| Fallback | Manual sales quotation process |
| Operational evidence | Trace ID, tool results, approval decisions, error and cost metrics |
| Success metric | Correct draft preparation time and manual intervention rate |

This is an **operating contract**, not a prompt. Its rules must be enforced by the workflow, API permissions, policy controls, and testing. Instructions in a system prompt alone cannot provide security guarantees.

## Make accountability explicit

Sales Operations owns the business result. Architecture defines boundaries. Engineering builds and tests integrations. Security and risk owners approve the relevant controls. Service Operations owns incident response and reliability.

When a quote contains an incorrect recommendation, these responsibilities determine who investigates, who assesses impact, and who approves the fix.

**Try it:** Fill in the same contract for one capability in your organization. Pay special attention to the difference between *information the agent can read* and *business actions it can perform*.

If you cannot name the owner, prohibited actions, and escalation path, the agent is not ready for production execution.

*Next in Part 5: How these boundaries change across Commerce, Healthcare, and Airlines.*
