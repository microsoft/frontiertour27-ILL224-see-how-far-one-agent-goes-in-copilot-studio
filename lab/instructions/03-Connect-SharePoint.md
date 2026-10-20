<!-- markdownlint-disable MD034 -->

# 3 - Add the SharePoint Connector

Now you'll enable your agent to perform actions by adding a Tool.

1. Select the **Plus button** in the **Tools** section.

    ![Select the add button](./assets/03.1-add-tool.png)

1. Select the **Connectors** tab.

    ![Select the MCP tab](./assets/03.2-connector-tab.png)

1. Type `SharePoint Get` in the text box, and select the **Get Item** action from the SharePoint Connector

    ![Select the SharePoint Get Item](./assets/03.3-select-get-item.png)

1. Select the **Add** button.

    ![Select the add button](./assets/03.4-add-get-item.png)

1. Select the **Plus button** in the **Tools** section again.

    ![Select the add button](./assets/03.5-plus-tool.png)

1. Select the **Connectors** tab.

    ![Select the MCP tab](./assets/03.2-connector-tab.png)

1. Type `SharePoint Create` in the text box, and select the **Create Item** action from the SharePoint Connector

    ![Select the SharePoint Create Item](./assets/03.6-select-create-item.png)

1. Select the **Add** button.

    ![Select the add button](./assets/03.7-add-create-item.png)

1. Select the **Plus button** in the **Tools** section again.

    ![Select the add button](./assets/03.8-add-tool.png)

1. Select the **Connectors** tab.

    ![Select the MCP tab](./assets/03.2-connector-tab.png)

1. Type `SharePoint Update` in the text box, and select the **Update Item** action from the SharePoint Connector

    ![Select the SharePoint Get Items](./assets/03.9-select-update-item.png)

1. Select the **Add** button.

    ![Select the add button](./assets/03.10-add-update-item.png)

1. Select the **Save** icon to save your changes.

    ![Save the changes](./assets/03.11-save.png)

1. Select the **Plus button** in the **Tools** section again.

    ![Select the add button](./assets/03.11-plus-button.png)

1. Select the **Connectors** tab.

    ![Select the MCP tab](./assets/03.2-connector-tab.png)

1. Type `SharePoint Get` in the text box, and select the **Get Lists** action from the SharePoint Connector

    ![Select the SharePoint Get Lists](./assets/03.12-select-get-lists.png)

1. Select the **Add** button.

    ![Select the add button](./assets/03.13-add-get-lists.png)

1. Select the **Save** icon to save your changes.

    ![Save the changes](./assets/03.14-save.png)

## Start a supplier invoice review

1. Select the **Preview** tab to go back to the testing screen.

    ![Test the changes](./assets/03.9-preview-tab.png)

1. Select the **New chat** button. Copy and paste the following into the text box and press **Enter**.

    ```text
    Astor Ridge Biologics has asked us to review invoice ARB-260814.

    Verify that the supplier is active and whether batch CDV-AX47 has an active quality hold. If the supplier is active and there is no active hold:
    1. Update invoice ARB-260814 from Pending Review to Review Requested.
    2. Look for an Invoice Review Requests item whose Title is Astor Ridge invoice review - ARB-260814. If it does not exist, create it. If it already exists, update it instead so there is only one request.
    3. Set Invoice ID to ARB-260814, Request Notes to Review the expedited production premium, cold-chain freight, and validation documentation charges against the contract, approvals, policy, and quality records, and Status to New.

    Read the invoice and request back. Report the supplier and quality checks, the invoice's new status, the request item ID, and whether you created or updated the request. Do not analyze the contract or decide which charges are supported yet.
    ```

    ![Enter the request](./assets/03.10-test-prompt.png)

1. If prompted, select **Approve** in the **Permission Required** message to call the SharePoint tools..

    ![Approve the request](./assets/03.11-approve-mcp.png)

1. Confirm the response reports an active supplier, no active quality hold, invoice status Review Requested, and the request item ID.

    ![Review the response](./assets/03.12-review-response.png)

1. Open the **Invoice Review Requests** list:

    +++https://@lab.CloudCredential(AITour27M365E7).TenantPrefix.sharepoint.com/sites/CaldovaSupplierOps/Lists/Invoice%20Review%20Requests/AllItems.aspx+++

    Verify one **Astor Ridge invoice review - ARB-260814** item has Status **New** and the specified request notes.

    ![Review the list](./assets/03.13-view-list-item.png)

1. Select the **Build** tab to go back to the configuration screen.

    ![GO back to the build tab](./assets/03.14-build-tab.png)

Select **Next** to add reusable skills.
