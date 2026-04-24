# 日志 — LLM Wiki 操作日志

> 只追加的时间线记录。每个条目以 `## [日期] 操作类型 | 标题` 格式开头。
> 可用 `grep "^## \[" log.md | tail -5` 快速查看最近 5 条记录。

---

## [2026-04-24] 摄取 | Karpathy llm-wiki Gist

- **来源**：`sources/karpathy-llm-wiki-gist.md`
- **操作**：初始摄取，创建 wiki 基础结构
- **新增页面**：
  - `wiki/概念/增量知识编译.md`
  - `wiki/概念/三层架构.md`
  - `wiki/概念/三种操作.md`
  - `wiki/概念/RAG对比LLM-Wiki.md`
  - `wiki/概念/持久复合产物.md`
  - `wiki/概念/Memex传统.md`
  - `wiki/实体/安德烈·卡帕西.md`
  - `wiki/实体/Obsidian.md`
  - `wiki/实体/QMD.md`
  - `wiki/实体/Marp.md`
  - `wiki/实体/Dataview.md`
  - `wiki/实体/OpenWiki.md`
  - `wiki/实体/Sparks.md`
  - `wiki/实体/CodeDNA.md`
  - `wiki/比较/RAG对比LLM-Wiki.md`
  - `wiki/概览/个人知识管理.md`
  - `wiki/概览/LLM-Wiki生态系统.md`
- **更新页面**：`index.md`（初始创建）
- **备注**：首次搭建，从单一来源派生全部初始页面

## [2026-04-24] 维护 | 全面汉化

- **操作**：将整个 wiki 汉化为中文
- **变更内容**：
  - 目录重命名：concepts→概念, entities→实体, comparisons→比较, overviews→概览
  - 文件名全部改为中文（专有名词保留原文）
  - Frontmatter 字段改为中文（title→标题, type→类型, created→创建日期, updated→更新日期, sources→来源, status→状态）
  - 状态值改为中文（stable→稳定, draft→草稿, needs-review→待审核）
  - 所有页面正文内容中文化
- **备注**：保持 Obsidian 双链兼容性
