# Bridle Voice Agent

A portable, skills-only plugin package for using the Bridle browser extension with Codex and other AI assistants. It includes the Bridle workflow skill and its five reference guides. It does not include an MCP server and does not grant browser or local-file access.

## Install the skill in Codex

In a Codex chat, ask:

> Use the skill-installer to install the Bridle Voice Agent skill from `https://github.com/sandundev/bridle/tree/main/skills/bridle-voice-agent`.

The skill-installer downloads the skill and its references from this public repository into your Codex skills folder. It becomes available on the following turn. Start a new chat after installation if you want a clean conversation.

## Use Bridle in a new chat

Before asking Codex to drive the site, make sure:

1. The Bridle extension is installed and enabled in Chrome.
2. Codex has browser control connected to that same Chrome profile and can access the target website.
3. For implementation, open the website's code repository in Codex.

Then ask, for example:

> Use Bridle to capture the broken avatar on my website as a Bug. Confirm the saved REQ ID before editing code, then fix it in this repository and report how you verified it.

The skill requires Bridle feedback to be saved and verified before implementation for Bridle tasks, unless the user explicitly asks to work outside Bridle. A skill teaches the workflow; it cannot connect Codex to Chrome by itself.

## Package contents

- `plugin.json` — portable plugin manifest
- `skills/bridle-voice-agent/SKILL.md` — main workflow
- `skills/bridle-voice-agent/references/` — detailed feedback, completion, connector, replay, and ticket guides

This repository is the source package for local testing and future directory submission. Public directory approval or publication is separate from committing this source.
