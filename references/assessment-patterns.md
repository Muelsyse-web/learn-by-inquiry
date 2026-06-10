# Assessment Patterns

Use this reference when creating formative checks, quizzes, practice tasks, and feedback.

## Default Feedback Loop

1. In Calibration Gate, ask one diagnostic question. In Inquiry Loop, assign one action manual and one observation-first question.
2. Require the learner to bring back reasoning, observation, or artifact evidence when feasible.
3. Identify the useful part of the answer.
4. Explain why the observation, result, difficulty, or misconception occurred.
5. Name the gap or missing evidence.
6. Route the learner into one next recommended action as a concrete micro-manual.

## Calibration vs Quiz

Calibration questions choose a starting point. Quiz questions check learning after practice. Do not treat calibration as grading.

Calibration questions belong to Calibration Gate and must not ask for inquiry actions. Quiz and formative questions belong to Inquiry Loop and must follow the one-question rule.

Use calibration questions to ask:

- What does the learner want to do with the topic?
- Which prerequisites can they actually use?
- Can they explain a core idea in their own words?
- Can they read the needed code, math, source, or terminology?

After calibration, state the readiness level and feasibility instead of giving a score. The first inquiry action belongs to the Inquiry Loop.

## Prompt Patterns

Use these patterns as design intents for an Inquiry Loop turn, not as text templates. Never output a compact `Action: ... Question: ...` pair as the full action. For each pattern, write a localized recommended action manual with materials or source, operation notes, numbered steps, completion standard, stuck-point fallback, one observation question, one bring-back item, and the action-type support line.

### Prediction

Manual goal: have the learner change or compare one condition and observe one result.

Use for causal models, systems, math, science, programming, economics, and psychology.

### Explain Why

Manual goal: have the learner inspect one example, case, result, or artifact detail before explaining why it works.

Use for conceptual understanding and circular-definition detection.

### Compare and Contrast

Manual goal: have the learner compare A and B in one concrete case and identify the difference that changes the outcome.

Use for adjacent concepts, common misconceptions, theories, and methods.

### Evidence Check

Manual goal: have the learner inspect one observation, example, or source and extract one piece of evidence.

Use for research literacy, critical thinking, and source evaluation.

### Transfer Case

Manual goal: have the learner apply the idea to one new case and observe one changed result.

Use after an explanation or worked example.

### Misconception Probe

Manual goal: have the learner test one plausible misconception against one case and find the contradiction.

Use when a topic has a known trap.

### Self-Rating With Evidence

Manual goal: have the learner review one answer or artifact and identify one piece of evidence that supports their confidence rating.

Use for metacognition and deciding the next support level.

### Readiness Probe

"To choose the right starting point, answer this one calibration question: [question]."

Use before new topics, complex concepts, papers, code, and long-term roadmaps.

### Action Confirmation

Use only after the micro-manual is already concrete. Ask whether the learner can do the action now, or offer a shorter alternative.

Use when the learner needs agency without splitting attention across a large menu.

## Feedback Templates

These are feedback intents, not final response templates. After using any feedback intent, immediately output the next localized action manual with materials/source, operation notes, numbered steps, completion standard, stuck-point fallback, one observation question, one bring-back item, and support line. Do not end with a bare question, a compact check, or the phrase "provide a manual" without actually providing it.

### Mostly Correct

Feedback intent: affirm the specific correct part, name the refinement, then immediately output a concrete action manual to test that refinement in one case, artifact, or source.

### Partly Correct

Feedback intent: identify the productive idea, name the gap, give one compact rule, then immediately output a concrete action manual that lets the learner observe the rule in one case.

### Misconception

Feedback intent: explain why the misconception is tempting, name the contradiction or missing condition, give one distinction, then immediately output a concrete action manual for applying the distinction to one new case.

### Insufficient Evidence

Feedback intent: explain why the evidence only supports a weaker claim, then immediately output a concrete action manual that lets the learner observe or compare one piece of evidence for the stronger claim.

### Start Lower

Feedback intent: explain the prerequisite bottleneck and why starting lower helps, then immediately output a localized first action manual with one observation question and one bring-back item.

### Ready To Proceed

Feedback intent: state that the answer shows enough readiness, name the action type, then immediately output a localized first action manual with one observation question and one bring-back item.

### Skip Ahead

Feedback intent: state that the learner can skip the basic explanation, then immediately output a localized concrete action manual for an experiment, source reading, AI interview, or artifact task, with one observation question, one bring-back item, and the action-type support line.

## Quiz Design Rules

- In Inquiry Loop review, assign one action manual with one observation question per turn unless the user explicitly requests a multi-question quiz.
- In an explicitly requested multi-question quiz, mix recall, reasoning, and transfer checks when appropriate.
- Do not provide answer keys before the learner attempts the questions unless they request self-study mode.
- Avoid trick questions unless the goal is misconception diagnosis.
- For exam preparation, ask whether to use exam-like format, but keep feedback formative.
- When the learner answers, explain why the answer or observation looks that way before assigning the next action.
- When the learner answers, adapt the next action manual or, for explicit quiz mode only, the next question rather than continuing a fixed quiz.
- When a mistake reveals a missing prerequisite, return to Calibration Gate or assign a lower-level action.
