# Inquiry Loop State Machine Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Convert `learn-by-inquiry` into a two-stage state machine with hard-separated readiness calibration and an observation-first inquiry loop.

**Architecture:** Keep `SKILL.md` as the compact orchestration layer. Put detailed behavior in focused reference files: readiness calibration owns the non-inquiry gate, inquiry actions owns action planning and loop control, mode library routes scenarios into the gate or loop, and assessment patterns owns one-question feedback behavior.

**Tech Stack:** Codex skill markdown files, `agents/openai.yaml`, official `quick_validate.py`, git.

---

## File Map

- Modify `SKILL.md`: state machine overview, workflow, hard-separation rules, one-question rule, feasibility redirection, loop-control references.
- Modify `references/readiness-calibration.md`: make calibration strictly non-inquiry, add feasibility mismatch handling, update Transformer example so it asks diagnostic questions only.
- Modify `references/inquiry-actions.md`: change action menu behavior to one recommended action plus optional alternatives, add observation-first question rules, add loop-control continue/redirect/exit behavior.
- Modify `references/mode-library.md`: route each learning mode into either Calibration Gate or Inquiry Loop without mixing them.
- Modify `references/assessment-patterns.md`: reduce formative questions to one per turn and route responses into explanation plus next action.
- Do not modify `README.md` or `agents/openai.yaml`.

## Task 1: Update `SKILL.md` State Machine

**Files:**
- Modify: `SKILL.md`

- [ ] **Step 1: Inspect current `SKILL.md`**

Run:

```bash
sed -n '1,220p' SKILL.md
```

Expected: see current action-first inquiry instructions, `Core Workflow`, `Diagnosis Router`, `Coaching Rules`, and references to `readiness-calibration.md` and `inquiry-actions.md`.

- [ ] **Step 2: Replace the `Overview` section**

Replace the text under `## Overview` through the language default line with:

```markdown
Guide personal learning through a two-stage inquiry state machine:

1. **Calibration Gate**: judge the learner's goal, readiness, prerequisites, and feasibility. Do not assign inquiry actions in this phase.
2. **Inquiry Loop**: after calibration, guide learning through one recommended action, one observation-first question, explanation of the observed result, and the next action plan.

Distinguish inquiry learning from guided tutoring. Guided tutoring explains toward an answer; inquiry learning asks the learner to do something, observe something, bring it back, and then understand why it happened.

Default to English. If the user writes in another language, continue in that language unless they ask otherwise.
```

- [ ] **Step 3: Replace the `Core Workflow` numbered list**

Replace the current numbered list under `## Core Workflow` with:

```markdown
1. Infer the learner's language, topic, goal, current understanding, and likely inquiry stage.
2. Decide whether the request needs the **Calibration Gate** or can enter the **Inquiry Loop** directly.
3. If calibration is needed, ask only calibration questions. Do not assign experiments, readings, side AI interviews, artifact tasks, or observation probes during calibration.
4. After calibration, state readiness, feasibility, recommended path, and how to proceed if the learner insists on a risky original goal.
5. In the Inquiry Loop, give one recommended action and at most short optional alternatives.
6. Ask exactly one question. Prefer an observation-first question that can only be answered after doing the action. Use one thinking question only when no meaningful observation question is possible.
7. When the learner answers, first explain why their observation, result, difficulty, or artifact looks that way.
8. Set the next action plan based on the new information.
9. Continue while the subgoal is unfinished and the current path is producing new observation, evidence, artifact, or understanding. Redirect or exit when loop-control conditions say to.

Read `references/readiness-calibration.md` for Calibration Gate rules. Read `references/inquiry-actions.md` for Inquiry Loop structure, observation-first questions, optional alternatives, and loop control.
```

- [ ] **Step 4: Add a `State Machine Rules` section before `## Diagnosis Router`**

Insert:

```markdown
## State Machine Rules

- Keep Calibration Gate and Inquiry Loop hard-separated.
- Calibration Gate may ask goal, prerequisite, and professional diagnostic questions. It must not ask the learner to perform an inquiry action.
- Inquiry Loop may assign actions, observations, source reading, side AI interviews, experiments, and artifacts.
- If the learner's goal and readiness are severely mismatched, gently redirect to a feasible path. If the learner insists on the original goal, continue with high scaffolding and explicit risk reminders.
- Do not end inquiry after a fixed number of turns. Continue while the subgoal remains unfinished and the path remains productive.
- Redirect when an action is not executable, produces no useful observation, exposes a missing prerequisite, lacks required external material, or stops producing progress.
- Exit when the subgoal is complete, the learner asks to stop or summarize, the learner asks for direct explanation, the learner accepts a redirected goal, or required external conditions cannot be met.
```

- [ ] **Step 5: Rewrite conflicting `Coaching Rules` bullets**

In `## Coaching Rules`, ensure these exact bullets appear, replacing older conflicting bullets where needed:

```markdown
- Avoid guided-tutoring drift. The center of the turn should be what the learner can do and observe, not what the assistant can explain.
- During Calibration Gate, do not assign inquiry actions or observation probes.
- During Inquiry Loop, default to action before explanation.
- Use a strict explanation budget before the first action: at most a short framing sentence or two, unless the user explicitly asks for a direct explanation.
- For specific confusions, do not give definition lists, formulas, tables, full analogies, or the target mapping before the learner attempts the first probe.
- Ask only one question per turn inside the Inquiry Loop.
- If the learner guesses without performing the action, do not advance as if evidence was collected. Ask them to perform the action or replace it with an easier action.
```

Keep existing high-stakes-domain and reliable-source bullets.

- [ ] **Step 6: Verify `SKILL.md` references**

Run:

```bash
rg -n "Calibration Gate|Inquiry Loop|one question|fixed number|readiness-calibration|inquiry-actions" SKILL.md
```

Expected: output includes the new overview, workflow, state machine rules, and reference links.

## Task 2: Make `readiness-calibration.md` Strictly Non-Inquiry

**Files:**
- Modify: `references/readiness-calibration.md`

- [ ] **Step 1: Inspect current readiness reference**

Run:

```bash
sed -n '1,220p' references/readiness-calibration.md
```

Expected: see current calibration flow, readiness levels, scaffold control, Transformer example, and output template.

- [ ] **Step 2: Add a hard-separation rule after the opening paragraph**

Insert:

```markdown
## Hard Separation Rule

Calibration chooses a path; it does not start the inquiry. Do not assign experiments, source readings, side AI interviews, artifact tasks, or observation probes during calibration.

Calibration may ask diagnostic questions only:

- goal/use-case questions,
- prerequisite questions,
- professional calibration questions.

After calibration, output readiness and feasibility. The first inquiry action belongs to the Inquiry Loop, not the Calibration Gate.
```

- [ ] **Step 3: Replace `Default Calibration Flow`**

Replace the section with:

```markdown
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
```

- [ ] **Step 4: Add feasibility levels after readiness levels**

Insert:

```markdown
## Feasibility Levels

| Level | Meaning | Response |
| --- | --- | --- |
| `feasible` | The learner can pursue the stated goal at the requested depth. | Proceed to Inquiry Loop with normal scaffolding. |
| `risky but possible` | The learner can try the goal, but prerequisites are shaky. | Recommend a safer path; continue if the learner accepts or insists. |
| `currently mismatched` | The stated goal is far above current readiness. | Gently redirect to a feasible subgoal; if the learner insists, continue with high scaffolding and explicit risk reminders. |
```

- [ ] **Step 5: Add mismatch handling section**

Insert:

````markdown
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
````

- [ ] **Step 6: Replace the Transformer calibration example**

Replace the four-question example with:

```markdown
Ask at most three calibration questions:

1. What do you want to do with Transformers: understand the intuition, read papers, use libraries, implement one, or debug/model-design work?
2. Can you reliably use the prerequisites for that goal: Python/PyTorch, vectors and dot products, loss/training basics, or paper reading?
3. In your current words, what problem do you think attention is trying to solve?

Do not ask the learner to run an attention experiment, read a paper section, inspect code, or classify Q/K/V during calibration.
```

- [ ] **Step 7: Replace output template**

Replace the current output template with:

```text
Readiness: foundation
Feasibility: risky but possible
Why: you know basic neural-network vocabulary, but Q/K/V and dot products are not stable yet.
Recommended path: start with attention as similarity-based information routing before multi-head attention.
If you insist on the original goal: we can continue toward paper/code reading, but I will use high scaffolding and pause on prerequisite gaps.
```

- [ ] **Step 8: Verify non-inquiry calibration language**

Run:

```bash
rg -n "Do not assign|Feasibility|currently mismatched|If the learner insists|Do not ask the learner to run" references/readiness-calibration.md
```

Expected: all new rules appear.

## Task 3: Rewrite `inquiry-actions.md` Around the Inquiry Loop

**Files:**
- Modify: `references/inquiry-actions.md`

- [ ] **Step 1: Inspect current inquiry actions reference**

Run:

```bash
sed -n '1,240p' references/inquiry-actions.md
```

Expected: see action menu rule, four action types, AI interview guidance, roadmap, and avoid patterns.

- [ ] **Step 2: Replace `Action Menu Rule` with one-action loop rule**

Replace the section with:

````markdown
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
````

- [ ] **Step 3: Add observation-first question rules**

Insert after `Inquiry Loop Turn`:

````markdown
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
````

- [ ] **Step 4: Add after-answer behavior**

Insert:

```markdown
## After the Learner Answers

Respond in this order:

1. Identify the observation, evidence, artifact, or difficulty the learner brought back.
2. Explain why that result happened.
3. Decide whether the current subgoal is complete.
4. If incomplete and productive, set the next recommended action.
5. If unproductive, redirect by lowering scaffold, switching action type, returning to calibration, or proposing a feasible subgoal.
```

- [ ] **Step 5: Add loop control section**

Insert before `## Four Default Action Types`:

````markdown
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
````

- [ ] **Step 6: Update optional alternatives rule**

Find references to "menu of 2-4 actions" and replace them with "one recommended action plus short optional alternatives".

- [ ] **Step 7: Verify inquiry loop language**

Run:

```bash
rg -n "Inquiry Loop Turn|Observation-First|Ask exactly one question|After the Learner Answers|Loop Control|Never stop only" references/inquiry-actions.md
```

Expected: all new sections appear.

## Task 4: Route Modes Through Gate or Loop

**Files:**
- Modify: `references/mode-library.md`

- [ ] **Step 1: Inspect current mode library**

Run:

```bash
sed -n '1,240p' references/mode-library.md
```

Expected: see mode selection table and mode-specific workflows.

- [ ] **Step 2: Update the mode selection table**

Replace the table rows with:

```markdown
| New topic onboarding | "I want to learn X", "Teach me X", no specific problem yet | Calibration Gate | Ask calibration questions only; no inquiry action yet |
| Confusion repair | "I don't understand", "Why", "What is the difference" | Inquiry Loop, unless readiness is unclear | One recommended action or observation task before explanation |
| Material exploration | User provides notes, excerpt, paper, lecture, document | Calibration Gate for technical material; otherwise Inquiry Loop | Calibrate reading level or assign one source/artifact action |
| Question shaping | User wants a research question, project, topic, or investigation path | Calibration Gate, then Inquiry Loop | Check feasibility, then build roadmap with first action |
| Transfer practice | User asks for applications, examples, problems, cases | Inquiry Loop | One application action plus one observation-first question |
| Review and formative assessment | User asks for quiz, practice, review, self-test, exam prep | Inquiry Loop | One diagnostic question, then explanation and next action |
```

- [ ] **Step 3: Replace `New Topic Onboarding` workflow**

Use:

```markdown
1. Enter Calibration Gate.
2. Ask at most three calibration questions: goal, prerequisite, professional diagnostic.
3. Do not offer an action menu, experiment, reading task, side AI task, or artifact task during calibration.
4. Output readiness, feasibility, recommended path, and insistence path.
5. Start the Inquiry Loop only after the learner answers calibration.
```

- [ ] **Step 4: Replace `Confusion Repair` workflow**

Use:

```markdown
1. If the confusion depends on missing prerequisites, ask one calibration question first.
2. Otherwise enter Inquiry Loop immediately.
3. Give one recommended action or observation task.
4. Ask one observation-first question.
5. Do not reveal definitions, formulas, tables, full analogies, or target mappings before the learner attempts the action.
6. After the learner answers, explain why their observation occurred, then set the next action.
```

- [ ] **Step 5: Replace action menu format**

Replace the existing `Action Menu Format` with:

````markdown
## Inquiry Loop Format

```text
Current subgoal: [active subgoal]
Recommended action: [one action]
Why this action: [one sentence]
Observation question: [one question]
Bring back: [specific output]
Optional alternatives: [short fallback options]
```

Optional alternatives must not be longer or more prominent than the recommended action.
````

- [ ] **Step 6: Add loop-control note**

Insert near the fallback cycle:

```markdown
Do not cap loops by turn count. Continue while the subgoal is unfinished and the current path produces progress. Redirect when the path stops producing new observation, evidence, artifact, or understanding.
```

- [ ] **Step 7: Verify mode routing**

Run:

```bash
rg -n "Calibration Gate|Inquiry Loop|Ask calibration questions only|Do not cap loops|Optional alternatives" references/mode-library.md
```

Expected: table and workflows now explicitly route through the two states.

## Task 5: Reduce Assessment to One Question and Route to Action

**Files:**
- Modify: `references/assessment-patterns.md`

- [ ] **Step 1: Inspect current assessment patterns**

Run:

```bash
sed -n '1,220p' references/assessment-patterns.md
```

Expected: see default feedback loop, calibration vs quiz, prompt patterns, feedback templates, and quiz design rules.

- [ ] **Step 2: Replace `Default Feedback Loop`**

Use:

```markdown
## Default Feedback Loop

1. Ask one diagnostic or observation-first question.
2. Require the learner to bring back reasoning, observation, or artifact evidence when feasible.
3. Identify the useful part of the answer.
4. Explain why the observation, result, difficulty, or misconception occurred.
5. Name the gap or missing evidence.
6. Route the learner into one next recommended action.
```

- [ ] **Step 3: Update `Calibration vs Quiz`**

Add:

```markdown
Calibration questions belong to Calibration Gate and must not ask for inquiry actions. Quiz and formative questions belong to Inquiry Loop and must follow the one-question rule.
```

- [ ] **Step 4: Replace `Action Selection` prompt pattern**

Use:

```markdown
### Action Confirmation

"Recommended action: [one action]. If you cannot do this, choose one optional alternative: [short alternatives]."

Use when the learner needs agency without splitting attention across a large menu.
```

- [ ] **Step 5: Update quiz design rules**

Ensure these bullets appear:

```markdown
- Ask one question per turn unless the user explicitly requests a multi-question quiz.
- Do not provide answer keys before the learner attempts the question unless they request self-study mode.
- When the learner answers, explain why the answer or observation looks that way before assigning the next action.
- When a mistake reveals a missing prerequisite, return to Calibration Gate or assign a lower-level action.
```

- [ ] **Step 6: Verify one-question assessment language**

Run:

```bash
rg -n "Ask one|one-question|explain why|Calibration Gate|Action Confirmation" references/assessment-patterns.md
```

Expected: one-question rule and explanation-before-next-action behavior are present.

## Task 6: Validate the Skill

**Files:**
- No file changes unless validation finds an issue.

- [ ] **Step 1: Run official validator**

Run:

```bash
PYTHONPATH=/private/tmp/codex-pyyaml /Users/singsan/.cache/codex-runtimes/codex-primary-runtime/dependencies/python/bin/python3 /Users/singsan/.codex/skills/.system/skill-creator/scripts/quick_validate.py /Users/singsan/Documents/探究式学习/learn-by-inquiry
```

Expected:

```text
Skill is valid!
```

If PyYAML is unavailable, install it into `/private/tmp/codex-pyyaml` using the already-approved bundled Python pip command, then rerun the validator.

- [ ] **Step 2: Scan for incomplete markers**

Run:

```bash
rg -n "TO""DO|TB""D|\\[TO""DO\\]|FIX""ME|implement"" later|fill"" in details" .
```

Expected: no matches.

- [ ] **Step 3: Check changed files**

Run:

```bash
git status --short --branch
git diff --stat
```

Expected: only `SKILL.md`, `references/readiness-calibration.md`, `references/inquiry-actions.md`, `references/mode-library.md`, and `references/assessment-patterns.md` are modified.

## Task 7: Forward-Test Behavior

**Files:**
- No file changes unless tests reveal issues.

- [ ] **Step 1: Test Calibration Gate separation**

Dispatch a fresh subagent or manually simulate:

```text
Use $learn-by-inquiry at /Users/singsan/Documents/探究式学习/learn-by-inquiry to answer: I want to understand Transformer architecture.
```

Expected: response asks calibration questions only. It does not assign an experiment, reading, side AI, artifact, or observation task yet.

- [ ] **Step 2: Test severe mismatch handling**

Prompt:

```text
Use $learn-by-inquiry at /Users/singsan/Documents/探究式学习/learn-by-inquiry to answer: I want to read the Transformer paper and implement it, but I cannot read Python and do not know vectors.
```

Expected: response gently redirects to a feasible path and states that if the learner insists on the original goal, it can continue with high scaffolding and risk reminders.

- [ ] **Step 3: Test concept learning without guided tutoring**

Prompt:

```text
Use $learn-by-inquiry at /Users/singsan/Documents/探究式学习/learn-by-inquiry to answer in Chinese: 我不理解 Q/K/V 的区别。
```

Expected: response gives one concrete action or observation task first. It does not provide a definition list, formula, table, full analogy, or target mapping before the learner attempts it.

- [ ] **Step 4: Test observation-first loop**

Prompt:

```text
Use $learn-by-inquiry at /Users/singsan/Documents/探究式学习/learn-by-inquiry to answer: Calibration is complete. My subgoal is to see why attention helps pronoun resolution. Give me the next step.
```

Expected: response uses `Current subgoal`, `Recommended action`, `Why this action`, `Observation question`, `Bring back`, and optional alternatives. It asks one question only.

- [ ] **Step 5: Test no-progress redirect**

Prompt:

```text
Use $learn-by-inquiry at /Users/singsan/Documents/探究式学习/learn-by-inquiry to answer: I cannot do the recommended action because I do not have the paper, code, or visualization tool.
```

Expected: response does not repeat the same action. It lowers scaffolding, switches action type, returns to calibration, or proposes a feasible substitute.

- [ ] **Step 6: Patch any failures**

If a forward test violates expectations, patch the narrowest relevant instruction file and rerun:

```bash
PYTHONPATH=/private/tmp/codex-pyyaml /Users/singsan/.cache/codex-runtimes/codex-primary-runtime/dependencies/python/bin/python3 /Users/singsan/.codex/skills/.system/skill-creator/scripts/quick_validate.py /Users/singsan/Documents/探究式学习/learn-by-inquiry
```

Expected after each patch:

```text
Skill is valid!
```

## Task 8: Commit Implementation

**Files:**
- Commit modified skill files only.

- [ ] **Step 1: Review final status**

Run:

```bash
git status --short --branch
git diff --stat
```

Expected: only planned implementation files are modified.

- [ ] **Step 2: Stage implementation files**

Run:

```bash
git add SKILL.md references/readiness-calibration.md references/inquiry-actions.md references/mode-library.md references/assessment-patterns.md
```

Expected: files staged.

- [ ] **Step 3: Commit**

Run:

```bash
git commit -m "Implement inquiry loop state machine"
```

Expected: commit succeeds.

- [ ] **Step 4: Verify clean state**

Run:

```bash
git status --short --branch
git log --oneline --decorate -5
```

Expected: clean working tree and latest commit `Implement inquiry loop state machine`.

## Self-Review Checklist

- Spec coverage: Tasks 1-5 implement all design sections; Tasks 6-7 verify all test scenarios; Task 8 commits the implementation.
- Incomplete-marker scan: this plan intentionally contains no unfinished-marker words or incomplete steps.
- Type consistency: the state names are consistently `Calibration Gate` and `Inquiry Loop`; feasibility levels are consistently `feasible`, `risky but possible`, and `currently mismatched`; readiness levels are consistently `novice`, `foundation`, `working`, and `advanced`.
