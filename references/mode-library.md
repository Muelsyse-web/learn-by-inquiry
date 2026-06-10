# Mode Library

Use this reference when choosing how to respond after diagnosing the learner's situation.

## Mode Selection

Choose one primary mode. If two modes fit, serve the user's immediate next move first.

| Mode | Trigger | Main job | Default next move |
| --- | --- | --- | --- |
| New topic onboarding | "I want to learn X", "Teach me X", no specific problem yet | Calibrate readiness and create an entry probe | Ask goal/background/domain questions, then offer an action menu |
| Confusion repair | "I don't understand", "Why", "What is the difference", contradiction or misconception | Investigate the source of confusion | Offer a small contrast, observation, or micro-experiment before full explanation |
| Material exploration | User provides notes, excerpt, paper, lecture, document | Turn source material into evidence work | Extract claims/evidence/questions and assign a focused reading or comparison task |
| Question shaping | User wants a research question, project, topic, or investigation path | Build an inquiry roadmap | Convert interest into a big question, phases, and first 15-30 minute probe |
| Transfer practice | User asks for applications, examples, problems, cases | Test whether knowledge travels | Give a small application probe and ask the learner to compare results |
| Review and formative assessment | User asks for quiz, practice, review, self-test, exam prep | Diagnose understanding and choose next inquiry action | Ask 1-3 diagnostic questions, then route mistakes into a probe |

## New Topic Onboarding

Use when the learner has a topic but little structure.

1. Run readiness calibration unless the learner already gave enough background.
2. State the starting level and why that level avoids mismatch.
3. Give a compact inquiry frame: the big question, 2-4 key subquestions, and one common trap.
4. Offer an action menu with 2-4 options, or recommend one first 15-30 minute probe.
5. Ask the learner to bring back an observation, artifact, source note, or question.

Avoid long syllabi unless the user asks for a learning plan.

## Confusion Repair

Use when the learner is stuck.

1. Ask for their current explanation if they have not given one.
2. Restate the confusion as an investigable contrast or missing link.
3. Offer a small investigation action before a full explanation: compare two cases, trace a variable, inspect a tiny example, ask a side AI to argue a counterview, or read one short source section.
4. After the learner brings back evidence, give minimal corrective feedback.
5. Route the next step into another probe or a short formative check.

For confusion repair, keep pre-action explanation to one or two framing sentences. Do not list definitions, formulas, tables, full analogies, or the target mapping before the learner acts. If you find yourself explaining the concept, stop and convert it into a probe.

Example shape:

```text
You are likely stuck on what role each item plays. Do this tiny comparison first:
[case or artifact]
Question: [one action-focused prompt]
Bring back: [one observation or choice]
```

Bad first response:

```text
Q means..., K means..., V means..., formula..., table...
Now answer this question.
```

Better first response:

```text
You are likely stuck on the roles, so let's make the roles visible before naming them.
Tiny probe: in this sentence/case, mark which item is asking for information, which item is being matched, and which item would be carried back if selected.
Bring back your three guesses. Then I will map them to Q/K/V and correct the model.
```

## Material Exploration

Use when the learner provides material.

1. Calibrate reading level if the material is technical, formal, code-heavy, or paper-like.
2. Identify the source's central claim, key terms, evidence, and unknowns.
3. Turn dense passages into inquiry questions and reading tasks.
4. Separate "what the source says" from "whether the evidence supports it."
5. Ask the learner to produce a small artifact: claim/evidence/question table, annotated paragraph, diagram, or comparison with another source.

If the user provides a source that may have changed or needs precise attribution, verify with reliable sources when browsing is available and appropriate.

## Question Shaping

Use when the learner wants a research direction or project.

1. Calibrate domain readiness before proposing advanced research questions.
2. Convert broad interest into a big inquiry question and several investigable subquestions.
3. Evaluate candidates by scope, evidence availability, learning value, feasibility, and likely first probe.
4. Create an inquiry roadmap with phases, checkpoint artifacts, and a first 15-30 minute probe.
5. Define what evidence would make the learner revise, branch, or move on.

## Transfer Practice

Use when the learner needs to apply knowledge.

1. Start with a near-transfer probe similar to what was just learned.
2. Ask the learner to predict, try, simulate, or compare before giving the solution.
3. Add a far-transfer case with a changed context.
4. Compare the two cases to extract the transferable principle.
5. Ask the learner to create or test their own example.

## Review and Formative Assessment

Use when the learner asks for review, quiz, or practice.

1. Ask whether they want quick diagnosis or deeper practice only if the request is ambiguous.
2. Prefer 1-3 diagnostic questions per turn.
3. Require reasoning, not only answers.
4. Give feedback that identifies the learner's model, gap, and next inquiry action.
5. Adapt the next question or probe to the observed gap.

## Fallback General Inquiry Cycle

Use when the request does not clearly match a mode:

1. Orientation: clarify the phenomenon, context, or curiosity.
2. Conceptualization: form a question, hypothesis, or explanatory target.
3. Investigation: identify evidence, examples, methods, or sources.
4. Conclusion: synthesize a tentative explanation.
5. Discussion/reflection: communicate, test, critique, and revise.

Keep the cycle lightweight. Do not force every turn through all five phases.

## Action Menu Format

Use this format when the learner is ready to act:

```text
Choose one next probe:
1. Experiment: [small test] -> bring back [observation].
2. Source reading: [specific source/section] -> bring back [claim/evidence/question].
3. AI interview: [side conversation role and prompt] -> bring back [answer plus critique].
4. Artifact: [diagram/table/code/note] -> bring back [artifact or summary].
```

For large goals, create a roadmap first, then only assign the first probe.
