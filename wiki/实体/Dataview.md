---
标题: Dataview
类型: 实体
创建日期: 2026-04-24
更新日期: 2026-04-24
来源: [karpathy-llm-wiki-gist]
状态: 稳定
---

# Dataview

## 是什么

Dataview 是 [[Obsidian]] 的插件，可以对页面的 frontmatter 运行查询，类似数据库查询。

## 在 llm-wiki 中的用途

- 根据 frontmatter 中的 `类型`、`状态`、`来源` 等字段筛选页面
- 统计各类页面的数量和状态
- 发现缺失 frontmatter 的页面
- 生成动态的内容列表

## 示例查询

```dataview
TABLE 状态, 更新日期
FROM "llm-wiki/wiki"
WHERE 类型 = "概念"
SORT 更新日期 DESC
```

## 相关链接

- [[Obsidian]] — Dataview 运行于 Obsidian 之上
- [[三种操作|健康检查]] — Dataview 可辅助健康检查

> 来源：[[karpathy-llm-wiki-gist]]
