# Readiness Calibration

Use this reference before teaching new topics, complex concepts, research/project starts, technical source material, or any request where the learner's prerequisite level may change the path.

Calibration is not an exam. It finds a productive starting point and prevents the assistant from assigning tasks far above the learner's current reach.

## When to Calibrate

Run readiness calibration when:

- The learner starts a new topic.
- The topic normally requires prerequisites, such as code, math, research methods, theory, or domain vocabulary.
- The learner asks for papers, source code, architecture, proofs, or advanced applications.
- The learner provides technical material and asks to understand it.
- The learner wants a long-term inquiry roadmap.

Use lightweight calibration for quick confusion repair, review, or follow-up questions. Do not stop a simple question with a full interview.

## Default Calibration Flow

Ask three kinds of questions before choosing depth:

1. **Goal/use case**: "What do you want to be able to do with this topic?"
2. **Prerequisite background**: "What related tools, concepts, math, code, or readings have you already used?"
3. **Domain-specific calibration**: Ask 1-3 questions that reveal whether the learner can work at the requested level.

After the learner answers, state:

- readiness level,
- recommended starting point,
- scaffold strength,
- first inquiry action.

## Readiness Levels

| Level | Signal | Start here | Avoid |
| --- | --- | --- | --- |
| `novice` | Missing core prerequisites or cannot parse basic vocabulary | Intuition, concrete examples, observations, simple artifacts | Papers, formal math, code-first tasks |
| `foundation` | Knows some prerequisites but cannot apply them reliably | Structured examples, guided comparisons, small experiments | Open-ended research tasks too early |
| `working` | Can apply core ideas with support | Inquiry tasks, source snippets, code walkthroughs, transfer cases | Over-explaining every step |
| `advanced` | Can reason with formalism, code, papers, tradeoffs, and evidence | Open inquiry, critiques, replications, design choices | Reducing everything to basics |

## Scaffold Control

Adjust support each turn based on the learner's response.

- **High scaffold**: analogy, vocabulary unpacking, worked micro-example, one-step probe, narrow observation task.
- **Medium scaffold**: hints, contrasts, partial examples, guided transfer, bounded source reading.
- **Low scaffold**: open inquiry, counterexamples, source/code/paper critique, experiment design, independent synthesis.

Raise or lower support by one level when the learner's response shows ease, confusion, missing prerequisites, or strong transfer.

## Transformer Calibration Example

If the learner wants to understand Transformer architecture, calibrate before explaining attention or assigning paper/code reading.

Ask a small set such as:

1. What do you want to do with Transformers: read papers, use libraries, implement one, or understand the intuition?
2. Can you read basic Python or PyTorch code? Give a rough yes/no and one example of code you have read.
3. Are vectors, matrices, dot products, and loss functions familiar enough that you can use them, or only words you have seen?
4. In your current words, what do you think attention or Q/K/V is trying to accomplish?

Route based on answers:

- If code and math are weak, start with token-to-vector intuition, similarity, and attention as weighted information gathering.
- If math is workable but code is weak, start with diagrams, tensor shapes, and a small numerical attention example.
- If code is workable but theory is weak, start with a minimal implementation or annotated library call.
- If both are strong, use the original paper, implementation comparisons, ablations, or failure modes.

## Output Template

Use this shape after calibration:

```text
Readiness: foundation
Why: you know basic neural-network vocabulary, but Q/K/V and dot products are not stable yet.
Starting point: attention as similarity-weighted retrieval, before multi-head attention.
Scaffold: high -> medium if the first probe goes well.
Next probe: [15-30 minute inquiry action]
Bring back: [specific observation/artifact/question]
```
