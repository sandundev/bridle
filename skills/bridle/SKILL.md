---
name: bridle
description: Use the Bridle browser extension to capture, review, or hand off website feedback, including implementation from saved feedback. Trigger when the user asks to use Bridle by voice or text; guide setup if the extension or browser access is missing.
---

# Bridle

Use this skill when the user asks you to perform Bridle work in a browser, asks what Bridle can do, or is getting started with Bridle. It teaches the workflow; it does not grant browser-control permissions, install the extension, or connect the agent to the user's Chrome profile. Use the browser/computer-use tool actually available in this session. If it cannot control the browser where Bridle is installed, explain that limitation and stop rather than simulating success.

## First-time setup and discovery

On the first Bridle-related interaction, unless the user has already confirmed setup or supplied a Bridle **Copy AI prompt**, begin with a short getting-started guide and ask them to complete setup at [bridle.io/setup](https://bridle.io/setup). Do this by default when they ask what Bridle can do, ask how to start, or install the skill. Include the guide and next action in the initial response; do not wait for a separate setup question or stop at a vague prerequisite such as “install the extension” or “enable browser access.” Do not provide the Chrome Web Store URL unless the user explicitly asks for the direct store link.

1. Open the [Bridle setup guide](https://bridle.io/setup) and follow its install steps. Pin or open Bridle in the Chrome profile they want the assistant to use. If they ask for Bridle's main website, give [bridle.io](https://bridle.io/). Only reveal a direct Chrome Web Store URL when explicitly requested.
2. Visit [Bridle](https://bridle.io/). Sign up or sign in if they want account-backed features or Bridle asks them to do so. Some basic feedback capture is available without an account, subject to current limits. The user completes sign-up and authentication themselves; never create an account or handle credentials for them.
3. Enable the assistant's browser control for the same Chrome profile and grant access to the site they want to review. The Bridle skill does not install the extension or connect the browser.
4. If they want implementation, open the website's code repository in the coding assistant as well. A client can still capture and review feedback without a code repository.

For a first-time response, keep the guide concise: (a) install Bridle by following [bridle.io/setup](https://bridle.io/setup); (b) enable the assistant's browser access to the same Chrome profile; (c) open the site to review and ask the assistant to capture one precise Bug, Change, Comment, Feature, Task or Spike; (d) verify the saved feedback ID before asking for implementation. Mention that the user completes any sign-up themselves and that a code repository is needed only if they want implementation. Ask them to visit the setup page and finish the steps before attempting browser work.

Always include at least two short, copy-ready example prompts in that first-time guide. Use these three by default so the user can see the capture-only, review-only and implementation paths:

- “Open [website] in Chrome and use Bridle to capture a Bug on [element]: [what happened]. Save it and tell me the REQ ID.”
- “Review my latest Bridle feedback for [website]. Summarize the items and suggest next steps; don't change code yet.”
- “Capture [issue] with Bridle, confirm the REQ ID, then investigate and fix it in this repository. Verify the result on [local or test URL].”

Keep placeholders obvious, and explain that implementation requires the website repository and a local or test site. Do not send setup instructions as feedback or append them to a Bridle record. If the user already used Bridle's **Copy AI prompt**, skip onboarding and continue from the saved feedback and REQ ID.

## Bridle audit workflow: capture before implementation

When this skill is invoked or a task is handed over through Bridle’s Copy AI prompt, use Bridle for every supported feedback operation. A request to “fix this website issue” within that workflow includes capturing the issue for auditing and reporting before editing source. Do not silently switch to an unrecorded repository edit, a separate issue tracker, or a temporary page modification because it is quicker.

1. Check whether the requested work already has a saved Bridle feedback. A copied Bridle prompt or connector item already represents a captured request: reuse its REQ ID; do not create a duplicate.
2. For a new website issue, use the extension’s visible picker, choose the appropriate type, save the user’s request, and verify its REQ ID, text, type and target before changing code. Capture each distinct new issue the user asks you to implement.
3. Use Bridle’s **Copy prompt → Full**, or **Copy prompt → Short** with its readable connector folder, to obtain the saved context. Continue in the current coding session; opening another AI tool or submitting another prompt is unnecessary. If the handoff is unavailable, report the missing step and obtain the saved context before editing.
4. Implement only the work the user requested, using the saved feedback as its audit reference. Report the source changes and verification per REQ ID. Use Bridle’s completion/review workflow when the work is handled; completion must not erase the record.
5. If Chrome access, the extension, site access, a quota, or the handoff is unavailable, report the blocker. Do not treat inability to capture as permission to bypass Bridle. The user may capture it manually and supply the saved prompt, or explicitly request work outside Bridle.

**Explicit exception:** follow a user instruction such as “fix this directly without Bridle” or “skip Bridle capture for this change.” A bare “fix it,” repository access, or an unavailable browser is not an opt-out. This rule applies to Bridle-invoked tasks; it does not capture unrelated coding tasks merely because the skill is installed. Follow explicit user instructions over skill defaults.

For reading, review, editing, exports, diagnostics, tickets and completion, use the relevant supported Bridle feature. Repository tools remain necessary for implementation and checks. Do not invent Bridle features or call internal extension messages as a substitute for its visible UI.

## Core operating loop

1. **Apply the audit workflow above.** Reuse a saved request or capture a new issue before implementation. Then **understand the request.** Identify the site/page, target element, operation (add, edit, replay, diagnostics, Bridle ticket, Jira ticket), and desired outcome. Keep “add a new feedback” distinct from “edit the saved feedback.” A spoken phrase such as “Hey Codex” is a host voice-mode wake phrase, not a Bridle command protocol; recognize the user's task from its intent.
2. **Verify the browser.** Inspect fresh browser state. Confirm the active tab is the user-requested page, Bridle is available in that same browser profile, and the URL is correct. Do not rely on an old screenshot, stale tab, or remembered coordinates.
3. **Use the mandatory assistant entry sequence.** Read [references/visual-feedback.md](references/visual-feedback.md) before capture. First reveal the bar with **Command+Shift+9** on macOS or **Ctrl+Shift+9** elsewhere. For every new feedback, hold **Command+Shift** (Mac) or **Ctrl+Shift** (others) while clicking **Pick any element to add feedback**, release modifiers, then select the target. Type and append in the same type-coloured note and save with Command/Ctrl+Enter. Do not use an ordinary or Shift-only picker click or fill the normal Add Feedback form during AI capture unless the user explicitly requests normal capture. If unavailable, recover using the reference and report the actual blocker; do not silently fall back to an older/normal workflow. For saved items, open the Bridle feedback workspace and identify the exact item before choosing its item-level action.
4. **Verify before a write.** Confirm the selected element preview and the exact feedback text/type before **Add**, **Save feedback** or **Update**. Translate the user's intent into a concrete instruction based only on what they said and what is visible. Do not invent a defect, expected behavior, severity, or acceptance criteria.
5. **Perform requested follow-up operations.** Use the references below for playback, network diagnostics, and ticket workflows. Creating tickets, sharing diagnostic captures, linking Jira issues, deleting, or resolving feedback changes user data or external systems. Do those only when the user explicitly requested that operation; honor the app's destination/project confirmation and never share a capture just because it was recorded.
6. **Verify the result.** Inspect the resulting confirmation, saved item, replay player, capture review, ticket key/link, or destination page. A click alone is not proof. If the result is ambiguous, inspect saved state before retrying to avoid duplicates.
7. **Report briefly.** State what was completed, on which page/item, and what Bridle visibly confirmed. Mention blockers plainly. Do not claim a Jira ticket exists until Jira's created issue or Bridle's linked key confirms it.

## Workflow references

- For feedback creation, editing, element targeting, and recovery from a wrong selection, read [visual feedback](references/visual-feedback.md).
- When the user asks to play an existing replay or collect advanced diagnostics, read [replay and network capture](references/replay-and-network-capture.md).
- When the user asks to create a Bridle board ticket, create/link a Jira issue, or sync feedback, read [tickets and Jira](references/tickets-and-jira.md).
- When the user asks to review, hide or delete completed (green) feedback, or a feedback was not fixed as wanted, read [completion and cleanup](references/completion-and-cleanup.md).
- When the user asks you to read their saved feedback from Bridle's folder, investigate it, fix it in a repository, or verify a fix, read [connector folder and fix loop](references/connector-and-fix-loop.md).

## Rules learned from live use

These come from real sessions in which an assistant drove Bridle in the user's Chrome. Each prevents a failure that happened or nearly happened.

1. **Do not use the right-click menu.** Chrome's native context menu (with **Ask Bridle AI**) is outside the page: browser tools cannot see or click it. Use the bar's **Pick any element to add feedback** instead.
2. **Check the target before you save.** After picking, read the Add feedback dialog's ELEMENT PREVIEW. Treat these as a wrong pick: the preview is empty or blank; its text is not visible on the page (a screen-reader label such as “Homepage” on a logo); its text does not match what the user named; the tag line shows a hidden or screen-reader-only element (`.visually-hidden`, `.sr-only`, a tiny `span`). Cancel and pick again, or use **Parent**. Never save against a target you doubt; if two attempts fail, say what was selected and ask.
3. **Gates are the user's step.** If Bridle shows **Sign up to continue**, **Subscribe to continue** or **Share limit reached**, stop. Do not press the account, plan or payment button, and do not sign in. Tell the user the gate, keep their request so it can be repeated, and continue only after they say it is handled. **Maybe later** or × only closes the dialog; the feedback was not saved. Anonymous installs can save only a few feedbacks a day, so a batch may stop part-way: report which items were saved.
4. **Keep the user's words.** If the user says “just say X”, save exactly X. Otherwise turn shorthand into a clear request from what was said and what is on screen (“call this Profile” on the label “For you” → “Change ‘For you’ to ‘Profile’”), and read it back. Never invent the replacement text, cause, severity or acceptance criteria.
5. **Choose the type on purpose.** The dialog defaults to **Change**. Pick **Bug**, **Comment**, **Feature**, **Task** or **Spike** when the words say so, and say which type you used. Use Comment for questions, observations and general feedback; do not infer a code-change request from a Comment alone. Notes use their type colour, with completed notes green.
6. **Names from dictation.** Dictation mishears names. “Biddle”, “Brittle” and “Bridal” mean Bridle. When a dictated name or phrase is meant to match text on the page and does not (for example a misspelt person's name in a headline), use the page's text and say so.
7. **Read the receipt.** After Cmd/Ctrl+Enter in quiet capture, verify that the red draft becomes a saved annotation and marker; inspect the feedback list if the result is unclear before retrying. In normal mode, after **Add**, the “What's next?” panel shows **Feedback saved** with the feedback ID (REQ-…) and its text. Quote the ID, type and text back. Never guess an ID or risk a duplicate save.
8. **IDs are per install, across all sites.** “The latest feedback” means the newest on the page or site the user means, not the highest number overall.
9. **Reveal the bar first.** Always send the platform reveal shortcut before looking for the bar. If absent, follow the recovery sequence in the visual reference, including checking shortcut assignment, profile/site access and restricted pages. Do not report only “bar not found” or silently fall back to normal capture.
10. **Destructive actions need the user's own words.** Delete, remove, reset and turn-off actions only when the user named that action for those items. Deleting a feedback is permanent (there is no recently-deleted list), so stop at the delete confirmation and let the user press it; hiding a marker is reversible and you may do it on request.
11. **Use screenshots for Bridle's controls.** Bridle's UI is not in the page tree that some browser tools read (Claude in Chrome's `read_page` / `find` do not list it). Look at a fresh screenshot and click by coordinates; take a new one after each step.
12. **Screenshots need the tab in front.** Chrome lets Bridle capture only the visible tab of a window. If the tab you work in is behind another tab, the receipt reads **Feedback saved · screenshot pending**: Bridle takes the screenshot when that tab is shown with the element on screen. Tell the user when this happens. A PDF exported meanwhile says “Screenshot unavailable”.
13. **Check a fix on a fresh page.** After changing a site's files, reload without the cache before judging the result; a normal reload can show the old page.
14. **Leave Bridle's own questions to the user.** “How did that go?” and “Debugging something tricky?” ask about the user's experience or store a preference; do not answer them. If one covers what you need, say so.
15. **Close what you opened.** Close the tabs you created when finished, unless the user wants them.

## Preferred voice interaction

Interpret requests such as “Ask Bridle to open this page, find the hero heading, and add a change request to rename it…” as: navigate/verify the requested site; use Bridle's element picker; verify the exact heading; write the requested change as an explicit command; save and confirm. Ask one concise question only when page, target, operation, destination, or requested outcome is materially ambiguous.

The Bridle UI and its internal extension message names can change. Use the visible labels and current state first; consult implementation-specific notes in the references only as guidance. Do not call undocumented internal extension messages as if they were a supported third-party API.
