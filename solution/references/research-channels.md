# Research Channels Guide

Detailed search strategies for each research channel. Subagents load this file to know exactly how to search.

## Channel 1: GitHub Trend Analysis

Search with `WebSearch`:
```
site:github.com [keyword] stars:>1000
[tech A] vs [tech B] site:github.com
```
Collect: star count, star growth trend, open issues vs closed ratio, last release date, contributor count, commit frequency (last 90 days).

## Channel 2: Package Registry Analysis

**npm (JavaScript/TypeScript):**
```
site:npmjs.com [package]
site:npmtrends.com [package-a]-vs-[package-b]
```

**PyPI (Python):**
```
site:pypi.org [package]
[package] download stats pypistats
```

**crates.io (Rust) / Go modules / Maven Central** - adjust per language.

Collect: weekly downloads, version stability, dependency count, bundle size (for frontend).

## Channel 3: Official Documentation (Context7)

Priority order:
1. `mcp__context7__resolve-library-id` to find the library
2. `mcp__context7__get-library-docs` for latest API docs
3. `WebFetch` for official documentation pages if Context7 lacks coverage

Collect: API surface area, migration guides, breaking changes in recent versions.

## Channel 4: Stack Overflow

```
site:stackoverflow.com [tech] problems OR issues OR migration
site:stackoverflow.com "[tech A] vs [tech B]"
```
Collect: common pain points, unanswered question ratio (signals poor docs), top-voted answers on comparison questions.

## Channel 5: Reddit

```
site:reddit.com/r/programming [tech] review OR experience
site:reddit.com/r/webdev [tech A] vs [tech B]
site:reddit.com/r/node OR /r/reactjs OR /r/rust [tech]
```
Collect: real developer sentiment, migration war stories, "I switched from X to Y because..." narratives.

## Channel 6: Hacker News / Lobste.rs

```
site:news.ycombinator.com [tech] OR [tech] show hn
site:lobste.rs [tech]
```
Collect: senior developer opinions, production war stories, nuanced technical critiques.

## Channel 7: Chinese Tech Communities

```
site:juejin.cn [tech] 对比 OR 选型 OR 实践
site:zhihu.com [tech] 怎么样 OR 优缺点 OR 对比
site:v2ex.com [tech] 推荐 OR 选择
```
Collect: Chinese ecosystem adoption, localization quality, Chinese community activity level.

## Channel 8: Benchmark & Performance Data

```
[tech A] vs [tech B] benchmark 2025 OR 2026
[tech] performance comparison
site:benchmarksgame-team.pages.debian.net [tech]
```
Collect: throughput, latency, memory usage, startup time. Note benchmark conditions and fairness.

## Channel 9: Security (Snyk / CVE)

```
site:snyk.io/advisor [package]
site:cve.org [tech] vulnerability
[tech] security audit OR CVE
```
Collect: known vulnerability count, severity distribution, average fix time, last security incident.

## Channel 10: Google General Search

```
[tech A] vs [tech B] [current year]
[tech] production experience [current year]
"migrated from [tech A] to [tech B]" OR "switched from [tech A] to [tech B]"
```
Collect: recent blog posts, case studies, migration guides, post-mortems. Prefer content from the last 12 months.

## Subagent Prompt Template

When dispatching a subagent, include this structure in the prompt:

```
Research the following candidates: [list]
User context: [paste Phase 1 summary]
Your assigned channels: [channel numbers]

For each candidate, return findings in this format:

### [Candidate Name]
**[Channel Name]:**
- Finding 1 (source: URL or description)
- Finding 2 (source: URL or description)

Flag any red flags or surprising findings prominently.
```
