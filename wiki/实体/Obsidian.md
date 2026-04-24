---
标题: Obsidian
类型: 实体
创建日期: 2026-04-24
更新日期: 2026-04-24b
来源: [karpathy-llm-wiki-gist, obsidian-local-ai-knowledge-base-guide]
状态: 稳定
---

# Obsidian

## 是什么

Obsidian 是一款基于本地 Markdown 文件的知识管理工具，卡帕西推荐将其作为 llm-wiki 的 IDE。

## 在 llm-wiki 中的角色

> "Obsidian 是 IDE；LLM 是程序员；wiki 是代码库。"

- **IDE 类比**：你用 Obsidian 浏览 wiki，就像程序员用 IDE 浏览代码
- **实时反馈**：LLM 编辑 wiki 时，你在 Obsidian 中实时看到变化
- **图形视图**：查看 wiki 形状的最佳方式——节点和连线可视化知识结构

## 关键特性

| 特性 | 对 llm-wiki 的价值 |
|------|-------------------|
| 双链 `[[]]` | 原生支持 wiki 的交叉引用 |
| 图形视图 | 可视化知识网络结构 |
| 本地文件 | Wiki 就是文件夹，LLM 可直接读写 |
| 插件生态 | [[Dataview]] 等增强查询 |
| Web Clipper | 网页文章转 markdown，便于摄取来源 |

## 与 AI 的天生契合

Obsidian 之所以成为 llm-wiki 的最佳搭档，有三个深层原因：

1. **数据主权完全交还给用户**：笔记以纯文本 Markdown 格式保存在本地，不存在任何云端锁定
2. **网状知识结构**：通过双向链接功能建立网状知识拓扑结构，与 wiki 的交叉引用理念天然一致
3. **本地 AI 可直接操作**：本地 AI Agent 可直接读取、分析和修改 Markdown 文件，无需 API 中转

## 实战搭建步骤

1. 下载 Obsidian 并创建 AI 知识库文件夹
2. 使用支持本地文件的 AI Agent（如 [[WorkBuddy]]、Claude Code 等）打开该文件夹
3. 让 AI 学习卡帕西的 LLM Wiki 教程并搭建目录结构
4. 分屏使用：左边 LLM Agent，右边 Obsidian 实时浏览

## 推荐设置

- 分屏使用：左边 LLM agent，右边 Obsidian
- 配置附件文件夹路径（图片本地化）
- 启用图形视图
- 安装 [[Dataview]] 插件

## 相关链接

- [[QMD]] — 另一个推荐的本地搜索工具
- [[WorkBuddy]] — 支持本地文件的 AI Agent
- [[三层架构]] — Obsidian 处于 Wiki 层的浏览端

> 来源：[[karpathy-llm-wiki-gist]]、[[obsidian-local-ai-knowledge-base-guide]]
