# Inquiry Actions

Use this reference whenever the learner needs a next step. Inquiry learning should produce actions and evidence, not only explanations and comprehension questions.

## Inquiry Loop Turn

Each Inquiry Loop turn gives one recommended action as a concrete micro-manual. Optional alternatives are allowed, but they must be shorter and secondary.

Use the learner's language for all user-visible labels. The English labels below are canonical placeholders, not text to copy when the learner is using another language. Use the local equivalent of this format:

```text
Current subgoal: [state the active subgoal]
Recommended action: [a concrete micro-manual with materials, term/operation notes, numbered steps, completion standard, and stuck points]
Observation question: [one question, preferably answerable only after doing the action]
Bring back: [exact observation, artifact, quote, screenshot summary, code output, or note]
Optional alternatives: [short alternatives if the learner cannot do the recommended action]
[Support line: If you have any question about this action type, you can ask me anytime.]
```

Chinese label equivalents:

```text
当前小目标
推荐行动
观察问题
带回内容
可选替代
如果你对这个[行动类型]的任何步骤有问题，可以随时问我。
```

Ask exactly one question. Do not combine an observation question with extra reflection questions.

For concept-confusion repair, the first action should expose one observable feature or one contrast only. Avoid multi-part actions that ask the learner to classify several roles, fill a whole table, or answer several hidden checks before the first feedback.

Default action size: 15-30 minutes. For large goals, create an inquiry roadmap with a big question and a sequence of actions that can span days, weeks, or months.

Before an action, explain only operational knowledge needed to do the action. Do not explain why the action will reveal the target concept, why the phenomenon occurs, or the answer the action is meant to uncover. A good first response makes the learner do, observe, compare, create, or bring back evidence without needing to invent the method.

## Action Manual Generator

Convert every recommended action into a micro-manual. Do not rely on saved examples to cover future topics; generate the manual from the action type and the learner's readiness.

1. Identify the action type: experiment, drawing/diagram, observation, comparison, source reading, code/tool run, AI interview, artifact production, or worked example.
2. Choose the smallest observable object: one path, one output difference, one source claim, one confusing line, one code result, one diagram feature, or one artifact decision.
3. Explain operational terms only. Define words such as "light clock", "ground observer", "source section", "run cell", or "screenshot summary" when needed, but do not explain the target concept's cause before the learner acts.
4. Embed self-regulation only as operational support, not as an extra question: a short planning note may tell the learner to note an expected result in their own words; monitoring belongs in stuck-point support; reflection belongs after the learner brings back evidence.
5. Write numbered steps specific enough that the learner knows the first mark, click, line to read, variable to change, or sentence to copy.
6. Add a completion standard: how the learner knows the action is finished.
7. Add stuck-point support: what to do if they cannot draw, cannot access a source, cannot run code, do not understand an operation, or notice that the result differs from their expectation.
8. End with one localized support line that matches the action type, such as "If you have any question about this drawing task, you can ask me anytime."

Adjust detail by readiness:

- `novice` and `foundation`: include materials, term/operation notes, 4-7 small steps, a completion standard, and a stuck-point fallback.
- `working`: include materials only when needed, 3-5 steps, and a clear completion standard.
- `advanced`: keep the manual concise, but still state the exact object, method, output, and bring-back item.

## Anti-Abstraction Check

Before sending a recommended action, check:

- Does the learner know what materials or tool to use?
- Does the learner know the first physical mark, click, command, source section, or sentence to inspect?
- Are invented or technical terms explained operationally?
- Is there exactly one observation question?
- Is `Bring back` a concrete output?
- Is there no `Why this action` or cause explanation before the learner acts?
- Is the support line localized and matched to the action type?

If any answer is no, make the recommended action more concrete before sending.

## Handling Learner Questions During an Action

If the learner asks an operational question about the current action, answer it directly and briefly, then return to the current action step or observation question.

Example pattern:

```text
[Answer the operational question.]
Now return to the current observation question: [repeat the one observation question].
```

Localize the recovery sentence too. For Chinese:

```text
[回答操作问题。]
现在回到刚才的观察问题：[重复那个观察问题]。
```

Do not switch to a different lesson, explanation, or goal unless the learner explicitly asks to stop, switch goals, summarize, or receive a direct explanation.

## Observation-First Questions

Prefer questions that require the learner to do the action first.

Good:

```text
After changing the prompt wording, which output changed: factual detail, tone, or structure?
```

```text
After reading the source section, what claim does the author make that is supported by an equation, diagram, or example?
```

Use a thinking question only when the action cannot produce an observable fact:

```text
Which assumption would make this explanation fail?
```

If the learner answers by guessing and did not perform the action, do not treat the answer as evidence.

## After the Learner Answers

Respond in this order:

1. Identify the observation, evidence, artifact, or difficulty the learner brought back.
2. Explain why that result happened.
3. Decide whether the current subgoal is complete.
4. If incomplete and productive, set the next recommended action.
5. If unproductive, redirect by lowering scaffold, switching action type, returning to calibration, or proposing a feasible subgoal.

## Loop Control

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

Exit when:

- the subgoal is complete,
- the learner asks to stop, summarize, switch goals, or receive direct explanation,
- the learner accepts a redirected goal,
- required external conditions cannot be met.

Never stop only because a fixed number of turns has passed.

## Default Action Types

### Worked Example

Use when a novice or foundation learner needs to see a small expert model before attempting a near-transfer action. A worked example is still an Inquiry Loop action: it must keep one current subgoal, one recommended action, one observation question, one bring-back item, optional short alternatives, and a localized support line.

The worked example may include brief expert annotations for steps that are already completed inside the example. This is not `Why this action`: annotations explain the finished example, not the learner's upcoming near-transfer action, and they must not reveal the answer to the learner's observation question.

Use this shape inside `Recommended action`; keep the shell-level `Observation question` and `Bring back` outside this block:

```text
Worked problem: [one small completed case]
Expert solution: [numbered steps with brief annotations for the completed case]
Key principle: [one operational sentence the learner can reuse]
Your turn: [one near-transfer case with the same structure]
Completion standard: [how the learner knows the near-transfer attempt is finished]
If stuck: [which completed step to imitate or which partial step to fill]
```

After the worked-example action, use the normal Inquiry Loop shell for the one observation question and one bring-back item. Do not create a second observation-question slot inside the worked example.

Fade worked examples by evidence, not by a fixed round count. If the learner brings back a correct near-transfer attempt with usable reasoning, move from full worked example to completion example or independent practice. If the learner guesses, copies without reasoning, or shows a misconception, keep or raise scaffold.

### Experiment

Use for questions that can be tested, simulated, compared, or observed.

Examples:

- Change one variable and predict the result.
- Run two prompts, code snippets, examples, or cases and compare outputs.
- Build a tiny simulation or table.
- Create a before/after observation.

Keep the design small: hypothesis, variable, observation, result, interpretation.

### Source Reading

Use when reliable material can anchor the inquiry.

Prefer official, academic, or stable sources. If the topic may have changed, verify sources with browsing before recommending exact links. Give a specific reading target, not a vague "read more."

Good source-reading task:

```text
Current subgoal: identify one concrete source item to investigate.
Recommended action:
Source: use the "Scaled Dot-Product Attention" subsection of the original Transformer paper or an official tutorial.
Operation note: a subsection is only the part under that heading, not the whole paper.
Steps:
1. Open the source and find the exact subsection heading.
2. Read only the first screen or first 2-4 paragraphs under that heading.
3. Mark one sentence, equation, or diagram element that seems central but confusing.
4. Copy that one item, or summarize it closely if copying is not possible.
Completion standard: you have one identifiable source item, not a whole page of notes.
If stuck: choose the first equation or diagram label you do not understand.
Observation question: Which one source item did you choose?
Bring back: that one item exactly enough that I can identify it.
If you have any question about this reading task, you can ask me anytime.
```

### AI Interview

Use another AI conversation as an inquiry instrument, not as an authority. Assign it a role and require the learner to bring back its output for critique.

Environment-aware options:

- In Codex, if side conversations are available, suggest `/side`.
- In Claude Code, if side conversations are available, suggest `/btw`.
- In other AI tools, provide a copyable prompt.

For AI interviews, still provide a full micro-manual. Do not only give a copyable prompt.

```text
Current subgoal: use another AI as an inquiry instrument, not as an answer authority.
Recommended action:
Tool/material: a side AI conversation, `/side` in Codex if available, `/btw` in Claude Code if available, or any other AI chat.
Operation note: the side AI is a source of claims to inspect. Do not accept its answer as true until you bring it back here.
Steps:
1. Open the side AI conversation or other AI tool.
2. Paste the role prompt below.
3. Ask it to propose one test, source, or distinction for [topic/question].
4. Copy its concise answer.
5. Mark one sentence you distrust or do not understand.
Completion standard: you have the side AI's answer plus one marked sentence.
If stuck: skip the side tool and ask me for a copyable prompt adapted to your topic.
Observation question: Which sentence from the side AI do you distrust or not understand?
Bring back: the side AI's answer and that one sentence.
If you have any question about this AI interview task, you can ask me anytime.
```

Copyable prompt template:

```text
You are my inquiry partner, not my tutor. Help me investigate [topic/question].
Role: [skeptic/explainer/opponent/source comparator/code reviewer].
Do not give a final answer immediately. Ask what evidence would distinguish competing explanations, propose one small test or reading task, and point out possible misconceptions.
Return a concise summary I can bring back to my main learning conversation.
```

### Artifact Production

Use when the learner can make something to externalize understanding.

Examples:

- Diagram or concept map.
- Question tree.
- Misconception table.
- Annotated code snippet.
- Mini-project.
- Reading notes with claims/evidence/questions.
- Comparison table.

The artifact should be small enough to finish or draft in one action.

## Inquiry Roadmap

Use for large goals such as "learn Transformers over a month" or "study BCI for a year."

Create:

1. A big inquiry question.
2. 3-6 phases.
3. A first 15-30 minute action.
4. A checkpoint artifact for each phase.
5. A rule for deciding whether to go deeper, branch, or move on.

Example shape:

```text
Big question: How does attention let a model route information?
Phase 1: observe attention behavior with toy examples.
Phase 2: connect observation to Q/K/V and dot products.
Phase 3: inspect code or tensor shapes.
Phase 4: compare single-head and multi-head behavior.
First action manual:
Source/tool: no external website needed. Use this toy attention table:
`it -> animal: 0.70`, `it -> street: 0.20`, `it -> tired: 0.10`.
Operation note: read `A -> B: 0.70` as "token A is mostly looking at token B"; the larger number is the stronger attention target.
Steps:
1. Look only at the three rows for `it`.
2. Find the largest number.
3. Record which token has the largest number.
4. Decide whether that target is surprising or expected.
Completion standard: you have one surprising token-target pair.
If stuck: choose the row with `0.70`.
Observation question: Which token does `it` attend to most strongly?
Bring back: the token you chose and whether it surprised you.
If you have any question about this observation task, you can ask me anytime.
```

## Avoid These Patterns

- "Here is the explanation; now answer a comprehension question."
- `Why this action` before the learner has acted.
- For confusion repair: definitions, equations, tables, or a full analogy before the first action.
- Giving away the mapping the action is supposed to uncover.
- Turning one action into several hidden concept checks before the learner gets feedback.
- "Go research this" without a concrete source, method, or output.
- "Draw/observe/compare X" without saying how to draw, observe, or compare it.
- Assigning papers or source code before readiness calibration.
- Using another AI as a shortcut answer generator.
- Giving a long roadmap with no first action.
