---
标题: CodeDNA
类型: 实体
创建日期: 2026-04-24
更新日期: 2026-04-24
来源: [karpathy-llm-wiki-gist]
状态: 稳定
---

# CodeDNA

## 是什么

CodeDNA 是由 Larens94 提出的一种方法，将 wiki 指针可选地（opt-in）应用于源文件。

## 核心思想

传统 llm-wiki 中，wiki 和源文件是分离的。CodeDNA 提议在源文件中嵌入指向 wiki 的指针，让源文件和 wiki 之间建立双向链接，而不是仅靠 wiki 单方面引用源文件。

## 与 llm-wiki 的关系

- **互补**：不替代 llm-wiki，而是增强源文件层和 wiki 层之间的连接
- **可选**：指针是可选的，不强制修改所有源文件
- **可追溯**：从源文件可以直接跳转到 wiki 中的相关综合页面

## 链接

- GitHub：github.com/Larens94/codedna

## 相关链接

- [[三层架构]] — CodeDNA 修改的是层间关系
- [[OpenWiki]] — 另一个实现思路

> 来源：[[karpathy-llm-wiki-gist]]
