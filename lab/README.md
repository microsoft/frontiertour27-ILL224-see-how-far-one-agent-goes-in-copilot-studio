# Caldova Supplier Assurance Agent

These instructions are for participants in the instructor-led Microsoft AI Tour lab **See How Far One Agent Goes in Copilot Studio**.

## Lab overview

In this 60-minute hands-on lab, you will build a Supplier Assurance Agent for Caldova Pharmaceuticals. The agent reviews a supplier invoice, checks current operational records through the SharePoint MCP, grounds its decisions in contracts and approvals stored in SharePoint, runs Python in the GitHub Copilot harness sandbox, creates a PDF review brief, records a nonfinancial review log, and participates in a workflow.

The agent recommends what Caldova can process and what it should challenge. It never pays an invoice, rejects a charge, changes supplier status, or replaces an authorized reviewer.

## Skillable conventions

Text surrounded by `+++` becomes clickable autotype text in Skillable. Variables such as `@lab.CloudCredential(...)` and `@lab.Variable(...)` resolve when the hosted lab runs.

> [!IMPORTANT]
> Wait for autotype to finish before clicking elsewhere in the virtual machine. At home, replace Skillable variables with values from your own environment.

## What you will build

- A Copilot Studio agent with focused instructions and guardrails
- SharePoint knowledge grounded in contracts, policies, approvals, and quality documents
- A SharePoint MCP connection for live list reads and a controlled review-log write
- An Invoice Fact Check skill created in the authoring experience
- An uploaded Invoice Review Decision skill with packaged Python
- A reusable Agent Ops evaluation
- A simple three-node workflow built from scratch with your published agent
- A published Supplier Assurance Agent tested in Microsoft 365 Copilot
- Optionally, a read-only Supplier Assurance Dashboard created with Copilot Studio Apps

## Lab sections

1. [Introduction and sign in](./instructions/00-Introduction.md)
2. [Build the Supplier Assurance Agent](./instructions/01-Build-The-Agent.md)
3. [Add skills and review an invoice](./instructions/02-Add-Skills-And-Review-Invoice.md)
4. [Personalize, evaluate, and publish the agent](./instructions/03-Evaluate-And-Publish.md)
5. [Build and test the workflow](./instructions/04-Create-The-Workflow.md)
6. [Publish and test in Microsoft 365 Copilot](./instructions/05-Publish-To-Microsoft-365-Copilot.md) (10-15 additional minutes)

The final required lab follows the workflow test and makes the agent available in Microsoft 365 Copilot, verifying its published behavior using read-only case prompts. Channel installation must be enabled before the session; organization-wide catalog submission is not required.

### Optional bonuses

1. [Build the Supplier Assurance Dashboard](./instructions/06-Bonus-Build-The-Supplier-Dashboard.md) (15-20 additional minutes).
2. [Create a Supplier Meeting Prep Agent with Copilot Cowork](./instructions/07-Bonus-Create-An-Agent-With-Cowork.md) (15-20 additional minutes).

The Apps bonus displays the recorded Astor Ridge review and the completed Northwind workflow response. It follows publishing and is not required to complete the workshop. Allow additional time beyond the base workshop for either bonus.

Use Cowork's Copilot Studio skill to create and refine a separate, read-only agent that prepares evidence-based supplier meeting agendas. The bonus requires the Frontier artifact-creation capability and leaves the new agent as a draft; it does not change the main Supplier Assurance Agent.

## Lab files

The Skillable virtual machine provides the files under:

```text
C:\LabFiles\ILL224
```

The SharePoint site, reference documents, operational lists, learner account, mailbox, and Power Platform environment are prepared before the session.

Select **Next** to begin.
