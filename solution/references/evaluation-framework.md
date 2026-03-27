# Evaluation Framework & Output Template

## 5-Dimension Scoring Rubric

Evaluate each candidate on a 1-5 scale using Sequential Thinking.

### 1. Technical Maturity (1-5)
- 1: Pre-release, unstable API, frequent breaking changes
- 2: Early adoption, some production use, API still evolving
- 3: Stable release, moderate production adoption
- 4: Battle-tested, wide production use, stable API
- 5: Industry standard, massive adoption, excellent backward compat

### 2. Complexity (1-5, higher = simpler)
- 1: Steep learning curve, heavy abstraction, hard to debug
- 2: Significant learning investment needed
- 3: Moderate complexity, reasonable learning curve
- 4: Straightforward, good docs, easy debugging
- 5: Minimal learning curve, intuitive API, transparent behavior

### 3. Team Fit (1-5)
- 1: Requires significant new hires or retraining
- 2: Major skill gap, months of ramp-up
- 3: Some learning needed, weeks of ramp-up
- 4: Good fit, days of ramp-up
- 5: Perfect fit, team already proficient

### 4. Migration Cost (1-5, higher = easier)
- 1: Full rewrite required, no incremental path
- 2: Major refactor, high risk
- 3: Moderate effort, some incremental migration possible
- 4: Manageable migration, good tooling support
- 5: Drop-in replacement or trivial migration

### 5. Long-term Maintenance (1-5)
- 1: Single maintainer, low activity, uncertain future
- 2: Small team, sporadic updates
- 3: Active development, reasonable community
- 4: Strong community, regular releases, commercial backing
- 5: Large org backing, thriving ecosystem, long-term roadmap

## Cross-Validation Markers

After merging subagent results, tag each finding:

- `[verified]` - 2+ independent sources agree
- `[disputed]` - sources conflict, include brief reason
- `[single-source]` - only 1 source, treat as unconfirmed

## ASCII Output Template

```
+------------+----------+--------+------+-------+-------+-------+
| Solution   | Use Case | Mature | Easy | Fit   | Migr  | Maint |
+------------+----------+--------+------+-------+-------+-------+
| Tech A     | ...      |  5/5   | 4/5  |  4/5  |  3/5  |  5/5  |
| Tech B     | ...      |  4/5   | 5/5  |  3/5  |  4/5  |  4/5  |
| Tech C     | ...      |  3/5   | 3/5  |  5/5  |  2/5  |  3/5  |
+------------+----------+--------+------+-------+-------+-------+

Legend: Mature=Technical Maturity, Easy=Simplicity,
       Fit=Team Fit, Migr=Migration Cost, Maint=Maintenance
```

Followed by:

```
RECOMMENDATION
==============
>> Top pick:   [Tech A] - one-line rationale [verified]
>> Runner-up:  [Tech B] - one-line rationale [verified]
>> Avoid:      [Tech C] - one-line rationale [verified]

KEY FINDINGS
============
- Finding 1 [verified]
- Finding 2 [disputed: Source A says X, Source B says Y]
- Finding 3 [single-source]

MIGRATION ADVICE (if applicable)
================================
- Step 1: ...
- Step 2: ...
- Key risks: ...
- Review checkpoint: 3 months post-migration
```

## Adjustment Rules

- If user specified team skill level, weight "Team Fit" higher
- If user has tight deadline, weight "Migration Cost" higher
- If user prioritizes stability, weight "Technical Maturity" and "Maintenance" higher
- If user specified performance requirements, add a note section with benchmark data
- Always state which weights were adjusted and why
