# ai-prompts

AI 常用提示词清单 —— 沉淀日常对 AI 说的常用指令，随用随取。

## 内容

| 文件 | 说明 |
| --- | --- |
| [`ai-prompts.md`](./ai-prompts.md) | Markdown 版，适合在编辑器 / 仓库中维护与追加 |
| [`ai-prompts.html`](./ai-prompts.html) | 单文件 HTML 版，浏览器打开即可，每段提示词带「复制」按钮 |

## 已收录

1. 任务交接与续接（长任务换窗口，`HANDOFF.md`）
2. 帮我做完并按清单验收
3. Review 当前工作区改动
4. GitHub 项目搜索（`github-idea-finder` 技能）
5. 运行测试

后续新增话术会同步追加到 MD 与 HTML 两个文件，并更新文件内的「收录记录」。

## 远程仓库

本仓库同时镜像到两个平台，执行一次 `git push` 会推送到两边：

- GitHub：<https://github.com/icecolaa/ai-prompts>
- Gitee：<https://gitee.com/ice-colaa/ai-prompts>

同步机制：`origin` 配置了两个 push 地址，`git push` 会依次推送。推送顺序为 Gitee 在前、GitHub 在后；若其中一个平台推送失败，Git 会中止并且不再推另一个平台，请留意命令退出码与报错。

```bash
git add -A
git commit -m "更新提示词"
git push          # 同时推送 Gitee + GitHub
```
