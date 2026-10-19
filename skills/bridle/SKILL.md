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

For a first-time response, keep the guide concise: (a) install Bridle by following [bridle.io/setup](https://bridle.io/setup); (b) enable the assistant's browser access to the same Chrome profile; (c) open the site to review and ask the assistant to capture one precise Bug, Change, Comment, Feature, Task or Spike; (d) save the requested feedback and report its ID before asking about implementation. Mention that the user completes any sign-up themselves and that a code repository is needed only if they want implementation. Ask them to visit the setup page and finish the steps before attempting browser work.

Always include at least two short, copy-ready example prompts in that first-time guide. Use these three by default so the user can see the capture-only, review-only and implementation paths:

- “Open [website] in Chrome and use Bridle to capture a Bug on [element]: [what happened]. Save it and tell me the REQ ID.”
- “Review my latest Bridle feedback for [website]. Summarize the items and suggest next steps; don't change code yet.”
- “Capture [issue] with Bridle, save it and report the REQ ID, then investigate and fix it in this repository. Verify the result on [local or test URL].”

Keep placeholders obvious, and explain that implementation requires the website repository and a local or test site. Do not send setup instructions as feedback or append them to a Bridle record. If the user already used Bridle's **Copy AI prompt**, skip onboarding and continue from the saved feedback and REQ ID.

## Capture, then fix: keep one record per request

When the user asks you to capture website feedback **and** fix it, capture it in Bridle first, report its REQ ID, then implement with that REQ as the reference. The record is what the user reviews afterwards (green marker, completion link), so it should exist before the code changes.

1. A copied Bridle prompt or a connector item is already saved feedback. Reuse its REQ ID; never capture it again.
2. Capture each distinct issue the user asks you to record. Verify its target, text, type and REQ ID before changing code.
3. You do not need Bridle's **Copy prompt** for feedback you just captured in this session: you already know the target and the request. Use the saved record (or the connector folder, when it is on) only if you need the captured details.
4. Other problems you notice on the way are not the user's request. List them in your reply; capture or fix one only when the user asks.
5. If capture is blocked (no browser access, no bar, a quota or sign-in gate), say exactly what blocked it and ask whether to fix the issue without a Bridle record. Do not decide that for the user, and do not report a capture that did not happen.
6. A plain request to fix code that does not mention Bridle or feedback is an ordinary coding task: having this skill installed does not bring it into Bridle.

For reading, review, editing, exports, diagnostics, tickets and completion, use the relevant supported Bridle feature. Repository tools remain necessary for implementation and checks. Do not invent Bridle features or call internal extension messages as a substitute for its visible UI.

## Core operating loop

1. **Understand the request**, and apply [capture, then fix](#capture-then-fix-keep-one-record-per-request) when it includes implementation. Identify the site/page, target element, operation (add, edit, replay, diagnostics, Bridle ticket, Jira ticket), and desired outcome. Keep “add a new feedback” distinct from “edit the saved feedback.” A spoken phrase such as “Hey Codex” is a host voice-mode wake phrase, not a Bridle command protocol; recognize the user's task from its intent.
2. **Verify the browser.** Inspect fresh browser state. Confirm the active tab is the user-requested page, Bridle is available in that same browser profile, and the URL is correct. Do not rely on an old screenshot, stale tab, or remembered coordinates.
3. **Use the mandatory assistant entry sequence.** Read [references/visual-feedback.md](references/visual-feedback.md) before capture. First reveal the bar with **Command+Shift+9** on macOS or **Ctrl+Shift+9** elsewhere. For every new feedback, hold **Command+Shift** (Mac) or **Ctrl+Shift** (others) while clicking **Pick any element to add feedback**, release modifiers, then select the target. Choose the type with the note's type label (**CHANGE ▾** opens a row of the six types inside the page), type and append in the same note, and save at once with the note's **Save** button or Command/Ctrl+Enter; the user's request is the permission to save, so never leave a typed draft waiting for consent. Change, Bug and Comment note text is red; other types use their own text colours. Use the normal picker (unmodified click, full Add Feedback form) only when the user asks for it or the target needs the preview and **Parent** (rule 2), and say so. If the bar or gesture is unavailable, recover using the reference and report the actual blocker. For saved items, open the Bridle feedback workspace and identify the exact item before choosing its item-level action.
4. **Check, then save the requested feedback.** Inspect the selected element preview and the feedback text/type yourself. When they match the user's request, save immediately with **Add**, **Save feedback** or **Update**; do not read a draft back for approval or ask whether to save. The user's request to capture, add, report or update feedback authorizes that Bridle write. Ask first only if the target, type or intended outcome is materially ambiguous, or if Bridle presents a real account/quota gate. Translate intent into a concrete instruction using only what the user said and what is visible. Do not invent a defect, expected behavior, severity or acceptance criteria.
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
2. **Check the target before you save.** Assistant capture shows no preview: check the picker's highlight on a screenshot before you click, and pick near the middle of visible text. For an icon, a logo or anything whose highlight you cannot judge, use the normal picker (unmodified click) so you can read the preview and use **Parent**, and tell the user why. In the normal form, read the Add feedback dialog's ELEMENT PREVIEW. Treat these as a wrong pick: the preview is empty or blank; its text is not visible on the page (a screen-reader label such as “Homepage” on a logo); its text does not match what the user named; the tag line shows a hidden or screen-reader-only element (`.visually-hidden`, `.sr-only`, a tiny `span`). Cancel and pick again, or use **Parent**. Never save against a target you doubt; if two attempts fail, say what was selected and ask.
3. **Gates are the user's step.** If Bridle shows **Sign up to continue**, **Subscribe to continue** or **Share limit reached**, stop. Do not press the account, plan or payment button, and do not sign in. Tell the user the gate, keep their request so it can be repeated, and continue only after they say it is handled. **Maybe later** or × only closes the dialog; the feedback was not saved. Anonymous installs can save only a few feedbacks a day, so a batch may stop part-way: report which items were saved.
4. **Keep the user's words and save without a second approval.** If the user says “just say X”, save exactly X. Otherwise turn clear shorthand into a concise request from what was said and what is on screen (“call this Profile” on the label “For you” → “Change ‘For you’ to ‘Profile’”). Do not read back the draft or ask whether to save; save it and report what Bridle confirmed. Ask a brief question only when the target or requested outcome is materially ambiguous. Never invent replacement text, cause, severity or acceptance criteria.
5. **Choose the type on purpose.** The dialog defaults to **Change**. Pick **Bug**, **Comment**, **Feature**, **Task** or **Spike** when the words say so, and report which type you used. Use Comment for questions, observations and general feedback; do not infer a code-change request from a Comment alone. Change, Bug and Comment note text is red; other note colors follow their type. Completed notes are green.
6. **Names from dictation.** Dictation mishears names. “Biddle”, “Brittle” and “Bridal” mean Bridle. When a dictated name or phrase is meant to match text on the page and does not (for example a misspelt person's name in a headline), use the page's text and say so.
7. **Read the receipt.** After Cmd/Ctrl+Enter in assistant capture, a dark toast at the bottom of the page reads **Saved REQ-… · Type: text** for a few seconds, and the draft becomes a saved note and marker; take the screenshot right after saving. If you missed it, find the feedback in the Feedbacks list before retrying. In normal mode, after **Add**, the “What's next?” panel shows **Feedback saved** with the feedback ID (REQ-…) and its text. Report the ID, type and text. Never guess an ID or risk a duplicate save.
8. **IDs are per install, across all sites.** “The latest feedback” means the newest on the page or site the user means, not the highest number overall.
9. **Reveal the bar first.** Always send the platform reveal shortcut before looking for the bar. If absent, follow the recovery sequence in the visual reference, including checking shortcut assignment, profile/site access and restricted pages. Do not report only “bar not found” or silently fall back to normal capture.
10. **Destructive actions need the user's own words.** Delete, remove, reset and turn-off actions only when the user named that action for those items. Deleting a feedback is permanent (there is no recently-deleted list), so stop at the delete confirmation and let the user press it; hiding a marker is reversible and you may do it on request.
11. **Use screenshots for Bridle's controls.** Bridle's UI is not in the page tree that some browser tools read (Claude in Chrome's `read_page` / `find` do not list it). Look at a fresh screenshot and click by coordinates; take a new one after each step.
12. **Screenshots need the tab in front.** Chrome lets Bridle capture only the visible tab of a window. If the tab you work in is behind another tab, the receipt reads **Feedback saved · screenshot pending**: Bridle takes the screenshot when that tab is shown with the element on screen. Tell the user when this happens. A PDF exported meanwhile says “Screenshot unavailable”.
13. **Check a fix on a fresh page.** After changing a site's files, reload without the cache before judging the result; a normal reload can show the old page.
14. **Leave Bridle's own questions to the user.** “How did that go?” and “Debugging something tricky?” ask about the user's experience or store a preference; do not answer them. If one covers what you need, say so.
15. **Close what you opened.** Close the tabs you created when finished, unless the user wants them.
16. **Several matches: count them, ask once.** When the user names something plural (“the install buttons”, “these links”), or more than one element on the page fits the description, find all of them first. Say how many there are and where (“three install buttons: in the hero, in the install card, at the bottom”), then ask one question: one feedback on each (separate REQ IDs), or one feedback covering all of them (multi-element, see [visual feedback](references/visual-feedback.md#one-feedback-on-several-elements)). If the user already said which, do it without asking. Never pick one of several silently.
17. **There is no page-level feedback.** Every Bridle feedback is attached to an element. For “feedback on the whole page” or “not on any particular element”, attach it to the page's main heading (the `<main>` region when there is no clear heading), begin the text with “Across this page:”, and tell the user which element it is attached to. Do not call it page-level.
18. **Report once.** After saving, give each feedback one line: REQ ID, type, its element in a few words, and the text Bridle confirmed. Do not repeat the same result as a separate “complete” summary.

## Preferred voice interaction

Interpret requests such as “Ask Bridle to open this page, find the hero heading, and add a change request to rename it…” as: navigate/verify the requested site; use Bridle's element picker; verify the exact heading; write the requested change as an explicit command; save it immediately and report the receipt. Do not pause for approval after drafting. Ask one concise question only when page, target, operation, destination, or requested outcome is materially ambiguous (several matching elements is the usual case: rule 16).

Spoken requests contain fillers, restarts and corrections (“uh”, “no, actually don't do that”, “I want, I want to add…”). Act on the last thing the user settled on, and keep their wording for the feedback text only where they said “say exactly…”.

The Bridle UI and its internal extension message names can change. Use the visible labels and current state first; consult implementation-specific notes in the references only as guidance. Do not call undocumented internal extension messages as if they were a supported third-party API.
