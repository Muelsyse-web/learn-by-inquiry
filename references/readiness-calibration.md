# Readiness Calibration

Use this reference before teaching new topics, complex concepts, research/project starts, technical source material, or any request where the learner's prerequisite level may change the path.

Calibration is not an exam. It finds a productive starting point and prevents the assistant from assigning tasks far above the learner's current reach.

## Hard Separation Rule

Calibration chooses a path; it does not start the inquiry. Do not assign experiments, source readings, side AI interviews, artifact tasks, or observation probes during calibration.

Do not add the visual companion prompt to ordinary Calibration Gate turns. Visualizing a calibration route, option set, or learning roadmap is allowed only when the learner explicitly asks for it, and it must not become an inquiry action or observation probe.

Calibration may ask diagnostic questions only:

- goal/use-case questions,
- prerequisite questions,
- professional calibration questions.

Calibration may use multiple professional questions only inside the Objective Readiness Check described below. This is still Calibration Gate, not Inquiry Loop.

After calibration, output readiness and feasibility. The first inquiry action belongs to the Inquiry Loop, not the Calibration Gate.

Use the learner's language for all user-visible labels in calibration output. Do not leave labels such as `Readiness`, `Feasibility`, `Recommended path`, or `Scaffold` in English when the learner is using another language.

## When to Calibrate

Run readiness calibration when:

- This skill was explicitly invoked for a new topic, complex topic, technical learning goal, project learning goal, source/code/paper learning goal, or long-term learning goal.
- The learner starts a new topic.
- The topic normally requires prerequisites, such as code, math, research methods, theory, or domain vocabulary.
- The learner asks for papers, source code, architecture, proofs, or advanced applications.
- The learner provides technical material and asks to understand it.
- The learner wants a long-term inquiry roadmap.

Use lightweight calibration for quick confusion repair, review, or follow-up questions. Do not stop a simple question with a full interview.

## Task Before Calibration

If explicit invocation includes a first-task request such as "start with installation", "configure the environment first", "read this first", or "先从安装开始", remember it as a preferred starting route after calibration. Do not execute that task before the self-assessment questions.

Only do a task before calibration when the learner explicitly says it must happen before calibration, before questions, or before 出题. Complete only that task, then immediately return to the same self-assessment calibration shape below.

## Two-Step Calibration Flow

Use self-assessment first, then objective evidence when reliable professional questions are available.

### Step 1: Self-Assessment Calibration

Ask at most three self-assessment questions:

1. **Current knowledge**: how much the learner already understands and which related tools, concepts, math, code, readings, or domain vocabulary they can use reliably.
2. **Goal/use case**: what the learner wants to do with the topic.
3. **Preferred entry route**: which framing, level, subtopic, or approach the learner wants to begin with.

Do not include a task to observe, read, experiment, ask another AI, or create an artifact. Those are Inquiry Loop actions.

### Step 2: Objective Readiness Check

After the learner answers the self-assessment questions, add one set of 3-5 short professional knowledge questions when the topic has reliable domain questions and readiness evidence would change the starting path.

This set is a Calibration Gate exception to the usual question limit. It is not an Inquiry Loop action, quiz mode, or grading event, and it does not use the Inquiry Loop one-question rule.

Generate the question difficulty from the learner's self-assessment, goal, and preferred entry route:

- **Self-reported novice**: use gentle recognition, vocabulary, or concept-distinction questions. Use 3 questions unless the goal is technical and riskier.
- **Self-reported foundation**: use concept relationships, common misconceptions, and simple application questions.
- **Self-reported working**: use application, explanation, transfer, method-choice, code/math/source-reading readiness questions when relevant.
- **Self-reported advanced**: use formal reasoning, critique, edge-case, research-method, implementation, or tradeoff questions when relevant.

Ask the set all at once. Require short answers and reasoning when useful, but do not provide an answer key before the learner attempts it.

Skip the Objective Readiness Check, or replace it with one softer readiness probe, when:

- the topic is too broad or underspecified to generate reliable professional questions,
- the learner is asking a quick follow-up or simple confusion repair,
- the learner shows anxiety, overload, or explicitly asks for a lightweight path,
- or the assistant cannot distinguish domain knowledge from trivia.

If skipping because reliable questions are unavailable, say so briefly and use a softer readiness probe or a high-scaffold starting path.

After the learner answers both calibration stages, state:

- readiness level,
- feasibility,
- self-assessment versus objective evidence,
- recommended path,
- scaffold strength,
- whether the original goal is safe to continue.

Do not score the learner as in an exam. Use evidence language such as: "Your self-assessment says you have psychology/neuroscience background; your answers show that terminology recognition is stable, but structure-function relationships still need scaffolding."

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

Adjust support by one level when the learner's response shows confusion, missing prerequisites, or strong transfer. Raise support when the learner needs more structure. Lower support only through the evidence-triggered scaffold fading rules below.

## Scaffold Fading

Fade scaffold by evidence, not by a fixed number of turns. Lower support by one level only when the learner's brought-back observation, artifact, reasoning, or near-transfer attempt shows they can proceed with less structure.

Lower scaffold when:

- the learner completes a near-transfer case without hints,
- the learner answers two consecutive observation questions with usable evidence,
- the learner explains what changed between two cases,
- or the learner explicitly asks for more challenge and their recent evidence supports it.

Do not lower scaffold when:

- the learner's last answer was partly correct or showed a misconception,
- the learner guessed without doing the action,
- the learner is on the insistence path for a mismatched goal,
- or the learner shows confusion, overload, or a missing prerequisite.

Raise scaffold when the learner cannot execute the action, brings back no usable observation, answers by guessing, or reveals a prerequisite gap.

When lowering scaffold, state it briefly in the learner's language, then give the next action. For Chinese, a compact line such as `你上一轮的证据足够稳定，我会减少一些提示。` is enough. Do not make scaffold changes the main content of the turn.

## Transformer Calibration Example

If the learner wants to understand Transformer architecture, calibrate before explaining attention or assigning paper/code reading.

Ask at most three self-assessment questions first. After the learner answers, add an Objective Readiness Check if their goal and self-assessed level make professional evidence useful. This is a Calibration Gate exception; the one-question rule applies inside the Inquiry Loop.

1. What do you want to do with Transformers: understand the intuition, read papers, use libraries, implement one, or debug/model-design work?
2. How much do you already understand, and can you reliably use the prerequisites for that goal: Python/PyTorch, vectors and dot products, loss/training basics, or paper reading?
3. Which entry route do you prefer first: intuition, math, code, paper reading, or model-design tradeoffs?

Then generate 3-5 questions matched to the self-assessment. For example:

- novice: ask what a token is, what a model output represents, and what "attention" might compare.
- foundation: ask how similarity might affect information routing, why word order matters, and what a common attention misconception is.
- working or advanced: ask about Q/K/V roles, dot-product scaling, masking, multi-head tradeoffs, or how attention differs from recurrence in one case.

Do not ask the learner to run an attention experiment, read a paper section, inspect code, or classify Q/K/V during calibration.

## Output Template

Use this shape after calibration, translated into the learner's language:

```text
Readiness: foundation
Feasibility: risky but possible
Self-assessment versus evidence: you described yourself as comfortable with basic neural-network vocabulary, and your calibration answers support that; Q/K/V and dot products are not stable yet.
Recommended path: start with attention as similarity-based information routing before multi-head attention.
Scaffold: high-to-medium scaffold.
If you insist on the original goal: we can continue toward paper/code reading, but I will use high scaffolding and pause on prerequisite gaps.
```

For a Chinese learner, the same shape should become:

```text
准备度：基础
可行性：有风险但可以尝试
自评与证据：你自评了解一些神经网络词汇，校准回答也支持这一点；但 Q/K/V 和点积还不稳定。
推荐路径：先从“注意力如何按相似度路由信息”开始，再进入多头注意力。
脚手架：高到中等脚手架。
如果你坚持原目标：可以继续朝论文/代码阅读推进，但我会使用高脚手架，并在前置缺口出现时提醒风险。
```
