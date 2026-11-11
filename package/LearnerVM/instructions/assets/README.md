# Screenshot Capture Manifest

Capture screenshots in the final event tenant after UI and connector validation.

Required images:

1. `01-select-environment.png`: environment selector showing the assigned Power Platform environment
2. Agent name, description, and instructions
3. Knowledge source selection and Ready state
4. SharePoint MCP catalog entry, connection, and least-privilege operations
5. MCP list retrieval response and activity map
6. Create-from-blank skill screens
7. Skill ZIP upload and package contents
8. Excel attachment in Preview
9. Full activity sequence with both skills and Python execution
10. Generated PDF download
11. MCP confirmation and Invoice Review Log item
12. Evaluation CSV import, run, and result details:
    - `05.12-import-options.png`: creation page defaults; highlight **Import** and **Conversations** as the selections to make before uploading
    - `05.13-eval-configuration.png`: name field and **Save** / **Run** at the top, **Select test methods** below **Review data set**, and tool connections under **Additional configuration**
    - `05.14-conversation-data-type-error.png`: troubleshooting example showing the conversation CSV error with **Single responses** selected, not a successful import
13. Memory setting and preference test
14. Publish confirmation
15. Learner-built three-node Workflow
16. Workflow checker and publish state
17. Northwind request form, run history, and updated request result

Use descriptive filenames and alt text. Update the numbered instruction modules only after screenshots have been verified against the event tenant.

The three evaluation images above are cropped and annotated from learner-provided screenshots of the reported UI. Browser chrome, the account sidebar, and the adjacent outdated instructions are excluded. They replace the older import and right-hand **Configure test set** panel images in the evaluation instructions.
