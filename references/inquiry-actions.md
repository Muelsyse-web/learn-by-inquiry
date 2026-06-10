# Inquiry Actions

Use this reference whenever the learner needs a next step. Inquiry learning should produce actions and evidence, not only explanations and comprehension questions.

## Inquiry Loop Turn

Each Inquiry Loop turn gives one recommended action. Optional alternatives are allowed, but they must be shorter and secondary.

Use this format:

```text
Current subgoal: [state the active subgoal]
Recommended action: [one concrete action]
Why this action: [one sentence connecting action to subgoal]
Observation question: [one question, preferably answerable only after doing the action]
Bring back: [exact observation, artifact, quote, screenshot summary, code output, or note]
Optional alternatives: [short alternatives if the learner cannot do the recommended action]
```

Ask exactly one question. Do not combine an observation question with extra reflection questions.

For concept-confusion repair, the first action should expose one observable feature or one contrast only. Avoid multi-part actions that ask the learner to classify several roles, fill a whole table, or answer several hidden checks before the first feedback.

Default action size: 15-30 minutes. For large goals, create an inquiry roadmap with a big question and a sequence of actions that can span days, weeks, or months.

Before the first action, keep explanation to the minimum needed to understand the task. A good first response should make the learner do, observe, compare, create, or bring back evidence within a few sentences.

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

## Four Default Action Types

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
Read the "Scaled Dot-Product Attention" subsection of the original Transformer paper or an official tutorial.
Find one sentence, equation, or diagram element that seems central but confusing.
Bring back that one item.
```

### AI Interview

Use another AI conversation as an inquiry instrument, not as an authority. Assign it a role and require the learner to bring back its output for critique.

Environment-aware options:

- In Codex, if side conversations are available, suggest `/side`.
- In Claude Code, if side conversations are available, suggest `/btw`.
- In other AI tools, provide a copyable prompt.

Always include a return instruction:

```text
Bring back the other AI's answer and one part you distrust or do not understand.
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
First action: run or inspect one attention visualization and choose one case where the model attends somewhere surprising.
Bring back: that one observation.
```

## Avoid These Patterns

- "Here is the explanation; now answer a comprehension question."
- For confusion repair: definitions, equations, tables, or a full analogy before the first action.
- Giving away the mapping the action is supposed to uncover.
- Turning one action into several hidden concept checks before the learner gets feedback.
- "Go research this" without a concrete source, method, or output.
- Assigning papers or source code before readiness calibration.
- Using another AI as a shortcut answer generator.
- Giving a long roadmap with no first action.
