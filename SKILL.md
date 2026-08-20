Exit code: 0
Wall time: 0.7 seconds
Output:
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

## Source-grounded lessons

When beginning a new chapter or genuinely new concept, inspect a source anchor before substantive teaching: prefer a learner-named source, then a well-known university course, then an authoritative textbook, scholarly organization, or primary academic publication. Consult GitHub only for relevant teaching or workflow design and only when it has at least 1,000 stars or similarly strong institutional maintenance; stars never establish factual authority. State the source and scope in the lesson contract and retain durable citations in `sources.md`.

## Lesson contracts and mastery checks

For a lesson grounded in a named course, textbook, or problem set, distinguish a short diagnostic warm-up from the source-based lesson. Before substantive teaching, state the source and scope (and whether it is direct or an aligned scaffold), one outcome, the challenge, and an observable completion standard. End by checking that standard and record any remaining uncertainty.

Do not call success on a transparent warm-up “mastery” of a larger unit. When the learner finds the task too easy, increase difficulty promptly with richer source data, underdetermined cases, or justification—not repetitive examples.

## Retrieval briefs

When the learner selects text or asks to find supporting material, turn the current learning state into a compact **retrieval brief**. This is a lightweight teaching aid, not a requirement to build or maintain a RAG system.

Build the brief from the selected text (if any), `_learning/CURRENT.md`, the active chapter, the learner's demonstrated level, and any named source scope. Include only the concept and likely textbook terms or synonyms, the immediate question and desired level, preferred sources, useful exclusions, and the desired evidence (definition, example, data, exercise, or page-level explanation).

- **“生成检索简报 / 压缩为检索关键词”**: show the brief and suggested Chinese/English queries; do not search yet.
- **“检索此段”**: use the brief to search lawful, authoritative public material and return a small complementary set with direct sources.
- **“在教材库检索此段”**: search only a learner-named and currently accessible source or folder. Narrow to likely chapters or pages first; do not assume access to a private library or obtain unauthorized copies.

Treat learner constraints as evidence rather than literal keywords: preserve synonyms and textbook terminology. Retrieve the smallest sufficient set, normally 2–5 passages or sources, with page/section locators when available. Record only durable citations or source decisions in `sources.md`; never paste a whole textbook chapter into notes or ongoing context.

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

When the learner says they are ending today's learning, pausing, or continuing later, record durable chapter progress and then overwrite `_learning/CURRENT.md` with one compact end-of-session alignment. Do not rewrite it after every small exchange; create the same handoff before context becomes unwieldy.

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

