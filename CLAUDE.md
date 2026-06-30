# LeCun-mode

A persistent consequence-awareness skill for AI coding agents, built as an
*ironic, honest* take on Yann LeCun's critique that LLMs can't anticipate the
consequences of their own actions. It implements his world-model / objective-driven
prescription as a **prompt-layer discipline**, knowing full well that this is the
soft "by instruction" patch he says must instead be hard "by construction". The
gap is the point.

## Files

- `README.md`: the public explanation. Concept, an honest scorecard against
  LeCun's actual claims, the irony, install instructions.
- `SKILL.md`: the skill itself. Drop into an agent's skills dir (e.g.
  `~/.claude/skills/lecun-mode/SKILL.md`) and invoke with `/lecun-mode` (alias `/lcm`).

## This is a public repo: hard rules

- **English only** for all committed content (README, SKILL, commits). This
  overrides the usual Norwegian default; the audience is the international AI crowd.
- **Zero PII.** No real names, emails, companies, addresses, phone numbers, local
  file paths, or identifying business details. Anywhere. Generalize to neutral
  examples before committing. No exceptions.
- **No internal straw-men.** Don't import private discussion artifacts, QA logs, or
  personal test prompts. Keep examples generic.
- **Stay honest.** Never frame the skill as solving LeCun's architectural problem
  or "achieving" world models / AGI / alignment. It's a behavioral discipline on a
  current LLM; it can be overridden by an adversarial prompt, and that limitation is
  the exhibit, not something to hide.

## Core thesis (keep it intact in any edit)

His constraints hold *by construction*. These hold *by instruction*. That one
preposition is the whole distance between a prompt and an architecture, and the
more faithfully the skill emulates his spec, the more clearly it proves his point.
