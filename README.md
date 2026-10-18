# Bridle Assistant

The Bridle Assistant is a reusable skill for working with the **Bridle Chrome extension** through an AI assistant. It works with typed or spoken requests. The skill guides feedback capture, review, handoff, implementation and verification; it does not install Bridle or grant browser or filesystem access.

## First-time setup

1. Install [Bridle from the Chrome Web Store](https://chromewebstore.google.com/detail/bridle-%E2%80%93-send-requests-to/pmjglidnlipdecmncbjfjoooeodjofnp) in the Chrome profile you want the assistant to use.
2. Visit [bridle.io](https://bridle.io/). Sign up or sign in if you want account-backed features or Bridle asks you to. Some basic feedback capture works without an account, subject to current limits. Complete sign-up yourself; an assistant should not handle account credentials.
3. Enable the assistant's browser control for that same Chrome profile and allow access to your website.
4. If you want the assistant to implement feedback, open the website's code repository in the coding assistant. Clients can use Bridle to capture and review feedback without a code repository.

## Install the skill in Codex

In a Codex chat, ask:

> Use the skill-installer to install the Bridle Assistant skill from `https://github.com/sandundev/bridle/tree/main/skills/bridle-voice-agent`.

Codex installs the skill and its reference guides into your user skills folder. It is available on the following turn; start a new chat if you want a clean conversation.

## Start a Bridle task

In the new chat, try:

> Use `$bridle-voice-agent`. In my connected Chrome tab, use Bridle to capture the broken avatar as a Bug. Confirm the saved REQ ID before editing code, then fix it in this repository and report how you verified it.

For Bridle tasks, the skill requires saving and verifying feedback before implementation, unless you explicitly ask the assistant to work outside Bridle. Existing Bridle feedback is reused by its REQ ID rather than captured twice.

## Package contents

- `plugin.json` — portable skills-only plugin manifest
- `skills/bridle-voice-agent/SKILL.md` — the workflow and first-time setup guidance
- `skills/bridle-voice-agent/references/` — detailed feedback, completion, connector, replay and ticket guides

The public GitHub repository is the distribution source for the skill. OpenAI directory review and publication are separate steps. No Bridle MCP or model API is included.
