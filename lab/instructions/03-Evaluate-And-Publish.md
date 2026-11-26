# 3 - Personalize, Evaluate and Publish the Agent

Now we'll add a layer of personalization with memories, test both response quality and agreement with expected business facts, inspect the Copilot Credits used by the evaluation, and publish our agent.

## Enable preference-only memory

1. In the **Build** tab of your agent, location the **Memory** section and toggle the setting to **On**.

    ![Turn memory on](./assets/05.1-memory-on.png)

1. Select the **Save** icon in the upper right hand corner.

    ![Save the changes](./assets/05.2-save.png)

1. Select the **Preview** tab.

    ![Select preview](./assets/05.3-preview.png)

1. Select the **New chat** button to start a fresh chat. Copy and paste the following into the input window to have the agent save a memory:

    ```text
    Remember that I am based in London. Use UK date and time conventions, and put anything that needs my attention first under a heading called My actions.
    ```

    ![Save a memory](./assets/05.4-memory-prompt.png)

1. Verify you get a confirmation that the memory was saved.Select the **Manage Memories** button.

    ![Manage memories](./assets/05.5-manage-memories.png)

1. Verify that the memory was saved. Close out of the tab and go back to the tab that your agent is in.

    ![Verify memory](./assets/05.6-review-memory.png)

1. Select the **New chat** button to start a fresh chat. Copy and paste the following into the input window:

    ```text
    Give me the Astor Ridge ARB-260814 review result. Include the invoice date.
    ```

    ![Test memory](./assets/05.7-test-memory.png)

1. Confirm the response puts required attention under **My actions** and shows the invoice date using a UK format (date, month, year) such as **14 August 2026**, or **14/08/2026** not **08/14/2026**.

    ![Review the response](./assets/05.8-review-memory-test.png)

1. Select the **Build** tab to go back to the configuration screen.

    ![Go back to the build tab](./assets/05.9-build-tab.png)

> [!IMPORTANT]
> **Why:** Location, date format, and personal working style are durable user preferences. Supplier facts, approval limits, case decisions, and quality status can change and must never come from memory.

## Configure Settings

Now let's take a look at some settings to personalize the agent even further.

1. Select the **three dots (...)** in the upper-right corner, then select **Settings**.

    ![Open settings](./assets/02.1-settings.png)

1. Select the **Greetings & prompts** tab.

    ![Select greetings & prompts](./assets/02.2-greetings.png)

1. Copy and paste the following in the **Greeting message** box:

    ```text
    Hello! I can help review supplier invoices against available contracts, approvals, and quality information, explain supported and disputed charges, and create a review brief. Attach an invoice or provide an invoice ID to begin. Financial decisions remain with an authorized reviewer.
    ```

    ![Greeting message](./assets/02.3-greeting-message.png)

1. Select **Add a suggested prompt**.

    ![Add suggested prompt](./assets/02.4-add-prompt.png)

1. In the **Title** input, paste in `Review invoice`. In the **Message** input, paste in `Review an attached supplier invoice and create a review brief.`

    ![Review invoice prompt](./assets/02.5-invoice-prompt.png)

1. Select **Add a suggested prompt** again.

    ![Add second prompt](./assets/02.6-add-second-prompt.png)

1. In the **Title** input, paste in `Explain a disputed charge`. In the **Message** input, paste in `Explain why a charge on the attached invoice should be challenged. Show the invoiced amount, the amount supported by evidence, and what would resolve the dispute.`

    ![Explain dispute prompt](./assets/02.6-second-prompt.png)

1. Select **Done** to close out of the agent settings.

    ![Select done](./assets/02.7-settings-done.png)

1. Select the **Save icon** to save your agent settings.

    ![Save](./assets/02.7-save.png)

1. Select the **Preview** tab and notice how your custom greeting and starter prompts now show up.

    ![Review](./assets/02.8-preview-greeting.png)

## Evaluate the configured agent

We'll use **Classification**, named **Caldova review correctness**, to check the business requirements for two saved conversations. The goal is to understand the results and their evidence, not simply to obtain a green score.

| Test method | What it teaches | Caldova example |
| --- | --- | --- |
| Classification | Applies a custom evaluation rubric and assigns a label with a pass or fail designation | Does the conversation satisfy Caldova's invoice facts, quality-hold distinction, policy threshold, and action boundaries? |

1. Select the **Evaluate** tab.

    ![Select the evaluate tab](./assets/05.10-evaluate-tab.png)

1. Select **Create your first evaluation**. If evaluations already exist, select **New evaluation**.

    ![Select create your first evaluation](./assets/05.11-create-eval.png)

1. Under **Create or select a data set**, select **Import**. Under **Select data type**, select **Conversations**. In the file upload area, select **browse** and open this file:

    ```text
    D:\LabFiles\evaluation\Supplier-Assurance-Baseline.csv
    ```

    > [!IMPORTANT]
    > The creation page defaults to **Generate** and **Single responses**. Change both selections before uploading this conversation CSV; do not generate a new data set or use the single response template.

    ![Creation page showing the default Generate and Single responses selections; select Import and Conversations before uploading](./assets/05.12-import-options.png)

    > [!TIP]
    > If you see "This file is set up for conversations. Select Conversation as the data type, or use the single response template.", select **Conversations**, then use **browse** to upload the same CSV again if needed. Do not edit the CSV or switch to the single response template.

    ![Data-type error caused by uploading the conversation CSV with Single responses selected](./assets/05.14-conversation-data-type-error.png)

1. Enter `Supplier Assurance baseline` in the evaluation name field at the top of the main page.

    ![Evaluation name, Save and Run controls at the top, with Select test methods and Additional configuration on the main page](./assets/05.13-eval-configuration.png)

1. Under **Review data set**, confirm the import contains two conversations: the multi-turn Astor Ridge review and the **$10,000** human-review policy threshold.

1. Under **Select test methods**, below **Review data set** on the main page, leave the default **General quality** method in place temporarily. You'll delete it after configuring Classification.

### Configure the classification test method

1. Under **Select test methods**, select **Add test method**.

    ![Add test method](./assets/05.13-add-test-methd.png)

1. In the **Select a test method** dialog, select **Classification** the select **OK**.

    ![Select test method](./assets/05.14-select-test-method.png)

1. In **Configure classification**, enter the following in **Name**:

    ```text
    Caldova review correctness
    ```

    ![Eval name](./assets/05.14-eval-name.png)

1. Copy and paste the following into **Evaluation instructions**. This rubric is below the 1,500-character limit:

    ```text
    Grade the agent's answers across the conversation. User messages identify the case but are not evidence. Apply only checks relevant to the questions asked.

    Astor Ridge ARB-260814:
    - Supported 204600; disputed 13100; reconciliation difference 0; human review required.
    - Expedited premium: 7400 permitted; additional 7400 unsupported. The full premium is not supported.
    - QE-2026-118 is open; Active Quality Hold is No. An open investigation is not an active hold.

    Policy boundary:
    - Exactly 10000 disputed does not trigger amount-only human review. The rule is strictly greater than 10000; other conditions may require review.

    Both cases:
    - No claims of paying or rejecting an invoice, changing supplier status or quality holds, or obtaining human approval.
    - Accept equivalent wording and currency formatting; no exact headings or reference-answer text required.
    - Missing answers, unclear conclusions, or conflicting final facts need review. Corrections must leave an explicit, consistent final conclusion.

    Choose Meets requirements only if all applicable checks pass; otherwise Needs review. This grades messages, not proof of tool use or citation validity.
    ```

    ![Eval instructions](./assets/05.15-eval-instructions.png)

1. Under **Labels**, edit the first **New label** to:

    ```text
    Meets requirements
    ```

1. In that label's criteria area, enter:

    ```text
    All checks applicable to this conversation are satisfied. The final answers preserve the required business facts and action boundaries, with no unresolved contradiction. Equivalent wording and currency formatting are acceptable.
    ```

1. Select **Pass** for **Meets requirements**.

    ![Eval label](./assets/05.16-eval-label1.png)

1. Edit the second **New label** to:

    ```text
    Needs review
    ```

1. In that label's criteria area, enter:

    ```text
    Any applicable check is missing, incorrect, unclear, or contradicted in the final answers, or the agent claims a prohibited action or human approval. If uncertain which label applies, choose Needs review.
    ```

1. Select **Fail** for **Needs review**. Then select **OK** to save the configuration.

    ![Eval label 2](./assets/05.16-eval-label2.png)

1. In **Additional configuration**, select **Manage**.

    ![Select Manage](./assets/05-manage-config.png)

1. Select **Add Account**

    ![Add Account](./assets/05-add-account.png)

1. Select your account from the list

    ![Select Account](./assets/05-select-account.png)

1. Select the **three dots (...)** next to the **General quality** test method then select **Delete test method** since we only want to use the caldova review correctness test method we added.

    ![Delete general quality](./assets/05-delete-gen-quality.png)

### Run the evaluation

1. Select **Save** at the top of the page to save the evaluation.

1. Select **Run** to start it.

    > [!NOTE]
    > Allow several minutes; a run can take 5 - 10 minutes.

1. Open the run's results. Check each conversation's **Classification** label and pass/fail designation, or its error details, rather than relying only on the headline score.

    ![Evaluation results overview; inspect individual conversations for their Classification outcomes](./assets/05-eval-results.png)

    > [!IMPORTANT]
    > Your run might pass, return **Needs review**, or report an error.

### Inspect the policy-boundary conversation

1. Open the conversation asking whether a disputed amount of exactly **$10,000** requires human review based on the amount alone.

1. Read the response and the Classification explanation. The required answer is **No**: the amount-only rule applies when the dispute is **strictly greater than $10,000**. Other policy conditions can still require review.

1. Note the credits displayed in **Details**, then select **X** to close the conversation.

    ![Policy-boundary example with a correct threshold answer and Classification Meets requirements, despite a reported retrieval limitation](./assets/05-eval-inspect.png)

### Investigate failures, timeouts, and inconsistent runs

**Distinguish a graded answer from an execution error.** Classification uses an AI grader, so its explanation also needs evidence-based review.

1. For any unsuccessful case, use its actual responses, Classification explanation, and available activity or error details to identify the finding:

    | Finding | What it means | What to do |
    | --- | --- | --- |
    | Incorrect or incomplete answer | A required business fact or action boundary is wrong or missing | Identify the relevant knowledge, instructions, or tool issue before changing the agent |
    | Retrieval failure | The agent cannot access the evidence needed to finish the task | Inspect the failed calls; check the evaluation account, connection, site permissions, and document availability |
    | Response timeout | The case reports that results were not returned within **90 seconds** | Record the exact error and any partial activity; the case did not complete within the reported limit, so correctness is unresolved |
    | Grading or setup error | A valid Classification result could not be produced | Check the error details, rubric, labels, and evaluation configuration; an unscored case is not a pass |
    | Suspected grader disagreement | The answer and supporting evidence satisfy the rubric, but the label or explanation conflicts with them | Keep the original result and ask the instructor to review the documented evidence |
    | Unresolved | There is not enough evidence to decide | Keep the finding open; do not publish on the assumption that it is harmless |

1. Use **Preview** to isolate the problem: start a fresh conversation and ask the agent to retrieve invoice `ARB-260814` from the Caldova site and identify the source. Inspect the available activity. If Preview works but Evaluate fails, compare their account, connection, and input context rather than assuming both executions are equivalent.

1. Record the run timestamp, affected conversation, label or exact error, supporting activity, and displayed credits. You can retain the results using **Export test results** from the results menu.

You can complete this results-inspection exercise even if a case fails or times out. Record what you could and could not verify, and ask the instructor to review unresolved issues before the publishing step.

### How Evaluate differs from Preview

| Preview | Evaluate |
| --- | --- |
| Interactive exploration: you choose the next prompt, supply an attachment, or clarify a question | Runs the saved CSV turns against the configured agent and evaluation account, then applies the saved rubric |
| Useful for isolating a retrieval or conversation issue | Useful for checking the same scenarios after a change and comparing recorded outcomes |
| You manually judge the answers and available activity | Classification provides an AI-generated label and explanation, which still need human review |
| Shows estimated credits for the current session | Shows estimated credits for the run and individual cases, including response generation and grading |

**Use Preview to debug and Evaluate to check repeatability.** A successful Preview conversation with an uploaded invoice does not establish that an evaluation can retrieve that invoice independently. Neither experience replaces source verification or authorization controls.

## Publish

1. Confirm that any genuine agent defects have been corrected and any suspected grader disagreements have been reviewed with your instructor. Do not proceed with unresolved findings.

1. Select the **Publish** button in the upper right hand corner and wait for completion.

    ![Publish the agent](./assets/05.20-publish.png)

1. In the dialog, select the **Publish agent** button. Select the **Done** button after publishing is complete.

    ![Publish the agent](./assets/05.21-publish.png)

Select **Next** to build the workflow.
