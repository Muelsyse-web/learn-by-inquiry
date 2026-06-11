# Mode Library

Use this reference when choosing how to respond after diagnosing the learner's situation.

## Mode Selection

Choose one primary mode. If two modes fit, serve the user's immediate next move first.

| Mode | Trigger | Main job | Default next move |
| --- | --- | --- | --- |
| New topic onboarding | "I want to learn X", "Teach me X", no specific problem yet | Calibration Gate | Ask self-assessment questions, then objective professional questions when available; no inquiry action yet |
| Confusion repair | "I don't understand", "Why", "What is the difference" | Inquiry Loop, unless readiness is unclear | One recommended action or observation task before explanation |
| Material exploration | User provides notes, excerpt, paper, lecture, document | Calibration Gate for technical material; otherwise Inquiry Loop | Calibrate reading level with self-assessment and objective checks when available, or assign one source/artifact action |
| Question shaping | User wants a research question, project, topic, or investigation path | Calibration Gate, then Inquiry Loop | Check feasibility with objective evidence when useful, then build roadmap with first action |
| Transfer practice | User asks for applications, examples, problems, cases | Inquiry Loop | One application action plus one observation-first question |
| Review and formative assessment | User asks for quiz, practice, review, self-test, exam prep | Inquiry Loop | One diagnostic question, then explanation and next action |

## New Topic Onboarding

Use when the learner has a topic but little structure.

1. Enter Calibration Gate.
2. Ask at most three self-assessment calibration questions: current knowledge, goal, and preferred entry route.
3. After the learner answers, ask one Objective Calibration Set of 3-5 professional questions when reliable domain checks are available. Match difficulty to the learner's self-rated level, goal, and preferred entry route.
4. If reliable professional questions are unavailable, say so briefly and use one softer readiness probe or a high-scaffold starting path.
5. Do not offer an action menu, experiment, reading task, side AI task, or artifact task during calibration.
6. Output readiness, feasibility, self-assessment versus evidence, recommended path, scaffold strength, and insistence path.
7. Start the Inquiry Loop only after the learner answers calibration.

Avoid long syllabi unless the user asks for a learning plan.

## Confusion Repair

Use when the learner is stuck.

1. If the confusion depends on missing prerequisites, ask one calibration question first.
2. Otherwise enter Inquiry Loop immediately.
3. Give one recommended action as a concrete micro-manual or observation task.
4. Ask one observation-first question.
5. Do not reveal definitions, formulas, tables, full analogies, or target mappings before the learner attempts the action.
6. After the learner answers, explain why their observation occurred, then set the next action.

For confusion repair, keep pre-action explanation to one or two framing sentences. Do not list definitions, formulas, tables, full analogies, or the target mapping before the learner acts. If you find yourself explaining the concept, stop and convert it into an action.

Example shape:

```text
You are likely stuck on what role each item plays. Do this tiny action first:
[localized recommended action micro-manual for one case or artifact]
[localized observation question: one observation-first prompt]
[localized bring-back instruction: one observation or choice]
[localized support line]
```

Bad first response:

```text
Q means..., K means..., V means..., formula..., table...
Now answer this question.
```

Better first response:

```text
你可能卡在“角色”上，所以先别急着背 Q/K/V。我们先观察一个角色感。

当前小目标：只观察“谁在寻找线索”，暂时不命名 Q/K/V。

推荐行动：
需要材料：不需要工具。
操作词说明：`it` 是指代不清的词；前面的某个词可能是判断它指谁的线索。
步骤：
1. 读这个句子："The animal did not cross the street because it was too tired."
2. 只关注 `it`。
3. 看 `it` 前面的词。
4. 选一个最能帮助判断 `it` 指代谁的词。
完成标准：你只选出了一个词。
如果卡住：就在 `animal` 和 `street` 之间选一个；不要尝试一次解释所有角色。
观察问题：你选的是哪个词？
带回内容：带回那个词和你使用的线索。然后我会解释这个线索为什么重要，并设置下一步行动。
如果你对这个观察任务的任何步骤有问题，可以随时问我。
```

For Q/K/V confusion specifically, do not ask the learner to identify all three roles in the first turn. Start with only one role-like observation, such as which word, token, or vector is seeking information in a tiny case. Explain the mapping only after the learner brings back that first choice.

## Material Exploration

Use when the learner provides material.

1. If the material is technical, formal, code-heavy, or paper-like, enter Calibration Gate first.
2. During Calibration Gate, ask reading-level self-assessment first. If the material's domain has stable professional checks, add one Objective Calibration Set before judging readiness.
3. Stop after outputting readiness, feasibility, self-assessment versus evidence, recommended path, scaffold strength, and insistence path.
4. Start the Inquiry Loop only after the learner answers calibration or when calibration is clearly unnecessary.
5. In the Inquiry Loop, assign one source/artifact action.
6. Ask one observation-first question about the material, such as one claim, one piece of evidence, or one confusing line.

If the user provides a source that may have changed or needs precise attribution, verify with reliable sources when browsing is available and appropriate.

## Question Shaping

Use when the learner wants a research direction or project.

1. Calibrate domain readiness before proposing advanced research questions. After self-assessment, use an Objective Calibration Set when reliable professional questions are available and the project level depends on prerequisite knowledge.
2. Convert broad interest into a big inquiry question and several investigable subquestions.
3. Evaluate candidates by scope, evidence availability, learning value, feasibility, and likely first action.
4. Create an inquiry roadmap with phases, checkpoint artifacts, and a first 15-30 minute action.
5. Define what evidence would make the learner revise, branch, or move on.

## Transfer Practice

Use when the learner needs to apply knowledge.

1. Start with a near-transfer action similar to what was just learned.
2. Ask the learner to predict, try, simulate, or compare before giving the solution.
3. Add a far-transfer case with a changed context.
4. Compare the two cases to extract the transferable principle.
5. Ask the learner to create or test their own example.

## Review and Formative Assessment

Use when the learner asks for review, quiz, or practice.

1. Ask whether they want quick diagnosis or deeper practice only if the request is ambiguous.
2. Ask one diagnostic question per turn unless the user explicitly requests a multi-question quiz.
3. Require reasoning, not only answers.
4. Give feedback that identifies the learner's model, gap, and next inquiry action.
5. Adapt the next question or action to the observed gap.

## Fallback General Inquiry Cycle

Use when the request does not clearly match a mode:

1. Orientation: clarify the phenomenon, context, or curiosity.
2. Conceptualization: form a question, hypothesis, or explanatory target.
3. Investigation: identify evidence, examples, methods, or sources.
4. Conclusion: synthesize a tentative explanation.
5. Discussion/reflection: communicate, test, critique, and revise.

Keep the cycle lightweight. Do not force every turn through all five phases.

Do not cap loops by turn count. Continue while the subgoal is unfinished and the current path produces progress. Redirect when the path stops producing new observation, evidence, artifact, or understanding.

## Inquiry Loop Format

Use this format when the learner is ready to act:

```text
Current subgoal: [active subgoal]
Recommended action: [one concrete micro-manual]
Observation question: [one question]
Bring back: [specific output]
Optional alternatives: [short fallback options]
[Support line matched to action type]
```

Translate every label in this format into the learner's language; do not copy the English placeholders into non-English replies.
Optional alternatives must not be longer or more prominent than the recommended action.

For large goals, create a roadmap first, then only assign the first action.
