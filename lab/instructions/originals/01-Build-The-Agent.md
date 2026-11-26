<!-- markdownlint-disable MD034 -->

# 1 - Build the Supplier Assurance Agent

The first step in creating your agent is to establish its purpose and boundaries before connecting data.

1. Open Microsoft Edge Browser (the Internet icon on the VM desktop) in your virtual machine and go to +++https://copilotstudio.microsoft.com+++.
1. Sign in using the username and Temporary Access Pass below.

    **Username:** +++@lab.CloudCredential(AITour27M365E7).AdministrativeUsername+++<br />
    **Temporary Access Pass:** +++@lab.CloudCredential(AITour27M365E7).AdministrativeTAP+++

1. Select the environment dropdown in the bottom left-hand corner and choose the **DevOne** environment.

    ![Select the assigned Power Platform environment](./assets/01.1-select-environment.png)

1. On the home page, select the **Agent** tile.

    ![Select the agent tile](./assets/01.2-select-agent.png)

1. Select the **Untitled Agent** text to re-name the agent. Name the agent:

    ```text
    Supplier Assurance Agent
    ```

    ![Change the agent name](./assets/01.3-change-name.png)

1. Paste the following in the **Instructions** text box:

    ```text
    You are the Caldova Supplier Assurance Agent.

    Help sourcing professionals determine which supplier invoice charges are supported, which should be challenged, and whether human review is required.

    Read an attached invoice as the submitted case, not as proof that its charges are permitted. Use the SharePoint MCP for current supplier, invoice, line, and quality records. Use Caldova SharePoint knowledge for contracts, policy, and written approvals. Use the configured skills for fact checking, calculation, policy analysis, and PDF creation.

    Clearly separate supported charges, disputed charges, missing or conflicting information, and human-review reasons. Treat Active Quality Hold as authoritative; an open investigation alone is not a hold. Cite governed documents.

    Ask for confirmation before creating an Invoice Review Log item. Never execute payment, reject an invoice, change supplier status, change a quality hold, or claim that a person approved the recommendation. Use memory only for communication preferences, never case facts.
    ```

    ![Enter the agent instructions](./assets/01.4-instructions.png)

1. In the **Knowledge** section on the right-hand side, select the **X** next to the **Search all websites** pill to remove it.

    ![Remove ability to search all websites](./assets/01.5-remove-all-websites.png)

    > [!NOTE]
    > **Why:** By default, this setting enables your agent to reference all information on the web. Disabling will ensure the agent only pulls data from the knowledge sources we explicitly add.

1. Select the **Work IQ** pill under **Tools** to open the edit tool screen.

    ![Select Work IQ](./assets/01.7-select-workiq.png)

    > [!NOTE]
    > **Why:** Contracts, policy, approvals, and quality documents govern supplier reviews. These files are stored in SharePoint, which is accessible as a source in the Work IQ tool.

1. The Work IQ tool exposes a variety of sources, but we don't need all of these. Select the **check mark** next to the **OneDrive**, **Teams**, **Outlook** and **Calendar** sources to **uncheck** them and make sure they aren't available.

    ![Checkmark before](./assets/01.8-check-marks.png)

    ![Checkmark after](./assets/01.8-unchecked.png)

1. Select the **arrow** next to the **People** source.

    ![Select people arrow](./assets/01.9-people-arrow.png)

1. Select the **Access level** dropdown and choose **Read-only** so that we only give the agent access to what it needs to do (retrieve people information).

    ![Change access level](./assets/01.10-read-only.png)

1. Select the **Done** button to save your changes. Leave the SharePoint source with read-write access.

    ![Done](./assets/01.11-confirm-readonly.png)

    > [!NOTE]
    > **Why:** The Work IQ tool can perform read and write operations on several sources (SharePoint, Outlook, Calendar, etc.). Use **least privilege** access: provide the agent with only the minimum access it needs.

1. Select the **Save icon** to save your agent configuration.

    ![Save](./assets/01.12-save.png)

Select **Next** to add knowledge.
