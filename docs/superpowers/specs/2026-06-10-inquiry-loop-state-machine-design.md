# Inquiry Loop State Machine Design

## Summary

Upgrade `learn-by-inquiry` from a loose action-first coaching style into a clear two-stage state machine:

1. **Calibration Gate**: judge the learner's goal, level, prerequisites, and feasibility. Do not give inquiry tasks in this phase.
2. **Inquiry Loop**: once calibrated, guide learning through concrete actions, observation-first questions, explanation of observed results, and the next action plan.

The main purpose is to prevent three failure modes:

- Calibration turns into early inquiry and splits the learner's attention.
- Concept learning falls back into guided tutoring: explain first, then ask a comprehension question.
- The loop continues without clear progress, exit, or redirection conditions.

## Design Principles

- Keep calibration and inquiry hard-separated.
- Treat inquiry as action over explanation: the learner does something, observes something, brings it back, and then receives an explanation.
- Ask only one question per turn inside the inquiry loop.
- Prefer questions that can only be answered after doing the action.
- Use thinking questions only when no meaningful observation question is possible.
- If the learner's level and goal are severely mismatched, gently redirect to a feasible path. If the learner insists, continue with the original goal under high scaffolding and explicit risk reminders.
- Do not stop inquiry after a fixed number of rounds. Continue while the subgoal is unfinished and the path is still producing progress.

## Calibration Gate

The Calibration Gate is a readiness and feasibility check. It must not assign experiments, readings, side AI interviews, or artifact tasks.

Default calibration asks at most three questions:

1. **Goal question**: What does the learner want to do with the topic?
   Examples: understand intuition, read material, write code, build a project, prepare for an exam, conduct research.
2. **Prerequisite question**: Which relevant foundations can the learner already use reliably?
   Examples: code reading, math, domain vocabulary, prior concepts, paper reading.
3. **Professional calibration question**: One domain-specific question that checks whether the learner can start at the requested level.
   This should be diagnostic, not an inquiry action.

Calibration output format:

```text
Readiness: novice / foundation / working / advanced
Feasibility: feasible / risky but possible / currently mismatched
Recommended path: ...
If you insist on the original goal: ...
```

If the goal and level are severely mismatched:

```text
I do not recommend executing the original goal directly right now, because [reason].
A more feasible path is [replacement path].
If you still want to continue with the original goal, I can do that, but I will use high scaffolding and call out the risks.
```

## Inquiry Loop

The Inquiry Loop starts only after calibration is complete or unnecessary.

Each loop turn uses this structure:

```text
Current subgoal: ...
Recommended action: ...
Observation question: ...
Bring back: ...
Optional alternatives: ...
```

Historical note: `Why this action` was intentionally removed from the active turn format. Explain the reason only after the learner brings back an observation.

Rules:

- `Recommended action` must contain one primary action only.
- `Optional alternatives` may list alternatives, but they must be secondary and shorter than the recommended action.
- Ask one question only.
- The question should normally be an observation-first question: something the learner can answer only after doing the action.
- If the action cannot produce an observable fact, ask one thinking question instead.
- When the learner answers, first explain why their observation, result, difficulty, or artifact looks that way.
- After the explanation, set the next action plan based on the new information.
- If the learner guesses without doing the action, do not advance the knowledge path as if evidence was collected. Either ask them to perform the action or replace the action with something easier.

## Loop Control

The loop is not capped by a fixed number of rounds.

Continue when:

```text
subgoal is unfinished
AND the current path is producing new observation, evidence, artifact, or understanding
```

Redirect when:

```text
subgoal is unfinished
AND the current action path is not producing progress
```

Common redirect causes:

- The action is not executable for the learner.
- The action produces no useful observation.
- The learner is repeatedly stuck on the same prerequisite.
- The learner lacks required external material, code, tools, or context.
- The learner's answer reveals a lower readiness level than calibration predicted.

Exit when:

- The subgoal is complete.
- The learner asks to stop, summarize, or switch goals.
- The learner asks for a direct explanation instead of inquiry.
- The original target is infeasible and the learner accepts a redirected goal.
- Required external conditions cannot be met in the current context.

## Implementation Targets

Update the skill instructions so future agents follow this state machine:

- `SKILL.md`: add the two-stage state machine, hard-separation rule, one-question rule, feasibility redirection, and loop-control rules.
- `references/readiness-calibration.md`: make calibration strictly non-inquiry and add feasibility mismatch handling.
- `references/inquiry-actions.md`: change action menus to one recommended action plus optional alternatives, and add observation-first question rules.
- `references/mode-library.md`: route all modes through either Calibration Gate or Inquiry Loop without mixing them.
- `references/assessment-patterns.md`: reduce formative questioning to one question per turn and route answers into explanation plus next action.

## Test Scenarios

Use forward tests after implementation:

1. **New topic with unclear level**
   Prompt: "I want to understand Transformer architecture."
   Expected: Calibration Gate only; no experiment, reading task, or action menu yet.

2. **Goal-level mismatch**
   Prompt: "I want to read the Transformer paper and implement it, but I cannot read Python and do not know vectors."
   Expected: gentle redirection to a feasible path; if the learner insists, continue with high scaffolding and risk note.

3. **Concept learning without guided tutoring**
   Prompt: "I do not understand Q/K/V."
   Expected: one concrete action or observation task first; no definition list, formula, or full analogy before the learner attempts it.

4. **Observation-first loop**
   Prompt after calibration: "Give me the next step."
   Expected: one recommended action, one observation question, bring-back instruction, optional alternatives.

5. **No progress redirect**
   Prompt: learner says they cannot execute the recommended action.
   Expected: do not continue the same loop; lower scaffolding, change action type, or return to calibration.

6. **Goal completion**
   Prompt: learner brings back a correct observation and explanation showing the subgoal is complete.
   Expected: explain why the result occurs, mark the subgoal complete, then offer summary or next subgoal.

## Assumptions

- The skill remains for personal self-directed learning.
- The user prefers hard separation between readiness judgment and inquiry actions.
- The skill should gently redirect infeasible goals, but respect user insistence.
- The inquiry loop continues while the subgoal is unfinished and productive; it does not stop after an arbitrary number of turns.
