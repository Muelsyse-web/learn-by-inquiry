# Learn by Inquiry

`learn-by-inquiry` is a Codex skill for action-first inquiry-based learning. When explicitly invoked through `/`, `$learn-by-inquiry`, or a clear request for inquiry-based learning, it helps self-directed learners calibrate their readiness, investigate questions, and learn through concrete actions such as experiments, source reading, AI interviews, artifact production, and formative feedback.

The skill is designed to avoid the common drift from inquiry learning into guided tutoring. Instead of defaulting to "explain first, then ask questions", it helps the learner do something that produces evidence, observations, or an artifact.

## What It Does

- Calibrates learner readiness before new or complex topics.
- Checks prerequisites before assigning code, math, papers, or advanced terminology.
- Routes learning requests into modes such as new-topic onboarding, confusion repair, material exploration, question shaping, transfer practice, and formative assessment.
- Offers concrete inquiry action manuals with observation-first questions.
- Builds long-term inquiry roadmaps from large goals, broken into 15-30 minute probes.
- Supports side AI interviews through Codex `/side`, Claude Code `/btw`, or copyable prompts for other AI tools.
- Offers an optional visual companion branch for high-value visual actions such as experiments, observation flows, diagrams, and step sequences.

## Install

Clone or copy this folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Muelsyse-web/learn-by-inquiry.git ~/.codex/skills/learn-by-inquiry
```

If you are developing the skill locally, you can symlink it instead:

```bash
ln -s /path/to/learn-by-inquiry ~/.codex/skills/learn-by-inquiry
```

Restart Codex or start a new conversation so the skill list refreshes.

## Usage

Invoke the skill explicitly through `/` or `$learn-by-inquiry`. Ordinary learning prompts such as "teach me X", "explain X", "review X", or "help me install X" are not meant to trigger this skill unless you explicitly ask for inquiry-based learning.

```text
$learn-by-inquiry I want to understand Transformer architecture.
```

Non-English learner example:

```text
$learn-by-inquiry I want to learn Transformer, but my coding foundation is weak. Please respond in my language.
```

Confusion repair example:

```text
$learn-by-inquiry I do not understand the difference between Q/K/V.
```

Long-term inquiry example:

```text
$learn-by-inquiry Help me design a three-month inquiry roadmap for learning brain-computer interfaces.
```

Composite request example:

```text
$learn-by-inquiry 我想通过探究式学习来学习 LangGraph，先从安装开始
```

The skill should still start with readiness calibration. "先从安装开始" is treated as a preferred route after calibration, not permission to skip the level-check questions.

If you truly need a task completed before calibration, say so explicitly:

```text
$learn-by-inquiry 我想通过探究式学习来学习 LangGraph，但在出题前先帮我确认安装命令
```

In that case, the skill should handle only that pre-calibration task, then immediately return to the usual readiness questions.

## Learning Approach

The skill treats inquiry learning as an evidence-building process:

1. Diagnose the learner's situation and language.
2. Calibrate readiness first when the explicitly invoked request is a new, complex, technical, project, or long-term learning goal.
3. Choose an appropriate inquiry mode.
4. Offer a concrete probe or action menu.
5. Ask the learner to bring back an observation, source note, artifact, or question.
6. Use feedback and formative checks to choose the next probe.

## Visual Companion

When an Inquiry Loop action would be easier to execute visually, the skill may add a lightweight localized prompt such as:

```text
需要我把这个步骤可视化吗？这会多消耗一些 token。
```

If the learner accepts, the skill treats visualization as a short branch from the current action. It preserves the current learning state, supports the action with a flowchart, step diagram, highlighted observation point, or simple click choice when the client allows it, then returns to the original observation question and bring-back instruction.

If a local browser or localhost visual tool is unavailable, the skill should automatically fall back to Mermaid, ASCII, or a concise text diagram instead of interrupting the learning loop.

## Repository Structure

```text
learn-by-inquiry/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- assessment-patterns.md
    |-- inquiry-actions.md
    |-- mode-library.md
    |-- readiness-calibration.md
    `-- research-basis.md
```

## Notes

- This skill is for personal self-directed learning, not classroom curriculum design.
- It supports learning in the user's language.
- It uses direct explanations only as minimal pre-briefing or post-action feedback.
- When recommending exact websites, it prefers official, academic, or stable sources and should verify freshness when needed.
