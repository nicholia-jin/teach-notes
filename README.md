# Teach Notes / 笔记私教

**English** · **中文**

`teach-notes` is a Codex skill for long-running learning. It adapts between concise explanation and Socratic questions, then keeps the learner's durable knowledge in a Markdown workspace.

`teach-notes` 是一个面向长期学习的 Codex skill：它在简洁讲解与苏格拉底式提问之间自适应切换，并把已确认的知识持续整理到 Markdown 学习笔记中。

## What it does / 它做什么

- **Teach at the right level:** a new concept gets a plain definition and one worked example before any question; partial understanding gets one focused question.
- **Small, adaptive Socratic dialogue:** clarify, evidence, connection, counterexample, transfer, and explain-back prompts reveal reasoning without turning the lesson into an interrogation.
- **Maintain useful notes:** write confirmed concepts to `README.md`, open questions to `questions.md`, sources to `sources.md`, and meaningful progress to short learning records.
- **Protect learning quality:** do not save full chat transcripts or unverified claims; clearly label constructed or simplified data.

- **按水平教学：** 新概念先给清晰定义和一个例子，再提问；有部分理解时只问一个聚焦问题。
- **小步苏格拉底对话：** 使用澄清、证据、连接、反例、迁移、复述等问题理解思路，而不是“拷问”。
- **维护有用笔记：** 已确认概念进入 `README.md`，未解决问题进入 `questions.md`，来源进入 `sources.md`，重要进步才写入简短学习记录。
- **保护笔记质量：** 不保存完整聊天记录或未经验证的结论；构造或简化数据会明确标记。

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

`直接讲` · `给提示` · `多问我 / 苏格拉底模式` · `总结 / 记录` · `暂停记录`

## License and attribution / 许可证与来源

This skill is independently written and released under the [MIT License](LICENSE). Its open-source teaching-design influences, licenses, and a statement that no prose or code was copied verbatim are in [ATTRIBUTIONS.md](ATTRIBUTIONS.md).

本技能独立编写，以 [MIT License](LICENSE) 发布。其开源教学设计参考、各自许可证，以及“未逐字复制代码或文字”的说明均见 [ATTRIBUTIONS.md](ATTRIBUTIONS.md)。

