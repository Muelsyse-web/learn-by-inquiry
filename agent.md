# Agent Notes for `learn-by-inquiry`

Read this before modifying the skill from another chat window. These are user requirements established during the inquiry-loop design work.

## Core Learning Model

- Keep **Calibration Gate** and **Inquiry Loop** hard-separated.
- Calibration Gate only judges goal, readiness, prerequisites, and feasibility.
- Calibration Gate must not assign experiments, source readings, side AI interviews, artifact tasks, or observation probes.
- Calibration now uses a two-step structure when a new or complex topic needs readiness judgment: first ask at most three self-assessment questions, then ask one 3-5 question Objective Calibration Set when reliable professional questions are available.
- Generate Objective Calibration Set difficulty from the learner's self-rated level, learning goal, and preferred entry route.
- Do not assign readiness from self-assessment alone when reliable objective professional questions are available and the starting level matters.
- Objective Calibration Sets are not quizzes or Inquiry Loop actions. Do not score them; compare self-assessment with evidence and use that comparison to choose readiness, feasibility, path, and scaffold.
- Inquiry Loop starts only after calibration is complete or clearly unnecessary.
- Inquiry learning is not guided tutoring. Do not default to "explain first, then ask a comprehension question".
- The learner should do something, observe something, bring it back, then receive an explanation of why the result happened.

## Language and Labels

- Match the user's language in all user-visible labels.
- For Chinese users, do not output English labels such as `Readiness`, `Feasibility`, `Recommended path`, `Current subgoal`, `Recommended action`, `Observation question`, or `Bring back`.
- Use localized labels such as `准备度`, `可行性`, `推荐路径`, `当前小目标`, `推荐行动`, `观察问题`, and `带回内容`.
- Internal canonical names may remain English in documentation, but examples shown to learners must be localized.

## Inquiry Loop Format

- Each Inquiry Loop turn gives one recommended action, optional short alternatives, exactly one observation-first question, and one concrete bring-back item.
- Do not include `Why this action` before the learner acts.
- Do not explain why the action is useful, why the phenomenon happens, or what answer the action should reveal before the learner acts.
- Explanation happens after the learner reports an observation, difficulty, result, or artifact.
- After explaining the observed result, set the next action plan.

## Phase 1/2 Fusion Decisions

- `Worked Example` is a default action type, not a separate mode. It must still use the Inquiry Loop shell and end with one near-transfer observation question.
- Expert annotations inside a worked example explain completed example steps only. They must not become `Why this action` for the learner's next action.
- Self-regulation support is embedded inside action manuals and feedback. Do not add visible SRL sections or a second question.
- Scaffold fading is evidence-triggered. Lower support only when the learner's brought-back evidence shows usable transfer, and do not lower support on guessed, partly correct, or mismatched-goal responses.
- Feedback should internally cover goal direction, current evidence, and next action. Do not expose `feed-up/feed-back/feed-forward` labels or localized equivalents unless the learner asks for that framework.

## Phase 3 Productive Failure Decisions

- Productive Failure is a restricted advanced strategy, not a default action type and not a sixth item in the default action type list.
- It may be proactively suggested only when all entry conditions hold: `working` or `advanced` readiness, partial prior knowledge that can generate plausible attempts, and a 15-25 minute exploration with immediate consolidation.
- A Productive Failure suggestion must name the risk briefly and offer guided discovery or a worked example as the safer alternative.
- Productive Failure uses a two-turn protocol: bounded exploration first, then mandatory consolidation after the learner brings back attempts and difficulty evidence.
- Exit Productive Failure immediately when the learner cannot start, brings back blank or guess-only output, shows anxiety or overload, exceeds the timebox, or reveals a prerequisite gap.
- Downgrade to guided discovery when the learner has partial evidence but needs narrower structure; downgrade to a worked example when the learner needs an expert model before another attempt.

## Objective Readiness Calibration Decisions

- This improvement was added after the user noticed that self-rating alone can misjudge real level.
- Preserve the screenshot-style three-question self-assessment first: current knowledge, learning goal, and preferred entry route.
- After the learner answers those self-assessment questions, generate 3-5 short professional questions if the topic has stable domain checks.
- Ask the professional questions all at once, matched to the self-assessed level: novice gets gentle recognition or concept distinctions; foundation gets relationships and misconceptions; working/advanced gets application, transfer, method, formalism, source, code, or tradeoff questions when relevant.
- If the topic is too broad, the user wants a quick path, the learner shows overload, or only trivia questions are available, skip the set or replace it with one softer readiness probe and say why.
- When objective answers conflict with self-rating, objective evidence should guide readiness and scaffold.
- Forward-test Chinese onboarding after self-assessment: the next turn should show localized labels and 3-5 professional questions before final readiness.
- Forward-test mismatch: a learner self-rates as advanced but answers reveal prerequisite gaps; expected result is a kind downgrade with evidence, not a score.
- Forward-test no reliable questions: expected result is a brief explanation and a high-scaffold or softer readiness path, not invented trivia.

## Recommended Action Must Be a Micro-Manual

`Recommended action` is the main part of the response. It must not be a vague one-line instruction.

For novice/foundation learners, include:

- needed materials, tool, source, or fallback object,
- operational terms and drawing/reading/tool conventions,
- numbered steps,
- completion standard,
- stuck-point fallback,
- one observation question,
- one bring-back item,
- localized support line.

For working/advanced learners, the manual may be shorter, but still must say exactly what to use, what to do first, how to know it is complete, what to answer, and what to bring back.

Do not rely on a case library. Generate the action manual from the action type and the learner's readiness.

## Support Line and Operational Questions

- End every action suggestion with a localized support line matched to the action type.
- Chinese examples:
  - `如果你对这个实验的任何步骤有问题，可以随时问我。`
  - `如果你对这个画图任务的任何步骤有问题，可以随时问我。`
  - `如果你对这个阅读任务的任何步骤有问题，可以随时问我。`
- If the learner asks an operational question during an action, answer that question directly, then return to the current action step or observation question.
- Example: if the learner asks "光钟怎么画？", answer the drawing procedure, then return to: `从地面观察者看，运动光钟里光走的是竖直线、斜线，还是曲线？`
- Do not let operational questions derail the flow unless the learner explicitly asks to stop, switch goals, summarize, or receive direct explanation.

## Concept Confusion

- For specific concept confusions, do not give definition lists, formulas, tables, full analogies, or target mappings before the first action.
- Start with one narrow observable feature, contrast, or choice.
- Do not hide multiple conceptual checks inside one action.
- For Q/K/V confusion, do not ask the learner to identify all three roles at once. Start with one role-like observation, then explain after the learner brings back the observation.

## Mismatch and Loop Control

- If the learner's goal and readiness are severely mismatched, gently recommend a feasible path.
- If the learner insists on the original goal, continue with high scaffolding and explicit risk reminders.
- Do not cap a subgoal at a fixed number of rounds.
- Continue while the subgoal is unfinished and the path is producing new observation, evidence, artifact, or understanding.
- Redirect when the path stops producing progress, the action is not executable, a prerequisite gap blocks progress, or required external material is unavailable.

## Sub-Agent Practice

- For each nontrivial task, evaluate whether sub-agents improve efficiency or quality.
- Use sub-agents especially for independent literature review, forward tests, and read-only spec review.
- Keep tightly coupled documentation edits local when multiple agents would create conflicts.
- Do not rely on a sub-agent's success report without local verification.

## Verification Expectations

- Run the official skill validation after edits:

```bash
PYTHONPATH=/private/tmp/codex-pyyaml /Users/singsan/.cache/codex-runtimes/codex-primary-runtime/dependencies/python/bin/python3 /Users/singsan/.codex/skills/.system/skill-creator/scripts/quick_validate.py /Users/singsan/Documents/探究式学习/learn-by-inquiry
```

- Also scan for unfinished markers and obvious prompt-template regressions.
- Forward-test at least:
  - Chinese light-clock action manual,
  - Chinese "光钟怎么画？" operational question recovery,
  - Chinese Q/K/V concept confusion,
  - Chinese worked-example near-transfer flow,
  - scaffold fading after strong transfer evidence,
  - Productive Failure suggestion for a working or advanced learner with a safer alternative,
  - Productive Failure downgrade after cannot-start, blank, guess-only, anxious, timebox-exceeded, or prerequisite-gap evidence,
  - English response to ensure English labels still work.
