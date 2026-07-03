# chenbao — 需求文档

> 版本: 0.1.0 | 日期: 2026-07-03 | 状态: approved

## 1. 概述

### 1.1 目标
搭建高性能、低维护成本的个人博客「chenbao」，支持技术文章与生活随笔，支持读者互动。

### 1.2 范围

**包含 (11 项):** 文章列表+详情、标签/分类、全文搜索、评论(Giscus)、RSS订阅、图片优化、友链、暗色模式、关于页、SEO优化、响应式

**不包含:** 用户系统、CMS后台、付费订阅、多语言、在线编辑器

## 2. 功能需求 (11项) + 非功能需求

详见原始版本（本次对话 CLARIFY 阶段产出）。

## 3. 技术选型

| 项 | 决策 |
|---|---|
| 框架 | Astro 7 (SSG) |
| 样式 | CSS 自定义属性 + 暗色模式 |
| 内容 | Markdown + Content Collections |
| 搜索 | Pagefind (extended 中文分词) |
| 评论 | Giscus (GitHub Discussions) |
| 部署 | GitHub Pages (Actions CI/CD) |
| SEO | @astrojs/sitemap + 自建 OG/JSON-LD |
