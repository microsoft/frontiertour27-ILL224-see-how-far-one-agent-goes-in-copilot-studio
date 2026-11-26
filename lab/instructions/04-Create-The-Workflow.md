<!-- markdownlint-disable MD034 -->

# 4 - Build and Test the Workflow

Now you'll create a Workflow that starts an invoice review when a SharePoint request is added. The Workflow only orchestrates the work; your agent retrieves records, applies policy, and produces the response.

## Create the Workflow

1. Select the **Workflows** tab in Copilot Studio.

    ![Select the workflow tab](./assets/06.1-select-workflow-tab.png)

1. Select the **Create your first workflow** button.

    ![Select the create workflow button](./assets/06.2-create-workflow.png)

1. Select the **Untitled workflow** text in the upper left hand corner. Replace the name with the following:

    ```text
    Process Supplier Invoice Review Request
    ```

    ![Change the workflow name](./assets/06.3-workflow-name.png)

## Add the SharePoint trigger

1. Select the **start node**. Select the **Trigger type** dropdown and select the **Connector** option.

    ![Change the trigger](./assets/06.4-select-trigger.png)

1. In the search box type ``SharePoint When an Item is Created`` and select the **When an item is created** trigger.

    ![Select the trigger](./assets/06.5-when-item-created-trigger.png)

1. In the right hand panel, configure the following:

    | Field | Value |
    | --- | --- |
    | Site Address | +++https://@lab.CloudCredential(AITour27M365E7).TenantPrefix.sharepoint.com/sites/CaldovaSupplierOps+++ |
    | List Name | `Invoice Review Requests` |

    ![Configure the trigger](./assets/06.6-trigger-config.png)

## Add the agent

1. Select the **plus button** next to the **when an item is created** node.

    ![Add an action](./assets/06.7-add.png)

1. Select the **Agent** action from the list of options.

    ![Select an action](./assets/06.8-select-agent-action.png)

1. Select the **Supplier Assurance Agent** in the **Agent** dropdown on the right hand side.

    ![Select the agent](./assets/06.9-select-agent.png)

1. Copy and paste the following into the **Message** input.

    ```text
    Review supplier invoice [Invoice ID].

    Request notes: [Request Notes]

    Use the the CaldovaSupplierOps SharePoint site for current invoice, line, supplier, quality records, the governing contract, approvals, and policy. Run both configured skills.

    Return supported and disputed amounts, reconciliation difference, human-review status and reasons, evidence citations, and a statement that no financial or supplier action was taken.
    ```

    ![Paste the message](./assets/06.10-message.png)

1. Delete the **[Invoice ID]** text in the message. With your cursor where you delete that text, select the **lightning bolt icon**.

    ![Paste the message](./assets/06.11-InvoiceID-lighting-bolt.png)

1. Select the **Invoice ID** property from the **When an item is created** trigger.

    ![Paste the message](./assets/06.12-invoiceid-select.png)

1. Select the **[Request Notes]** text in the message. With your cursor where you delete that text, select the **lightning bolt icon**.

    ![Paste the message](./assets/06.13-requestnotes-lighting.png)

1. Select the **Request Note** property from the **When an item is created** trigger.

    ![Paste the message](./assets/06.14-requestnotes.png)

## Update the request

1. Select the **plus button** next to the **Agent** node.

    ![Add a node](./assets/06.15-addnode.png)

1. In the search box, type ``SharePoint update item`` and select the **Update item** action.

    ![Select the action](./assets/06.16-select%20action.png)

1. In the right hand side, configure the properties as follows. Select the **lighting bolt icon** to select the properties:

    | Field | Value |
    | --- | --- |
    | Site Address | +++https://@lab.CloudCredential(AITour27M365E7).TenantPrefix.sharepoint.com/sites/CaldovaSupplierOps+++  |
    | List Name | `Invoice Review Requests` |
    | Id | Trigger `ID` |
    | Title | Trigger `Title` |
    | Invoice ID | Trigger `Invoice ID` |
    | Request Notes | Trigger `Request Notes` |
    | Status | `Complete` |
    | Agent Response | Trigger `Result` |
    | Error Detail | Leave blank |

    ![Review the properties](./assets/06.17-review-update-item.png)

1. Select the **Publish button** to save and publish your changes.

    ![Save the changes](./assets/06.18-publish.png)

> [!NOTE]
> **Why:** The workflow provides a predictable trigger and stores the result. The agent owns MCP retrieval, knowledge grounding, skill execution, and policy reasoning and the workflow helps to make this process autonomous.

## Test the workflow end to end

Your agent and published workflow are ready. Create an invoice review request to test the autonomous process.

1. Open the invoice review request list:

   +++https://@lab.CloudCredential(AITour27M365E7).TenantPrefix.sharepoint.com/sites/CaldovaSupplierOps/Lists/Invoice%20Review%20Requests/AllItems.aspx+++

1. Select the **New** button.

    ![Add a new item](./assets/07.1-new-item.png)

1. Enter the following information in the form then select **Save**:

    | Field | Value |
    | --- | --- |
    | Title | `Review NWT-260821` |
    | Invoice ID | `NWT-260821` |
    | Request Notes | `Review the submitted charges against current records, contract, approvals, policy, and quality holds.` |
    | Status | `New` |

    ![Enter the info](./assets/07.2-form-info.png)

1. Return to the tab with the Workflow open and select the **Activity** tab.

    ![Select the activity tab](./assets/07.3-select-activity-tab.png)

1. Select the **Refresh icon** until you see a running task.

    ![Select the refresh button](./assets/07.4-refresh.png)

1. Confirm the trigger, Run an agent, and Update item nodes complete.

    ![Check it completes](./assets/07.5-check-completion.png)

1. Go back to the invoice review request SharePoint list and verify that an item appears for **Review NWT-260821**.

    ![Check the list](./assets/07.6-check-list.png)

1. Open the request item and review the Agent Response for the expected result:

    | Result | Expected amount |
    | --- | --- |
    | Invoice total | $122,300 |
    | Supported | $108,800 |
    | Disputed | $13,500 |
    | Reconciliation difference | $0 |

    ![Check the response](./assets/07.7-agent-response.png)

## What happened

| Layer | Responsibility |
| --- | --- |
| Request list and Workflow | Started the review and stored the readable response |
| SharePoint MCP | Retrieved current records and enabled a controlled log write |
| SharePoint knowledge | Supplied contract, approval, policy, and quality-document facts |
| Skills and sandbox | Organized facts, calculated the result, and created the PDF |
| Human reviewer | Owns every financial decision |

No payment, rejection, supplier change, or quality-hold change was made.

Select **Next** to publish and test the Supplier Assurance Agent in Microsoft 365 Copilot.
