Exit code: 0
Wall time: 0.7 seconds
Output:
# Teach Notes / 笔记私教

**English** · **中文**

`teach-notes` is a Codex skill for long-running learning. It turns a Markdown workspace into a lightweight learning loop: recover where the learner stopped, teach one small step, use adaptive Socratic questions, retrieve only the material needed for the current question, and preserve durable notes for the next session.

`teach-notes` 是一个面向长期学习的 Codex skill：它把 Markdown 工作区变成轻量学习闭环——恢复上次进度、小步教学、苏格拉底式提问、按当前问题检索少量资料，并把真正学会的内容沉淀到下一次仍能接上的笔记中。

## What it does / 它做什么

- **Teach at the right level:** a new concept gets a plain definition and one worked example before any question; partial understanding gets one focused question.
- **Small, adaptive Socratic dialogue:** clarify, evidence, connection, counterexample, transfer, and explain-back prompts reveal reasoning without turning the lesson into an interrogation.
- **Maintain useful notes:** write confirmed concepts to `README.md`, open questions to `questions.md`, sources to `sources.md`, and meaningful progress to short learning records.
- **Protect learning quality:** do not save full chat transcripts or unverified claims; clearly label constructed or simplified data.
- **Create retrieval briefs:** turn selected notes plus the current learning state into focused Chinese/English source queries; inspect the brief first, search public sources, or constrain a search to a named accessible textbook folder.
- **Set lesson contracts:** for source-based lessons, state the source scope, outcome, challenge, and observable completion standard; separate a diagnostic warm-up from demonstrated mastery.
- **Ground new topics in sources:** anchor a new chapter or concept in a named source, university course, or authoritative academic material; GitHub is workflow inspiration only, never factual authority.
- **End cleanly:** when the learner stops for the day, update durable notes and one compact handoff rather than relying on chat history.

- **按水平教学：** 新概念先给清晰定义和一个例子，再提问；有部分理解时只问一个聚焦问题。
- **小步苏格拉底对话：** 使用澄清、证据、连接、反例、迁移、复述等问题理解思路，而不是“拷问”。
- **维护有用笔记：** 已确认概念进入 `README.md`，未解决问题进入 `questions.md`，来源进入 `sources.md`，重要进步才写入简短学习记录。
- **保护笔记质量：** 不保存完整聊天记录或未经验证的结论；构造或简化数据会明确标记。
- **生成检索简报：** 将选中的笔记和当前学习状态压缩为中英文查询、同义术语、难度与范围；可先查看简报，再检索公开资料，或限制在指定且可访问的教材资料夹中检索。

## Learning loop / 学习闭环

```text
Current learning state + selected note
        ↓
Retrieval brief (optional)
        ↓
Small, source-aware lesson
        ↓
One question, worked example, or practice task
        ↓
Durable Markdown notes + next-session handoff
```

The skill is intentionally not a heavyweight RAG system. It keeps the working context small by retrieving the smallest useful set of passages rather than loading whole books or chat histories.

该技能刻意不是重型 RAG 系统：它只取当前问题真正需要的少量资料，而不会把整本教材或全部聊天历史塞进上下文。

## Install / 安装

Copy this folder as `teach-notes` into your Codex skills directory:

将本文件夹以 `teach-notes` 为名称复制到 Codex 的 skills 目录：

```text
~/.codex/skills/teach-notes/
```

On Windows this is usually / Windows 通常是：

```text
C:\Users\<your-user-name>\.codex\skills\teach-notes\
```

Restart or refresh Codex, then say / 重启或刷新 Codex 后，可以说：

```text
Use $teach-notes to teach me from my current chapter and update the learning notes.
```

## Learner controls / 学习者控制语句

`直接讲` · `给提示` · `多问我 / 苏格拉底模式` · `总结 / 记录` · `暂停记录` · `生成检索简报` · `压缩为检索关键词` · `检索此段` · `在教材库检索此段`

## Continue in a new chat / 在新聊天中继续

Long conversations should not be the only memory. The skill maintains one short, visible `_learning/CURRENT.md` file (about 200 words): current chapter, confirmed understanding, unfinished question or exercise, one next step, and an optional recall prompt. It reads this file—not the whole archive—when a new chat starts.

长对话不应成为唯一的记忆来源。技能会维护一份简短、可见的 `_learning/CURRENT.md`（约 200 词）：当前章节、已确认理解、未完成问题或练习、下一步和可选回忆题。新聊天只读这一份，不会自动载入全部历史。

Start the next conversation with / 下次新开聊天时直接说：

```text
Use $teach-notes. Read _learning/CURRENT.md, tell me where we stopped, then start with one short recall question.
```

## License and attribution / 许可证与来源

This skill is independently written and released under the [MIT License](LICENSE). Its open-source teaching-design influences, licenses, and a statement that no prose or code was copied verbatim are in [ATTRIBUTIONS.md](ATTRIBUTIONS.md).

本技能独立编写，以 [MIT License](LICENSE) 发布。其开源教学设计参考、各自许可证，以及“未逐字复制代码或文字”的说明均见 [ATTRIBUTIONS.md](ATTRIBUTIONS.md)。

