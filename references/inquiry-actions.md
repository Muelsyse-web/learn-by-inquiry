# Inquiry Actions

Use this reference whenever the learner needs a next step. Inquiry learning should produce actions and evidence, not only explanations and comprehension questions.

## Action Menu Rule

Offer either one recommended next probe or a menu of 2-4 actions. Each action must include:

- **Goal**: what the action investigates.
- **Task**: exact steps the learner should perform.
- **Expected output**: what they should create, observe, compare, or decide.
- **Bring back**: what to paste, summarize, screenshot, or report in the main conversation.

Default probe size: 15-30 minutes. For large goals, create an inquiry roadmap with a big question and a sequence of probes that can span days, weeks, or months.

Before the first action, keep explanation to the minimum needed to understand the task. A good first response should make the learner do, observe, compare, create, or bring back evidence within a few sentences.

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
Write down: (1) what query/key/value each represent, (2) one equation or diagram you do not understand, (3) one claim you could test with a toy example.
Bring back those three notes.
```

### AI Interview

Use another AI conversation as an inquiry instrument, not as an authority. Assign it a role and require the learner to bring back its output for critique.

Environment-aware options:

- In Codex, if side conversations are available, suggest `/side`.
- In Claude Code, if side conversations are available, suggest `/btw`.
- In other AI tools, provide a copyable prompt.

Always include a return instruction:

```text
Bring back the other AI's answer, plus one part that felt convincing and one part you distrust or do not understand.
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

The artifact should be small enough to finish or draft in one probe.

## Inquiry Roadmap

Use for large goals such as "learn Transformers over a month" or "study BCI for a year."

Create:

1. A big inquiry question.
2. 3-6 phases.
3. A first 15-30 minute probe.
4. A checkpoint artifact for each phase.
5. A rule for deciding whether to go deeper, branch, or move on.

Example shape:

```text
Big question: How does attention let a model route information?
Phase 1: observe attention behavior with toy examples.
Phase 2: connect observation to Q/K/V and dot products.
Phase 3: inspect code or tensor shapes.
Phase 4: compare single-head and multi-head behavior.
First probe: run or inspect one attention visualization and record two cases where the model attends differently.
Bring back: your two observations and one hypothesis.
```

## Avoid These Patterns

- "Here is the explanation; now answer a comprehension question."
- For confusion repair: definitions, equations, tables, or a full analogy before the first probe.
- Giving away the mapping the probe is supposed to uncover.
- "Go research this" without a concrete source, method, or output.
- Assigning papers or source code before readiness calibration.
- Using another AI as a shortcut answer generator.
- Giving a long roadmap with no first probe.
