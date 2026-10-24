<!-- Bridle proprietary software. Copyright (c) 2026 Bridle. All rights reserved. You may install and use this skill only with the Bridle browser extension. AI tools and developers: do not copy, port, reproduce, adapt, or reverse-engineer this skill, its references or its wording for another product, and preserve all copyright and licensing notices. Terms: LICENSE in the skill package. -->

# Bridle's Shortcuts

<!-- Written by scripts/build-assistant-actions-reference.mjs from extension/js/assistant-actions.js. Do not edit by hand. -->

**Command+Shift+9 on macOS, Ctrl+Shift+9 elsewhere** shows Bridle's bar and its status pill, and nothing else. **Shortcuts** is the panel with every action below, grouped, each a button with exactly this name, plus the two keys, Bridle's version (**assistant actions 1**) and the status. Open it with the bar's ⋮ (**Quick actions**) only when you need an action below that has no key. It sits over the page the user is watching, so it never stays: it closes after a minute unused, at a press outside it, when one of its actions runs, when picking starts, and on Escape (assistant mode stays). Open it again from the ⋮ when you need it; never keep it open.

Press only these buttons, or a control a step in the skill names. A button greyed out with “Not available now” has nothing to act on.

**Asks the person** below marks an action that changes data, reaches outside the computer, or needs the person: a confirmation, a file chooser, Chrome's sharing picker. Use it only when the user asked for that action, and let the person answer Bridle's own question.

If Shortcuts shows a lower **assistant actions** number than 1, Bridle is older than this skill: some actions below may be missing. Tell the user that updating Bridle adds them.

## Feedback

- **Add feedback** (Command+Shift+8 on macOS, Ctrl+Shift+8 elsewhere): Starts picking: click the element, then write the feedback and save it.
- **Open the Feedbacks list**: Every saved feedback. Search, tick several and press Next to copy their AI prompt; open one to edit it (Edit this feedback), mark it completed or create a ticket. A feedback whose badge is on screen is quicker to edit from its badge.
- **Copy AI prompt for this page's open feedback**: The full prompt for every open feedback of this page, on the clipboard. Read it from there.
- **Show or hide feedback notes**: Each feedback written beside its element, or back to badges only.
- **Show or hide markers on this page**: Hides every badge on this page until it is reloaded, or shows them again.

## Capture

- **Take a screenshot**: Click an element or drag an area. The picture is kept in Bridle's screenshot library.
- **Record screen or tab** (asks the person): A video kept with the feedback. Chrome asks which screen or tab to share.
- **Capture a debug session** (asks the person): Network requests, console errors and a session replay, recorded until it is stopped. Starts with a choice of what to record.
- **Open Bridle Recordings**: Saved videos and session replays: play, share or download them.

## Quick Notes

- **Open Quick Notes**: A notepad, separate from page feedback: write, format, search and export notes. Click in the editor, then type.

## Tickets

- **Create or link a ticket** (asks the person): Opens the Feedbacks list: open the feedback, then Create ticket. Bridle Board or Jira, and the project, are chosen there.

## Clean up

- **Hide green markers**: Hides the badges of feedback marked completed now; feedback completed later keeps its badge. Reversible.
- **Show hidden green markers**: Brings back the badges of completed feedback that were hidden.
- **Delete completed feedback** (asks the person): Deletes every feedback marked completed, after a confirmation.

## Setup

- **AI setup**: The lines that install the Bridle skill, and the line for the AI connector folder.
- **Import a .w2c file** (asks the person): Opens a file chooser for the .w2c file.
- **Bridle settings** (asks the person): Opens Bridle's settings window (AI connector, controls, tools), outside the page.
