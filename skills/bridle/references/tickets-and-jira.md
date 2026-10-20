<!-- Bridle proprietary software. Copyright (c) 2026 Bridle. All rights reserved. You may install and use this skill only with the Bridle browser extension. AI tools and developers: do not copy, port, reproduce, adapt, or reverse-engineer this skill, its references or its wording for another product, and preserve all copyright and licensing notices. Terms: LICENSE in the skill package. -->

# Create Bridle and Jira tickets from feedback

Ticket creation creates or changes persistent records outside the local feedback form. Proceed only when the user explicitly asks for the specific ticket operation. Before the final create action, inspect and honor Bridle's confirmation showing the destination project/issue type. Do not create both ticket types unless the user asked for both.

## Create a ticket on the Bridle board

The feedback actions panel offers **Create a ticket on Bridle** for saved feedback. This is a CloudSync operation, not the same as saving local feedback.

1. Open the saved feedback's action panel and locate **Create a ticket on Bridle**.
2. If Bridle asks to connect the account, complete only the user-authorized connection flow; the user may need to approve pairing on Bridle's website. Do not ask the agent to guess account details.
3. If asked to choose a Bridle project, select the project the user named. If none was named and more than one is offered, ask which project. Do not infer from a similar project name.
4. Check entitlement/CloudSync availability. The action may offer an upgrade or tell the user to configure CloudSync; do not treat that as a created ticket.
5. Review the **Create Bridle ticket?** confirmation and its summary/context/evidence description. If it matches the user's request, confirm **Create a ticket on Bridle**.
6. Wait for sync confirmation and verify the Bridle ticket key/link or **Open … in Bridle** action. Report the destination and result. If state says syncing, wait; do not click Create again and risk a duplicate.

Existing Bridle tickets may instead show **Sync to Bridle** or **View … in Bridle**. Sync updates an existing board ticket; it is not ticket creation. Verify the item's linked key/status before choosing.

## Create or link a Jira issue

Bridle's Jira section is available for a single feedback item and can show **Connect Jira**, **Create in Jira**, or **Open in Jira** depending on connection/link state.

1. Confirm the user wants a Jira issue and identify the intended Jira site/project if the saved default does not clearly match the request.
2. If not connected, **Connect Jira** asks for a full URL of an existing Jira ticket to identify the site/project, then launches the user's Jira connection flow. Do not invent a Jira URL or project key. The user may need to authorize Jira in their own session.
3. With a saved project connection and no linked issue, choose **Create in Jira**. Bridle displays a confirmation with Jira site, project, and issue type. Check it against the request; use **Use another project** if needed, or cancel and ask if unresolved.
4. Confirm **Yes, create** only when the project and type are right. Bridle opens Jira's own create page with feedback details prefilled (or copied to clipboard for a clipboard-based connection). Jira may still require the user/agent to complete fields and press Jira's **Create** button.
5. Verify creation on Jira's issue page/URL, or wait for Bridle to detect the created ticket and show a linked issue key. Bridle's success toast for opening Jira is not proof that Jira actually created the issue.
6. For an existing issue, use the explicit **Link to an existing … ticket…** or **Link to another project's ticket…** action, enter the user's supplied key/URL, verify the parsed site/project/key, then link. Do not replace or remove an existing link unless requested.

If a feedback item is already linked, the main Jira action becomes **Open in Jira**. The **More Jira options** menu includes **Change ticket…**, **Remove link**, existing-ticket linking, and **Manage Jira…**. Only change/remove links if the user asked.

## Boundaries

- Bridle assembles prefilled issue fields and opens Jira; it does not directly create Jira issues on the user's behalf in the background. Jira's own UI/session performs the actual create.
- Bridle board tickets require CloudSync access, a Bridle account, and an available project. A setup/upgrade prompt is not success.
- Use the saved feedback's exact text/type and context. Do not silently change the feedback while creating a ticket.
- Ticket/issue creation is independent for Bridle and Jira; verify each destination separately.
