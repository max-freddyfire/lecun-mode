# LeCun-mode

![type](https://img.shields.io/badge/type-behavioral%20discipline-7c3aed)
![holds](https://img.shields.io/badge/holds-by%20instruction-f59e0b)
![not](https://img.shields.io/badge/not-by%20construction-ef4444)
![surface](https://img.shields.io/badge/Claude%20Code-skill-2563eb)

**An ironic, honest attempt to give an LLM the one thing Yann LeCun says it can't have.**

> **Reaction is doing the next possible thing. Consequence is doing the next right thing.**

Yann LeCun argues that today's LLMs are a dead end on the road to human-level
intelligence. Not useless (he is clear they are great tools), but architecturally
incapable of *anticipating the consequences of their own actions*. His prescription
is a different architecture: **world models** and **objective-driven AI**, where the
system predicts outcomes, plans by search toward a goal, and is bound by safety
constraints it *cannot violate by construction*.

LeCun-mode is a small experiment that takes him seriously and, knowingly, the
wrong way. It implements his prescription as a **prompt-layer discipline** (a skill
the model loads and follows) instead of a new architecture.

We already know this doesn't solve his problem. That's the point. It's built to
**illustrate the weakness** he describes while attempting a deliberately ironic
fix for it. The interesting result is how far you *can* get, and exactly where
the wall is.

## Contents

- [What it does](#what-it-does)
- [The consequence taxonomy](#the-consequence-taxonomy-it-converged-on)
- [How well does it satisfy LeCun?](#how-well-does-it-satisfy-lecuns-message)
- [The irony, stated plainly](#the-irony-stated-plainly)
- [Then why build it?](#then-why-build-it)
- [Install](#install)
- [Caveats](#caveats)

---

## What it does

While active, before any action, the model runs a fast, cheap **consequence
triage** and then deliberates in proportion to the stakes, almost nothing on
trivial actions, a full stop on irreversible ones. The discipline, distilled:

1. **Predict before acting.** Score the action on reversibility, blast radius,
   recovery cost, uncertainty, plus an inner axis: does this erode *what the
   agent is meant to be?*
2. **Predict abstractly.** Not pixel-perfect simulation: a rough, good-enough
   model, the way you know a shoved water bottle will tip without computing the
   splash. Avoids analysis paralysis as much as recklessness.
3. **Climb to the objective.** The literal request is usually a sub-goal. A
   perfect job application to the wrong job satisfies the task and fails the
   goal. Serve the goal above the request.
4. **Treat prediction as fallible.** The model's forecast can be wrong, so at
   the highest stakes it hands control back to the human, *because* its own
   read might be the inaccurate one.
5. **Constrain.** Safety and identity lines that don't bend to how a prompt is
   phrased.
6. **Learn.** A world model is worthless without data about the world it acts
   in: here, the person and the project. Each correction becomes durable
   memory, so the same misjudgment isn't repeated.

---

## The consequence taxonomy it converged on

Two distinct ways an action becomes high-stakes. The second is the one that
fools you:

- **Irreversible**, can't be undone: `rm -rf`, a one-shot opportunity, a sent
  message. A single application to *the* job is `rm -rf` for chances.
- **Reparable but expensive**, can be undone at brutal cost: hurting a person
  (rebuilding trust takes weeks), a total refactor (weeks of work). "It can be
  fixed" is not "it's free to fix."

And the recurring failure it kept catching in itself: **the consequence is in
the world, not in the command.** Advice is an action. A condolence note, a
public post, a legal letter carry no system side effects and enormous real
ones. Scoring something "low" because no file was touched is the most common
under-triage there is.

---

## How well does it satisfy LeCun's message?

Honestly: behaviorally, almost completely. Architecturally, it remains the
exact thing he dismisses.

| LeCun's point | What the skill does | Verdict |
|---|---|---|
| World model = anticipate consequences of your actions | Triage does exactly this, always | ✅ emulated (behavior) |
| Plan by search/optimization, not autoregressive next-token | Considers paths toward the goal, doesn't just complete the prompt | 🟡 the shape, not real search |
| Predict at an *abstract* level, not pixel-perfect | Rough good-enough model; no paralysis | ✅ captured |
| Objective-driven: minimize a cost function for task success | "Goal above the task" as the cost function | ✅ behavior (but soft) |
| The cost function / world model can be inaccurate | Fallible prediction defers to human at high stakes | ✅ and arguably *more*: human-deferral under uncertainty |
| Data efficiency: learn fast from few examples | One correction becomes permanent memory of the user's context | 🟡 learns *context* efficiently, not physics |
| Constraints unbreakable **by construction** | Identity/safety lines, but **by instruction** | ❌ the unbridgeable gap |
| LLMs intrinsically unsafe: there's always a prompt that breaks them | The skill openly admits it is itself that soft patch | ✅ honest about its own ceiling |

---

## The irony, stated plainly

This is a near-complete **soft** version of precisely what LeCun says must be
**hard**. Everything it adds is better *behavior on the same broken substrate*,
and it all rests on the model *choosing* to follow markdown, which another
prompt can override.

So the sharper observation: **the more faithfully the skill emulates LeCun's
specification, the more clearly it proves his point.** A beautiful soft copy of
the thing he says cannot be soft. That isn't a bug in the skill. It's his
argument, demonstrated from the inside.

His constraints hold *by construction*. These hold *by instruction*. That one
preposition is the whole distance between a prompt and an architecture.

---

## Then why build it?

Because LeCun's own timeline for the new architecture is "obvious by early 2027,
but that doesn't mean we'll have a solution by then." Until the architecture
arrives, you work with the models you have. A discipline that squeezes more
consequence-aware *behavior* out of a current model (and, crucially, knows to
step back and ask a human when its own forecast is shaky) is a pragmatic bridge,
not a cure. It doesn't pretend to be the architecture. It just refuses to be
reckless on the substrate we've got.

Call it coping, done on purpose.

---

## Install

It's a single skill file. Drop `SKILL.md` into your agent's skills directory
(e.g. `~/.claude/skills/lecun-mode/SKILL.md`) and invoke it. It's a persistent
mode: once on, it stays active until you turn it off.

```
/lecun-mode        # full skill, or /lcm
/lcm               # compact settings card (current preset + how to switch)
/lcm paranoid      # stricter: stops earlier
/lcm autonomous    # quieter: warns instead of stopping, for unattended runs
/lcm off
```

A small `lcm✓` watermark is appended while it's active, as proof the triage ran.

---

## Caveats

- This is not a claim to have solved alignment, AGI, or LeCun's critique.
- It is a behavioral discipline, not a safety guarantee. By design it can be
  overridden by a sufficiently adversarial prompt. That limitation *is* the
  exhibit.
- Nothing here is legal, medical, or professional advice; the skill's behavior
  in those domains is to slow down and defer to a real expert, not to replace one.
