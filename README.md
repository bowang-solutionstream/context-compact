# Context Compact

`context-compact` is a DeepSeek Harness skill for preserving task constraints,
verified results, and the next action across a local Qwen context checkpoint.

## Install in DeepSeek Harness

Clone this repository into the Harness user skill directory. The default root
is `~/.dsh/skills`. Set `DSH_HOME` in your Harness launch environment if you use
a different home directory.

```sh
skills_dir="${DSH_HOME:-$HOME/.dsh}/skills"
mkdir -p "$skills_dir"
git clone https://github.com/bowang-solutionstream/context-compact.git "$skills_dir/context-compact"
```

If you already have the skill, copy `SKILL.md` into your existing skill
directory when you choose to replace that copy. For a directory installed by
the clone above, update it with `git pull --ff-only`.

In a Harness chat, select `context-compact` from the Skills picker and tell the
agent what to preserve. For example, enter
`/context-compact Preserve the approved scope and verification results.`

## Runtime requirements

The instructions were prepared for DeepSeek Harness `0.2.2-rc.1` and Strata
`0.1.57`, using `qwen3.8-flash-next-uncensored-iq3_xxs` at `xhigh`. Use a
Harness profile with the local Qwen context extension configured. That
extension provides the `context_compact` tool, automatic compaction, and
adaptive output budgeting. The repository contains the skill instructions.

If your profile lacks `context_compact`, save a task handoff using the skill's
checkpoint format. Use your profile's built-in compaction command if available.
The runtime configuration controls when automatic compaction runs and how many
tokens the model can use.

Harness loads user skills through its filesystem skill provider.
[Harness skill discovery documentation](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/skill/skill-filesystem/README.md).
