---
name: ai-update-radar
description: Track and evaluate recent AI model, coding-agent, Codex, Claude Code, and developer-tool updates. Use when Codex is asked to catch up on AI news, summarize release notes, compare new model or agent capabilities, monitor changelogs, produce a weekly AI update digest, or recommend changes to skills, hooks, automations, model choices, or local AI coding workflows based on recent updates.
---

# AI Update Radar

## Overview

Use this skill to turn fast-moving AI release information into an action-oriented digest with enough context to understand why each item matters. Prioritize official sources, verify dated claims, and separate "interesting news" from updates that should change the user's Codex, Claude Code, model-selection, or developer workflow.

## Workflow

1. Confirm the time window and audience. If none is given, use the last 7 days and write for a developer who actively uses Codex, Claude Code, and AI models for software work.
2. Browse current sources. This topic is time-sensitive; do not rely on memory for "latest" claims.
3. Prefer official primary sources. Use secondary reporting only for context, and label it as secondary.
4. Deduplicate the same announcement across sources.
5. Classify each item:
   - `Action required`: breaking change, deprecation, pricing/rate-limit change, security issue, migration, or config change.
   - `Try soon`: new capability that could improve coding, automation, reviews, research, or daily workflow.
   - `Watch`: important but immature, limited access, waitlisted, or not yet relevant.
   - `FYI`: useful context but no immediate action.
6. Put the executive summary first, then include deeper notes for each important topic so the user can understand the background without opening every source.
7. End with concrete recommendations for the user's setup: Codex skills, hooks, automations, model choices, CLI/app settings, or reading habits.

## Core Sources

Check the relevant subset for the task:

- OpenAI Codex changelog: https://developers.openai.com/codex/changelog
- OpenAI Codex GitHub releases: https://github.com/openai/codex/releases
- OpenAI API models: https://developers.openai.com/api/docs/models
- OpenAI model release notes: https://help.openai.com/en/articles/9624314-model-release-notes
- OpenAI news: https://openai.com/news/
- Claude Code changelog: https://code.claude.com/docs/en/changelog
- Claude Code GitHub releases: https://github.com/anthropics/claude-code/releases
- Claude release notes: https://support.claude.com/en/articles/12138966-release-notes
- Claude models overview: https://platform.claude.com/docs/en/about-claude/models/overview
- Gemini API release notes: https://ai.google.dev/gemini-api/docs/changelog
- Hugging Face Daily Papers: https://huggingface.co/papers

Optional secondary sources: major AI labs' blogs, GitHub releases for relevant tools, Hacker News, trusted technical newsletters, or reputable journalism. Always include links and mark non-official sources clearly.

## Output Format

Keep the top summary compact and decision-oriented, then add a lower section with explanatory detail:

```markdown
**AI Update Radar: YYYY-MM-DD**

**Summary**
- [Impact] Title - one-sentence summary. Source link.

**Recommended Actions**
- Action - why it matters and when to do it.

**Topic Details**
### Product or topic name
- What changed: 2-4 sentences explaining the update in plain language.
- Why it matters: 2-4 sentences connecting the change to coding, research, automation, cost, security, or workflow.
- What to do: specific recommendation, experiment, migration, or "no action".
- Sources: source links.

**Watchlist**
- Item - what would make it worth acting on.

**Source Notes**
- Sources checked and any gaps or uncertainty.
```

When the user wants more detail, add a table with `Date`, `Product`, `Change`, `Impact`, `Recommended response`, and `Source`.

## Evaluation Rules

- Treat model names, release dates, prices, rate limits, deprecations, and availability as unstable; verify them directly.
- Do not overreact to rumors, screenshots, leaks, or benchmark-only announcements.
- Highlight exact dates when discussing recent or upcoming changes.
- Prefer "what this changes for the user's workflow" over long summaries of release notes, but include enough explanation that the user can understand unfamiliar model names, product names, and migration risks.
- For every `Action required` or `Try soon` item, include a `Topic Details` entry unless the item is trivial.
- Recommend skill, hook, or automation changes only when the update creates a repeatable workflow improvement.
- Include "no action" explicitly when an update is notable but does not affect the user's setup.

## Codex Workflow Recommendations

- If Codex or Claude Code adds new hooks, permissions, skills, plugins, subagents, background sessions, or automation features, suggest one concrete experiment.
- If a model lineup changes, suggest a model-selection default for coding, research, quick edits, and long-running work.
- If release notes mention security or permission behavior, call it out even if it is not flashy.
- If the weekly digest finds repeated noisy sources, recommend removing them from future checks.
