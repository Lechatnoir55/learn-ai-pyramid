# Changelog

## 2.2.0 — 2026-09-23
- Skill 重命名：`learn-ai-explain` → `learn-ai-pyramid`（目录名 + frontmatter `name:` + 触发命令 `/learn-ai-pyramid`）。
- 配置路径同步迁移：`~/.learn-ai-explain/config.json` → `~/.learn-ai-pyramid/config.json`（本机原配置未创建，无数据需迁移）。
- 助记由 `pex` 改为 `pyr`；保留 2.1.0「pex 仅作助记」历史条目不改写。
- mindmap 白板输出文件名前缀同步改为 `learn-ai-pyramid-whiteboard-<slug>.html`。

## 2.1.0 — 2026-09-23
- `SKILL.md` frontmatter 新增 `version` 与 `allowed-tools`：元数据层锁死「不调 API、不需要 key、无 scripts」的硬约束。
- 修正触发命令：文档内 `/pex` 一律改为真实可用命令 `/learn-ai-explain`（pex 仅作助记标签，不重命名 skill）。
- 新增 `references/modes/_examples/concise-sample.md`：端到端成品样例（取材→草稿→审计→定稿），补最大缺口。
- `references/pyramid-audit.md`：审计格式改为强制引用原文；新增「熔断」段（同批最多重写 3 轮，超限低调标注未通过项）。
