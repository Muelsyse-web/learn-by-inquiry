# Learn by Inquiry

`learn-by-inquiry` is a Codex skill for action-first inquiry-based learning. It helps self-directed learners calibrate their readiness, investigate questions, and learn through concrete actions such as experiments, source reading, AI interviews, artifact production, and formative feedback.

The skill is designed to avoid the common drift from inquiry learning into guided tutoring. Instead of defaulting to "explain first, then ask questions", it helps the learner do something that produces evidence, observations, or an artifact.

## What It Does

- Calibrates learner readiness before new or complex topics.
- Checks prerequisites before assigning code, math, papers, or advanced terminology.
- Routes learning requests into modes such as new-topic onboarding, confusion repair, material exploration, question shaping, transfer practice, and formative assessment.
- Offers inquiry action menus with concrete next probes.
- Builds long-term inquiry roadmaps from large goals, broken into 15-30 minute probes.
- Supports side AI interviews through Codex `/side`, Claude Code `/btw`, or copyable prompts for other AI tools.

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

Invoke the skill explicitly:

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

## Learning Approach

The skill treats inquiry learning as an evidence-building process:

1. Diagnose the learner's situation and language.
2. Calibrate readiness when the topic is new, complex, or technical.
3. Choose an appropriate inquiry mode.
4. Offer a concrete probe or action menu.
5. Ask the learner to bring back an observation, source note, artifact, or question.
6. Use feedback and formative checks to choose the next probe.

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
