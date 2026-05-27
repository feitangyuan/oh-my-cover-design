# Evolution Policy

This Skill can persistently improve, but it must not rewrite itself after a single generation.

## Layers

Use three layers:

```text
memory/evolution-log.md      # per-run observations
memory/rule-candidates.md    # repeated patterns awaiting promotion
memory/deprecated-rules.md   # weak or risky patterns to avoid
```

## When To Write Memory

Write memory when the user asks for:

- 持久进化
- 自升级
- 复盘
- 集中训练
- 记录这次经验
- 升级这个 Skill

For normal cover generation, show a short `本轮记忆` in the response, but do not write files unless requested.

## Observation Format

Append to `memory/evolution-log.md`:

```yaml
date: YYYY-MM-DD
task_type: ""
article_type: ""
mode: prompt_mode | image_mode | production_mode
style_used: ""
title_used: ""
judge_weakness: ""
improvement_action: ""
final_direction: ""
keep:
  - ""
avoid:
  - ""
feedback_source: self | human | market
confidence: low | medium | high
```

## Rule Promotion

Use this threshold:

- 1 observation: log only.
- 3 similar observations: add to `memory/rule-candidates.md`.
- 5-10 stable observations: promote to a reference rule.
- Strong expert prior with low risk: may become a candidate immediately.
- Conflicting evidence: keep observing, do not promote.

Promote to references when a rule affects recurring decisions such as:

- title length or title pattern
- style selection by article type
- whether to use `production_mode`
- safe handling of Chinese typography
- product screenshot size and placement
- person/product/title hierarchy

Only edit `SKILL.md` when the rule changes the core execution flow.

## Deprecation

Add to `memory/deprecated-rules.md` when a pattern repeatedly creates risk:

- Chinese title rendered directly by image model is unreadable.
- Product screenshot is too small to inspect.
- Abstract visual metaphors cannot be generated reliably.
- Too many elements compete for first attention.
- A style repeatedly mismatches a specific article type.

## Concentrated Training

For batch improvement, process 20-50 tasks:

```text
Input sample
→ generate 3 candidate directions
→ Judge Improver revises each promising direction
→ human or market feedback selects winner when available
→ log keep/avoid rules
→ summarize candidates
→ promote stable rules
```

Do not treat self-judgment as market proof. Mark feedback source clearly.
