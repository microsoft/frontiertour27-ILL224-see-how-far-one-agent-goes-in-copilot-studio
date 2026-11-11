# Evaluation Release Gate

`Supplier-Assurance-Baseline.csv` uses the Copilot Studio conversation import template. Conversation 1 tests a contextual Astor Ridge review and its grounding and action guardrails. Conversation 2 verifies the policy boundary for a disputed amount of exactly $10,000.

Under **Create or select a data set**, select **Import**, then select **Conversations** under **Select data type** before using **browse** to upload the CSV. The defaults, **Generate** and **Single responses**, are not suitable for this file. If an error says the file is set up for conversations, select **Conversations** and upload the same file again if needed; do not convert it to the single response template.

Enter `Supplier Assurance baseline` in the evaluation name field at the top of the main page. Under **Review data set**, confirm that two conversations were imported. Keep **General quality** under **Select test methods**, below **Review data set**. Check **Connections** under **Additional configuration** and connect tools using the learner's SharePoint connection if prompted. Select **Save**, then **Run**, at the top of the page; saving alone does not start the evaluation.

The imported `response` values are reference replies for reviewers; Copilot Studio does not compare agent output directly with them. The import adds the General quality test method by default. Select any additional test methods in Copilot Studio after import.
