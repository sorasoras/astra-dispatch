# Astra dispatch

A ZCode skill that prepends OpenAI GPT-6 Astra [initiative and follow-through](https://developers.openai.com/api/docs/guides/latest-model#gpt-6-astra-initiative-and-follow-through) prompts whenever dispatching the Smartest-coder / Astra subagent.

Astra asks for clarification and stops where earlier models assumed and persisted. This skill makes the dispatcher prepend the official blocks at the top of every Astra `prompt`, then the task. Do not summarize the blocks away. Do not wait for the user to paste them again.

Start with [SKILL.md](SKILL.md).

## What it does

- Triggers on Astra / Smartest-coder launches, and on phrasing such as "use astra", "delegate to astra", or "command astra".
- Requires the three official initiative-and-follow-through blocks at the top of `prompt`.
- Optionally appends the skill-precedence / pause-diagnosis blocks when another skill or `AGENTS.md` is making Astra stall.
- Keeps user instructions above this skill when they conflict. Destructive or irreversible actions still need a stop.
- Includes extra bars for GQA-MLC-Sakura kernel work after the official blocks. Drop or replace that section if you install this skill outside that campaign.

## Install

Clone the repository into your agent's skill directory, using `astra-dispatch` as the folder name. For ZCode:

```sh
git clone https://github.com/sorasoras/astra-dispatch.git ~/.zcode/skills/astra-dispatch
```

Authenticate with GitHub first when the repository is private. If that directory already exists, preserve it before replacing it; do not clone over an installed copy. Other compatible agents can use their own skill directories.

## Layout

- `SKILL.md`: trigger description, official Astra blocks, optional pause-diagnosis blocks, and campaign extra bars.
