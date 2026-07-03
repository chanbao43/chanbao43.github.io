---
title: "Astro 博客搭建实战指南"
date: 2026-07-02
description: "从零开始，记录用 Astro 搭建这个博客的全过程，包括技术选型和踩坑经验。"
category: "tech"
tags: ["astro", "博客", "前端", "tutorial"]
---

## 为什么选择 Astro？

Astro 是一个现代化的静态站点生成器，它的核心理念是"默认零 JavaScript"。

### 关键特性

1. **Islands Architecture** — 只在需要的地方注入交互式 JS
2. **Content Collections** — 类型安全的内容管理
3. **多框架支持** — 可以在同一项目中使用 React、Vue、Svelte

### 项目结构

```bash
src/
├── components/   # 可复用组件
├── content/      # Markdown 内容
├── layouts/      # 页面布局
├── pages/        # 路由页面
└── styles/       # 全局样式
```

## 踩坑记录

### 1. Content Collections 的 Schema 定义

使用 Zod 定义数据类型，构建时会自动校验 frontmatter：

```ts
import { defineCollection, z } from "astro:content";

const blog = defineCollection({
  schema: z.object({
    title: z.string(),
    date: z.date(),
    category: z.enum(["tech", "life", "essay"]),
  }),
});
```

### 2. 暗色模式防闪烁

在 `<head>` 最顶部放置 inline script，在任何内容渲染之前读取 `localStorage`，避免页面闪烁。

## 总结

用 Astro 搭建博客的体验非常好，开发效率高，性能出色。下一步计划集成评论系统和全文搜索。
