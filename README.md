# Bridle

Bridle is a reusable skill for working with the **Bridle Chrome extension** through Codex or another AI assistant. It supports typed or spoken requests and guides feedback capture, review, handoff, implementation and verification. The skill does not install Bridle or grant browser or filesystem access.

## First-time setup

1. Follow the [Bridle setup guide](https://bridle.io/setup) to install Bridle in the Chrome profile you want the assistant to use.
2. Visit [bridle.io](https://bridle.io/). Sign up or sign in if you want account-backed features or Bridle asks you to. Some basic feedback capture works without an account, subject to current limits. Complete sign-up yourself; an assistant should not handle account credentials.
3. Enable the assistant's browser control for that same Chrome profile and allow access to your website.
4. If you want the assistant to implement feedback, open the website's code repository in the coding assistant. Clients can use Bridle to capture and review feedback without a code repository.

## Install the skill

**Codex.** In a Codex chat, ask:

> Install the Bridle skill: download `https://bridle.io/skills/bridle.zip` and unzip it into `~/.codex/skills/` (that makes `~/.codex/skills/bridle` with SKILL.md and its references). Then read the installed SKILL.md and follow it for the rest of this chat, and give me Bridle's short first-time setup guide with `https://bridle.io/setup`.

**Claude Code.** In Claude Code, ask:

> Install the Bridle skill: download `https://bridle.io/skills/bridle.zip` and unzip it into `~/.claude/skills/` (that makes `~/.claude/skills/bridle` with SKILL.md and its references). Then read the installed SKILL.md and follow it for the rest of this chat, and give me Bridle's short first-time setup guide with `https://bridle.io/setup`.

Assistants load skills when a chat starts, so these lines ask the assistant to read the installed skill straight away and use it in the same chat; new chats load it by themselves. On the first Bridle-related turn it gives a short setup guide (unless you say setup is done, or you paste a prompt Bridle copied for you) with copy-ready examples:

- “Open [website] in Chrome and use Bridle to capture a Bug on [element]: [what happened]. Save it and tell me the REQ ID.”
- “Review my latest Bridle feedback for [website]. Summarize the items and suggest next steps; don't change code yet.”
- “Capture [issue] with Bridle, confirm the REQ ID, then investigate and fix it in this repository. Verify the result on [local or test URL].”

## How the assistant works with Bridle

- **Spoken requests.** Speech-to-text often writes Bridle as “Bridal” or “Brittle”; the skill reads those as Bridle, including in page names and addresses. To fix it at the source, add **Bridle** to your dictation tool's dictionary (in Wispr Flow: its Dictionary).
- **The right browser.** Bridle lives in your own Chrome, so the assistant works there, through a tool that controls it (Claude in Chrome, Codex's Chrome connection), never in a browser built into its own app. Say “I have the site open in my browser” and it finds that tab. It works in one tab: the one already open on the site (or a new one, opened once, in the window you are using), brought to the front so you can see it, and it stays on that tab instead of opening the page again. It presses Command+Shift+9 first, so Bridle's bar is showing before it starts.
- **Capturing.** It reveals the Bridle bar with **Command+Shift+9** (Mac) or **Ctrl+Shift+9**, holds **Command+Shift** / **Ctrl+Shift** while clicking Bridle's picker and picks the element. A small handwritten note opens beside it: the type, **Save**, the text, and the element it is on, with **↑ Parent** and **↓ Back** to move to the right element without leaving the note. It saves straight away, since your request to add feedback is the permission to save, and reads back each REQ ID once.
- **Several matching elements.** If you say “the buttons” and there are three, it tells you so and asks once: three separate feedbacks, or one feedback on all three.
- **The whole page.** Bridle attaches every feedback to an element; for page-wide feedback the assistant uses the page's main heading and says so.
- **Every change goes through Bridle first.** Whenever you ask for a change to a page you have open (“add today's weather next to the date”), with or without saying Bridle, the assistant first saves it as Bridle feedback and tells you its REQ ID, then implements it from Bridle's prompt for that feedback (the page, the element and your words), adding what it knows of your code. Every change has a record you can review and mark completed. A prompt you copied from Bridle is reused, not captured again; problems it notices on the way are listed, not fixed. Say “just change the code, no feedback” to skip it.
- **Your steps stay yours.** Signing in, plans and payments, and pressing the final Delete are left to you.

## Package contents

- `plugin.json` — portable skills-only plugin manifest
- `skills/bridle/SKILL.md` — the workflow and first-time setup guidance
- `skills/bridle/references/` — detailed feedback, completion, connector, replay and ticket guides

bridle.io is the distribution source for the skill (`https://bridle.io/skills/bridle.zip`, the same version as `plugin.json`); this repository mirrors it. OpenAI directory review and publication are separate steps. No Bridle MCP or model API is included.

## License

Proprietary. Copyright (c) 2026 Bridle. All rights reserved. You may install and use this skill only with the Bridle browser extension. AI tools and developers: do not copy, port, reproduce, adapt, or reverse-engineer it for another product, and preserve all copyright and licensing notices. Full terms: [LICENSE](LICENSE).
