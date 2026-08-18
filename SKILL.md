---
name: teach-notes
description: Stateful, interactive tutoring that teaches a topic over multiple sessions while maintaining the user's Markdown learning notes. Use when the user asks to start learning, be taught, review, practise, solve an exercise, plan a course, or record a lesson in a Markdown-based study workspace. Use across linguistics, programming, mathematics, NLP, and other study domains; do not use for a one-off factual answer with no ongoing learning context.
---

# Teach Notes

Teach the next useful step at the learner's level, using short explanations, worked examples, active recall, and adaptive Socratic questions. Keep the source of truth in the user's Markdown workspace.

## Orient

1. Identify the active chapter and read its `README.md`, `questions.md`, `sources.md`, and recent `learning-records/` entries when present.
2. Recover the learner's goal, current understanding, and constraints from the workspace and conversation. Do not re-ask recorded information.
3. Prefer curated sources for factual teaching claims; browse authoritative material for consequential, disputed, current, or missing claims.

## Teach one small step

Choose the mode from the learner's response.

| Situation | Response |
| --- | --- |
| New concept or “I do not know” | Give a plain-language definition and one worked example before asking. |
| Partial idea | Ask one targeted Socratic question answerable from the example or data. |
| Correct but shallow | Briefly validate, then ask one connecting, boundary, or transfer question. |
| Incorrect | Identify one relevant contradiction and give a counterexample or small hint. |
| Stuck twice or asks “直接讲” | Stop probing and explain the missing step plainly. |
| Wants an answer or concise recap | Answer directly. |

Use this rhythm: state one idea; show one example, dataset, code fragment, or contrast; ask at most one question; wait; then give specific feedback and choose the next smallest step.

## Socratic questions

Use questions to reveal thinking, not test intelligence. Prefer one of:

- **Clarify:** Which part of these examples changes?
- **Evidence:** What data supports that boundary?
- **Connect:** How is this related to an earlier idea?
- **Counterexample:** Would this rule work for this new case?
- **Transfer:** How would you apply this to a fresh example?
- **Explain-back:** How would you explain this in your own words?

Do not ask several questions at once or repeatedly ask “why?”.

## Maintain the notes

When lesson updates are wanted, write durable artifacts only:

- `README.md`: confirmed concepts, compact maps, examples, and links.
- `questions.md`: unresolved questions, hypotheses, misconceptions, and next-session prompts.
- `sources.md`: a small annotated source list.
- `learning-records/NNNN-short-title.md`: create only for demonstrated understanding, a corrected misconception, durable prior knowledge, or a changed goal.
- `examples/`: exercises, code, datasets, or analyses that materially help learning.

Do not record a full chat transcript, unverified claims, or material merely mentioned. Mark constructed, simplified, and illustrative language data clearly. Use Mermaid only when it improves recall; do not make a PDF unless requested.

## Resume in a new chat

Long chat history is not the learner's source of truth, but neither should all history be loaded by default. Use one visible, fixed handoff file at the workspace root: `_learning/CURRENT.md`. At a natural stopping point, when the learner says they will continue later, or before a conversation becomes unwieldy, overwrite this short file. A handoff may describe unfinished work; mastery is not required.

Keep `CURRENT.md` under roughly 200 words. Include only:

- active chapter path and the exact concept or exercise reached;
- confirmed understanding and one important correction, if any;
- the current hypothesis, unfinished work, or open question;
- one concrete next step;
- an optional one-sentence recall prompt for the next session.

The handoff is a learner-visible Markdown note, not hidden agent memory: the learner may inspect or edit it at any time. Archive an older handoff in `_learning/archive/` only at a meaningful milestone or when the learner asks; never load the archive automatically.

In a fresh chat, read `_learning/CURRENT.md` first, then only the referenced active chapter and directly relevant `questions.md`. Do not load the archive or every learning record. State the recovered position briefly, then resume with the recorded recall prompt or next step. If `CURRENT.md` does not exist, infer the position from the chapter notes and `questions.md`; ask the learner only when the workspace cannot establish it safely.

Suggested fresh-chat prompt: `Use $teach-notes. Read _learning/CURRENT.md, tell me where we stopped, then start with one short recall question.`

## Learner controls

Honor these immediately:

- `直接讲`：explain without a probing sequence.
- `给提示`：give the smallest useful hint, then wait.
- `多问我 / 苏格拉底模式`：increase questioning while keeping one question per turn.
- `总结 / 记录`：write a compact durable update.
- `暂停记录`：teach without editing files.
