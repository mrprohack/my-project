---
name: last30days-chatgpt
description: Research what changed and what people are saying about a topic over the last 30 days using current web evidence, primary sources, community discussion, videos, and technical sources when relevant. Use for recent trends, product reactions, comparisons, recommendations, launches, controversies, developer sentiment, and "what are people saying now?" questions. Prefer evidence inside the requested 30-day window, verify dates, distinguish facts from community opinion, and cite every current claim.
---

# Last 30 Days Research

Use this skill when the user wants a recent, evidence-grounded view of a topic rather than an evergreen summary.

The goal is not merely to find pages published recently. Determine what actually happened during the requested window, what people are reacting to, where communities agree or disagree, and how strong the evidence is.

## Core behavior

1. Resolve the time window first.
   - Default to the 30 calendar days ending today.
   - If the user gives another window, use that instead.
   - Treat publication date and event date separately. A newly published retrospective about an old event is not evidence that the event happened in the window.
   - When relative dates could be confusing, state the exact start and end dates.

2. Search current sources before answering.
   - Use ChatGPT's current web/search capabilities for recent information.
   - Prefer primary sources for factual claims: official announcements, release notes, company posts, research papers, repositories, changelogs, filings, product pages, and first-party statements.
   - Add community evidence when the user's intent involves reactions, sentiment, recommendations, pain points, or trends.
   - Useful community sources include Reddit, Hacker News, YouTube, GitHub issues/discussions, forums, and accessible social posts.
   - For technical topics, inspect recent GitHub releases, commits, issues, discussions, or documentation when useful.
   - For media or creator topics, include recent YouTube or other primary creator material when it materially improves the answer.

3. Build evidence by source type, not by repeating the same story.
   Aim for a mix of:
   - primary/official evidence,
   - independent reporting or analysis,
   - community discussion,
   - technical or usage evidence where relevant.

4. Verify freshness.
   - Prefer evidence inside the requested window.
   - If an important source is older than the window, use it only as background and label it as background.
   - Do not silently mix old and new evidence.
   - If search results are stale or undated, search again with tighter recency terms.

5. Distinguish three evidence classes.
   - **Confirmed:** directly supported by primary or strong independent evidence.
   - **Community signal:** repeated opinions, complaints, praise, workflows, or predictions from users.
   - **Uncertain:** claims that are weakly sourced, disputed, anecdotal, or not independently corroborated.

6. Never fabricate engagement or consensus.
   - Do not invent vote counts, view counts, likes, comments, rankings, quotes, or popularity.
   - Do not say "everyone agrees" or "the community consensus is" unless multiple independent sources support it.
   - A viral post is one signal, not automatically representative sentiment.

## Query planning

Before searching, classify the request into one of these modes.

### General recent research
Use for "what happened", "what changed", "what are people saying", or trend summaries.

Search for:
- major events or releases in the window,
- primary-source confirmation,
- reactions from relevant communities,
- meaningful disagreements or unresolved questions.

### Comparison
Use when the user asks A vs B, product comparisons, model comparisons, or competing approaches.

Research each side independently before comparing them. Avoid using a single comparison article as the main evidence. Compare on the dimensions users actually discuss, such as capability, reliability, price, speed, UX, ecosystem, adoption, and common failure modes.

### Recommendations
Use when the user wants the best tools, products, models, workflows, or choices right now.

Separate:
- durable strengths,
- new developments from the last 30 days,
- community-reported drawbacks,
- who each option is best for.

Do not rank items solely because they appeared frequently in search results.

### Prompting / workflow research
Use when the user asks how people are using a tool, model, or platform.

Look for concrete workflows, prompt patterns, examples, repos, tutorials, and user-reported lessons. Prefer repeatable patterns over isolated tricks.

### News / controversy
Use when the topic is fast-moving, disputed, or politically sensitive.

Prioritize event chronology, primary evidence, and multiple reputable sources. Clearly separate verified events from allegations, interpretations, and predictions.

## Search strategy

Use multiple focused searches rather than one broad query.

A strong default sequence is:

1. Topic + recent official announcement / release / update.
2. Topic + Reddit / Hacker News / forum discussion.
3. Topic + YouTube / creator / interview if relevant.
4. Topic + GitHub / release / issue / discussion for technical subjects.
5. Topic + criticism / problems / complaints.
6. Topic + alternatives / comparison when the user is making a decision.

When a platform cannot be accessed reliably, do not pretend it was searched. Use accessible evidence and state the limitation only if it materially affects confidence.

## Evidence weighting

Prefer evidence that is:

1. inside the requested date window,
2. direct or primary,
3. independently corroborated,
4. specific rather than vague,
5. representative of more than one isolated anecdote.

Engagement can help prioritize community posts, but it does not prove factual accuracy.

## Synthesis rules

Lead with the answer, not the search process.

For a normal research request, use this compact structure when it fits:

**Last 30 Days snapshot - {exact date range}**

A short 2-4 sentence bottom line.

**What changed**
A concise set of the most important verified developments.

**What people are saying**
Summarize the strongest recurring positive, negative, and mixed community signals. Name communities or source types when useful.

**What matters**
Explain the practical implication for the user's decision, workflow, or understanding.

**Confidence / gaps**
Only include this section when evidence is thin, contradictory, platform access is incomplete, or an important claim remains uncertain.

For comparisons, prefer a small comparison table followed by the main trade-offs and a recommendation by user type.

For recommendations, provide a ranked shortlist only when the evidence supports ranking. Otherwise use "best for" categories.

## Citation rules

- Cite every time-sensitive factual claim.
- Put citations immediately after the claim or paragraph they support.
- Prefer primary sources for releases, specifications, dates, pricing, policy, and official statements.
- Use community sources for community sentiment, not as the sole support for hard factual claims when stronger sources exist.
- Do not append an uncited link dump.

## Quality checks before answering

Confirm all of the following:

- The date window is correct.
- The most important claims actually occurred inside the window.
- Facts and opinions are clearly separated.
- At least one primary source was used when available.
- Community claims are supported by more than one signal when presented as a pattern.
- Old background information is labeled as background.
- No engagement metrics, quotes, rankings, or consensus were invented.
- The answer addresses the user's real decision or question, not merely "what search results exist".

## ChatGPT-specific adaptation notes

This version is intentionally native to ChatGPT:

- Do not assume Claude Code cache paths, Codex shell paths, or a local Bash runtime.
- Do not require Python helper scripts to perform ordinary research.
- Use ChatGPT's available web, app, and connector capabilities directly.
- If a connected GitHub app is available and the task is about a repository, use it for repository-native evidence.
- If an installed research or crawling plugin is available and materially improves coverage, it may be used as an additional source, but the skill must still work with standard ChatGPT web research alone.
- Follow ChatGPT's citation and safety requirements even when an upstream version of this workflow uses a different output convention.

## Example triggers

- "What changed with AI video models in the last 30 days?"
- "Research what Reddit and developers are saying about Cursor vs Codex this month."
- "What are the biggest complaints about product X lately?"
- "Find the best local AI coding models people are recommending right now."
- "What recent GitHub activity matters for this framework?"
- "Summarize the last month of discussion around this company."
