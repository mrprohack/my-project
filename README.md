# Last 30 Days Research for ChatGPT

A ChatGPT-native adaptation of the idea behind [`mvanhorn/last30days-skill`](https://github.com/mvanhorn/last30days-skill).

It researches what actually changed and what people are saying about a topic over the most recent 30 days, using current web evidence, primary sources, community discussion, videos, and technical sources when relevant.

## What changed for ChatGPT

The upstream project contains a large cross-agent workflow with Claude/Codex-specific runtime assumptions, helper scripts, cache-path checks, external API integrations, and its own strict output contract.

This adaptation keeps the useful research behavior but makes it native to ChatGPT:

- Uses the Agent Skills `SKILL.md` format supported by ChatGPT.
- Does not depend on Claude Code cache paths or Codex shell paths.
- Does not require Bash or Python for normal research.
- Uses ChatGPT web research and citations directly.
- Can use connected GitHub or research plugins when available, but still works without them.
- Separates confirmed facts, community signals, and uncertain claims.
- Verifies event dates instead of assuming a recently published page describes a recent event.
- Avoids invented engagement metrics or fake community consensus.

## Files

```text
.codex-plugin/
  plugin.json
skills/
  last30days-chatgpt/
    SKILL.md
    agents/
      openai.yaml
THIRD_PARTY_NOTICE.md
README.md
```

## Use as a ChatGPT Skill

ChatGPT Skills use the Agent Skills open standard. The uploadable skill is:

```text
skills/last30days-chatgpt/
```

The important file is `SKILL.md`; `agents/openai.yaml` provides user-facing interface metadata.

Typical prompts:

```text
Research what changed in AI video generation in the last 30 days.

What are developers saying about Codex vs Cursor this month?

Find the strongest recent complaints and praise for <product>.

What recent GitHub activity matters for <framework>?
```

## Research workflow

The skill resolves the exact 30-day date range, searches current evidence, checks primary sources, adds community signals, verifies freshness, then synthesizes the result with inline citations.

It supports general research, comparisons, recommendations, prompting/workflow research, technical GitHub research, and fast-moving news or controversy.

## Plugin packaging

`.codex-plugin/plugin.json` packages the skill as a skill-only OpenAI plugin-style repository so it can also be evolved for broader ChatGPT/Codex plugin distribution.

## Upstream credit

Inspired by [`mvanhorn/last30days-skill`](https://github.com/mvanhorn/last30days-skill), licensed under MIT. See `THIRD_PARTY_NOTICE.md`.
