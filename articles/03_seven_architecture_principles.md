# Seven Principles for Enterprise Agentic Transformation

*Part 3 of 7 | Design rules for agent-enabled business capabilities*

It is easy to build a demonstration in which an AI agent calls tools and completes a task. It is much harder to build a system that operates safely with real customers, data, policies, and business consequences.

A useful way to close that gap is to establish architectural principles *before* choosing a model or agent framework.

Here are the seven principles I would use to guide an enterprise transformation.

## 1. Start with the business capability

Describe the problem, outcome, owner, and baseline first. “Deploy a Procurement Agent” is a solution idea. “Reduce the manual effort required to validate supplier quotes” is a business problem we can measure.

## 2. Be deterministic where possible, agentic where valuable

AI reasoning helps with ambiguity, context, and changing decision paths. Conventional software should continue to handle stable rules, calculations, validations, and critical transactions.

In B2B Commerce, the agent can interpret a buyer’s request. The ERP should calculate the contractual price.

## 3. Preserve ownership of enterprise data and transactions

Agents should access business capabilities through governed APIs and tools. They should not directly change systems of record because the model believes an action is correct.

A healthcare scheduling agent can recommend available appointments, but the scheduling system remains responsible for the booking transaction.

## 4. Define autonomy at the action level

“Autonomous agent” is too broad to be a permission model. An agent may read inventory, prepare a quote, or recommend a replacement flight. Each action needs its own limits, checks, and approval conditions.

An agent’s ability to call a tool is not proof that the action is authorized.

## 5. Keep the architecture composable

Separate reasoning, workflow state, tool access, domain logic, and policy enforcement. This makes it possible to improve the agent or change models without rewriting the ERP integration or order service.

Start with one agent when one agent is enough. Multi-agent coordination should solve a demonstrated problem, not become the default diagram.

## 6. Design for production from day one

Include security, audit trails, evaluation datasets, timeouts, retries, recovery, and monitoring in the initial design.

If the pricing API fails, the agent must not invent a price. If an external document contains malicious instructions, those instructions must not override the agent’s operating rules.

## 7. Measure business outcomes, not agent activity

The number of model calls, tools, or agents says little about business value. Measure quote turnaround time, correctness, intervention rate, cost, and customer experience. Compare the new approach with a simpler baseline.

## Practical artifact: The Seven-Principle Architecture Review

Use these questions in an architecture review. Record **Yes, No, or Needs Evidence** and assign an owner to each unresolved issue.

| Review question | Evidence to request |
|---|---|
| Is the business outcome measurable? | Capability owner and baseline |
| Are deterministic decisions kept outside the model? | Workflow and rule mapping |
| Do domain systems retain authority? | API and transaction boundaries |
| Are permissions defined per action? | Tool permission matrix |
| Can the AI layer be replaced independently? | Component and integration design |
| Are failures and attacks tested? | Evaluation and failure test results |
| Is the business impact measured? | KPI dashboard and cost model |

**Try it:** Review a proposed agent using this table. Any “No” is a design issue to resolve, not a reason to hide the problem behind a more advanced framework.

These principles will serve as our common rules across B2B Commerce, Healthcare, and Airlines. The industries differ, but the need for trusted systems, explicit responsibility, and controlled actions remains the same.

*Next in Part 4: How to turn these principles into a practical Agent Operating Contract.*
