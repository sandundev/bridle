# Replay and advanced network capture

## Play a saved feedback replay

1. Open Bridle's feedback workspace and find the requested saved item.
2. Inspect the item's replay action. If enabled, its accessible name is **View session replay**; select that item-specific button, not a general recording action.
3. Bridle opens the replay overlay and autoplays it. Use the player's controls to inspect the requested interval. Close with **Close session replay** when done. If the embedded player cannot load, use its **Open full page** fallback if available.
4. If the replay button is disabled and says **No session replay — start recording before capturing feedback**, report that this feedback has no replay. Do not silently start a new recording or imply a replay exists.

Replay review is a read action. Exporting replay video is a separate action and may present an export/permission confirmation; only export when the user asks.

## Start a network diagnostic capture

Bridle's bottom bar has a **Capture network requests** button. When there are no saved captures it opens the **Capture network activity** setup; when captures exist it can open the recordings/review library. If already recording, the same button reports the active capture rather than silently starting another.

Before starting, check what is being recorded with the user. The setup says captured data stays local until the user shares it. Default evidence options include **Network activity**, **Console logs**, **User actions**, **Session replay**, and **Screenshots**. Advanced options include:

- **Include header values**: off by default; header names are captured with values redacted. Only enable actual header values when the user specifically needs them and understands the sensitivity.
- **Include HTML, CSS and JavaScript bodies**: off by default; includes static asset file bodies.
- **Exclude URLs or domains**: enabled by default; review or add sensitive domains/routes where appropriate.

Network requests/responses may contain private content or identifiers even when values are redacted. Do not enable sensitive options or share/export/send the capture without the user's clear authorization. Keep the capture limited to the requested site and reproduction window.

### Capture lifecycle

1. Open **Capture network requests** and review the evidence choices and exclusions.
2. Start only after the user has clearly requested the capture and the capture scope is understood. Confirm the UI reports **Network capture started** and shows the NET indicator.
3. Reproduce only the user-described behavior. Keep the browser on the relevant page; don't browse unrelated accounts or records while capturing.
4. Stop with the in-page NET indicator's **Stop** control or the Bridle toolbar action. The stop path saves and opens/reveals the result for review; **Discard** deletes the unsaved capture. Choose discard only when asked or when the user approves discarding.
5. Review the saved capture. The launcher may open the capture recording list; the newly stopped capture may also have a review notification. Verify the capture and any replay before reporting completion.
6. Sharing, exporting, attaching to a feedback item, or sending to an AI tool is a separate decision. Do not assume a standalone network capture is attached to the selected feedback automatically; verify an explicit link/attachment in the UI.

When the user asks to capture diagnostics and attach them to a feedback item, perform the capture first, then inspect the feedback's available attach/share UI and verify the link. If Bridle does not expose the requested attachment path in the current UI, report that limitation rather than claiming attachment.

## Implementation notes

- The launcher button is `.w2c-send-launcher-debug` with accessible name **Capture network requests**.
- Existing captures open the network recordings modal; an empty library opens capture consent/setup.
- The setup defaults to request/response capture, console, user actions, replay, and screenshots; header values and static HTML/CSS/JS bodies are opt-in. Domain/URL exclusion is available.
- Active capture uses an in-page NET indicator with **Stop** and **Discard** paths. Stop uses `STOP_NETWORK_CAPTURE_AND_SAVE`; discard stops both the network and its associated replay stream.
- A feedback row's replay action is **View session replay** and is disabled when that feedback has no saved replay.

## Source anchors

- Saved feedback replay action and open call: [`extension/js/content.js`](../../../../extension/js/content.js#L16519).
- Replay overlay/player initialization: [`extension/js/content.js`](../../../../extension/js/content.js#L3769) and [`extension/js/content.js`](../../../../extension/js/content.js#L5870).
- Network capture launch routing and consent setup: [`extension/js/content.js`](../../../../extension/js/content.js#L308) and [`extension/js/content.js`](../../../../extension/js/content.js#L1090).
- Network stop/save indicator: [`extension/js/content.js`](../../../../extension/js/content.js#L952) and [`extension/js/content.js`](../../../../extension/js/content.js#L978).
