# AI 常用提示词清单

> 用途：沉淀日常对 AI 说的常用指令（提示词模板），随用随取。
> 维护方式：后续新增内容直接追加到「新增提示词模板」之前，并同步更新同名 HTML 文件 `ai-prompts.html`。
> 最后更新：2026-09-12 02:13
> 每条提示词均记录录入时间，便于追溯新增与修订。

---

## 目录

1. [任务交接与续接（长任务换窗口）](#1-任务交接与续接长任务换窗口)
2. [帮我做完并按清单验收](#2-帮我做完并按清单验收)
3. [Review 当前工作区改动](#3-review-当前工作区改动)
4. [GitHub 项目搜索（技能调用）](#4-github-项目搜索技能调用)
5. [运行测试](#5-运行测试)
6. [新增提示词模板](#6-新增提示词模板)
7. [收录记录](#7-收录记录)

---

## 1. 任务交接与续接（长任务换窗口）

> 记录时间：2026-09-12 02:13

**适用场景**：当前任务窗口上下文过多、即将超出容量，需要开新窗口继续，避免丢失进度。

**第一步 · 让当前窗口交接（复制以下内容发送）：**

```text
当前任务窗口内容过多。请：
1. 记录当前任务的完整过程与关键结论；
2. 总结经验、踩坑点与下一步计划；
3. 把这些内容写入项目根目录的 HANDOFF.md，确保新窗口只读该文件即可无缝继续。
```

**第二步 · 在新窗口开场（直接发送）：**

```text
读取 HANDOFF.md，继续任务。
```

---

## 2. 帮我做完并按清单验收

> 记录时间：2026-09-12 02:13

**适用场景**：功能开发/修改完成后，要求 AI 自测并逐项验收，避免「口头完成、实际没跑通」。

```text
“帮我做完并按清单验收”：
• 每个按钮都点击一遍；
• 用正常、空值、超长内容各测试一次；
• 检查移动端与网页端；
• 把错误、复现步骤和截图写进报告；
• 只有全部通过，才标记完成。
```

---

## 3. Review 当前工作区改动

> 记录时间：2026-09-12 02:13

**适用场景**：改动完成后做一次代码审查，先列问题再动手修。

```text
请 review 当前工作区的改动。
重点检查：
- 是否有明显 Bug。
- 是否破坏已有功能。
- 是否有未使用变量或调试代码。
- 是否需要补充测试。
请先给出问题列表，再直接修改文件。
```

---

## 4. GitHub 项目搜索（技能调用）

> 记录时间：2026-09-12 02:13

**适用场景**：想找某个产品/功能的开源替代品或竞品，用 `github-idea-finder` 技能做多轮检索与证据核验。
一句话触发：`使用技能来通过 git 搜索相关项目`。

**1. 创建搜索会话**

```bash
python scripts/github_discovery.py session `
  --state-file work/github-idea-session.json `
  --idea "完整产品，类似当前项目的有 GUI、可独立运行的通用 AI Agent，支持工具调用和多步骤任务" `
  --max-rounds 4 `
  --max-searches 30 `
  --max-inspections 50
```

**2. 执行第一轮搜索**

```bash
python scripts/github_discovery.py search `
  --state-file work/github-idea-session.json `
  --query "open source AI agent" `
  --query "desktop AI agent" `
  --query "self-hosted autonomous agent" `
  --query "AI agent tool execution" `
  --query "AI agent task planning" `
  --topic ai-agent `
  --topic ai-assistant `
  --fetch-limit 30
```

**3. 检查候选项目**

```bash
python scripts/github_discovery.py inspect `
  --state-file work/github-idea-session.json `
  --repo owner/repo `
  --repo another-owner/another-repo
```

**4. 根据 README 证据继续搜索**

```text
open source cowork desktop in:readme
local-first AI agent workspace in:readme
computer-use agent desktop in:readme
agent harness desktop app in:readme
multi-agent workforce desktop in:readme
```

**5. 运行测试**（在 scripts 目录执行）

```bash
python -m unittest discover -s scripts -p "test_*.py" -v
```

---

## 5. 运行测试

> 记录时间：2026-09-12 02:13

**适用场景**：快速跑一遍项目单测。

```text
在 scripts 目录执行：
python -m unittest discover -s scripts -p "test_*.py" -v
```

---

## 6. 新增提示词模板

> 以后要收录新的一句话指令时，复制下面的空模板填写即可（MD 与 HTML 同步添加）。

```markdown
## N. 标题

**适用场景**：一句话说明什么时候用。

**提示词：**

```text
（在此粘贴要对 AI 说的原文）
```
```

---

## 7. 收录记录

| 日期 | 时间 | 新增内容 |
| --- | --- | --- |
| 2026-09-12 | 02:13 | 初版：任务交接、验收清单、代码 Review、GitHub 搜索、运行测试 |
