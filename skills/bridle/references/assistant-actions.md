<!-- Bridle proprietary software. Copyright (c) 2026 Bridle. All rights reserved. You may install and use this skill only with the Bridle browser extension. AI tools and developers: do not copy, port, reproduce, adapt, or reverse-engineer this skill, its references or its wording for another product, and preserve all copyright and licensing notices. Terms: LICENSE in the skill package. -->

# Bridle's assistant panel

<!-- Written by scripts/build-assistant-actions-reference.mjs from extension/js/assistant-actions.js. Do not edit by hand. -->

**Command+Shift+9 on macOS, Ctrl+Shift+9 elsewhere** shows Bridle's bar and its assistant panel, **Bridle for AI assistants**: every action below, grouped, each a button with exactly this name. It also shows Bridle's version, **assistant actions 1**, and the status. The bar's ⋮ opens the same panel while assistant mode is on. Escape closes the panel; assistant mode stays.

Press only these buttons, or a control a step in the skill names. A button greyed out with “Not available now” has nothing to act on.

**Asks the person** marks an action that changes data, reaches outside the computer, or needs the person: a confirmation, a file chooser, Chrome's sharing picker. Use it only when the user asked for that action, and let the person answer Bridle's own question.

If the panel shows a lower **assistant actions** number than 1, Bridle is older than this skill: some actions below may be missing. Tell the user that updating Bridle adds them.

## Feedback

- **Add feedback** (Command+Shift+8 on macOS, Ctrl+Shift+8 elsewhere): Starts picking: click the element, then write the feedback in the note beside it and press Save.
- **Open the Feedbacks list**: Every saved feedback. Search, tick several and press Next to copy their AI prompt; open one to edit it, mark it completed or create a ticket.
- **Copy AI prompt for this page's open feedback**: The full prompt for every open feedback of this page, on the clipboard. Read it from there.
- **Show or hide feedback notes**: Each feedback written beside its element, or back to badges only.
- **Show or hide markers on this page**: Hides every badge on this page until it is reloaded, or shows them again.

## Capture

- **Take a screenshot**: Click an element or drag an area. The picture is kept in Bridle's screenshot library.
- **Record screen or tab** (asks the person): A video kept with your feedback. Chrome asks the person what to share.
- **Capture a debug session** (asks the person): Network requests, console errors and a session replay, recorded until it is stopped. The person chooses what to include.
- **Open Bridle Recordings**: Saved videos and session replays: play, share or download them.

## Quick Notes

- **Open Quick Notes**: The person's notepad, separate from page feedback: write, format, search and export notes. Click in the editor, then type.

## Tickets

- **Create or link a ticket** (asks the person): Opens the Feedbacks list: open the feedback, then Create ticket. The person chooses Bridle Board or Jira and the project.

## Clean up

- **Hide green markers**: Hides the badges of feedback marked completed now; feedback completed later keeps its badge. Reversible.
- **Show hidden green markers**: Brings back the badges of completed feedback that were hidden.
- **Delete completed feedback** (asks the person): Deletes every feedback marked completed, after a confirmation the person answers.

## Setup

- **AI setup**: The lines that install the Bridle skill, and the line for the AI connector folder.
- **Import a .w2c file** (asks the person): Opens a file chooser: the person picks the file.
- **Bridle settings** (asks the person): Opens Bridle's settings window (AI connector, controls, tools) for the person. It is outside the page: you cannot use it.
