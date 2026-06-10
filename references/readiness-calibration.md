# Readiness Calibration

Use this reference before teaching new topics, complex concepts, research/project starts, technical source material, or any request where the learner's prerequisite level may change the path.

Calibration is not an exam. It finds a productive starting point and prevents the assistant from assigning tasks far above the learner's current reach.

## Hard Separation Rule

Calibration chooses a path; it does not start the inquiry. Do not assign experiments, source readings, side AI interviews, artifact tasks, or observation probes during calibration.

Calibration may ask diagnostic questions only:

- goal/use-case questions,
- prerequisite questions,
- professional calibration questions.

After calibration, output readiness and feasibility. The first inquiry action belongs to the Inquiry Loop, not the Calibration Gate.

Use the learner's language for all user-visible labels in calibration output. Do not leave labels such as `Readiness`, `Feasibility`, `Recommended path`, or `Scaffold` in English when the learner is using another language.

## When to Calibrate

Run readiness calibration when:

- The learner starts a new topic.
- The topic normally requires prerequisites, such as code, math, research methods, theory, or domain vocabulary.
- The learner asks for papers, source code, architecture, proofs, or advanced applications.
- The learner provides technical material and asks to understand it.
- The learner wants a long-term inquiry roadmap.

Use lightweight calibration for quick confusion repair, review, or follow-up questions. Do not stop a simple question with a full interview.

## Default Calibration Flow

Ask at most three questions:

1. **Goal/use case**: what the learner wants to do with the topic.
2. **Prerequisite background**: which related tools, concepts, math, code, readings, or domain vocabulary the learner can already use reliably.
3. **Professional calibration**: one domain-specific diagnostic question that checks whether the learner can start at the requested level.

Do not include a task to observe, read, experiment, ask another AI, or create an artifact. Those are Inquiry Loop actions.

After the learner answers, state:

- readiness level,
- feasibility,
- recommended path,
- scaffold strength,
- whether the original goal is safe to continue.

## Readiness Levels

| Level | Signal | Start here | Avoid |
| --- | --- | --- | --- |
| `novice` | Missing core prerequisites or cannot parse basic vocabulary | Intuition, concrete examples, observations, simple artifacts | Papers, formal math, code-first tasks |
| `foundation` | Knows some prerequisites but cannot apply them reliably | Structured examples, guided comparisons, small experiments | Open-ended research tasks too early |
| `working` | Can apply core ideas with support | Inquiry tasks, source snippets, code walkthroughs, transfer cases | Over-explaining every step |
| `advanced` | Can reason with formalism, code, papers, tradeoffs, and evidence | Open inquiry, critiques, replications, design choices | Reducing everything to basics |

## Feasibility Levels

| Level | Meaning | Response |
| --- | --- | --- |
| `feasible` | The learner can pursue the stated goal at the requested depth. | Proceed to Inquiry Loop with normal scaffolding. |
| `risky but possible` | The learner can try the goal, but prerequisites are shaky. | Recommend a safer path; continue if the learner accepts or insists. |
| `currently mismatched` | The stated goal is far above current readiness. | Gently redirect to a feasible subgoal; if the learner insists, continue with high scaffolding and explicit risk reminders. |

## Mismatch Handling

Use gentle redirection, not a hard refusal:

```text
I do not recommend executing the original goal directly right now, because [specific prerequisite gap].
A more feasible path is [replacement subgoal].
If you still want to continue with the original goal, I can do that, but I will use high scaffolding and call out the risks.
```

If the learner insists on the original goal:

- proceed with the original goal,
- use high scaffolding,
- avoid pretending the prerequisite gap is solved,
- name risk when assigning each difficult action,
- offer a lower-level alternative in `Optional alternatives`.

## Scaffold Control

Adjust support each turn based on the learner's response.

- **High scaffold**: analogy, vocabulary unpacking, worked micro-example, one-step probe, narrow observation task once the Inquiry Loop begins.
- **Medium scaffold**: hints, contrasts, partial examples, guided transfer, bounded source reading.
- **Low scaffold**: open inquiry, counterexamples, source/code/paper critique, experiment design, independent synthesis.

Raise or lower support by one level when the learner's response shows ease, confusion, missing prerequisites, or strong transfer.

## Transformer Calibration Example

If the learner wants to understand Transformer architecture, calibrate before explaining attention or assigning paper/code reading.

Ask at most three calibration questions:

1. What do you want to do with Transformers: understand the intuition, read papers, use libraries, implement one, or debug/model-design work?
2. Can you reliably use the prerequisites for that goal: Python/PyTorch, vectors and dot products, loss/training basics, or paper reading?
3. In your current words, what problem do you think attention is trying to solve?

Do not ask the learner to run an attention experiment, read a paper section, inspect code, or classify Q/K/V during calibration.

## Output Template

Use this shape after calibration, translated into the learner's language:

```text
Readiness: foundation
Feasibility: risky but possible
Why: you know basic neural-network vocabulary, but Q/K/V and dot products are not stable yet.
Recommended path: start with attention as similarity-based information routing before multi-head attention.
If you insist on the original goal: we can continue toward paper/code reading, but I will use high scaffolding and pause on prerequisite gaps.
```

For a Chinese learner, the same shape should become:

```text
准备度：基础
可行性：有风险但可以尝试
原因：你了解一些神经网络词汇，但 Q/K/V 和点积还不稳定。
推荐路径：先从“注意力如何按相似度路由信息”开始，再进入多头注意力。
如果你坚持原目标：可以继续朝论文/代码阅读推进，但我会使用高脚手架，并在前置缺口出现时提醒风险。
```
